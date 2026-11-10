# From a personal app to shared use

Use this only when the participant asks to share, deploy, schedule, or roll out the app, or when their stated use case requires it. Do not make a solo first build complete a company rollout checklist.

## Share the right thing

Clarify whether the user means sharing instructions, copying the app's code, sharing input/output files, or inviting someone into a running app. Check the host's actual behavior. Do not imply that sharing a skill grants the recipient the creator's account access, or that copying code copies a working authenticated service.

For shared app use, establish the intended audience and authentication, actual data storage, account identity for integrations, and who can read or change what. Test access with appropriate separate identities when available. If that test cannot be performed, label access controls unverified. Never claim tenant isolation from a screenshot or a login form alone.

Prepare the requested deployment up to a concrete reviewable result. Check existing authorization before the publishing step. Explicitly requested publishing can authorize publishing the intended app, but not accidentally bundling private source documents, credentials, or workshop materials. Inspect the deployable files and public data paths.

A domain, GitHub repository, and hosting account are choices to justify from the actual deployment path, not mandatory purchases. Explain what stops working when a local machine sleeps or an app closes. Verify the real platform behavior instead of promising permanent uptime.

## Run repeatedly

For a daily or hourly workflow, define the input source, timezone, authorized read/write actions, persistent "already seen" state, duplicate handling, and what constitutes a meaningful new result. Use an available scheduling capability and verify its saved configuration. Never claim scheduling is active merely because a script exists.

Use a manual run with real authorized input first. Check a repeat run for duplicate outputs before enabling external effects. For record matching, preserve uncertain entries for review. Establish where failed runs appear, who responds, how retries stop, and how the participant can pause the schedule. Do not send notifications or messages to other people without authorization.

## Address company restrictions concretely

For sensitive HR, client, or regulated information, investigate the actual product, plan, execution environment, connected identity, retention, training-use settings, and available audit events relevant to the task. Do not certify compliance. If company approval is genuinely required, prepare a precise administrator brief: purpose, system, requested operations, identity, data involved, unresolved control, and proposed verification. Continue other authorized work while that issue is pending.

Explain maturity with evidence: a preview can demonstrate the workflow; shared use additionally needs appropriate access, durable data, error handling, and an operating owner. Recommend implementation help for a concrete unresolved need, without promising that the guide itself provides those services.
