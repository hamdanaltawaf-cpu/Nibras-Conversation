# DECISION-5B.23 — Number Formatting and Numeric UI Visibility

**Status:** ACCEPTED  
**Date:** 2026-10-28  
**Scope:** YemReact product/UI policy only. This does not prove implementation or testing.

## Global rules
- Use Western digits (0–9) in Arabic and English UI.
- Show full counts with comma thousands separators (example: 1,250); do not abbreviate with K/M.
- Video duration uses minutes:seconds with two-digit seconds (examples: 0:08, 1:05). Card duration remains at the media's top-right. Do not duplicate a duration badge on reaction detail; the player supplies timing.
- Dates use the Gregorian calendar. Arabic UI uses Arabic month names (example: 27 أكتوبر 2026).
- Use a 12-hour clock. Arabic UI uses ص/م (example: 2:35 م), two-digit minutes, and no unnecessary leading zero on the hour. Localize the AM/PM marker in other languages.
- Do not expose internal IDs or technical numbers without an approved user-facing purpose.

## UI locations and visibility
- **Library (/):** no total-library count by default. Video cards may show duration. No views, likes, shares, followers, or social-engagement counters.
- **Search (/?q=; /search redirects to /?q=):** no total-results count or manual result numbering. The five-suggestion cap is not displayed as a count.
- **Reaction detail (/r/[code]):** the player may show elapsed/total duration (example: 0:08 / 0:42). No duplicate duration badge or numbered reaction position.
- **Related/recommended clips:** do not show counts of related or recommended clips and do not turn those counts into headings/labels such as “10 رياكشنات”. If related/recommended clips are displayed, their section must not advertise a numeric total.
- **Collections (/collections and /collections/[slug]):** may show the actual clip count per collection with a clear label (example: “12 مقطعًا”). This is a content count, not engagement. Empty states must be accurate.
- **Account (/account):** signed-in users may see separate, clearly labelled counts for saved reactions and published contributions. Guests see no account statistics. Pending submissions do not count as published contributions.
- **Submission (/submit):** communicate the allowed video duration as 2–60 seconds. Validation may show the actual measured duration and allowed range. Do not show upload-time estimates without reliable data.
- **Settings, login, and help:** no numeric statistics without a clear user need. Any dates/times follow the global rules.
- **Admin/moderation:** if/when defined, follow the same rules. This does not finalize any admin routes.

## Governance
Show numbers only when useful and grounded in real data. Do not invent values, duplicate counts, or add social-network metrics. This decision resolves the open Stage 5-B number/count-formatting topic and prohibits visible counts for related/recommended clips.

Stage 5 remains OPEN. No Stage 5.3 or Stage 6 is created. OPEN-Q-08 and OPEN-Q-09 remain separate/open. SEC-06, upload enforcement, routes, tests, build, and runtime remain unverified. This is product policy, not implementation evidence.

## Current status reconciliation — 2026-10-30
Any statement above that Stage 5 remains open or that OPEN-Q-08/OPEN-Q-09 remain open reflects the state when this decision was recorded. Current status: Stage 5 is **CLOSED FOR DOCUMENTATION ONLY**; OPEN-Q-08 and OPEN-Q-09 are each **CLOSED FOR DOCUMENTATION ONLY** in their separate documents. This decision remains accepted product policy; actual formatting behavior is unverified until separately authorized technical verification. No implementation is authorized by this addendum.
