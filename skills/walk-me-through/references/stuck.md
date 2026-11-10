# Stuck: get them moving again

Use this the moment something blocks the participant: a popup, a sign-in, a connector, a file, a data problem, an install, an error or a limit. Hosts may be in the room, but they cannot reach everyone. Unblock this person in as few turns as you can, then hand back.

## 1. Name it

Say in one plain line, in their terms, what kind of snag this is, so they know it is a known kind of problem. The kinds below are for you, not to read out. Skip this when they are simply asking for something rather than reporting a problem.
- **Popup**: a permission request they do not understand, or one they declined.
- **Access**: a sign-in, a connector that will not connect or cannot do the job, or a file Claude cannot reach.
- **Data**: the information is not anywhere you can get it, or is not in a usable shape.
- **Install**: something needs installing, or an install is blocked.
- **Limit**: a usage or plan limit.
- **Error**: an error message, a wrong result, or going in circles.

## 2. Look before you ask

Check what you can observe first: the exact error text, which connectors and tools this session actually has, which account a connector is signed in as, and whether the file exists and where. Ask only for what you cannot see, such as a popup's wording or what their browser shows. Never ask for a password, code or token.

## 3. Try the known fixes

These match the Claude desktop app's documentation as of October 2026. Use the list as it is during a session. Fetch the current docs (https://code.claude.com/docs/en/desktop and https://code.claude.com/docs/en/errors) only when their screen does not match it, and then trust their screen.

**Popups and modes**
- Most popups come from your own next step; warn first (see [decisions](decisions.md)). In Manual mode, file edits, most commands, reads outside the project folder and web lookups all ask. Auto mode asks far less: a background safety check reviews commands, but the first read outside the project folder still asks.
- The mode selector is in the row under the message box (Cmd+Shift+M on a Mac), and the choice is remembered per folder. Auto is on every plan with a recent model, but a company admin can turn it off; if it is missing, use Accept edits.
- They clicked No: a plain No stops the step. Treat it as a no (see [decisions](decisions.md)). If they typed a reason with it, answer that.
- Auto mode refused a step: it judged the step risky. Say in one line what you were trying to do and take a safer route. After three refusals in a row, Auto pauses and popups come back until one is approved.
- Writing into any `.claude` folder (skills, settings) always asks, even in Accept edits. Warn before saving a skill.

**Connectors**
- The connector is not in your tools, or a call to it fails. If you have the app's connector tools (one reports each connector's status, one switches a connector on for this session, one reconnects a failed one), check its status first and fix what you can yourself:
  - off for this session (disabled): switch it on. Its tools arrive on your next turn, so end the turn by saying what you switched on.
  - failed: reconnect it, end the turn, then check again.
  - needs sign-in (needs_auth): only they can sign in. They type /mcp in this session and sign in there, or click Customize in the sidebar, then Connectors.
  - not listed: they click the + next to the message box, then Add connectors (on some versions Connectors, then Browse connectors), or Customize in the sidebar, then Connectors.

  Without those tools, they open the + next to the message box, then Connectors, where each connector can be switched on for this session. If it still does not appear, start a new session in the same folder.
- On a company Team or Enterprise plan, an owner must switch a connector on for the organization before anyone can sign in to it. If it is not offered, that is for a host and their admin.
- Microsoft 365 says "Need admin approval" or "an administrator must grant app permissions": a Microsoft administrator has to approve Claude once for the whole organization. At a small firm that may be the participant: the page may offer to sign in as an administrator, who can approve for everyone. Some companies show "Approval required" with a button that sends the request to IT. Otherwise nothing they click fixes it. Personal Outlook or Hotmail accounts cannot connect at all. Go to the ladder (step 4), and send them to a host only if they want to chase the approval.
- Microsoft 365 connects but cannot send, draft or change anything: it is read-only unless an administrator turns on its write tools. More permission on their side will not add them. Write the drafts into a file in the project folder instead.
- Google says "Access blocked: your institution's admin needs to review Claude": their Google Workspace administrator has to mark Claude as trusted. Handle it like the Microsoft case.
- Gmail asks for approval before sending, replying or forwarding. That is expected, not a fault.
- An organization owner can block individual connector actions. In the desktop app a blocked action is simply missing from your tools, which looks the same as a read-only connector. Treat it as unsupported, not as a sign-in problem.
- It worked earlier and now fails with an expired or unauthorized error: check its status as above. Without the connector tools, they reconnect it from /mcp, or disconnect and reconnect it under Customize, Connectors. Either way, make one small test read before carrying on. If Claude's own sign-in is rejected, they sign out and back in, quit the app fully, and reopen it.
- Their company's own (custom) connector cannot be reached: it is often behind their firewall, and custom connectors are reached from Anthropic's cloud. Send them to a host.

