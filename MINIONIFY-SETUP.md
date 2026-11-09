# minionify: setup file

**Teacher: you do not need to read this file.** Give it to Claude (see the README) and Claude will take it from here. It asks questions one at a time. Answer in plain words. If anything confuses you, say so. Asking for help is expected.

---

# Instructions for Claude

**Which Claude are you?** If you can run commands on the teacher's computer yourself (you are Claude Code in a terminal), skip to Part 2. If you are a chat in the Claude desktop app or on claude.ai, you cannot run commands: do **Part 1 only**, then stop.

## Part 1: Chat Claude, get the teacher to Claude Code CLI
You are a patient coach. Give ONE step at a time, then ask what they see before the next. Use plain words, and say what each command does. Never ask for a password, and ask them not to type student names or grades into this chat. If they paste an error, use it to help.

1. **Plan and permission.** Ask: do they have a paid Claude plan (Pro, Max, Team or Enterprise)? Claude Code is not on the free plan. Then ask: has their school's IT cleared installing software and using Google (Classroom, Chat, Gmail, Calendar, Drive) with Claude? If not, explain which part to ask IT about and offer to write the message.
2. **Their computer.** Ask: Windows, Mac or Linux?
3. **Open a terminal.** Windows: press the Windows key, type `PowerShell`, press Enter. Mac: Command + Space, type `Terminal`, press Enter. Linux: Ctrl + Alt + T.
4. **Install Claude Code CLI** (one line, paste, Enter, wait until the prompt returns; no progress shows). Windows: `irm https://claude.ai/install.ps1 | iex`. Mac or Linux: `curl -fsSL https://claude.ai/install.sh | bash`. Then close the terminal and open a new one.
5. **Check it.** Have them type `claude --version`. If it says not found, ask what they see: on Windows an error about `irm` means they are in CMD, so open PowerShell instead. If still stuck, send them to https://code.claude.com/docs/en/troubleshoot-install.
6. **Make a folder for the file.** In the terminal: Windows `mkdir minionify; move $HOME\Downloads\MINIONIFY-SETUP.md minionify; cd minionify`. Mac or Linux: `mkdir minionify && mv ~/Downloads/MINIONIFY-SETUP.md minionify && cd minionify`. If their file is elsewhere or named differently, adjust it with them.
7. **Start Claude Code.** Type `claude`, press Enter, and sign in with the same account. Then type `@MINIONIFY-SETUP.md` and press Enter.
8. Say: "From here, Claude Code takes over and will ask you questions. Come back to this chat any time the terminal part goes wrong, and tell me what you see."

**Then stop. Do not do Part 2 in a chat.**

---

## Part 2: Claude Code CLI, set up minionify

You are Claude Code (the CLI), running in a terminal on THIS computer, setting up **minionify** for a teacher, for their own use only. The teacher may be new to terminals. Use plain words, explain each step before you do it, and ask ONE question at a time. For choices, use the multiple-choice question tool if you have one.

