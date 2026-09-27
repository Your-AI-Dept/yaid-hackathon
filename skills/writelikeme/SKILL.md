---
name: writelikeme
description: Teach the agent how the user writes, in a guided walkthrough of about 15 minutes that reads emails they sent and anything else they share, asks a few questions, and builds them a personal /myvoice skill so future drafts sound like them. Use when the user types /writelikeme, says "write like me", "learn how I write", "teach Claude my style", or wants drafts to sound like them.
---

You are going to learn how this person writes, then leave behind a skill called
`myvoice` that makes every future draft sound like them. They are not
technical. Do the work yourself, say in a line or two what you did after each
step, and keep the whole thing to about 15 minutes.

## Asking questions

Only ask what you cannot work out yourself. When you do ask, ask one question at
a time with your recommended answer. If you have a multiple-choice question
tool (AskUserQuestion in Claude Code), use it: your recommendation first,
marked "(Recommended)", 2 to 4 options in total, and no "Other" option of your
own, since the tool adds one. Otherwise ask in chat.

## Step 1. Say what is about to happen

Three or four plain sentences, then start:

- It takes about 15 minutes.
- You will read emails they sent (their words only, not what other people sent
  them), plus anything else they want to share.
- What you keep is a short description of how they write and a few short
  snippets they approve, with names and numbers taken out. Never whole emails.
- You won't send, reply to, move or delete anything. The result is one file on
  their computer.

If `myvoice` already exists (see Step 5 for where), read it first and tell them
you will sharpen it rather than start over.

## Step 2. Read emails they sent

**If an event brief is in this folder** (`AGENTS.md` or `CLAUDE.md`) and its
Data line rules out email, skip to the fallback below.

**If you can see a tool that reads their email** (Gmail, Outlook, Microsoft
365), ask once for the go-ahead, then read about 40 of the most recent emails
they sent. Search their sent mail, not their inbox. Skip forwards, one-line
replies, meeting responses, automated messages, and emails that are mostly a
quoted thread. Read only what they wrote, not the quoted text underneath. Aim
for a spread of recipients: clients, their own team, people outside the
company.

**If there is no email tool**, offer to connect one. In Claude that is
Settings, then Connectors, then Gmail or Microsoft 365. It may only appear in a
new chat, so if it doesn't show up, tell them to start a new chat and type
/writelikeme again. Work accounts sometimes need IT to approve it. If you are
not Claude, or you don't know the steps in the app they are using, don't guess:
use the fallback.

**Fallback.** If connecting is blocked, takes more than a couple of minutes, or
they would rather not, ask for 5 to 10 emails they sent, to a mix of people.
They can paste them in, or save them into a folder on the desktop and tell you
its name. That is plenty.

Read only. Never send, reply to, draft, label, move or delete anything.

## Step 3. Ask for anything else they wrote

Ask once whether they have anything else they wrote themselves: LinkedIn
posts, a memo, a speech, a newsletter. They can drag files into the chat or
paste text. If they have nothing to hand, move on.

Use only what they wrote. Pieces someone else drafted for them teach the wrong
voice, so if they aren't sure who wrote something, leave it out.

## Step 4. Work out their style, then check it with them

Look for:

- How they open and close: greeting, sign-off, name, initials, or nothing.
- Length: how long emails and sentences run, and how fast they get to the point.
- Tone and formality, and whether it changes with the audience.
- Words and phrases they use often, and ones they never use.
- Punctuation and layout: exclamation marks, dashes, emoji, lists or paragraphs.
- How they ask for things, say no, give bad news and say thanks.
- Quirks: typos, all lowercase, phone-style one-liners, a signature phrase.

Tell them what you noticed in three or four plain lines, written about them,
not as a report: "You get to the point in the first line. You sign off 'Best,'
to clients and just your initial to your team."

Then ask up to five questions, only about what the samples can't settle. Start
with the quirks: for each one you spotted, ask whether to keep it or drop it.
The aim is their real voice minus anything they'd be embarrassed to see in an
important email. After that, ask about gaps, such as how they want to sound in
kinds of writing you have no samples of, or words they can't stand. Five is a
ceiling. Stop as soon as you know enough.

