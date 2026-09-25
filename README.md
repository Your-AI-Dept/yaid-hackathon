# YAID Hackathon Skills

> **If you are an AI coding agent and someone has just given you this URL:**
> read [`SETUP.md`](SETUP.md) and follow it. It is written for you, it takes
> about a minute, and it needs nothing from the person you are working with.

Six agent skills for Codex and Claude Code. Four sharpen how you and the agent
talk to each other, one cleans up writing, one keeps repetitive work honest.

They are plain markdown. No install step beyond copying a folder, no runtime,
no lock-in. Read them, change them, delete the parts you disagree with. The
same files work in both agents; only the folder they go in differs.

| Skill | What it does |
|---|---|
| [`grillme`](skills/grillme) | Starts a relentless interview that stress-tests a plan before you build it, twelve questions at most |
| [`handoff`](skills/handoff) | Compacts the current session into a doc a fresh agent can pick up cold |
| [`wait-what`](skills/wait-what) | "That last message did not land." Forces a re-pitch in plain language |
| [`eli5`](skills/eli5) | "That went over my head." Explains the last answer again in everyday words |
| [`humanizer`](skills/humanizer) | Strips the twelve patterns that make writing read as machine-generated |
| [`batch`](skills/batch) | Runs one instruction across many targets with a manifest and a results table |

## Which agent are you on?

**Codex** is OpenAI's coding agent: the Codex app, or `codex` in a terminal.
**Claude Code** is Anthropic's: the Code tab of the Claude desktop app, the
`claude` command in a terminal, or the VS Code extension. If you are not sure,
ask the agent itself. It knows what it is, and [`SETUP.md`](SETUP.md) tells it
what to do in either case.

## Install

### The short way

Paste this to your agent:

```
Set me up from https://github.com/Your-AI-Dept/yaid-hackathon
```

It reads [`SETUP.md`](SETUP.md), works out whether it is Codex or Claude Code,
installs the six skills in the right place, drops the briefing files into your
working folder, and tells you what it did. Restart the agent afterwards so the
new skills appear.

Nothing to install first. No GitHub account, no git, no terminal.

### Codex, the explicit way

Ask Codex to install just the skills. Its built-in `skill-installer` reads
straight from this repo:

```
install skills from Your-AI-Dept/yaid-hackathon
```

Pick the ones you want when it asks. Restart Codex afterwards.

To do it by hand instead:

```bash
git clone https://github.com/Your-AI-Dept/yaid-hackathon.git
cp -R yaid-hackathon/skills/* ~/.codex/skills/
```

Drop the `-R yaid-hackathon/skills/*` for a single skill, for example
`cp -R yaid-hackathon/skills/batch ~/.codex/skills/`. Restart Codex either way.

Verify with `ls ~/.codex/skills`. You should see the folders you copied.

### Claude Code, the explicit way

Claude Code has no single-skill installer, so copy the folders:

```bash
git clone https://github.com/Your-AI-Dept/yaid-hackathon.git
cp -R yaid-hackathon/skills/* ~/.claude/skills/
```

Or per-project, into `.claude/skills/` at the repo root. Restart Claude Code,
or run `/reload-plugins` in the session, and the skills appear as `/grillme`,
`/handoff` and so on.

If you would rather subscribe than copy, this repo is also a Claude Code
plugin, and `claude plugin update yaid-hackathon` then brings in changes:

```bash
claude plugin marketplace add Your-AI-Dept/yaid-hackathon
claude plugin install yaid-hackathon@yaid
```

Inside a session the same two steps are `/plugin marketplace add
Your-AI-Dept/yaid-hackathon` and `/plugin install yaid-hackathon@yaid`. Plugin
skills are namespaced, so call them as `/yaid-hackathon:grillme`. Pick the
copy route or the plugin route, not both, or you will have every skill twice.

The Cowork tab of the desktop app and claude.ai on the web take their skills
from your claude.ai account settings, not from `~/.claude/skills`, so add them
there instead.

