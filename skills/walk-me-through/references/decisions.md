# Explain decisions and troubleshoot connections

Load the relevant part when the participant encounters a decision. Answer briefly, then return to their app.

## Approvals

Inspect the exact operation, affected files or system, identity, destination, and permission duration. Explain what it would do in plain language. Recommend the narrowest sufficient option when the available choices are known. Use existing task authorization for ordinary reversible work; do not invent a new approval checkpoint for every tool call.

Keep materially different actions separate: reading selected files, changing project files, installing software, connecting an account, creating drafts, sending messages, editing business records, deleting data, spending money, and publishing. Approval for one is not evidence of approval for another. Before an action with a new external effect, check whether it was already authorized in this session; ask only for what remains missing.

Most popups come from your own next step, so you know what they will ask. Before that step, say in one line what the popup will ask, what it does, and which choice to pick. Describe the choice by what it does ("allow it this once") unless you have seen the button's exact label. Auto mode runs many steps without asking, so when you are not sure a popup will appear, say they may see one. If they decline one, treat it as a no: say in one sentence what it was for, then offer a way that does not need it, or try again only if they now want to.

Sign-in and consent screens from other services, such as Microsoft or Google, are not yours to predict word for word. Say what kind of screen to expect, and if it asks for more than the task needs, ask them to read it out before they accept.

Never recommend "allow everything" as a general fix. If the prompt is not visible, ask for its exact wording and target rather than guessing whether it is safe. Do not click a user's sign-in or authorization consent on their behalf where the host requires their interaction. Never ask them to paste a password or token into chat.

If a downloaded skill or installer is involved, inspect its origin, instructions, scripts, hooks, and declared connections before recommending use. A trusted-looking name or marketplace listing is not proof of the behavior of its code. Stay proportional to the actual action.

## Connections: purpose, identity, action, evidence

Explain a connector as permission for this environment to interact with a particular service. For the current task, determine:
- The available integration and the account or workspace it uses.
- The exact operations needed: search, read, create a draft, update, send, or delete.
- The granted scope and organizational restrictions, if observable.
- Evidence from one appropriately scoped operation.

Discover installed tools before proposing a new integration. A service appearing in a plugin list does not prove authentication or a working operation. Reading messages does not prove draft creation is supported. A tool description is not proof that the current account has access.

For a failed connection, distinguish unsupported operation, expired authentication, missing scope, workspace policy, wrong account, absent records, and transient failure. Inspect the actual error. Do not respond to every failure by requesting wider access or reinstalling. For the known fixes, and for what to do when access stays blocked, read [stuck](stuck.md).

For an explicit "do not write to the CRM" request, use only read operations. Where available, verify read-only credentials or enforce a tool allowlist. If write-capable credentials cannot be narrowed, disclose that the connection itself is broader than requested; do not call it technically read-only. For a strict read-only connection requirement, offer an approved export or have the administrator provision restricted access. Do not test permissions by writing and deleting a dummy record.

## Research and matching

An empty result can mean no matches, failed access, an unsupported source, a bad filter, or incomplete coverage. Check those before saying no such people or companies exist. Do not bypass access controls or anti-automation measures. Offer an authorized API, user-provided export, or permitted supervised browsing route as appropriate; a headless browser is not an automatic solution.

For lists compared with CRM records, establish matching rules. Check normalized names, aliases, acronyms, office locations, firm moves, and stable identifiers only where the real evidence supports them. Keep uncertain matches in a review list. "Net New" means no match found in the accessible records under the stated rules; do not imply a search covered an inaccessible or incomplete database.

Human review precedes CRM mutations when the participant requests it. Keep review decisions and source evidence separate from any later write step. Do not turn approving a review list into permission to send outreach.

## Models, effort, context, and cost

Use current official documentation and any actual account controls available. Recommend one appropriate available model and starting effort for this task, with a short reason. Preserve an explicit model choice. Do not burden a beginner with a full model comparison or silently change their settings.

Explain tokens as units of text or other content processed by a model. Distinguish context capacity, subscription usage limits, and metered API costs. Do not equate a token count with a specific bill or claim that an operation is free. Show measured usage only when accessible, and say when it is not. Inspect before recommending a paid service or higher-cost setting; obtain missing spending authorization for a concrete proposal.

Reduce unnecessary work by carrying the plan and concise progress forward, reading targeted files, and resolving a repeated error before another attempt. A new chat should receive a handoff, not rely on an assumption of shared memory. A fresh context, saved project, skill, and durable app data serve different purposes.

Official starting point, checked during authoring on 2026-09-30:
- Claude Code documentation: https://code.claude.com/docs/en/overview

Fetch the exact relevant current page for product guidance. For third-party permissions and integrations, use that provider's documentation and the observed account state. Do not provide legal or regulated-data assurances from generic product descriptions.
