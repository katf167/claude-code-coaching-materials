# Getting Started with Claude Code
*Your daily AI assistant in 5 minutes a morning*

---

## Before you paste anything: compliance

**Do not paste proprietary data, client lists, or anything your security team would not approve into Claude.** If your organization uses Glean, Copilot, or a similar enterprise tool, that is your sanitization layer. Always summarize first, then paste the summary. If you are not sure whether a piece of information is proprietary, do not paste it.

If your organization has written AI data-handling rules, read them before your first session. If they do not, ask your security team before using Claude on any work data.

---

## First-Time Setup (do this once)

You do this once, then you never touch it again. Budget 15 to 30 minutes.

### Step 1. Install Claude Code

**Option A (recommended on Mac): Homebrew cask.** Open Terminal (Cmd+Space, type "Terminal", hit enter) and run:
```
brew install --cask claude-code
```

If Homebrew is not installed on your Mac, install it first:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Option B (any OS): native installer.** Go to [claude.com/code](https://claude.com/code), download for your operating system, run the installer.

**If Homebrew is blocked by your IT team:** use Option B.

### Step 2. Launch Claude and log in

In Terminal (or PowerShell on Windows), type:
```
claude
```

The first launch opens a browser to log you in.

**If you are on an enterprise license (e.g., Infoblox):** select "Enterprise" at the login prompt. You will authenticate via your organization's SSO (Okta, Azure AD, etc.).

**If you are on a personal plan:** select "Personal" and sign in with your Claude account.

### Step 3. Make a project folder

Pick a sensible name based on the work you will do with Claude. Type these commands one at a time:
```
cd Documents
mkdir [your-project-name]
cd [your-project-name]
```

Example: `mkdir dns-aid` if you are on the Infoblox DNS-AID team.

**Where Claude Code looks for your files:** whatever folder you `cd` into before running `claude` is the base folder for that session. Keep this folder separate from any code repositories you already have, so Claude does not accidentally touch existing work.

### Step 4. Create your CLAUDE.md

**Easiest path: have Claude build it for you.** Start a session in your project folder (`claude`), then say to it:

> "Help me write a CLAUDE.md for my work as [your role] on the [your team or project]. Ask me 3 to 5 questions before you write it so the draft is actually useful. Save the result as CLAUDE.md in this folder."

Claude will ask you questions, you answer them, Claude writes the file. Edit what feels wrong. Save.

**Alternative fast path:** type `/init` at the Claude prompt. Claude Code has a built-in CLAUDE.md generator that walks you through the basics. Good if you just want a starter template you will expand later.

You are set up. Everything below takes 5 minutes a morning.

---

## Your Morning Routine (do this every day)

1. **Open Terminal**, `cd` into your project folder, type `claude`.
2. **Open Glean** (or your enterprise-approved equivalent) and ask it: *"Summarize my emails, Teams messages, and calendar from the last 24 hours."* Copy the result.
3. **Paste into Claude and save as a daily briefing.** In the Claude session, type:

   > "Save the following text as daily-briefings/[today's date].md, then read it and give me action items by urgency, conflicts or discrepancies, proposed next steps, and any quick replies I should send. [paste Glean summary]"

   Claude saves the file and runs the analysis in one go.

That is the whole habit. Five minutes. The more days you do this, the more context Claude has to spot patterns and catch things you would miss.

**Why this works:** You are not learning to "prompt." You are having a conversation with an assistant who already knows your job. The more days of briefings it has, the more it catches, like a colleague who has been sitting next to you for months.

---

## Review every output before you use it

Claude is an assistant, not a replacement for your judgment. Read what it gives you. If something is wrong, say so and have it try again. If you are about to send a draft email, read the draft yourself first. The thinking is still yours; Claude is doing the grinding.

A useful framing: think of it like using R for statistics. You still know how to calculate a least-squares regression; you just do not do it by hand anymore. You check the output, you know when it is wrong. Same here.

---

## Project Structure

Claude Code works from a project folder on your computer. A working structure looks like:

```
your-project/
  CLAUDE.md              Instructions that tell Claude who you are and how to help
  .claude/
    settings.json        Claude Code configuration
    skills/              Your saved skills (created automatically when you save one)
      daily-briefing/
        SKILL.md
  daily-briefings/       One file per day (Glean summaries + Claude's analysis)
    2026-04-15.md
    2026-04-16.md
  docs/                  Reference documents Claude should know about
    org-chart.md
    project-roadmap.md
    meeting-notes/
```

You do not need to create every folder up front. Make them as you need them.

---

## How CLAUDE.md Works

Think of CLAUDE.md as a briefing doc for your AI assistant. Just like you would brief a new team member on their first day, this file tells Claude everything it needs to know to be useful immediately. Claude reads it at the start of every session. It covers:
- Who you are and what you do
- What your daily workflow looks like
- What tools you use (Glean, Outlook, Teams)
- How you want Claude to communicate (your writing style goes here)
- Rules and preferences

You do not need to write code or learn special syntax. It is plain English in a text file. If you can write an email, you can write a CLAUDE.md.

**CLAUDE.md is a living document.** Update it as you learn what works. When Claude does something well, add the pattern. When Claude does something wrong, add a rule.

**Writing style goes in CLAUDE.md.** Unlike some other Claude products, Claude Code does not have a separate "writing style" toggle. Instead, add a section like:

```markdown
## Writing Style
- Keep emails under 3 sentences unless the topic requires more
- Direct, no filler
- Sign off with "Best, [Name]"
- Never use exclamation marks in external emails
```

---

## Memory

Claude Code's memory works two ways:

1. **CLAUDE.md is the guaranteed memory.** Every time you launch Claude in your project folder, it reads CLAUDE.md first. Anything you put in there will be remembered every session, no exceptions. Treat CLAUDE.md as the source of truth for "Claude should always know this."
2. **In-session memory and updates.** During a single session, Claude remembers everything you said. If you correct it on something important ("no, the X meeting is more urgent than Y because of Z") and you want that to stick, ask Claude to add the correction to CLAUDE.md. One sentence: *"Add a note to CLAUDE.md that..."* and it will edit the file.

If Claude keeps forgetting something, that means it is not in CLAUDE.md yet. Put it there.

For more advanced auto-memory across sessions (notes Claude takes on its own without you asking), Anthropic offers a Memory Tool that can be enabled. We can set that up in a follow-up session if it becomes useful.

---

## Adding Context (the more, the better)

Drop files into your `docs/` folder:
- Org charts, project plans, templates you use often
- Meeting notes, strategy docs, reference materials
- Anything Claude should know about to do its job

Claude reads files when you ask it to, or when your CLAUDE.md tells it to check specific folders.

**Tip for keeping things fast:** Claude works better with markdown summaries than with raw PDFs or PowerPoints. If you are dropping in reference docs, ask Claude to convert them to markdown first ("read this PDF and save a markdown summary in docs/").

---

## Skills (teach Claude to repeat tasks)

A "skill" is a set of written instructions for a task you do regularly, saved as a text file. Think of it like a recipe card: once the skill is saved, Claude uses it the same way every time.

**You do not invoke skills manually.** Once a skill is saved, Claude will use it automatically when the task matches. You do not have to type `/use skill-name` or anything like that. Just describe what you want and Claude picks the right skill.

**Example:** A `daily-briefing` skill tells Claude exactly how to process your Glean summary: structure as action items, flag urgencies, cross-reference against yesterday, propose next steps. Once saved, Claude runs it every morning when you paste a summary. You do not have to explain the format every time.

**Where skills live:** Claude Code looks in `.claude/skills/[skill-name]/SKILL.md` inside your project folder. So your daily briefing skill would live at `your-project/.claude/skills/daily-briefing/SKILL.md`. Do not worry about creating these folders yourself; just say to Claude: *"Save the daily briefing workflow we just did as a skill called daily-briefing."* It will create the folder and the file for you.

**To create one:**
1. Do the workflow manually with Claude a few times.
2. When the output is consistently what you want, say: *"Save this workflow as a skill called [name]. Use the past few sessions as examples of good input and output. Analyze how we got there and write the skill so it does the same thing every time."*
3. Claude writes the skill, saves it, and from that point on, it picks the skill up automatically when relevant.

---

## Token efficiency (save money, move faster)

Every read, write, and thinking step consumes tokens. You do not need to optimize obsessively, but a few habits help:

- **Summaries beat raw files.** Converting PDFs and slide decks to markdown summaries is faster and cheaper than reading the raw file every session.
- **Keep projects scoped.** Do not point Claude at a folder with every project you have ever worked on. Give it only what is relevant to the task.
- **Use CLAUDE.md as a router.** Instead of putting all your reference content in one long CLAUDE.md, use CLAUDE.md to point Claude to other markdown files ("for IETF draft tasks, read docs/ietf-process.md"). Claude loads the sub-file only when needed.
- **Ask for self-review.** At the end of a heavy session, say *"analyze your token consumption for this session and tell me how we could have done it more efficiently. Add any patterns worth keeping to CLAUDE.md."* Claude is good at critiquing its own runs.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Claude forgot something I told it | Add it to CLAUDE.md (guaranteed to be read every session) |
| Claude's tone is wrong | Add or update the Writing Style section in CLAUDE.md |
| Claude seems confused about my work | Add more context documents to your `docs/` folder |
| Claude gave a bad answer | Be specific about what was wrong. It learns from corrections. |
| Claude isn't reading my files | Tell it explicitly: "Read the file at daily-briefings/2026-04-15.md" |
| Session is consuming too many tokens | Ask Claude to analyze its own token use and suggest fixes |
| Install or login fails on enterprise laptop | Check with IT on whether Homebrew is allowed, or use the native installer from claude.com/code |

---

## What Claude Code Can Do

- Read and write files on your computer (within your project folder)
- Run shell commands and scripts
- Analyze documents, data, and code
- Draft emails, reports, summaries in your style
- Cross-reference across multiple files and days of briefings
- Build automations (scripts, scheduled workflows)
- Fetch web pages and search the web when given a URL or query

## What Claude Code Cannot Do

- Access your work email, calendar, or Teams directly (use Glean as the bridge)
- Send emails or messages on your behalf (it drafts, you send)
- Run in the background automatically (you start each session manually; if you want scheduled tasks, that lives in Cowork, a different Anthropic product)
- Take actions in other apps without you (it can read and write files in your project folder, run terminal commands, fetch web pages, but it will ask before touching anything outside the folder)

---

## Need Help?

Email **aicoach@atticusprojectai.org** to schedule a follow-up session.
