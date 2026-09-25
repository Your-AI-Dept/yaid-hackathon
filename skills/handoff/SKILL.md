---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up. Use when the user types /handoff, asks for a handoff, or wants to carry the work into a fresh session.
argument-hint: "What will the next session be used for?"
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save it as `HANDOFF.md` in the folder you are working in, replacing any earlier one, so the user can find it again.

Include a "suggested skills" section in the document, naming which skills the next agent should call the Skill tool for.

Do not duplicate content already captured in other artifacts (specs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.

Finish by telling the user, in one line, what to type in a fresh session to pick the work back up, for example: "Read HANDOFF.md and pick up where we left off."
