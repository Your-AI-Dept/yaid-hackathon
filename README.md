# YAID Hackathon Skills

> **If you are an AI coding agent and someone has just given you this URL:**
> read [`SETUP.md`](SETUP.md) and follow it. It is written for you, it takes
> about a minute, and it needs nothing from the person you are working with.

Six agent skills for Codex. Four sharpen how you and the agent talk to each
other, one cleans up writing, one keeps repetitive work honest.

They are plain markdown. No install step beyond copying a folder, no runtime,
no lock-in. Read them, change them, delete the parts you disagree with.

| Skill | What it does |
|---|---|
| [`grill-me`](skills/grill-me) | Starts a relentless interview that stress-tests a plan before you build it |
| [`grilling`](skills/grilling) | The interview engine behind `grill-me`. Required for it to work |
| [`handoff`](skills/handoff) | Compacts the current session into a doc a fresh agent can pick up cold |
| [`wait-what`](skills/wait-what) | "That last message did not land." Forces a re-pitch in plain language |
| [`humanizer`](skills/humanizer) | Strips the twelve patterns that make writing read as machine-generated |
| [`batch`](skills/batch) | Runs one instruction across many targets with a manifest and a results table |

## Install

### The short way

Paste this to your agent:

```
Set me up from https://github.com/Your-AI-Dept/yaid-hackathon
```

It reads [`SETUP.md`](SETUP.md), installs the six skills, drops the briefing
files into your working folder, and tells you what it did. Restart Codex
afterwards so the new skills appear.

Nothing to install first. No GitHub account, no git, no terminal.

### The explicit way

Ask Codex to install just the skills. Its built-in `skill-installer` reads
straight from this repo:

```
install skills from Your-AI-Dept/yaid-hackathon
```

Pick the ones you want when it asks. Take `grill-me` and `grilling` together or
neither. Restart Codex afterwards.

To do it by hand instead:

```bash
git clone https://github.com/Your-AI-Dept/yaid-hackathon.git
cp -R yaid-hackathon/skills/* ~/.codex/skills/
```

Drop the `-R yaid-hackathon/skills/*` for a single skill, for example
`cp -R yaid-hackathon/skills/batch ~/.codex/skills/`. Restart Codex either way.

Verify with `ls ~/.codex/skills`. You should see the folders you copied.

### Claude Code

Same files, different directory:

```bash
cp -R yaid-hackathon/skills/* ~/.claude/skills/
```

Or per-project, into `.claude/skills/` at the repo root.

The four Matt Pocock skills are also available as a maintained Claude Code
plugin, which is the better route if you want updates:

```bash
claude plugins install mattpocock-skills
```

### Other agents

Anything that reads a `SKILL.md` with YAML frontmatter will work. Point it at
`skills/`. The `agents/openai.yaml` files carry display names for Codex and are
harmless everywhere else.

## Using them

`grill-me`, `handoff`, and `wait-what` are set to `disable-model-invocation`,
so the agent will not reach for them on its own. Call them by name.

`grilling`, `humanizer`, and `batch` trigger on their own when the work matches
their description. You can still invoke them directly.

### grill-me

Run it when you have a plan you believe in. It maps your plan as a decision
tree and works the tree in rounds, asking every question it can answer now,
each with its recommended answer. It is not done until nothing is left silently
assumed.

Best used before you write code, not after.

### handoff

Run it when a session is getting long or you are about to switch machines. It
writes a handoff doc to your OS temp directory, references existing artifacts
rather than restating them, and redacts secrets.

Give it an argument to bias the doc: `handoff, next session is about the
migration rollback`.

### wait-what

For when the agent has gotten ahead of you. It forces a re-pitch with context,
in Simplified Technical English, using your project's own vocabulary.

It reads `CONTEXT.md` from your repo root for that vocabulary. Without one it
still works, just with less of your language in it. Worth writing.

### humanizer

Paste in text, or point it at a file. It works through twelve patterns:
promotional tone, rule-of-three, em dash overuse, filler phrases, mechanical
transitions, weasel words, grandiosity, gerund openers, conjunctive adverbs,
negative parallelism, formulaic conclusions, fake specificity.

It edits invisibly. If the output reads as "humanized," it has failed.

### batch

For any "do this to all of these" job. It resolves the target list first and
shows it to you before touching anything, writes a manifest, processes targets
one at a time with an acceptance test per target, and reports a table built
from its own checkpoint file rather than from memory.

The point is that a batch of forty cannot quietly become a batch of thirty-one.

## Running an event with these

[`hackathon/`](hackathon) holds two files for a facilitated session where the
people building are not developers:

- [`AGENTS.md`](hackathon/AGENTS.md) sets the agent's brief. Who it is working
  with, what to assume they know, how long it has, what to produce. Codex reads
  it automatically at the start of every session, so nobody has to remember to
  explain the context.
- [`CONTEXT.md`](hackathon/CONTEXT.md) is the vocabulary of the participants'
  world, so the agent uses their words from the first message. `wait-what` reads
  this file directly.

Copy both into the folder each participant works in. They are written for a
specific event and are meant to be rewritten for yours.

## Credits and licensing

`grill-me`, `grilling`, `handoff`, and `wait-what` are by
[Matt Pocock](https://github.com/mattpocock/skills), MIT licensed, bundled
verbatim. His repo is the canonical source and gets changes first.

`humanizer` is by Anthropic, from the `anthropic-skills` plugin, bundled
verbatim.

`batch` is original work by [Your AI Dept.](https://youraidept.com), MIT.

Full detail in [NOTICE](NOTICE).
