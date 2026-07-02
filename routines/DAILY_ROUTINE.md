# Rillix Content Agent — Daily Routine
# Schedule: 10:00am IST (4:30am UTC), every day
# Runtime: Claude Code Routines (runs on Anthropic servers, no laptop needed)
# Output: 2 LinkedIn posts, 2 X posts, and a Substack piece (if warranted) delivered by 10:30am IST

---

## WHAT THIS ROUTINE DOES

Every morning:
1. Reads every agent file and the library from this repo
2. Runs the Scanner Agent — separate searches for LinkedIn and X, plus a Substack yes/no call
3. Runs the Angle + POV Agent — one brief per platform
4. Runs the LinkedIn Writer Agent — 2 posts
5. Runs the X Writer Agent — 2 posts
6. Runs the Substack Writer Agent — only if the Scanner said Substack = Yes today
7. Runs the full quality check on every draft
8. Compiles one complete daily document covering all platforms
9. Delivers that document to Sanjay's Gmail

---

## STEP-BY-STEP EXECUTION

### Step 1 — Load context
Read, in order:
- `library/STYLE_LIBRARY.md`
- `library/05_PERSUASION_WRITING_SKILL.md`
- `agents/01_SCANNER_AGENT.md`
- `agents/02_ANGLE_POV_AGENT.md`
- `agents/03_LINKEDIN_WRITER_AGENT.md`
- `agents/04_X_WRITER_AGENT.md`
- `agents/05_SUBSTACK_WRITER_AGENT.md`

### Step 2 — Run the Scanner Agent
Follow `agents/01_SCANNER_AGENT.md` exactly. Run all 9 searches (4 LinkedIn, 4 X, 1 combined). Score every candidate. Output the Scanner Report, including the Substack yes/no call and any Watchlist alerts.

### Step 3 — Run the Angle + POV Agent
Follow `agents/02_ANGLE_POV_AGENT.md`. Produce one brief for LinkedIn, one for X, and one for Substack only if the Scanner said yes. Enforce topic split per platform.

### Step 4 — Run the LinkedIn Writer Agent
Follow `agents/03_LINKEDIN_WRITER_AGENT.md`. Write 2 full posts from the brief and the second-strongest LinkedIn candidate.

### Step 5 — Run the X Writer Agent
Follow `agents/04_X_WRITER_AGENT.md`. Write 2 full posts (format auto-selected per post) from the brief and the second-strongest X candidate.

### Step 6 — Run the Substack Writer Agent (conditional)
Only if Step 2 said Substack = Yes. Follow `agents/05_SUBSTACK_WRITER_AGENT.md`.

### Step 7 — Quality check every draft
- [ ] Hook works standalone
- [ ] No banned phrases from STYLE_LIBRARY.md
- [ ] CTA is specific (not "what do you think?")
- [ ] Sounds like Sanjay, not an AI or a content agency
- [ ] Proof point used is real (from STYLE_LIBRARY.md, never invented)
- [ ] Topic split respected per platform
- [ ] Creative asset brief included on every post
- [ ] Hashtags correct for platform (LinkedIn 4-8, X 0-2, Substack none)

If any item fails, fix it before outputting. Do not output a draft that fails the checklist.

### Step 8 — Compile the daily output document

```
RILLIX DAILY CONTENT — [DATE] — Generated 10:00am IST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

WHAT I FOUND TODAY
[Scanner summary — top pick for each platform, 3-4 lines each]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LINKEDIN POST 1
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Full draft]

CREATIVE ASSET:
[Full brief]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LINKEDIN POST 2
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Full draft]

CREATIVE ASSET:
[Full brief]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
X POST 1
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Full draft or thread]

CREATIVE ASSET:
[Full brief]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
X POST 2
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Full draft or thread]

CREATIVE ASSET:
[Full brief]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SUBSTACK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Full piece — or "No Substack today: [reason]"]

CREATIVE ASSET:
[Full brief if applicable]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NOTES FOR SANJAY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Why these topics today
- Timing notes (post LinkedIn before 9am or after 5pm IST for best reach)
- What to watch in comments if a post spikes
- Other candidates available on request: [one line each]
```

### Step 9 — Email delivery

Send the complete daily content document (the exact output from Step 8) to Sanjay's Gmail.

**Delivery method:** a Gmail connector is available to this account, but it only supports creating drafts — there is no send capability. "Delivery" therefore means creating a Gmail draft, not sending a live email; Sanjay opens Gmail and reads it straight from Drafts, no send required on the agent's part. Do not treat the absence of a send tool as an error — this is expected and correct. If a send-capable tool is ever connected instead, use it and actually send.

Use the connected Gmail MCP connector's `create_draft` tool (tool name looks like `mcp__<uuid>__create_draft`; if deferred, load it via ToolSearch with query "gmail draft" or "select:create_draft").

Email fields:
- **To:** i2ksanjayg@gmail.com
- **Subject:** Rillix Daily Content — [Date] — [Today's top topic in 5 words, drawn from the Scanner Report's top recommended candidate]
- **Body:** the full daily output document from Step 8, exactly as generated — all platform drafts, all creative asset briefs, all image prompts, all video script triggers, and the Notes for Sanjay section. Nothing summarized or trimmed. Format it cleanly for mobile reading: keep each platform section separated with the same ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ dividers used in the document itself, short paragraphs, no wide tables.

Confirm at the end of the run whether the draft was created successfully. If it fails, say so explicitly rather than silently skipping this step — the daily document should still be delivered as the routine's final response either way.

---

## IF NO STRONG TOPIC IS FOUND ON A PLATFORM

Default to an evergreen Topic Bank item from STYLE_LIBRARY.md for that platform specifically — never force a weak news peg on any single platform just because another platform found something strong.

---

## ROUTINE METADATA

- Timezone: IST (UTC+5:30)
- Run time: 10:00am IST (4:30am UTC)
- Target delivery: 10:30am IST
- Frequency: Daily
- Output: 2 LinkedIn posts, 2 X posts, Substack (conditional) — one compiled document
- Delivery: Gmail draft to i2ksanjayg@gmail.com (create_draft only — no send capability currently connected)
- Model: claude-sonnet-5
