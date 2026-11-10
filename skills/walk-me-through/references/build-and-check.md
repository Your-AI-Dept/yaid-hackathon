# Build a real, checkable first app

## Interview in the participant's language

Use the context already supplied. Ask the next question that would change the build rather than every question below:
- What is the problem today, in their words?
- What should be different once it works? That is the goal, which is not the same as the output.
- Do they already picture a solution? It is fine if not.
- What recurring job should this make easier, and who does it?
- What real input starts the job? Where is it, and can this session access it?
- What would the person normally produce or decide?
- Which rule would make an otherwise plausible answer wrong?
- What should the app be allowed to change, and who reviews the result?
- Which recent example has a result the participant can check?

If they skip questions, proceed using explicit, reversible assumptions where possible. Ask only for indispensable missing information. For example, do not guess a rule that would change a price or send a message to a customer. Accept an existing use case, requirements document, or interview output (such as a grillme summary) as the starting point.

Produce a short plan in ordinary language and call it "your plan". Open with three lines in their words: **Problem**, **Solution** and **Goal**. Ask for the problem and goal as open questions, not as options with a recommended answer; offer an example only if they are stuck. If they have no solution in mind, propose one and label it "Suggested". The goal is what changes for them ("walk into Monday's meeting knowing who owes what"); the output is what the app hands them ("a task list with owners and dates"). Then fill in the rest of the layout below, which is also the layout for a grillme closing summary, and mention the first user under Goal or Later when it matters. Put later features in one short sentence. Show the plan and build once they say go. Use a separate requirements document only when complexity or the participant's request makes it useful.

```text
Problem:
Solution: (theirs, or "Not sure yet. Suggested: ...")
Goal:
Input:
Output:
Rules:
Actions:
First check:
Later:
```

## Implement the requested app

The agent performs the build using available tools. A proposed prompt is useful when moving between environments, but is not completion of an authorized build in a capable environment.

Choose the smallest complete workflow: an understandable input control, useful processing, visible results, necessary saving, and a way to run it again. Avoid unnecessary accounts, frameworks, APIs, or connectors. Do not remove a connection the participant actually needs just to simplify the demo; establish the real prerequisite and resolve it or offer a transparent temporary alternative.

Default to the shapes participants already learn in YAID sessions. A **skill** they can re-run with new input (for example `/chase-invoices`) keeps the AI work inside Claude, so there are no API keys or servers to manage; save it in the project's `.claude/skills` folder so it stays with the project. Writing there asks permission even in Accept edits, so warn them first. Save results as a **file** in the project folder (a spreadsheet, a Word document, a page), or publish them as a shareable **artifact** when they want a link. Use a **routine** only when they want it to run on a schedule. Build a coded app only when the job truly needs one, and say what that adds: something that must be running, and an API key if it calls AI itself. Prefer files Claude can read and write without extra tools, such as CSV, plain text and simple web pages (it can also read PDFs and images), so the app needs nothing installed. Excel and Word files usually mean Python and an add-on (see [stuck](stuck.md)).

Use the participant's real files or authorized read access. Ask them to select files when access is unavailable. Do not search their entire computer or download whole accounts for convenience. Preserve originals and identify generated outputs separately.

If the app requires AI at runtime, distinguish the assistant building it from the model service the finished app calls. Never imply the participant's chat subscription automatically funds or authenticates an app's API calls. Verify available authentication and usage options. Keep secrets out of source files, browser code, screenshots, progress notes, and shared prompts.

## Verify business behavior

Check a real example with a participant-known correct outcome. Then check a different real example when available. Do not invent a ground truth. If no expected answer exists, ask the participant to inspect a small result and label the check as review, not demonstrated accuracy. Never substitute a dummy-data exercise without their agreement.

Show the relevant source beside important extracted facts or decisions. Separate missing information from "not applicable." For research, show sources and uncertainty. For calculations, verify arithmetic and supplied business rules. A polished interface is not evidence of correctness.

If an output is wrong, inspect the input, rule, extraction, or calculation responsible. Update the implementation or instructions and rerun the same case to prove the correction. Explain the change in the participant's terms. Do not merely instruct the model to be more accurate.

For saved state, verify an edit survives a reload and an appropriate stop/reopen cycle. Explain actual limits: browser-only storage, a file on one device, or a database are different. Check the real data location and backup/export option when loss would matter. Do not claim team readiness from a single-person preview.

## Let the participant finish the loop

At the first useful version:
1. Open the actual output or running app through an available mechanism.
2. Let the participant check a meaningful result or request a small change.
3. Give a precise return path and what must be running. A skill saved during this session appears only in a new one, so to prove it reopens, have them start a new session in the same folder and run it once before they leave. If it fails there, the folder's instructions bring this guide back.
4. Save the progress note under the rules in [progress](progress.md).
5. Write the take-home page (below), or update it if it exists. Do it again when they say "wrap up".

Report separately: built, checked, participant-reviewed, and still unverified. Avoid invented completion percentages. If a test cannot run in this environment, preserve the work and name the remaining check.

## The take-home page

Save it in the project folder as `What I built.md`, in their words, not yours. It is for them and for whoever picks the work up later. Cover:
- **Problem, Solution and Goal**, from the plan, updated to what was actually built. Say plainly whether the goal was met.
- **What it does**, in three or four sentences a colleague could follow.
- **How to use it again**: exactly what to open and what to type.
- **What it needs**: which files, systems and fields.
- **The rules it follows**: every judgment call built into it. These are the things they know and nobody else does.
- **What has been checked**, and what is still unverified.
- **Where it falls short**: anything faked, skipped or hardcoded to fit the time. Be specific and honest.
- **What a full version would need**: access, connections, people, scale.

End with this line: "Your AI Department builds full versions of tools like this. youraidept.com". It is the only place the guide mentions YAID without being asked. Leave client names, figures and message contents off the page, because it may be shared. Offer to publish the page as a shareable artifact if they want to show it; do not publish without their yes. The page doubles as their notes for show-and-tell.

At wrap-up, keep the chat short: whether the goal was met, where the page is, and the next step. The page holds the detail, so skip a separate **Your app so far** summary unless they ask for one.