**Files**
- The file is somewhere else, such as Downloads: ask them to open it and use Save As into the project folder, or offer to copy it in yourself, warning that popups may ask to read that folder and to copy the file. Do not search their whole computer.
- A spreadsheet (.xlsx): Claude cannot read Excel files without extra tools. The no-install route is a CSV copy in the project folder (Excel: File, Save As, CSV UTF-8; Google Sheets: File, Download, CSV). On a Mac without Apple's developer tools, the first `python3` command opens a system dialog offering to install them, a download of a few minutes; warn before it, or use the CSV route.
- A file dragged into the message box is attached to that message, not saved in the folder. Anything the app must reuse needs a copy in the project folder.

**Skills and installs**
- A new skill does not appear when they type /: run /reload-skills, or start a new session in the same folder. A CLAUDE.md added mid-session takes effect only in a new session.
- Something just installed (Python, for example) still is not found: the app needs a full quit and reopen to see it, then a new session.
- An install blocked on a company computer is an IT matter. Signs include "no matching versions", certificate errors and proxy errors. Do not switch package sources, turn off certificate checks, or suggest another network. Find a route that needs no install (Python's built-in tools often do the job), or send them to a host if they want IT to help.
- Before any new session or restart, update the [progress note](progress.md), and tell them to say "pick up where I left off" in the new session.

**Limits**
- "You've hit your session limit, resets (time)": Claude can do nothing more until the reset. Their files are safe, and the limit card may offer to continue automatically at the reset. Switching models does not lift a session or weekly limit. Extra usage is available on Pro and Max, and from their admin on Team and Enterprise. If it stops their build, send them to a host.
- Close to the limit (the usage ring in the row under the message box; click it to see plan usage): save the progress note, keep steps short and targeted, and do not start a long rebuild. They can lower the effort setting, next to the message box, for simple steps.

**Claude itself**
- The app will not open, will not sign in, or keeps erroring: send them to a host. On a Mac, Claude, About Claude shows the version and Claude, Check for Updates gets the newest; on Windows both are under Help. Start a new session afterwards. If the environment and folder controls sit above the message box instead of under it, the app is out of date.

## 4. If access stays blocked, step down the ladder

Each rung keeps them building with their real material. Take the first one that works. Tell them it is a temporary route, and note what a full version would need in the progress note, so it reaches the take-home page.

1. **Connector**: a live read through the service.
2. **Export into the project folder.** Be specific; this is one of the few things only they can do:
   - Emails: in Outlook on a Mac or in Apple Mail, select the messages and drag them into the project folder. In classic Outlook on Windows, select them and use File, Save As, Text Only, saving into the folder; dragging there makes .msg files that are hard to read. In Outlook on the web or Gmail, open a message and download it from its More menu. For more than a handful, take one representative week, or paste the text instead.
   - Spreadsheets and trackers: save a CSV copy into the project folder (Excel: File, Save As, CSV UTF-8; Google Sheets: File, Download, CSV).
   - Lists in a CRM or other system (HubSpot, Salesforce, Dynamics and the like): open the list view and export to CSV.
   - Reports: download them as CSV where offered, otherwise Excel or PDF.
   - Documents in SharePoint, OneDrive or Google Drive: download a copy into the folder.
   - Meeting transcripts: download or copy the transcript into a text file in the folder.
3. **Paste**: copy just the part needed into the chat.
4. **Screenshot**: drop a picture of the screen into the chat.

Use the smallest real slice that answers the question: one week, one client, one report. If an export turns into a fight, stop and work with whatever they already have.

## 5. When to send them to a host

Send them to a host, in one plain sentence ("This one needs a host: raise your hand, or say so in the chat if you are on a call"), when:
- the problem is their Claude account, plan, billing or sign-in;
- it needs their company's IT (admin approval, a blocked install, a managed computer) and they want to pursue it;
- the same snag survives two different attempts and no other route is left;
- you would have to guess.

Always give them something to do meanwhile: a ladder rung, the next build step, or checking an output.

## 6. Hand back

When it is fixed, say in one line what was wrong and what changed. Then go straight back to what they were doing. Do not restart scoping, recap the plan, or add a lesson.

## Do not

- Ask whether they are allowed to use their own data.
- Widen access, reinstall, or "allow everything" as a reflex.
- Repeat a failed step unchanged. A declined popup is not a failure: try it again if they now want to.
- Say something works before you have seen it work: one real read through the connector, or the file actually opening.
