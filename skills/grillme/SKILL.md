---
name: grillme
description: Interview the user about a plan before anything gets built, asking only what it can't decide itself, with a recommended answer for each and 12 questions at most. Use when the user types /grillme, says "grill me", or wants a plan, decision, or idea stress-tested before work starts.
---

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask the frontier in one round, or as much of it as the budget allows: number each question and give your recommended answer. Then wait for the user's answers before the next round.

Only ask what you are genuinely unsure about: a real judgment call, a preference, or context only the user has. If you would confidently pick one answer and the user would likely agree, don't spend a question on it; decide it and list it under **Assuming**. A round can be a single question.

The **budget** is 12 questions at most for the whole session, counted across every round, not per round. It is a ceiling, not a target: most plans need far fewer, and you stop as soon as the plan is clear. Number questions continuously (Q1, Q2 and so on) so the count never restarts. When the frontier holds more questions than you have left, ask the ones whose answers would change the plan most or unblock the most downstream decisions, and list the rest under **Assuming** with the answer you are taking as given, so the user can object without spending a question. Pace it: a first round that spends the whole budget leaves nothing for the decisions that only open up once the user has answered.

Ask in plain English. The user may know their own business in depth and never have written a line of code, so leave out jargon; when a technical choice matters, put it in terms of what it changes for them.

If you have a multiple-choice question tool (AskUserQuestion in Claude Code), ask each round through it: up to four questions per call, the Q number in each question, your recommended answer as the first option marked "(Recommended)", 2 to 4 options per question with the trade-off in each option's description, and no "Other" option of your own, since the tool adds one. Otherwise, format a round in chat like so:

```
❓ **Q1** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>

---

❓ **Q2** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Each round the user answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open in this round belongs to a _later_ round, not this one.

Finding _facts_ is your job, never the user's. When a frontier question needs a fact from the environment (filesystem, tools, etc.), dispatch a sub-agent to find it; don't ask the user for anything you could look up yourself. Don't block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for the sub-agent to report; ask the rest of the frontier now. The _decisions_ are the user's: put each to them and wait.

The session is done as soon as nothing you are unsure about is left, or the budget is spent: every branch of the design tree either settled by the user or covered by a stated assumption, nothing left silently assumed. If the budget runs out with the frontier still open, do not ask another question; list every open decision with the answer you are assuming for it. Either way, finish with the agreed plan in a few plain sentences, and do not act on it until the user confirms you have reached a shared understanding.
