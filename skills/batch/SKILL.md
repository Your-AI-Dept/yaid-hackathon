---
name: batch
description: Apply one instruction across many targets (files, tickets, rows, URLs) one at a time, with a manifest, checkpointing, and a results table. Use when the user asks to do the same thing to a list of things ("for each", "across all", "run this on every", "go through these one by one", "bulk update", "sweep").
metadata:
  short-description: Run one instruction across many targets
---

# Batch

Repetitive work fails in predictable ways. The agent starts strong, drifts by item eight, silently skips item twelve, and reports "done" over a job that is two-thirds finished. This skill exists to make that failure mode impossible.

The rule underneath everything here: **the run must be inspectable while it is happening and verifiable after it ends.**

## The Four Phases

### Phase 1. Resolve the target list

Never start from a description of the targets. Start from the targets.

Turn the user's phrasing ("all the API route files", "every ticket labelled `stale`") into an explicit, enumerated list. Use the filesystem, the CLI, the API. Whatever produces ground truth. Then show the user the list and the count, and wait.

```
Resolved 14 targets from `src/api/**/*.ts`:

 1. src/api/auth/login.ts
 2. src/api/auth/logout.ts
 ...
14. src/api/webhooks/stripe.ts

Proceed on all 14?
```

Two things to watch for, because both are common and both are silent:

- **The glob is wrong.** If the count is surprising (3 when the user expected 30, or 300 when they expected 30) say so before running anything.
- **The list is heterogeneous.** If some targets are clearly a different shape than the rest, flag them. They are where the batch will break.

If the batch is destructive or outward-facing (deleting, publishing, sending, force-pushing), confirmation here is mandatory, not optional. One bad instruction times 200 targets is a very bad afternoon.

### Phase 2. Write the manifest

Create a work directory outside the user's project. The OS temp directory is the right home for it.

```
$TMPDIR/batch-<short-slug>/
  manifest.md      # the instruction, the target list, the acceptance test
  results.jsonl    # one line appended per completed target
```

`manifest.md` holds:

- **The instruction**, written once, in full. Every target gets this exact text. Do not paraphrase it per item. Paraphrasing is how drift starts.
- **The target list**, numbered.
- **The acceptance test**: how you will know a single target succeeded. Be concrete. "Typechecks and the old import is gone" is a test. "Looks right" is not.

The manifest is the contract. If you find yourself wanting to change it mid-run, stop and talk to the user instead.

### Phase 3. Process, one target at a time

For each target, in order:

1. Read the target fresh.
2. Apply the instruction from the manifest, meaning the text in the manifest, not your memory of it.
3. Run the acceptance test.
4. Append one line to `results.jsonl`:
   ```json
   {"n": 3, "target": "src/api/auth/session.ts", "status": "ok", "note": "3 call sites updated"}
   ```
5. Move on.

Four rules govern this loop:

**Isolate each target.** What you learned on target 3 does not entitle you to assume anything about target 4. A pattern that held for the first six files is a hypothesis about the seventh, not a fact.

**Never batch-edit across targets.** A single regex swept over all 14 files is not this skill. It is the thing this skill exists to replace. It cannot run an acceptance test per target, and it fails as one indivisible unit.

**A failure stops that target, not the run.** Record `{"status": "failed", "note": "<what broke>"}` and continue. Exception: if three consecutive targets fail, stop and report. The instruction itself is probably wrong, and grinding through 40 more failures helps nobody.

**Checkpoint honestly.** `results.jsonl` is appended after the acceptance test, never before. A line in that file means the work is actually done.

Where the agent supports parallel sub-agents, fan out, but only when targets are genuinely independent (no shared files, no ordering dependency, no shared lock). Each sub-agent gets the manifest and exactly one target. Same acceptance test, same result line. Parallelism changes the scheduling, never the contract.

### Phase 4. Report

End with a table, built from `results.jsonl`, not from recollection.

```
Batch complete: 12 ok, 1 failed, 1 skipped (14 total)

| #  | Target                        | Status  | Note                          |
|----|-------------------------------|---------|-------------------------------|
| 1  | src/api/auth/login.ts         | ok      | 2 call sites updated          |
| 7  | src/api/webhooks/stripe.ts    | failed  | no matching handler signature |
| 9  | src/api/legacy/v1.ts          | skipped | file is generated             |
```

Then, in order:

1. **Lead with the failures.** They are the only rows anyone needs to act on.
2. **State the skips and why.** A skipped target that goes unmentioned reads as a completed one.
3. **Give the resume path.** Name the manifest path and the target numbers still outstanding, so a fresh session can pick the job up cold.

Never report a batch as complete when any target failed or was skipped. Say what happened. The whole point of the manifest is that you do not have to guess, and neither does the user.

## When Not To Use This

- **Fewer than three targets.** Just do the work.
- **The instruction differs per target.** That is not a batch, that is a list of tasks. Handle them individually.
- **The targets are ordered and interdependent**, each one's output feeding the next. That is a pipeline. A batch assumes independence.
