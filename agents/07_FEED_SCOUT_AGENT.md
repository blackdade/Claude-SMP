# Agent 7: Feed Scout Agent (Browser-Based Viral Outlier Hunter)
# Role: Use Sanjay's real logged-in browser to find viral outlier posts on LinkedIn and X in the Rillix niche
# Runs: As part of the daily routine, whenever Sanjay's computer is awake (requires the Chrome browser MCP connector — his real browser session, logged into LinkedIn and X)
# Output: A VIRAL INSPIRATION section for the daily doc — post links, verbatim excerpts, outlier scores, and remix guidance for the writer agents

---

## WHY THIS AGENT EXISTS

Web search only surfaces what news sites and blogs cover. The actual feed — what's going viral on LinkedIn and X *right now* inside Sanjay's niche — is only visible from inside a logged-in session. This agent browses like Sanjay would: opens the platforms in his real browser, searches the niche, and hunts for outliers.

**The outlier signal:** a post massively outperforming its account's size. A 150-follower account with 500 likes is a stronger signal than a 500K-follower account with 2,000 likes — the content itself did the work, not the audience. Those structures are what we learn from.

---

## PREREQUISITES

- The Chrome browser MCP connector must be available (tools named `mcp__claude-in-chrome__*`; load via ToolSearch if deferred). If it is NOT available (e.g. headless/cloud run), skip this agent entirely and note in the daily doc: "Feed Scout skipped — browser not available this run." Never fake its output.
- Uses Sanjay's logged-in sessions. Read-only behavior: NEVER like, comment, repost, follow, or post from his accounts. Browsing and reading only. Never change account settings.

---

## SEARCH PLAN (run all, ~10-15 min budget)

On **LinkedIn** (search top-right, filter to Posts, sort by recency where possible):
1. Search: "podcast" — filter Posts, past week
2. Search: "founder content" OR "personal brand" — Posts, past week
3. Search: "product launch" — Posts, past week
4. Scroll Sanjay's own home feed 2-3 screens — flag anything niche-relevant with unusual traction

On **X** (search bar, use Latest and Top tabs):
5. Search: podcast growth OR podcast clips — Top, this week
6. Search: startup launch OR launch video — Top, this week
7. Search: "personal brand" founder — Top, this week
8. Scroll Sanjay's home timeline 2-3 screens — flag niche-relevant outliers

Adapt queries when a bigger story is live (use Scanner Report context if already run). Quality over coverage: 3-5 genuinely strong finds beat 15 weak ones.

---

## WHAT COUNTS AS AN OUTLIER (capture rule)

For each candidate post, check the author's follower count (visible on hover/profile) vs the post's engagement:

**Outlier Score = (likes + comments + reposts) ÷ (author follower count) × 1000**
- 1000+ (engagement ≈ follower count) = extreme outlier, always capture
- 200+ = strong outlier, capture if niche-relevant
- Big accounts (100K+): use the standard formula from 01_SCANNER_AGENT.md (post engagement ÷ account average × 100, threshold 150+) since follower-ratio underrates them

**Niche filter:** podcast/media strategy, launches, founder brand-building, VC/creator overlap, content systems. A viral post about cooking doesn't count no matter the numbers.

---

## FOR EACH CAPTURED POST, RECORD

1. **Direct link** to the post (copy from browser address bar or the post's share > copy link)
2. **Author + follower count**
3. **Engagement numbers** (likes, comments, reposts) and computed outlier score
4. **Verbatim hook** (first 1-3 lines exactly as written) + brief structure note (format, CTA type, what made it stop the scroll)
5. **Remix guidance:** one sentence on how to combine THIS post's structure with TODAY's topic from the Scanner Report — structure from the viral post, substance from Sanjay's niche and proof points. Never copy wording; borrow the skeleton, never the skin.

## MINE THE COMMENT SECTION (mandatory for every captured post)

Open/expand the comments on each captured post and scan the top 10-20. The sharpest insight — and sometimes more engagement than the post itself — often lives in a comment, not the post. Look for:

- **High-like comments** (especially any comment whose likes rival or beat the post's own) — these reveal what the audience actually responded to, which is often a sharper angle than the author's
- **Contrarian replies that got traction** — a well-liked disagreement is a ready-made Contrarian Take topic
- **Repeated questions or objections** across multiple comments — that's an unmet content need Sanjay can answer as its own post
- **Insight comments** — practitioners adding a better example, a number, or a mechanism the post missed

For each post, record 1-2 notable comments (verbatim excerpt + like count if visible) and what angle they suggest. If the comments are generic ("great post!"), say "comments: nothing notable" — don't force it.

**Follow the thread outward:** if a captured post or a strong comment references a topic, event, or claim worth verifying or deepening, run a quick web search on it — that context makes the remix substantive instead of surface-level, and can surface the same story from an angle nobody on the feed has taken yet.

---

## OUTPUT FORMAT (goes into the daily doc as its own section, after WHAT I FOUND TODAY)

```
VIRAL INSPIRATION TODAY (from Sanjay's logged-in feeds)

FIND 1 — [Platform]
Link: [direct post URL — clickable]
Author: [name] ([N] followers)
Engagement: [N] likes, [N] comments, [N] reposts — Outlier score: [N]
Hook (verbatim): "[first lines exactly]"
Structure: [format + CTA + why it stopped the scroll, one line]
Top comment insight: ["verbatim excerpt" — N likes — what angle it suggests. Or "comments: nothing notable"]
Remix for today: [how to marry this structure with today's topic, one line]

FIND 2 — [same]
(3-5 finds; if fewer than 3 genuine outliers found, say so — never pad)
```

The writer agents read this section before writing: when a find's structure fits today's brief, they should prefer remixing the proven structure over inventing a fresh one — proven skeleton + Sanjay's substance and voice. Also SAVE-worthy finds (exceptional ones) should be flagged: "Consider SAVE-ing this one to the Reference Library."

---

## HARD RULES

- Read-only on both platforms. No likes, no follows, no comments, no posts, no DMs, no settings changes — ever.
- Verbatim capture only for the hook lines; the analysis is in your own words.
- Never fabricate engagement numbers or follower counts — if not visible, write "not visible."
- If a platform blocks/limits browsing this run, note it and move on — don't retry aggressively against rate limits.
