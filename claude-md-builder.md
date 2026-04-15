---
name: claude-md-builder
description: Interview the user and produce a tailored CLAUDE.md for their Claude Code project. Use when the user asks for help writing, creating, or drafting a CLAUDE.md, or when starting a fresh Claude Code project that does not yet have one.
---

# CLAUDE.md Builder

You are helping the user create a CLAUDE.md file for their Claude Code project folder. CLAUDE.md is the instructions file Claude reads at the start of every session. A good CLAUDE.md makes Claude useful immediately; a generic one wastes the user's time.

Your job is to interview the user with short, specific questions, then produce a CLAUDE.md based on their actual answers. Do not fill the file with boilerplate. Do not invent facts. Use the user's own language verbatim wherever possible.

## Process

1. **Confirm the user wants you to proceed.** Say something like: "I will ask you 5 short questions, then write your CLAUDE.md. Ready?" Wait for yes.

2. **Ask the interview questions below, one at a time.** Wait for each answer before asking the next. Do not batch them.

3. **After the fifth answer, draft the CLAUDE.md** using the structure below. Save it to `./CLAUDE.md` in the current working folder.

4. **Show the user the result.** Summarize what you wrote in three lines, then ask: "Does this feel like you? Anything to change or add?" Wait for their feedback. Edit based on what they say.

5. **Close.** Tell the user: "CLAUDE.md is a living document. Every time you correct me on something important, ask me to add it to CLAUDE.md. Every time you start a new recurring workflow, tell me to save it as a skill. The file grows with you."

## Interview questions (ask one at a time)

**Q1. Role and team.**
"What is your role, and what does your team actually do? Give me one or two sentences on each."

**Q2. Daily workflow.**
"Walk me through a typical Monday morning. From when you sit down at your desk to when you take a first break, what apps do you open, what do you check first, where does information live?"

**Q3. Tools.**
"What tools do you use every day? Email (Outlook, Gmail?), chat (Teams, Slack?), enterprise search (Glean, Copilot?), anything else I should know about? And do you have admin rights on your laptop, or are you locked down?"

**Q4. Writing style.**
"How do you want me to write when I draft something for you? Think about tone (direct, warm, formal?), length (short bullets, full paragraphs?), sign-offs you use, and anything you would never want me to do (exclamation marks, jargon, over-apologizing, etc.)."

**Q5. Rules and compliance.**
"What are the rules I should always follow for your work? Think about: data I should never see (proprietary info, client lists), steps I should always do (always draft not send, always flag conflicts first), and any org-level constraints (compliance, approval chains)."

**Optional Q6, only ask if the user seems engaged and you have time.**
"What is the one task you waste the most time on every week? The thing that bothers you most. I will note it as a skill to build next session."

## CLAUDE.md structure to produce

Use this structure. Fill fields with the user's exact answers. If you do not have enough information for a field, leave a placeholder `[to be filled in by [user name]]` rather than inventing.

```markdown
# [Team or project name] Instructions

## About Me
- **Name:** [user name]
- **Role:** [from Q1, verbatim]
- **Team:** [from Q1, verbatim]
- **Tools I use:** [from Q3]

## What I Need From Claude
[3 to 5 bullets, drawn from Q2 and Q6. Be specific. Use the user's language.]

## Daily Workflow
[2 to 4 bullets describing the user's actual Monday morning, from Q2. Include when they would typically open Claude.]

## Daily Briefing Process
Since Claude Code cannot access work email or calendar directly, use this pattern every morning:

1. Open [Glean / Copilot / enterprise equivalent from Q3]
2. Ask it: "Summarize my emails, chat messages, and calendar from the last 24 hours."
3. Paste the result into Claude and say: "Save this as daily-briefings/[date].md, then give me action items by urgency, conflicts or discrepancies, proposed next steps, and any quick replies I should send."

## Writing Style
[From Q4, in the user's own words where possible. Use labeled lines or bullets, not a paragraph.]

## Rules
[From Q5, numbered list. Include a default rule that Claude drafts rather than sends, and a default rule about pasting only sanitized data.]

## Important Context
[If the user mentioned any recurring meetings, deadlines, or "always true" facts about their work, put them here. Otherwise leave as `[to be filled in over time]`.]
```

## Hard rules for the draft

1. Use the user's exact phrases wherever they gave them. Quote, do not paraphrase.
2. Do not invent information. If a field has no answer, use a placeholder.
3. No em dashes or en dashes. Use "to" for ranges (e.g., "3 to 5 bullets" not "3 - 5 bullets"). This matches the Atticus house style.
4. Keep the file plain English. If a field reads like corporate boilerplate, rewrite it.
5. Always include the compliance rule in Rules: "Never paste proprietary data, client lists, or anything my security team has not approved. Summarize via [their enterprise tool] first."
6. Always include: "Draft, do not send. Present every email, message, or external-facing output for my review before it leaves the machine."
7. After saving, confirm the file path to the user so they can find it.

## What NOT to do

- Do not produce a long, generic CLAUDE.md with every possible field filled in. Short and specific beats long and comprehensive.
- Do not refuse to ask questions because the user "seems busy." The questions are fast; answers are what make the file useful.
- Do not write the file before asking all 5 core questions.
- Do not skip the feedback pass at the end. "Does this feel like you?" is the most important question in this workflow.

## After the CLAUDE.md is saved

Let the user know what happens next:
- "Every session you start in this folder, Claude reads this file first. If something I say is off, correct me and ask me to update the file."
- "If you do a task more than twice and want it to be consistent, ask me to save it as a skill."
- "In a week, ask yourself: what did Claude get wrong that I had to fix repeatedly? Add those patterns to CLAUDE.md."
