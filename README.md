# minionify

**Your own Claude Code, helping with routine teacher admin.**

minionify is one setup file. You give it to the **Claude desktop app**, which walks you through installing **Claude Code CLI** (the terminal program from Anthropic, not the desktop app's Code tab or the phone app). Claude Code then asks you questions, connects only the tools you use, and builds small helpers for attendance, grades, class posts and more. Everything runs on your own computer, with your own accounts.

You need a **paid Claude plan** (https://claude.ai). This is not a one-click app: you will paste a few lines into a terminal, and a wrong step can expose student data. This repo has instructions only: no code, no logins, no student data.

## 1. Ask your school's IT first
Ask about these three things. Skip any you do not plan to use.
- **Google access:** creating a Google Cloud project, letting apps read Classroom, Chat, Gmail, Calendar and Drive, and using Claude's connectors (your Google sign-in is then stored on Anthropic's side).
- **Automating the gradebook or school websites** with your login. Many terms forbid it.
- **Installing software:** the Claude desktop app, Claude Code, Node.js and a browser tool.

```text
Hello, I would like to use Claude on my own computer to save time on routine tasks. Could you tell me if I may: (1) use Google Classroom, Chat, Gmail, Calendar and Drive with my own account, including creating my own Google Cloud project; (2) automate my own login to our gradebook or school websites; (3) install the Claude desktop app, Claude Code, Node.js and a browser tool? Thank you.
```

## 2. Set up (about 5 steps)
1. Install the **Claude desktop app** from https://claude.com/download and sign in.
2. Download [MINIONIFY-SETUP.md](MINIONIFY-SETUP.md): open it on GitHub and click the download icon (**Download raw file**). It saves to your Downloads folder.
3. In the Claude app, start a **new chat**, attach the file (or copy its text and paste it) and type: `Set me up with this file.`
4. Follow along. Claude gives one step at a time: open PowerShell (Windows) or Terminal (Mac), paste one line, tell it what you see. Next it makes a `minionify` folder, you type `claude` and sign in, then `@MINIONIFY-SETUP.md`.
5. Claude Code takes over and asks questions. Start **Quick** (Gmail, Calendar, Drive connectors, about 10 minutes) and add **Full** later (your own Google Cloud project for Classroom and Chat, your school's gradebook, practice sites). For each tool you choose **Off, Read only, Draft only, or Read and write with preview**. Nothing changes without your "yes".

If you do not see Claude say hello and ask for your title and last name, tell the chat what you see. Anthropic's own install page: https://code.claude.com/docs/en/setup.

## How to ask for help
Claude is there to be asked. Copy these and change the details. Never paste a password or student data.
- `I am stuck on step 4. Here is what I see: ...`
- `Explain what that command does before I run it.`
- `Reconnect everything.` (When a connection stops working. Claude tries `/mcp` Reconnect and Re-authenticate for you. A website that logged you out, you sign in yourself.)
- `Add Quill to my setup.` (any new site or tool: Claude checks for an official connection first, then uses Playwright, with your OK)
- `Undo that.` / `Show me exactly what you are about to change.`
- `What is still connected, and at what level?`

Common problems: `claude` not found, close the terminal, open a new one, run `claude --version`; an error about `irm` means you are in CMD, open PowerShell; Google sign-in expires about every 7 days for your own Google Cloud app in Testing mode, which is normal; if you approved something you did not understand, stop, check your gradebook and class site, and ask a tech-comfortable colleague.

## What to ask for once it works
Start with the read-only ones. Each shows a preview and waits for your yes.

| Say this | What it does | Writes? |
|---|---|---|
| `Give me a morning check` | Calendar and school system status | No |
| `Who was absent or late this week?` | Weekly attendance summary | No |
| `Who has not started the practice unit?` | Practice-site progress | No |
| `Compare my gradebook and class site` | Finds differences | No |
| `Draft a one-page sub plan for tomorrow` | Draft only | No |
| `Draft report-card comments for my class` | Positive, no student data leaves your computer | After yes |
| `Take attendance: Class A, Joe absent, Mateo late` | Attendance, nicknames from a local file | After yes |
| `Enter scores for Essay 3` | Grades in the school record, then the class site | After yes |
| `Return graded work to students` | Class site | After yes |
| `Post this reading to my class` | Class post and matching gradebook entry | After yes |
| `Log a behavior point, draft an email home` | Email is a draft, never sent | After yes |
| `Move today's classes 30 minutes later` | Calendar | After yes |

## Rules
- Never turn on "auto-approve" or "skip permissions". Read every command before you approve it.
- No student names, grades or messages in the desktop chat. They stay on your computer and in your school's systems.
- Run Claude Code in the terminal on your own computer, not in a cloud or web session.
- Do not share your logins, build this for others, or charge for it without the vendor's written consent.

Not affiliated with Anthropic, Google or any school-software vendor. Provided as is, no warranty. MIT license: [LICENSE](LICENSE).