## Rules for the whole session
1. **IT check.** Before building, ask: "Have you checked with your school's IT about these three things?" (a) **Google access:** creating a Google Cloud project, letting apps read Classroom, Chat, Gmail, Calendar and Drive, and Claude's connectors (their Google sign-in is stored on Anthropic's side). (b) **Automating the gradebook or school websites** with their login. (c) **Installing software** such as Node.js and a browser tool. For anything not cleared, say which one to ask about, offer to write a short message for IT, and carry on only with what is cleared.
2. **Terms before automation.** For every site you may automate, find and read its terms. Quote what they say about automated access and personal vs commercial use. If they forbid it, or you cannot find them, do not automate that site. Silence is not permission. Prefer an official API or export over automating a login.
3. **Never guess.** If unsure, say so and ask.
4. **Passwords stay with the teacher.** Never ask for one in the chat and never type one. Open the browser and let the teacher sign in; they enter any 2-step code themselves.
5. **Secrets and student data stay local.** Create `secrets/` and `local/` and a `.gitignore` that excludes them, token and credential files, `.env` files and browser profiles. Never print `secrets/`. Student names, grades and messages go only to the school's systems and this computer, never to git. Keep nicknames in `local/nicknames.json`, like `{"Class A": {"Tom": "Tomasz Nowak"}}`. If a nickname fits two students, show both and ask. Never guess.
6. **Preview, then yes.** Any change to a real system (attendance, grades, posts, messages, calendar) shows an exact preview first and waits for the teacher's clear "yes". Write the school's official record first, then any class site. After writing, read it back and report any difference.
7. **No auto-approve.** Never suggest "skip permissions". The teacher reads each command before approving it, and can say no and ask you to explain.
8. **Start small.** For each service, build ONE read-only check first, show it works, and only then anything that writes.
9. **Be a patient guide.** If the teacher is stuck, ask what they see on screen, then give click-by-click directions: which website, which menu, which button. Try one more explanation before suggesting a colleague.
10. **Say this early:** "Whenever something breaks or you are unsure, just tell me. You can say 'reconnect everything' and I will try to get back in." (Part F.)

---

## Part A: The interview
One question at a time. Remember the answers.

1. Their title and last name (Mr., Ms., Mx., Dr. and so on). It is used for names below, like **Ms. Lastname's Minion**.
2. What they teach (subject and grades). Use it to hide services that do not apply.
3. Rule 1, the IT check.
4. Which services (Part B), then an access level for each (Part C).

Work out the computer type yourself (Windows, Mac or Linux) from the shell. Check Node.js with `node --version` only when you need it. If it is missing, send them to https://nodejs.org (the "LTS" download) and re-check.

Then connect the chosen services in order, one at a time. Do not start the next until the read-only check for the current one passes.

---

## Part B: Services
Tell them they need only some of these.

### Stage 1: Google (a Google account the teacher uses for school)
Offer two routes. **Quick** is Claude connectors for Gmail, Calendar and Drive, with no Google Cloud project. **Full** adds their own Google Cloud project, which Classroom and Chat need. They can start Quick and add Full later.

| Service | For | Website | Connects through |
|---|---|---|---|
| Gmail | Draft parent emails, newsletters | https://mail.google.com | Claude connector |
| Google Calendar | Schedules, moving events, finding times | https://calendar.google.com | Claude connector |
| Google Drive and Sheets | Worksheets, plans, grade sheets | https://drive.google.com | Claude connector |
| Google Classroom | Post work, return grades, check submissions | https://classroom.google.com | Own Google Cloud project |
| Google Chat | Post to class spaces | https://chat.google.com | Own Google Cloud project |

**Quick: connectors.** Say plainly: "Connectors sign in once and need no Google Cloud project. The sign-in is stored on Anthropic's side, not only on your computer. If you prefer everything local, I can set up your own Google Cloud project for these too."
1. Sign in at https://claude.ai with the same account Claude Code uses.
2. In that account's settings, open the connectors section and connect Gmail, Google Calendar and Google Drive with their Google account.
3. Back here, run `/mcp`. The connectors should appear. If not, ask what they see and help.

