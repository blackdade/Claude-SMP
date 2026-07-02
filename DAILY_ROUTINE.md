# Rillix Content Agent — Daily Routine
# Schedule: 10:00am IST (4:30am UTC), every day
# Runtime: Claude Code Routines (runs on Anthropic servers, no laptop needed)
# Output: One LinkedIn draft delivered to Sanjay by 10:30am IST

---

## WHAT THIS ROUTINE DOES

Every morning at 9:30am, this routine:
1. Reads the style library and agent prompts from this repo
2. Runs the Scanner Agent to find today's best topic
3. Runs the Angle + POV Agent to build the post brief
4. Runs the LinkedIn Writer Agent to write the draft
5. Outputs the final draft as a document Sanjay can review and post manually

---

## STEP-BY-STEP EXECUTION

### Step 1 — Load context
Read these files before doing anything else:
- `library/STYLE_LIBRARY.md` — Sanjay's voice, formats, proof points, topic rules
- `agents/01_SCANNER_AGENT.md` — Scanner instructions
- `agents/02_ANGLE_POV_AGENT.md` — Angle agent instructions
- `agents/03_LINKEDIN_WRITER_AGENT.md` — Writer instructions

### Step 2 — Run the Scanner Agent
Follow the instructions in `agents/01_SCANNER_AGENT.md` exactly.
Run all 6 searches. Score each candidate. Output the Scanner Report.

### Step 3 — Run the Angle + POV Agent
Take the Scanner Report.
Follow `agents/02_ANGLE_POV_AGENT.md`.
Enforce the topic split rule — check what type of posts have gone out this week.
Output the Post Brief.

### Step 4 — Run the LinkedIn Writer Agent
Take the Post Brief.
Follow `agents/03_LINKEDIN_WRITER_AGENT.md`.
Write the full draft.

### Step 5 — Compile the daily output document
Assemble everything into this format:

---

```
RILLIX CONTENT — DAILY DRAFT
[Date] | Generated at 9:30am IST

═══════════════════════════════════════
WHAT I FOUND TODAY
═══════════════════════════════════════

[Scanner Report — top candidate only, 4-5 lines]

Source: [URL]

═══════════════════════════════════════
SANJAY'S ANGLE
═══════════════════════════════════════

[Post Brief — position, proof point, key points, 6-8 lines]

═══════════════════════════════════════
LINKEDIN DRAFT — READY TO POST
═══════════════════════════════════════

[Full post — copy-paste ready]

═══════════════════════════════════════
NOTES FOR SANJAY
═══════════════════════════════════════

[2-3 lines: why this topic today, any timing considerations, 
what to watch for in comments if this one performs]

Also considered today:
- [Candidate 2 topic in one line]
- [Candidate 3 topic in one line]
(Available on request if you want a different angle today)
```

---

## QUALITY CHECK BEFORE OUTPUTTING

Before finalising, check every item on this list:

- [ ] Hook works as a standalone first line
- [ ] No banned phrases from STYLE_LIBRARY.md
- [ ] CTA is specific (not "what do you think?")
- [ ] Post sounds like Sanjay, not like a content agency
- [ ] Proof point used is real (from the style library, not invented)
- [ ] Topic split rule respected (not the 3rd industry signal post this week)
- [ ] Post length is appropriate for format (not padding, not cut short)
- [ ] Hashtags are at the end, 4-8 total

If any item fails — fix it before outputting. Do not output a draft that fails the checklist.

---

## IF NO STRONG TOPIC IS FOUND TODAY

If all scanner candidates score below 6/9:

Default to one of these evergreen formats:
1. A breakdown of a core Rillix process (clip hunting, launch strategy, distribution system)
2. A stat or observation from Sanjay's own client work (no specific client named without permission)
3. A founder journey moment — something honest about building Rillix right now

Do not force a bad topic. A solid evergreen post beats a weak news-peg post every time.

---

## ROUTINE METADATA

- Timezone: IST (UTC+5:30)
- Run time: 10:00am IST (4:30am UTC)
- Target delivery: 10:30am IST
- Frequency: Daily
- Output: Text document (paste-ready)
- Model: claude-sonnet-4-6
