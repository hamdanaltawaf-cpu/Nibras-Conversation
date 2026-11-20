# YEMREACT-PROVENANCE-MAP.md — Phase 1A — Provenance Map

> Phase 1A only — No decisions. Evidence types: DIRECT (file content itself), DOCUMENT (doc claims), IMPLEMENTATION (code/DB/command), INFERENCE (logical deduction), UNKNOWN (insufficient)

| Claim | Source(s) | Evidence Type | Confidence | Notes |
|---|---|---|---|---|
| Brand v1.0 LOCKED | S10 CLAUDE-FOUNDATION, S02 VISION, S09 ARENA-TECHNICAL (tokens.css matches), S01 TAXONOMY | DOCUMENT + IMPLEMENTATION (S09 says tokens.css matches LOCKED HTML) | High | S10 says tested on 8 scenarios. S09 confirms tokens.css matches LOCKED HTML but watermark spec conflicts. |
| Logo/Qussasa Mark: torn corner + play hole negative | S10 CLAUDE-FOUNDATION | DOCUMENT | High | Described as fill-rule evenodd, paper peel angle. No code check in these 12. |
| Colors Ink #121214, Qishr Amber #C1592E, Paper #F3EAE0, Coral #FF5A36 etc. | S10 CLAUDE-FOUNDATION | DOCUMENT | High for foundation, CONFLICTED with S05 | S05 says #006633 deep green primary — conflict. Need direct LOCKED HTML read. |
| 9 Category Colors: ضحك #F4C430, صدمة #7C5CFF etc. | S10 CLAUDE-FOUNDATION | DOCUMENT | High | Listed explicitly. Enبهار merged into استغراب. |
| Typography Lalezar ≤5 words + Cairo body + Archivo Black/Inter + IBM Plex Mono | S10 CLAUDE-FOUNDATION | DOCUMENT | High | S05 says Cairo + Roboto — conflict. |
| Watermark double-shadow + flip rule Default/Mirrored | S10 CLAUDE-FOUNDATION | DOCUMENT | High | S10 says v2 strengthened after failure on light backgrounds. |
| Reaction = المثل الشعبي الرقمي | S10 CLAUDE-FOUNDATION, S08 ARENA-DISCUSSION | DOCUMENT | High | Central creative concept, never contradicted. |
| Video only, no static images | S02 VISION, S06 CONTENT, S10 CLAUDE | DOCUMENT | High | Explicitly rejected mixed content. |
| Content Type Video duration 2-8s linked to concept | S06 CONTENT, S10 CLAUDE | DOCUMENT | High historically, CONFLICTED now | Later note up to 60s in S01 — versioned. |
| Video not fixed size, up to 1 min max — note only | S01 TAXONOMY (note) | DOCUMENT | Low — note only, not adopted | User correction in recent axis notes, not in synthesis files. |
| Home = Library, no separate /search conceptually | S03 IA, S08 DISCUSSION, S09 TECHNICAL (code has / as library) | DOCUMENT + IMPLEMENTATION | High — ACCEPTED in 01-DECISIONS-LOG cited by S03/S08 | S09 confirms / returns 200. |
| Search updates same page via ?q= | S03 IA, S04 FEATURES, S08 DISCUSSION | DOCUMENT | Medium — ACCEPTED but later versioned to separate /بحث | S07 C1 says keep home as only search entry. |
| Reaction Detail = Page /r/[code] not Modal | S03 IA, S04 FEATURES, S08 DISCUSSION, S10 CLAUDE | DOCUMENT + IMPLEMENTATION (S09 shows /r/[code] 200) | High — ACCEPTED | Modal rejected for SEO/shareability. |
| No permanent sidebar ACCEPTED | S03 IA, S08 DISCUSSION | DOCUMENT | Medium — ACCEPTED but code has sidebar | S09 shows sidebar 286px exists, hidden via !important in admin. |
| BottomNav 4 items mobile | S03 IA, S05 UI, S08 DISCUSSION, S12 MANUS-V2 | DOCUMENT + IMPLEMENTATION | High existence, CONFLICTED on 4th item | 4th item evolution: Submit → Collections → Saved. |
| BottomNav 4th = Saved PROPOSED | S03 IA, S08 DISCUSSION | DOCUMENT | Medium | History SUPERSEDED twice. |
| BottomNav 4th = Submit Reaction per MVP | S05 UI, S07 GAPS C2, S09 TECHNICAL | DOCUMENT + IMPLEMENTATION (S09 shows BottomNav has Submit) | Medium | S09 docblock says Home/Search/Submit/Account. |
| Categories = fixed 9, data-only / filter | S03 IA, S02 VISION, S10 CLAUDE | DOCUMENT | Medium — role versioned | Early filter bar, later data-only + color. |
| Collections = editorial, future rail post 150-300 | S03 IA, S07 GAPS, S08 DISCUSSION | DOCUMENT | Medium | Not built until threshold. |
| Save = local ↔ cloud, guest localStorage yr:saved | S04 FEATURES, S09 TECHNICAL, S05 UI | DOCUMENT + IMPLEMENTATION | High — code shows union logic | S09 details SavesProvider union, optimistic toggle. |
| Save requires Google account only (recent axis) | Recent Axis C notes (not in these 12, but referenced in S01 note) | DOCUMENT (note) | Low — not in these 12, but S10 says guest-first historically | Tension: guest-first vs Google required. |
| Submit = video + optional note minimal | S06 CONTENT, S10 CLAUDE | DOCUMENT | Medium — evolved from many fields | S04 shows keywords/sourceUrl ignored. |
| Account = Menu/Sheet not full page | S03 IA, S05 UI, S08 DISCUSSION | DOCUMENT | High — ACCEPTED | Matches weight in product. |
| Admin = 4 cards Reactions/Categories/Collections/Submissions | S09 TECHNICAL, S04 FEATURES | IMPLEMENTATION | High — code shows 4 cards, curl 200 | S09 says no Featured/Users/Audit UI. |
| Auth = Google-only (Auth.js v5 JWT) | S04 FEATURES, S07 GAPS, S09 TECHNICAL | DOCUMENT + IMPLEMENTATION | High — code shows Google provider conditional, 2 users in DB | Historical OTP (ADR-0001) vs Google. |
| Auth = Manus OAuth + GOOGLE_CLIENT_ID server | S12 MANUS-V2, S11 MANUS-V1 | DOCUMENT + IMPLEMENTATION (S12 says oauth.ts) | Medium — WebDev project specific | Not in Next.js stack. |
| Media pipeline = validate + storage.put + enqueueProcessing + ffprobe/ffmpeg thumbnail + watermark | S04 FEATURES, S09 TECHNICAL, S06 CONTENT | DOCUMENT + IMPLEMENTATION | High for local logic, CONFIRMED blocked in prod | S09: 829 files local, 216 pairs, media=0 in prod Neon. |
| Storage = LocalStorage ./storage default, S3 optional via minio | S04 FEATURES, S09 TECHNICAL | IMPLEMENTATION | High — interface exists | S3 driver tested with mocks only. |
| Search = pg_trgm similarity + ILIKE + keyset cursor | S04 FEATURES, S09 TECHNICAL | IMPLEMENTATION | High — code search method | S09: /api/reactions?q=خبر returns 2. |
| Saves counts always zero due to UUID vs code | S09 TECHNICAL, S07 GAPS BUG-1 | IMPLEMENTATION | High — COMMAND OUTPUT 404 + DB events=3 view only | Client sends id UUID, route expects code. |
| Collection media include PROCESSED vs WATERMARKED | S09 TECHNICAL, S07 GAPS BUG-2 | IMPLEMENTATION | High — code L7 | Causes placeholder. |
| DurationMs NULL due to seed not writing | S09 TECHNICAL, S07 GAPS BUG-3 | IMPLEMENTATION | High — CODE + DB NULL | Seed defines duration not written. |
| 3 raw indexes not in schema (GIN etc.) | S09 TECHNICAL, S07 GAPS G5 | IMPLEMENTATION | High — migrate diff DROP INDEX | Drift. |
| Processing status stuck no timeout | S09 TECHNICAL, S07 GAPS G6 BUG-5 | IMPLEMENTATION | High — code processor.ts | No lease. |
| /media/submissions/* streams without auth | S09 TECHNICAL, S07 GAPS G7 SEC-3 | IMPLEMENTATION | High — code media/[...key]/route.ts | Security leak. |
| Git: 1 commit 331c1b3, 28 modified, 119 untracked, no remote | S09 TECHNICAL, S07 GAPS G11 | IMPLEMENTATION | High — git status output | Risk loss. |
| Env .env.local = production Neon creds | S09 TECHNICAL, S07 GAPS G8 | IMPLEMENTATION | High — file contains prod creds | Dev = prod. |
| Terminology الفئات vs التصنيفات 20 occurrences | S07 GAPS G10, S08 DISCUSSION | DOCUMENT + IMPLEMENTATION (grep) | High | Mass replace needed. |
| Footer: brand description + groups link | S03 IA, S05 UI | DOCUMENT | Medium | Recent Axis C says info+map+accounts+developer no legal — versioned. |
| Core Loop utility vs discovery vs hybrid | S02 VISION, S08 DISCUSSION, S10 CLAUDE, S11 MANUS-V1 | DOCUMENT | CONFLICTED | Utility-first vs Hybrid vs library-first. |
| Library size 30-50 test, 150-300 realistic | S02 VISION, S04 FEATURES, S08 DISCUSSION, S09 DB 12 reactions | DOCUMENT + IMPLEMENTATION (DB counts) | Medium | DB shows 12 seed only. |
| Settings System localStorage yem-data-saver etc. | S11 MANUS-V1, S12 MANUS-V2, S03 IA (PROPOSED) | DOCUMENT + IMPLEMENTATION (S11/S12) | Medium — built in Astro, not in Next.js | S09 says not built. |
| Debounce 300ms + recent searches 4 | S11 MANUS-V1 | IMPLEMENTATION (S11 claims) | Medium — React/Vite path | Not in Next.js. |
| Content 9 categories 13 reactions in WebDev | S12 MANUS-V2 | DOCUMENT | Medium — numeric check in conversation | S09 shows 9 categories 12 reactions — similar. |
| No video files in workspace, mock API used | S11 MANUS-V1, S12 MANUS-V2, S06 CONTENT | DOCUMENT + IMPLEMENTATION | High — .storage has 829 test files but no real production video | Production = seed only. |
| Brand tokens in tokens.css match LOCKED HTML | S09 TECHNICAL | IMPLEMENTATION | High — S09 says match | But S05 values differ — need direct HTML read to confirm. |