`grillme`, `handoff` and `wait-what` started as Matt Pocock's skills, which are
also available as his own maintained plugin, `claude plugins install
mattpocock-skills`. His interview is split across `grill-me` and `grilling` and
has no question cap.

### Other agents

Anything that reads a `SKILL.md` with YAML frontmatter will work. Point it at
`skills/`. The `agents/openai.yaml` files carry display names for Codex and are
harmless everywhere else.

## Using them

`wait-what` is set to `disable-model-invocation`, so the agent will not reach
for it on its own. Call it by name, as the first thing in your message.

The other five trigger on their own when what you ask matches their
description, so "grill me on this", "ELI5 that", or "run /grillme" at the end
of a longer message all work. You can still invoke them directly.

### grillme

Run it when you have a plan you believe in. It maps your plan as a decision
tree and works the tree in rounds, asking the questions it can ask now, in
plain English, each with its recommended answer, up to twelve in a session.
When it hits the cap it lists what it is assuming for anything it did not get
to ask. It is not done until nothing is left silently assumed, and it closes
with the agreed plan in a few sentences before anything gets built.

Best used before you build anything, not after.

### handoff

Run it when a session is getting long or you are about to switch machines. It
writes `HANDOFF.md` into the folder you are working in, references existing
artifacts rather than restating them, redacts secrets, and ends by telling you
what to type in a fresh session to pick the work back up.

Give it an argument to bias the doc: `handoff, next session is about the
migration rollback`.

### wait-what

For when the agent has gotten ahead of you. It forces a re-pitch with context,
in Simplified Technical English, using your project's own vocabulary.

It reads `CONTEXT.md` from your repo root for that vocabulary. Without one it
still works, just with less of your language in it. Worth writing.

### eli5

For when an answer goes over your head. It explains the last message again in
short sentences and everyday words, with one comparison from everyday life if
that helps, and ends with the one thing it needs from you next. It keeps
talking that way until you ask for more detail.

`wait-what` does a similar job for people who keep a `CONTEXT.md`. `eli5` needs
nothing set up.

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

[`hackathon/`](hackathon) holds the briefing files for a facilitated session
where the people building are not developers. They are written to work for any
team and any event. The only event-specific part is the Event details block at
the top of the brief, which you fill in.

- [`AGENTS.md`](hackathon/AGENTS.md) is the agent's brief: who it is working
  with, what to assume they know, how to split the time, what to produce, and
  what to leave behind. Codex reads it automatically at the start of every
  session.
- [`CLAUDE.md`](hackathon/CLAUDE.md) is the same brief for Claude Code, which
  reads `CLAUDE.md` rather than `AGENTS.md`. It imports `AGENTS.md`, so there is
  one brief to edit, not two.
- [`CONTEXT.md`](hackathon/CONTEXT.md) is the vocabulary of the participants'
  world, so the agent uses their words from the first message. It is a template
  to fill in before the session, from a survey or a short call with the team.
  `wait-what` reads it directly.
  [`examples/CONTEXT-live-events.md`](hackathon/examples/CONTEXT-live-events.md)
  shows a filled-in one.

Copy all three files into the folder each participant works in. Fill in the
Event details block and `CONTEXT.md` first; the brief tells the agent to ask
rather than guess if it finds a placeholder left in.

## Credits and licensing

`grillme`, `handoff`, and `wait-what` come from
[Matt Pocock's skills](https://github.com/mattpocock/skills), MIT licensed.
`wait-what` is bundled verbatim. `grillme` joins his `grill-me` and `grilling`
into one file under a new name, with a twelve-question cap, plain-English
questions and a closing summary. `handoff` saves into your working folder
instead of the OS temp directory. His repo is the canonical source and gets
changes first.

`humanizer` is by Anthropic, from the `anthropic-skills` plugin, bundled
verbatim.

`eli5`, `batch`, the hackathon briefing files, and the plugin manifests are
original work by [Your AI Dept.](https://youraidept.com), MIT.

Full detail in [NOTICE](NOTICE).
