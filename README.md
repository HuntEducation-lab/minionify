# minionify

**Your own Claude Code, helping with routine teacher admin.**

Give one setup file to the **Claude desktop app**. It walks you through installing **Claude Code CLI** (the terminal program, not the Code tab or the phone app). Claude Code then asks you questions, connects only the tools you use, and builds small helpers for attendance, grades, class posts and more. It all runs on your computer, with your accounts.

You need a **paid Claude plan** (https://claude.ai) and a few lines pasted into a terminal. This repo is instructions only: no code, logins or student data.

## Ask your school's IT first
- **Google access:** a Google Cloud project, apps reading Classroom, Chat, Gmail, Calendar and Drive, and Claude's connectors (your Google sign-in is then stored on Anthropic's side).
- **Automating the gradebook or school websites** with your login.
- **Installing software:** the Claude desktop app, Claude Code, Node.js and a browser tool.

## Set up
1. Install the **Claude desktop app** from https://claude.com/download and sign in.
2. Download [MINIONIFY-SETUP.md](MINIONIFY-SETUP.md): open it on GitHub, click the download icon (**Download raw file**).
3. In the app, start a **new chat**, attach the file (or paste its text) and type: `Set me up with this file.`
4. Follow along, one step at a time: open PowerShell (Windows) or Terminal (Mac), paste a line, say what you see. Then type `claude`, sign in, and type `@MINIONIFY-SETUP.md`.
5. Claude Code takes over. Start **Quick** (Gmail, Calendar, Drive, about 10 minutes), add **Full** later (Google Cloud project for Classroom and Chat, gradebook, practice sites). For each tool pick **Off, Read only, Draft only, or Read and write with preview**.

## Asking for help
Claude is there to be asked. Never paste a password or student data.
- `I am stuck on step 4. Here is what I see: ...`
- `Explain what that command does before I run it.`
- `Reconnect everything.` (a connection stopped working)
- `Add Quill to my setup.` (any new site or tool)
- `Undo that.` / `Show me exactly what you are about to change.`

Common fixes: `claude` not found, open a new terminal and run `claude --version`; an `irm` error means you are in CMD, so open PowerShell; Google sign-in expires about every 7 days in Testing mode, which is normal.

## You are the human in the loop
You read, then say yes  
The robot drafts, you decide  
Your name on each change

## Rules
- No student names, grades or messages in the desktop chat. They stay on your computer and in your school's systems.
- Run Claude Code on your own computer, not in a cloud or web session.
- Do not share your logins, build this for others, or charge for it without the vendor's written consent.

Not affiliated with Anthropic, Google or any school-software vendor. Provided as is, no warranty. MIT license: [LICENSE](LICENSE).
