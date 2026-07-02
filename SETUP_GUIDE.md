# Rillix Content Agent — Setup Guide
# What to do once Claude Code is installed

---

## What you have in this folder

```
rillix-content-agent/
├── library/
│   └── STYLE_LIBRARY.md          ← Your voice, formats, proof points, watchlist
├── agents/
│   ├── 01_SCANNER_AGENT.md       ← Finds today's topic every morning
│   ├── 02_ANGLE_POV_AGENT.md     ← Turns topic into Sanjay's actual take
│   ├── 03_LINKEDIN_WRITER_AGENT.md ← Writes the final post
│   └── 04_REFERENCE_AGENT.md     ← Processes posts you share into the library
├── routines/
│   └── DAILY_ROUTINE.md          ← The master daily automation prompt
└── SETUP_GUIDE.md                ← This file
```

---

## Step 1 — Create a GitHub repo for this project

1. Go to github.com and sign in
2. Click the "+" button → "New repository"
3. Name it: `rillix-content-agent`
4. Set it to **Private** (this contains your content strategy — keep it private)
5. Click "Create repository"
6. Upload all the files from this folder into that repo (drag and drop on the GitHub page)

That repo is now your persistent memory. Every agent prompt, style update, and reference post lives there and survives across every Claude Code session.

---

## Step 2 — Open Claude Code desktop app

1. Open the Claude Code desktop app (downloaded from claude.com/download)
2. Click on the **Code** tab
3. Start a new session

---

## Step 3 — Run the system for the first time (manual test)

In Claude Code, paste this exact message:

```
I want you to run my Rillix content agent. 

Here's how it works:
- My style library and agent prompts are in my GitHub repo: [paste your GitHub repo URL here]
- First, read the SETUP_GUIDE.md and DAILY_ROUTINE.md from that repo
- Then run the full daily routine: Scanner → Angle + POV → LinkedIn Writer
- Output the completed daily draft document at the end

Today's date is [today's date]. Run it now.
```

Claude Code will read your GitHub repo, run all three agents in sequence, and produce your first draft. This is the manual version — run it whenever you want.

---

## Step 4 — Set up the automated daily Routine

Once you've tested it manually and the output looks good:

1. Inside Claude Code, go to **Routines** (in the sidebar or settings)
2. Create a new Routine
3. Set the schedule: **Daily at 4:00am UTC** (= 9:30am IST)
4. Paste this as the Routine prompt:

```
Run my Rillix daily content agent routine.

Repo: [your GitHub repo URL]

Instructions: Read DAILY_ROUTINE.md from the repo and execute every step exactly as written. Today's date is {{date}}. Output the complete daily draft document.
```

5. Save the Routine

From that point forward, every morning at 9:30am IST, the system runs automatically — no laptop needed, no input from you. The draft is ready by 10am.

---

## Step 5 — How to share a post into the library

Any time you see a post you want the system to learn from or respond to:

Open Claude Code and say:
```
Run the Reference Agent on this post: [paste URL or post text]

[Optional: add a note like "this person is a competitor" or "this post went viral, I want to understand why" or "I want to write something like this"]
```

The agent will research it, extract what's useful, and add it to your STYLE_LIBRARY.md reference section automatically.

---

## Step 6 — How to add people to your Watchlist

Open Claude Code and say:
```
Add [Name] on [Platform — LinkedIn/X/Substack] to my watchlist. They are [why they matter — competitor / mentor / admired creator / potential client].

Update the Watchlist table in library/STYLE_LIBRARY.md in my GitHub repo.
```

From the next daily run onwards, the scanner will watch for their activity.

---

## How to update your style as you evolve

Every few weeks, open Claude Code and say:
```
I want to update my style library. Here are some recent posts that performed well: [paste them]

Review what's working, update the STYLE_LIBRARY.md with any new patterns you notice, and flag anything that should change in how the writing agent works.
```

The system learns over time because you update the library, not because it has memory — which means you're always in control of what it knows.

---

## What to do if a draft isn't right

If the post doesn't sound like you, paste it back into Claude Code and say:
```
This draft doesn't sound like me. Here's what's wrong: [describe specifically]

Fix it. Don't rewrite the whole thing — just [specific change].
```

Over time, patterns you spot repeatedly → add them to the DO NOT section in STYLE_LIBRARY.md.

---

## The one maintenance task worth doing weekly

Every Sunday, spend 5 minutes:
1. Note which posts you actually published that week
2. Note which ones got strong engagement
3. Open Claude Code and say: "Update the engagement signals section of STYLE_LIBRARY.md with these results: [paste]"

That feedback loop is what makes this system compound. Without it, the system keeps producing the same type of posts. With it, it learns what's actually working for your specific audience.
