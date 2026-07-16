# CLAUDE.md — Rillix Media Content Agent System

## Who this is for

Sanjay G, 23, founder of Rillix Media (Chennai, India). Rillix produces podcast production, short-form clips, and launch videos for VCs, tech founders, and early-stage startups (~$400/episode, team of 2-3). This repo is the persistent memory and instruction set for Sanjay's automated content system — every agent prompt, style rule, and reference post lives here so any Claude Code session (manual or scheduled) picks up exactly where the last one left off.

Core belief driving all content: media is the new moat — trust compounds, distribution beats everything.

---

## What this system does

Every morning (or on demand), a pipeline of agents finds a topic, builds Sanjay's angle on it, and writes ready-to-post drafts for LinkedIn, X, and (when warranted) Substack — plus creative asset briefs, image-generation prompts, and video-script triggers for each post. The output is a formatted Google Doc saved automatically to Drive.

This is NOT a news channel. It's a thought-leadership engine that occasionally uses news as a hook. See "Content philosophy" below.

---

## The agent pipeline

Read `library/STYLE_LIBRARY.md`, `library/05_PERSUASION_WRITING_SKILL.md`, and `library/06_IMAGE_PROMPT_FRAMEWORK.md` before any agent runs — they govern voice, persuasion structure, and image style for everything downstream. The image framework matters especially: never generate a flat quote-card or generic infographic — every graphic picks a specific "scroll-stopping" style (cyberpunk anime workstation, data-mosaic matrix art, neon typography, etc.) matched to the post's theme.

1. **agents/01_SCANNER_AGENT.md** — finds today's topics. Runs 9 searches (4 LinkedIn, 4 X, 1 combined) plus daily Watchlist monitoring, scores every candidate (topic-fit rubric, plus an Outlier Score for post-shaped candidates), and calls a Substack yes/no.
2. **agents/07_FEED_SCOUT_AGENT.md** — browses Sanjay's real logged-in LinkedIn and X (Chrome browser MCP) for viral outlier posts in the niche: small accounts with disproportionate engagement. Captures links, verbatim hooks, and remix guidance into a VIRAL INSPIRATION section. Browser-dependent — runs whenever the computer is awake; skips cleanly (never fakes output) when the browser isn't available. Strictly read-only on Sanjay's accounts.
3. **agents/02_ANGLE_POV_AGENT.md** — turns each platform's top topic into a brief: Sanjay's actual position, proof point, key points, engagement hook. One brief per platform. Notes which viral structure from the Feed Scout to remix when one fits.
4. **agents/03_LINKEDIN_WRITER_AGENT.md** — writes 2 LinkedIn posts/day from the briefs.
5. **agents/04_X_WRITER_AGENT.md** — writes 2 X posts/day (format auto-selected: single post, thread, hot take, or video callout).
6. **agents/05_SUBSTACK_WRITER_AGENT.md** — writes a Substack piece 2-3x/week, only when the Scanner says it's warranted.
7. **agents/06_REFERENCE_AGENT.md** — manual trigger. Processes a post Sanjay shares (or the "SAVE" command, see below) into the reference library.

`routines/DAILY_ROUTINE.md` ties all of this together end to end, including the quality checklist and the final Google Drive save step.

---

## Content philosophy

- **50%** thought leadership — how podcast production, guest research, clip hunting, launch strategy, and distribution actually work
- **20-30%** news peg done right — news is the hook, Sanjay's expertise is the content, never just reporting
- **10-20%** client proof and case studies
- **10%** founder journey — honest, vulnerable, real

Never invent proof points or stats — only use what's in `library/STYLE_LIBRARY.md`'s Proof Points list, or new ones Sanjay explicitly provides.

---

## Platform split

- **LinkedIn:** 1-2 posts/day. 60-70% podcast/media authority, 30-40% launch/startup content. Best performing format: numbered system breakdown + comment-trigger CTA.
- **X:** 1-2 posts/day. 50-60% launch/startup, 30-40% podcast. Shorter and punchier than LinkedIn — format auto-selected by topic (single post, thread, hot take, or video callout).
- **Substack:** 2-3x/week, only when a topic genuinely warrants it. 40% personal, 30% industry thought leadership, 20% podcast breakdowns, 10% quote + take. More personal voice. No hard CTA — soft close only.

---

## Where everything is saved

Google Drive (the account connected to this Claude session — currently `rillixmedia@gmail.com`):
- **"Rillix Daily Content"** folder — one Google Doc per day, from the daily routine
- **"Rillix Reference Library"** folder — one Google Doc per saved reference post, from the SAVE command

Docs are built as real HTML (not plain text — plain text doesn't get parsed for Markdown or formatting at all) with real headings, bold field labels, and explicit blank-paragraph spacing (`<p>&nbsp;</p>` between paragraphs, since consecutive `<p>` tags alone don't render a visible gap). See `routines/DAILY_ROUTINE.md` Step 9 for the exact rules if writing a new Drive-saving step.

---

## The SAVE command

Say **"SAVE"** followed by a link, pasted post, or note to file it as a reference post — no need to explain what to do with it. Handled by `agents/06_REFERENCE_AGENT.md`:
- Researches the post and its author — prefers navigating directly with a Chrome browser connector for login-walled platforms (LinkedIn, X) over WebFetch, since WebFetch summaries on those can be inaccurate (wrong engagement numbers, paraphrased instead of verbatim text)
- Captures the **full verbatim post text**, preserving the author's original paragraph structure — never a paraphrase
- Analyses why it works and what angle Sanjay could take
- Saves a formatted Google Doc to **"Rillix Reference Library"** (filename: `[DD Mon] — [topic in 5 words] — [platform if known]`), with a real clickable link, not plain text
- Also logs a row in the Reference Posts Library table in `library/STYLE_LIBRARY.md`
- Confirms with just the filename and Drive link

---

## Watchlist

People and accounts monitored daily for signal and angle inspiration — checked every morning by the Scanner Agent before its other searches. Full list with reasons lives in `library/STYLE_LIBRARY.md`'s Watchlist table:

Gary Vaynerchuk, Alex Hormozi, Dan Koe, Shaan Puri, Sam Parr, Harry Stebbings/20VC, David Weisburd (Rillix client), a16z, Sequoia, YC.

Sanjay can add more anytime by saying: **"Add [name] to my watchlist — [why they matter]."**

Posts from Watchlist people (and any post surfaced by general search) get an **Outlier Score** — post engagement ÷ that account's average engagement × 100. 200+ is a strong outlier worth covering, 500+ is viral and should be prioritised immediately. See `agents/01_SCANNER_AGENT.md` for the full formula and thresholds.

---

## How to run the daily routine

**Manually:** ask Claude to run `routines/DAILY_ROUTINE.md` end to end.

**Automatically:** a scheduled task (`rillix-daily-content`) runs it every morning at ~10:08am IST (4:30am UTC), pulling the latest repo state each time — so any update to these files takes effect on the next run without the schedule itself needing to be touched.
