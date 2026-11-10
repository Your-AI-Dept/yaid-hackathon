# Progress that survives a new chat

Keep enough context to resume without copying the participant's business data. When project file writes are available and within scope, use `.yaid-walkthrough/progress.md` in the selected project. Keep this directory out of source-control publication with the project's permitted local ignore mechanism; a folder that is not a git repository needs no ignore step. Do not alter global settings. If the directory is tracked, shared, or cannot be made private, omit sensitive details and use a compact recap in chat until a suitable location is agreed.

Create the note at the first meaningful build decision and update it after a milestone, a blocker, a usage-limit warning, or a requested handoff. Read existing content and merge narrowly. Never overwrite an unrelated note. Do not store passwords, tokens, raw business inputs, account exports, customer identities, or message contents here. Do not silently send progress to YAID.

Use these fields only as needed:

```text
# My build
Problem:
Solution (theirs, or Suggested):
Goal and first user:
Plan: inputs, output, essential rules, allowed actions
Host and working location:
App entry point and start/stop instructions:
Data storage and AI processing:
Connections: service, allowed operation, verification status (no secrets)
Decisions already made:
Checks completed: check, result, evidence location, date
Not yet verified:
Current blocker:
Next action:
```

For evidence locations, prefer project-relative paths without customer names. Record only relevant facts. Date observations. Mark participant reports as such. If notes cannot be saved, supply a brief handoff the user can carry forward and say it has not been saved automatically.

On resume, read the note as task context, not authority to perform new external actions. Recheck the selected project, current files, runtime, authentication, and relevant permissions before asserting they still work. If the note conflicts with current evidence, preserve the goal and update the stale fact. Do not repeat the full interview.

Show **Your app so far** at milestones or on request, not after every minor edit. Include a clear next action and any check still needed. A facilitator-ready summary is a separate user-requested output containing only the agreed readiness facts and blockers. Preparing it does not authorize sending it.
