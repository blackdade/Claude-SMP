# Rillix Content Agent — Daily Routine
# Schedule: 10:00am IST (4:30am UTC), every day
# Runtime: Claude Code Routines (runs on Anthropic servers, no laptop needed)
# Output: 2 LinkedIn posts, 2 X posts, and a Substack piece (if warranted) delivered by 10:30am IST

---

## WHAT THIS ROUTINE DOES

Every morning:
1. Reads every agent file and the library from this repo
2. Runs the Scanner Agent — separate searches for LinkedIn and X, plus a Substack yes/no call
3. Runs the Feed Scout Agent — browses Sanjay's real logged-in LinkedIn and X for viral outlier posts in the niche (only when the browser is available; skip cleanly otherwise)
4. Runs the Angle + POV Agent — one brief per platform
5. Runs the LinkedIn Writer Agent — 2 posts
6. Runs the X Writer Agent — 2 posts
7. Runs the Substack Writer Agent — only if the Scanner said Substack = Yes today
8. Runs the full quality check on every draft
9. Compiles one complete daily document covering all platforms
10. Saves that document to Google Drive as a Google Doc

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

### Step 2b — Run the Feed Scout Agent (browser-dependent)
Follow `agents/07_FEED_SCOUT_AGENT.md`. Requires the Chrome browser MCP connector (Sanjay's real logged-in browser) — if it isn't available this run, skip and write "Feed Scout skipped — browser not available this run" in the daily doc instead; never fake its findings. Output the VIRAL INSPIRATION section: 3-5 outlier posts from LinkedIn and X with direct links, verbatim hooks, outlier scores, and remix guidance. Strictly read-only on Sanjay's accounts.

### Step 3 — Run the Angle + POV Agent
Follow `agents/02_ANGLE_POV_AGENT.md`. Produce one brief for LinkedIn, one for X, and one for Substack only if the Scanner said yes. Enforce topic split per platform. If the Feed Scout found outliers whose structure fits a brief's topic, note in the brief which viral structure the writer should remix — proven skeleton, Sanjay's substance and voice, never copied wording.

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
- [ ] Opening technique differs from the previous post on the same platform (check yesterday's daily doc) — no back-to-back repeats of the same hook pattern
- [ ] Post format differs from yesterday's on the same platform where the topic allows — rotate the 6 LinkedIn formats, don't default to System Breakdown daily
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
VIRAL INSPIRATION TODAY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Feed Scout output — 3-5 outlier posts with clickable links, verbatim hooks,
outlier scores, and remix guidance. Or "Feed Scout skipped — browser not
available this run." Links must be real <a href> hyperlinks in the Drive doc.]

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

### Step 9 — Save to Google Drive

After all drafts are generated and quality checked, use the connected Google Drive MCP tool to save the complete daily content document (the same content as Step 8, reformatted per the rules below — do not upload flat plain text).

Save as a Google Doc with:
- **Folder:** "Rillix Daily Content" — search for it first (Drive search, `title = 'Rillix Daily Content' and mimeType = 'application/vnd.google-apps.folder'`); create it only if it doesn't already exist. Never create a duplicate folder.
- **Filename:** `Rillix Content — [Day, Date Month Year]`, e.g. `Rillix Content — Friday, 04 July 2026`

**Formatting rules (critical — upload as HTML, not plain text; `text/plain` uploads do NOT get parsed for Markdown, they insert literal `#`/`**` characters with no real formatting):**
- Build the document body as real HTML (`<html><body>...</body></html>`) and upload with `contentMimeType: "text/html"`. Google Drive's import conversion turns HTML tags into native Google Docs formatting.
- Document title: `<h1>`. Section titles (What I Found Today, LinkedIn Post 1, LinkedIn Post 2, X Post 1, X Post 2, Substack, Notes for Sanjay): `<h2>`. Real headings populate the Doc's Outline panel, giving one-click jump-to-section navigation — the closest available substitute for tabs, since this upload path cannot create actual multi-tab Google Docs.
- Field labels inside a Creative Asset block (`Type:`, `Required:`, `Duration:`, `Visual direction:`, `Caption style:`), plus `CREATIVE ASSET`, `IMAGE PROMPT`, `VIDEO SCRIPT TRIGGER`, `Variant A:`, and `Variant B:` — all wrapped in `<b>...</b>`.
- Every other line of body text (including the variant prompt text itself) is a plain `<p>` paragraph, no bold.
- The actual post copy (the LinkedIn/X/Substack text a human copy-pastes to the platform) stays in plain `<p>` tags with no bold or heading markup inside it — that would corrupt what gets copy-pasted. Hashtag lines inside post bodies must stay as plain paragraph text, never inside a heading tag.
- **Consecutive `<p>` tags do NOT render with a visible blank-line gap in the Drive HTML→Docs conversion — verified by inspection, not just by reading the file back (the read-file tool always shows double-newlines regardless of real rendered spacing, so it can't catch this).** To match STYLE_LIBRARY.md's "blank line between every paragraph" rule, insert an explicit empty paragraph (`<p>&nbsp;</p>`) between every paragraph of post copy and between every field in a Creative Asset block. Do this everywhere in the document, not just inside posts.
- Use `<hr>` between major sections and `<ul><li>` for the Notes for Sanjay bullet list.
- Keep paragraphs short so it reads cleanly on mobile.

Document contents, in order (each as a `##` heading):
1. What I Found Today (scanner summary)
2. LinkedIn Post 1 (full draft + creative asset brief, formatted per the rules above)
3. LinkedIn Post 2 (same)
4. X Post 1 (same)
5. X Post 2 (same)
6. Substack (full draft, or "No Substack today — [reason]")
7. Notes for Sanjay (timing, what to watch, other candidates)

Use the connected Google Drive MCP connector's file-creation tool (tool name looks like `mcp__<uuid>__create_file`; if deferred, load it via ToolSearch with query "google drive create file" or "select:create_file"). To create the Google Doc: pass the HTML document as `textContent` with `contentMimeType: "text/html"` and the folder's id as `parentId` — the upload converts the HTML tags into native Google Docs formatting.

After saving, confirm at the end of the run:
- File name created
- Folder it was saved in
- Direct link to the doc

If saving fails, say so explicitly rather than silently skipping this step — the daily document should still be delivered as the routine's final response either way.

### Step 9b — Save a local markdown copy for the Rillix OS dashboard

ALSO save the same daily content as a plain markdown file (not HTML) so it appears in
the Rillix OS dashboard's "Daily Content" panel and its search index:

- Read the vault path from `D:\Claude\SMP\rillix-os\config.json` key `vault_path`
  (NEVER hand-type vault paths — some contain invisible trailing characters).
- Write to: `<vault_path>\Rillix\Content\YYYY-MM-DD — Daily Content.md`
- Content: a `# Daily Content — YYYY-MM-DD` heading, then the same sections as the
  Google Doc in plain markdown, and at the top a line linking to the Google Doc:
  `*Google Doc: <link>*`.
- This step must not replace the Drive save — do both. If the local write fails,
  say so in the final response.

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
- Delivery: Google Doc saved to the "Rillix Daily Content" folder in Google Drive
- Model: claude-sonnet-5
