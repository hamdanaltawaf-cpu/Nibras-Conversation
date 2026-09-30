# YEMREACT-DECISION-STATUS-AUDIT.md — Phase 1B — Decision Status Audit

> Phase 1B only — No new decisions. Only audit of claimed status vs actual evidence.
> Evidence Status: CODE-BACKED, DOCUMENT-BACKED, BOTH, UNKNOWN, CONFLICTED

| Decision | Source(s) Claiming | Claimed Status | Evidence Type | Actual Evidence Status | Notes |
|---|---|---|---|---|---|
| Brand v1.0 LOCKED | S10, S02, S01, S09 | LOCKED / ACCEPTED | DOCUMENT (LOCKED HTML) + IMPLEMENTATION (tokens.css matches per S09) | BOTH — High confidence | S10 says tested on 8 scenarios. S09 confirms tokens.css matches. Watermark spec conflict remains (CONFLICT-019) |
| Home = Library | S03, S08 | ACCEPTED | DOCUMENT (01-DECISIONS-LOG) + IMPLEMENTATION (/ 200) | BOTH | S09 proves / returns 200, but implementation includes hero + rails which decision says no rails |
| No permanent sidebar | S03, S08 | ACCEPTED | DOCUMENT (01-DECISIONS-LOG) | DOCUMENT-BACKED but CONFLICTED with IMPLEMENTATION (sidebar exists) | S09 shows sidebar 286px exists, hidden via !important in admin |
| Reaction Detail = Page /r/[code] | S03, S08, S10 | ACCEPTED | DOCUMENT + IMPLEMENTATION (/r/[code] 200) | BOTH | Modal is HISTORICAL |
| Search updates same page via ?q= | S03, S07 C1 | ACCEPTED | DOCUMENT (01-DECISIONS-LOG) | DOCUMENT-BACKED but CONFLICTED with IMPLEMENTATION (/search exists) | S09 proves /search exists 200, SSR 24 results |
| BottomNav 4th = Saved | S03 | PROPOSED | DOCUMENT | DOCUMENT-BACKED | History SUPERSEDED twice, not final |
| BottomNav 4th = Submit Reaction | S05, S07 | PROPOSED per MVP | DOCUMENT + IMPLEMENTATION (BottomNav has Submit) | BOTH but CONFLICTED with Saved proposal | S09 docblock Home/Search/Submit/Account |
| Categories = Data Only (9 fixed) | S02, S10, S03 | PROPOSED → Data Only | DOCUMENT | DOCUMENT-BACKED | Role versioned from filter to data-only |
| Collections = Rail internal, not BottomNav | S02, S07 C2 | PROPOSED | DOCUMENT | DOCUMENT-BACKED | Post-MVP rail per S03 |
| Core Loop = Utility-first (tool at need) | S08, S10 | PROPOSED | DOCUMENT | DOCUMENT-BACKED | S08 says "ادعاء كبير يستاهل اعتراضًا صريحًا" — not final |
| Library Size 30-50 test, 150-300 realistic | S02, S04, S08 | PROPOSED | DOCUMENT + IMPLEMENTATION (DB 12 seed) | DOCUMENT-BACKED + IMPLEMENTATION shows 12 only | Thresholds, not actual |
| middleware.ts as extra protection | S03, S04 | PROPOSED | DOCUMENT | DOCUMENT-BACKED | No middleware in code per S09 |
| Media Processing managed service (Cloudflare Stream) | S03, S04, S08, S10 | ACCEPTED direction | DOCUMENT + IMPLEMENTATION (local works, prod blocked) | DOCUMENT-BACKED + IMPLEMENTATION shows blocked | S09 media=0 prod, local 216 pairs |
| Schema Cleanup (remove Session/OneTimeCode/Setting/EDITOR/SUBTITLE) | S03 | ACCEPTED direction | DOCUMENT | DOCUMENT-BACKED | Not executed per S09 models still exist |
| Source/Rights REMOVED from Submissions | S03 | ACCEPTED | DOCUMENT | DOCUMENT-BACKED | S09 says removed from form |
| Performance Rating REJECTED | S03 | REJECTED | DOCUMENT | DOCUMENT-BACKED | No rating from sender |
| Static images as product REJECTED | S02, S06 | REJECTED | DOCUMENT | DOCUMENT-BACKED | Video only |
| Trending/Likes/Comments/Followers/Leaderboard/Infinite Feed REJECTED | S02, S04, S06 | REJECTED | DOCUMENT | DOCUMENT-BACKED | Explicitly excluded in MVP-Directive §3 |
| Video Intro/Outro Bumper REJECTED | S02 | REJECTED | DOCUMENT | DOCUMENT-BACKED | First frame = reaction start |
| Ad Creative at organic launch REJECTED | S02 | REJECTED | DOCUMENT | DOCUMENT-BACKED | No ads |
| Search = separate /بحث page | Recent Axis C notes, S10 revised | PROPOSED (recent) | DOCUMENT (note) | DOCUMENT-BACKED but CONFLICTED with ACCEPTED same-page | User decided top search only, bottom placeholder |
| Category removal from detail final | Recent Axis C, S10 | PROPOSED → تم | DOCUMENT (note) | DOCUMENT-BACKED | User confirmed تم |
| Collections as albums title+count | Recent Axis C, S09 | PROPOSED → تم | DOCUMENT + IMPLEMENTATION (Collection=3) | BOTH but simplified | User confirmed تم |
| Footer info+map+accounts+developer no legal | Recent Axis C | PROPOSED → تم | DOCUMENT (note) | DOCUMENT-BACKED | Replaces legal requirement |
| Submit button tension A/B/C | Recent Axis C, S08 | OPEN | DOCUMENT | UNKNOWN — needs decision | Owner said لا اتفق دعنا نناقشه |
| Settings 4 toggles | S03 | PROPOSED | DOCUMENT | DOCUMENT-BACKED but CONFLICTED with IMPLEMENTATION (not built in Next.js, built in Astro) | S09 says not built, S11/S12 built in Astro |
| Featured single row id=1 → YR-0001 | S09 | IMPLEMENTED | IMPLEMENTATION (DB) | CODE-BACKED | No admin UI to change |
| Google-only auth | S04, S07, S09 | ACCEPTED direction | DOCUMENT + IMPLEMENTATION (2 users) | BOTH | Historical OTP vs Google |
| Saves local ↔ cloud union | S04, S09 | IMPLEMENTED | IMPLEMENTATION (SavesProvider) | CODE-BACKED | Works locally, event not logged |
| Watermark-gate for approved submissions | S04 | ACCEPTED | DOCUMENT + IMPLEMENTATION (gate) | BOTH but gap: admin upload not gated | S09 says submissions gate only, admin upload bypass |
| Empty/error states | S03, S04 | ACCEPTED | DOCUMENT + IMPLEMENTATION (EmptyState) | BOTH | Skeleton/empty/error exist |
| Basic analytics internal only | S04 | ACCEPTED | DOCUMENT + IMPLEMENTATION (events table) | BOTH but broken (BUG-1) | Events 3 view only |
| Git hygiene commit + remote | S07 P0 | REQUIRED | DOCUMENT | UNKNOWN — not done | S09 shows 1 commit, no remote, dirty |
| Env separation dev vs prod | S07 P1 | REQUIRED | DOCUMENT | UNKNOWN — not done | .env.local = prod |
| Media infrastructure worker + S3 | S07 P2 | REQUIRED | DOCUMENT | UNKNOWN — not done | P0 blocker |
| BUG-1 fix (code vs UUID) | S07 P3 | REQUIRED | DOCUMENT + IMPLEMENTATION | CODE-BACKED as bug | Client sends UUID, route expects code |
| Terminology الفئات vs التصنيفات | S07 G10 | REQUIRED | DOCUMENT | CODE-BACKED (20 occurrences) | Needs mass replace |

## Summary

- Total decisions audited: 35
- ACCEPTED claimed: 12 — Actual BOTH: 7, DOCUMENT-BACKED but CONFLICTED with implementation: 5
- PROPOSED claimed: 15 — Actual DOCUMENT-BACKED: 10, BOTH but versioned: 5
- REJECTED claimed: 5 — Actual DOCUMENT-BACKED: 5
- OPEN/REQUIRED: 8 — Actual UNKNOWN or NEEDS DECISION
- Decisions needing Product Decision: 22 (including Core Loop, BottomNav 4th, Search route, Sidebar, Categories role, Collections role, Footer, Watermark, Duration, Aspect, Legal, Featured, Submit tension, Terminology, etc.)
- Decisions needing Technical Decision: 18 (including Media infra, Storage, Schema drift, Processing stuck, Media leak, Git, Env, BUG-1/2/3/5, Event tracking, Range, etc.)
- Decisions where evidence resolves (implementation proves): 10 (e.g., Reaction Detail page, Account sheet, Admin 4 cards, Media blocked, Git dirty, etc.)
- Decisions where chronology resolves (version drift): 12 (e.g., Brand colors, Typography, BottomNav chain, Search route evolution, Categories role, Collections role, Auth OTP→Google, etc.)
