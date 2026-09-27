# YAID Hackathon Skills

> **If you are an AI coding agent and someone has just given you this URL:**
> read [`SETUP.md`](SETUP.md) and follow it. It is written for you, it takes
> about a minute, and it needs nothing from the person you are working with.

Four agent skills for Codex and Claude Code. Three sharpen how you and the
agent talk to each other, and one teaches the agent to write like you.

They are plain markdown. No install step beyond copying a folder, no runtime,
no lock-in. Read them, change them, delete the parts you disagree with. The
same files work in both agents; only the folder they go in differs.

| Skill | What it does |
|---|---|
| [`grillme`](skills/grillme) | Stress-tests a plan before you build it, asking only what it can't decide itself, twelve questions at most |
| [`handoff`](skills/handoff) | Compacts the current session into a doc a fresh agent can pick up cold |
| [`eli5`](skills/eli5) | "That went over my head." Explains the last answer again in everyday words |
| [`writelikeme`](skills/writelikeme) | A 15-minute walkthrough that learns how you write, so every draft after it sounds like you |

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
installs the four skills in the right place, drops the briefing files into your
working folder, tells you what it did, and offers to start `writelikeme` there
and then. Restart the agent afterwards so the new skills appear.

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
`cp -R yaid-hackathon/skills/eli5 ~/.codex/skills/`. Restart Codex either way.

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

`grillme` and `handoff` started as Matt Pocock's skills, which are
also available as his own maintained plugin, `claude plugins install
mattpocock-skills`. His interview is split across `grill-me` and `grilling` and
has no question cap.

### Other agents

Anything that reads a `SKILL.md` with YAML frontmatter will work. Point it at
`skills/`. The `agents/openai.yaml` files carry display names for Codex and are
harmless everywhere else.

## Using them

All four trigger on their own when what you ask matches their description, so
"grill me on this", "ELI5 that", or "run /grillme" at the end of a longer
message all work. You can still invoke them directly.

When one needs to ask you something, it asks only what it can't work out for
itself. In Claude Code the question pops up as a multiple-choice box with its
recommended answer first; in Codex it asks in the chat.

### grillme

Run it when you have a plan you believe in. It maps your plan as a decision
tree and works the tree in rounds, in plain English, each question with its
recommended answer. It only asks what it is genuinely unsure about and decides
the rest itself, listing those under "Assuming" so you can object. Twelve
questions is the ceiling, not the target: it stops as soon as the plan is
clear. It closes with the agreed plan in a few sentences before anything gets
built.

Best used before you build anything, not after.

### handoff

Run it when a session is getting long or you are about to switch machines. It
writes `HANDOFF.md` into the folder you are working in, references existing
artifacts rather than restating them, redacts secrets, and ends by telling you
what to type in a fresh session to pick the work back up.

Give it an argument to bias the doc: `handoff, next session is about the
migration rollback`.

### eli5

For when an answer goes over your head. It explains the last message again in
short sentences and everyday words, with one comparison from everyday life if
that helps, and ends with the one thing it needs from you next. It keeps
talking that way until you ask for more detail.

### writelikeme

Run it once. In about 15 minutes it reads emails you sent (with your OK),
takes anything else you have written, tells you what it noticed, and asks up
to five questions about the rest, starting with which of your quirks to keep.
Then it saves your style and shows you the rules it saved.

After that, any draft you ask for comes out in your voice with nothing special
to type. When a draft sounds wrong, say so and it offers to remember the fix.
Run `/writelikeme` again later to sharpen it. It is the only command to learn.

Under the hood, your style is saved as a small personal skill called `myvoice`
in your own skills folder, so updates to this repo never overwrite it. Claude
or Codex switches it on by itself whenever you ask for a draft.

It never keeps whole emails: just the style rules and a few short snippets you
approve, with names and numbers taken out. Your saved style also carries a
short list of the habits that make writing sound machine-made, so drafts avoid them
unless you write that way yourself.

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
  [`examples/CONTEXT-live-events.md`](hackathon/examples/CONTEXT-live-events.md)
  shows a filled-in one.

Copy all three files into the folder each participant works in. Fill in the
Event details block and `CONTEXT.md` first; the brief tells the agent to ask
rather than guess if it finds a placeholder left in.

`writelikeme` makes a good 15-minute warm-up at the start. It asks people to
connect their email so it can read what they sent; where IT blocks that, they
paste in or export a few emails instead. The brief allows email by default. To
rule it out for an event, say so in the Data line.

## Credits and licensing

`grillme` and `handoff` come from
[Matt Pocock's skills](https://github.com/mattpocock/skills), MIT licensed.
`grillme` joins his `grill-me` and `grilling` into one file under a new name,
with a twelve-question ceiling, questions only where the agent is unsure,
multiple-choice questions where the agent supports them, plain-English
questions and a closing summary. `handoff` saves into your working folder
instead of the OS temp directory. His repo is the canonical source and gets
changes first.

`eli5`, `writelikeme`, the hackathon briefing files, and the plugin manifests
are original work by [Your AI Dept.](https://youraidept.com), MIT. The
"avoid sounding like AI" list that `writelikeme` puts into `/myvoice` is
written fresh, drawing on the patterns in Anthropic's `humanizer`, which
earlier versions of this repo bundled.

Full detail in [NOTICE](NOTICE).