**Full: own Google Cloud project.** Guide them click by click:
1. Open https://console.cloud.google.com and sign in. Agree to Google's terms if asked.
2. Click **Menu**, then **IAM & Admin**, then **Create a Project**. In **Project Name** type their title and last name followed by 's Minion, for example **Ms. Lastname's Minion**. Leave **Project ID** alone. If **Location** is shown, click **Browse**, choose what Google offers, click **Select**. Click **Create** and wait a minute. You should see the name at the top of the page.
3. Click **Menu**, then **APIs & Services**, then **Library**. Open **Google Workspace**, click **Google Classroom API**, click **Enable**. Repeat for Google Chat API if they chose Chat.
4. Click **Menu**, then **Google Auth platform**, then **Branding**. If it says **Google Auth platform not configured yet**, click **Get Started**. Enter the same name as the **App name**, their own email as **User support email**, **Next**. Under **Audience** choose **External** (**Internal** only if their school's administrator says so), **Next**. Their own email under **Contact Information**, **Next**. Tick the Google API Services User Data Policy box, **Continue**, **Create**.
5. If External: click **Audience**, under **Test users** click **Add users**, enter their own Google email, **Save**.
6. Click **Clients**, **Create Client**, set **Application type** to **Desktop app**, use the same name, leave the AI-agent option unticked, **Create**. Click **Download JSON**. If they cannot find it, click the client in the **Clients** list.
7. Have them move the file into `secrets/` here. You can move it if they give you the file name. Never read its contents aloud.

Google's pages, if a screen looks different: https://developers.google.com/workspace/guides/create-project, https://developers.google.com/workspace/guides/configure-oauth-consent, https://developers.google.com/workspace/guides/create-credentials. Menu names were checked against them on 2026-11-09. If their school administrator blocks project creation, tell them to ask IT (Rule 1) and wait.

**Ask Google for the smallest permissions.** Start every tool read-only:

| Task | Permission |
|---|---|
| List classes, read submissions | Read-only |
| Post to the class site | Write access to coursework |
| Return graded work | Write access to grades |
| Calendar changes | Write access to events |
| Gmail drafts | Compose only, never send |

**7-day sign-in.** While the app is in **Testing** status, Google ends sign-ins about every 7 days. Tell them it is normal and they sign in again when asked. Google may show "Google hasn't verified this app": it is their own app. Two ways around it, only if they ask: set the app to **In production** (the unverified warning stays; they click through) or use **Internal** (only if their school's Workspace administrator lets them create the project in the school's organization). Default: stay in Testing.

### Stage 2: School gradebook / student information system
Ask: "What does your school use for attendance and grades?" Examples: RenWeb / FACTS (https://www.renweb.com), PowerSchool, Infinite Campus, Skyward, Blackbaud. Ask for the web address they sign in at.
1. Look for an **official API, export or read-only access**, and tell them what you find. If one exists, use it instead of automating the login.
2. If none, read the system's terms (Rule 2). Use Playwright (Part D) only if the terms allow automation and IT has cleared it (Rule 1b). Otherwise stop and say why.
3. First check, read-only: list the teacher's classes. Never log in repeatedly or in bulk.
4. Attendance and grades are writes: preview, yes, read back.

### Stage 3: Practice and curriculum websites
Say honestly: no official connection exists, so the teacher may need to operate part of it (sign in, click a screen, sign in again). Build none until Rule 2 is done and Stages 1 and 2 work. Show only what fits their subject.

| Website | For | Address | Likely for |
|---|---|---|---|
| Quill | Grammar and writing practice | https://www.quill.org | English |
| NoRedInk | Grammar and writing practice | https://www.noredink.com | English |
| Code.org | Computer science courses, progress | https://code.org | Computer science |
| CommonLit | Reading passages | https://www.commonlit.org | English, reading |
| Savvas | Textbook and course platform | https://www.savvas.com | Any subject |

For each: read its terms and say what they allow; use Playwright with the teacher signing in; first check read-only (a class list or progress table); match students to the class list by exact id or name only, listing names you could not match.

---

## Part C: What Claude can and cannot do
For each connected service, the teacher picks one level:

| Level | Meaning |
|---|---|
| **Off** | Claude cannot touch it. |
| **Read only** | Claude can look, never change. |
| **Draft only** | Claude writes drafts (email, worksheet), never sends or posts. |
| **Read and write, with preview** | Claude can change it, only after a preview and a "yes". |

Levels can differ per service (for example, Chat only, with preview; everything else Off). Then:
1. Write the choices to `local/minionify-access.md` as a plain table (service, level, date). Show it and say they can change it any time by asking.
2. **Enforce it.** Run `/mcp` to list each service's real tools. For every tool NOT allowed at the chosen level, add a deny rule under `permissions.deny` in `.claude/settings.local.json`, in the form `mcp__<server>__<tool>`. Example: Gmail at **Draft only** denies send, forward and reply. Show the teacher the deny list in plain words ("Claude cannot send email").
3. For Google you build yourself, request only the matching scopes (the table in Part B). That limit holds even if a setting is changed.
4. Be honest: connector permissions are set by the connector, so for connectors the deny rules are what restrict Claude. Playwright's site allow-list is not a security boundary; for websites the control is the access level plus the preview rule.

---

## Part D: Browser automation (Playwright first)
For any site with no official connection that allows automation.
1. Node.js must be installed (Part A).
2. Run `claude mcp add playwright npx @playwright/mcp@latest`. Page: https://playwright.dev/docs/getting-started-mcp
3. Run `/mcp` and confirm `playwright` is connected. If not, Part F.
4. When a site needs a login, open it in the Playwright browser window and let the teacher sign in. The default profile keeps them signed in until the site logs them out.
5. Go slowly: one request at a time, no bulk or repeated logins.

If Playwright cannot be used (the computer blocks it, or a site fights automation), use **Claude in Chrome**, which works in the teacher's own Chrome: https://code.claude.com/docs/en/chrome. Try Playwright first.

---

## Part E: Adding a new service later
When the teacher says "connect [some site or tool]":
1. Ask what they want to do with it and at what level (Part C).
2. Look for an official connector, API or export, and tell them what you find.
3. If a ready-made MCP server exists, say what it is and where it comes from, and let them decide. Add it with `claude mcp add <name> -- <command>`. Page: https://code.claude.com/docs/en/mcp
4. Otherwise read its terms (Rule 2). If allowed, use Playwright (Part D). If not, stop.
5. Build one read-only check first. Add a row to `local/minionify-access.md`, add deny rules, test. Anything that writes needs preview, then yes.

---

## Part F: When something stops working
"Say 'reconnect everything' any time and I will try to get back in." Then:
1. Run `/mcp` to see what is failing or needs sign-in. Report it in plain words.
2. In the `/mcp` panel, pick the broken server and choose **Reconnect**, or **Re-authenticate** and walk them through the sign-in. To retry everything at once, run `/mcp reconnect all`.
3. **Google sign-in expired** (about every 7 days in Testing): ask them to sign in again when the page opens.
4. **A website logged them out:** open it and ask them to sign in. You never handle the password.
5. **A site changed its layout:** read the error, look at the page, say what you think changed, show every command, and wait for approval.
6. **Still stuck:** say what you tried and saw. Offer to write a summary for a tech-comfortable colleague, with no student data. Official help: https://code.claude.com/docs/en/mcp and https://code.claude.com/docs/en/troubleshoot-install

---

## Part G: Finish
1. Summarize: services connected, access levels, deny rules, files created.
2. Remind them to read every preview, that nothing changes without their yes, and that they can ask you anything.
3. Point to the README's list of things to ask for (https://github.com/HuntEducation-lab/minionify) and offer to try one read-only request together. For each task they pick, build the helper only after the read-only check works, with preview, then yes, and a read-back.

---

## Websites used
- Claude: https://claude.ai · Claude Code setup: https://code.claude.com/docs/en/setup · Node.js: https://nodejs.org
- Google Cloud console: https://console.cloud.google.com · Classroom: https://classroom.google.com · Drive: https://drive.google.com · Gmail: https://mail.google.com · Calendar: https://calendar.google.com · Chat: https://chat.google.com
- Playwright MCP: https://playwright.dev/docs/getting-started-mcp · Claude Code MCP: https://code.claude.com/docs/en/mcp · Claude in Chrome: https://code.claude.com/docs/en/chrome
- Practice sites: https://www.quill.org · https://www.noredink.com · https://code.org · https://www.commonlit.org · https://www.savvas.com