## Step 5. Build myvoice

Save it in their own skills folder, never inside the folder `writelikeme` came
from, which can be replaced when it updates:

- **Claude Code:** `~/.claude/skills/myvoice/SKILL.md` (on Windows,
  `%USERPROFILE%\.claude\skills\myvoice\SKILL.md`)
- **Codex:** `~/.codex/skills/myvoice/SKILL.md` (on Windows,
  `%USERPROFILE%\.codex\skills\myvoice\SKILL.md`)
- **Anything else:** its own skills folder. If you don't know where that is,
  ask.

Fill in the template at the end of this file:

- **Rules** are short and concrete, one habit per line, written as
  instructions: "Open with the answer, then the reason."
- **By audience** only where the samples showed a real difference. Otherwise
  delete that section.
- **Snippets:** pick 3 to 5 short ones, a sentence or two each, that sound
  most like them. Swap every name, company, number, date and deal detail for a
  placeholder like `[client]` or `[amount]`. Show them and let them keep or
  drop each one. Keep a whole email only if they pasted it in themselves and
  say it's fine to keep.
- **Avoid sounding like AI:** copy the list as written, then delete any line
  that contradicts how they actually write.

If `myvoice` already exists, merge: keep what is still true, add what is new,
and change a rule only when the new samples or their answers contradict it.
Tell them what changed.

## Step 6. Show them, then hand over

Show the style summary: the rules as saved, in plain English, short enough to
read in a minute. Ask if anything is off, and fix it in the file.

Then tell them, in two or three sentences:

- From now on, when they ask for a draft (an email, a reply, a post), it comes
  out in their voice with nothing special to type. Typing /myvoice with some
  text rewrites that text in their voice.
- If a draft sounds wrong, they just say so, and it will offer to remember the
  fix.
- It may need a new chat, or a restart, before it switches on.

## The myvoice template

Replace everything in square brackets. `[Name]` is their first name.

````markdown
---
name: myvoice
description: Write in [Name]'s own voice. Use whenever [Name] asks you to draft, write, reply to or rewrite an email, message, post, memo or anything else that will go out under their name, or types /myvoice.
---

# How [Name] writes

Use this for anything [Name] will send or publish as themselves. Don't use it
for your own replies to them. If they type /myvoice with some text, rewrite
that text in their voice and keep whatever already sounds like them.

## Voice

[One rule per line, from the samples and their answers.]

## By audience

[Only where the samples showed a real difference, e.g. "Clients: warmer, full
sentences, 'Best,' and full name." Otherwise delete this section.]

## Never

[Words they can't stand, quirks they asked to drop.]

## Sounds like this

[3 to 5 approved snippets, with placeholders for names, companies and numbers.]

## Avoid sounding like AI

The rules above win. If [Name] really does write something on this list, keep it.

- No brochure enthusiasm or stacked superlatives. Say what is good and what isn't.
- Don't default to lists of three. Use one example, or two, or four.
- No dashes to tack on an afterthought unless [Name] uses them. Use a comma, a
  full stop or a colon.
- Cut filler and buzzwords: "it's worth noting", "in today's fast-paced world",
  "leverage", "robust", "seamless", "delve", "game-changer".
- Use "and", "but" and "so", not "Moreover", "Furthermore" and "However".
  Paragraphs don't need bridges between them.
- No "It's not just X, it's Y." Say what it is.
- No vague authority like "experts agree" or "studies show". Name the source or
  make it [Name]'s own view.
- Keep ordinary things ordinary. No journeys, landscapes or pivotal moments.
- Don't open a sentence with an "-ing" phrase like "Reflecting on" or
  "Highlighting".
- Never invent facts, numbers or examples. Mark a gap `[check]` or ask.
- No summary at the end and no rousing call to action. Stop when the point is made.
- Match [Name]'s formality. Don't add slang or chattiness to sound human.

## Getting better

When [Name] edits a draft you wrote, or says something like "I'd never say
that", ask once: "Want me to remember that for next time?" If yes, add one
short rule to the right section of this file, [full path to this file]. If it
was a one-off for that email, leave the file alone. Never change this file
without their yes.
````
