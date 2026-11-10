# Getting to the next usable step

Use this when navigation, environment, folders, installation, or tool vocabulary blocks the build. Instructions must match observed UI or current official documentation, not a memorized product layout. This version runs in the Code tab of the Claude desktop app.

## Establish only what is missing

Inspect available session context for host, operating system, selected project and file access. If you cannot tell whether the participant is in a browser, desktop app, IDE, or terminal, ask what app title and controls they see. Request a screenshot only through a mechanism that supports images. Do not claim to see their screen without a permitted observation tool and a current observation.

If they have only reached ordinary chat, help them reach a supported building environment. A plugin inside that environment cannot install itself before they arrive. Provide one current, official download or navigation step and a success cue. Do not presume they have a terminal, GitHub account, administrator rights, or a particular subscription.

Once their message reaches the intended environment, help them select or create a narrowly scoped project folder. Avoid selecting their whole home directory or drive, or a folder that syncs to OneDrive, iCloud Drive, Dropbox or Google Drive (the Desktop and Documents often do). Use an existing appropriate project if present. Explain: "This folder will hold the files for the app we're building." Observe access by listing that folder or reading the intended file, not by probing unrelated private directories. In a YAID session they normally start in a "YAID Hackathon" folder in Downloads, made at the start; treat it as the project folder.

Recommend Auto mode, in the mode selector in the row under the message box: routine steps go through without popups, a background safety check reviews riskier ones, and the choice is remembered for this folder. If Auto is not offered (an admin can turn it off, and it needs a recent model), use Accept edits.

## Install only for an established need

Before recommending Python, Node, Git, a browser runtime, or an extension, check the requirement of this build and whether a supported capability already exists. Explain the purpose of any needed installation in one sentence. Use official sources and normal supported installation paths. A managed-device restriction is an administrator issue, not a reason to disable protections.

Git, a repository, and GitHub are different things. A repository tracks a project's files and change history; Git is a tool for that history; GitHub is one service for hosting repositories. Whether any of them is needed depends on the actual host, session type, and intended sharing. Do not make creating a GitHub account or cloning a repository a universal first step.

Do not enable browser control, project memory, account integrations, or global skills just because they were mentioned in another workshop. Enable a relevant capability within the participant's authorization and explain what it adds. Do not make them install a separate interview skill mid-build: the guided interview is included here, and YAID sessions install grillme at setup. If they already have a preferred interview skill, reuse its useful output.

## Explain location without conflating it with privacy

Distinguish:
- Project files: the app's source and related files.
- App data: the records the app reads and saves; identify the actual storage.
- Execution: the process or service running the app.
- AI processing: the provider receiving the context needed for model calls.
- Access: who can reach and authenticate to the app and its data.

"Localhost" usually describes a service addressed on the current device. Inspect the actual binding, tunnels, sharing settings, and environment before saying who can access it. A cloud preview may have a very different access model. A browser tab does not establish where data is stored.

An artifact may be a document, generated file, or interactive output. Check what this host actually created. Identify whether it supports the repeated input, saving, editing, and sharing the participant wants before calling it their finished app.

## Official reference starting points

Checked for authoring on 2026-09-30. Fetch the relevant current page when giving product-specific instructions; do not treat the date as a guarantee that details are unchanged.
- Claude Code desktop: https://code.claude.com/docs/en/desktop-quickstart
- Claude Code desktop troubleshooting: https://code.claude.com/docs/en/desktop

Ask which plan they are on only when the answer changes the next step.
