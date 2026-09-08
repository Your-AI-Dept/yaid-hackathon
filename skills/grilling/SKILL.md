---
name: grilling
description: Grill the user relentlessly about a plan, decision, or idea. Use when the user wants to stress-test their thinking, or uses any 'grill' trigger phrases.
---

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled — the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask the whole frontier in one round, or as much of it as the budget allows: number each question and give your recommended answer. Then wait for the user's answers before the next round.

The **budget** is 12 questions for the whole session, counted across every round, not per round. Number questions continuously (Q1 through Q12) so the count never restarts, and end each round with how many questions remain. When the frontier holds more questions than you have left, ask the ones whose answers would change the plan most or unblock the most downstream decisions, and list the rest under **Assuming** with the answer you are taking as given, so the user can object without spending a question. Pace it: a first round that spends the whole budget leaves nothing for the decisions that only open up once the user has answered.

Each question should be formatted like so:

```
❓ **Q1** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Each round the user answers reshapes the tree — settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open in this round belongs to a _later_ round, not this one.

Finding _facts_ is your job, never the user's. When a frontier question needs a fact from the environment (filesystem, tools, etc.), dispatch a sub-agent to find it — don't ask the user for anything you could look up yourself. Don't block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for the sub-agent to report — ask the rest of the frontier now. The _decisions_ are the user's — put each to them and wait.

The session is done when the frontier is empty or the budget is spent: every branch of the design tree either settled by the user or covered by a stated assumption, nothing left silently assumed. If the budget runs out with the frontier still open, do not ask another question; close with every open decision and the answer you are assuming for it. Do not act on it until the user confirms you have reached a shared understanding.
