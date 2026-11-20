# YEMREACT-HISTORICAL-TIMELINE.md — Phase 1A — Historical Timeline

> Phase 1A only — No decisions, only evidence-based timeline. No CURRENT unless explicit evidence.
> Sources: S01-S12

## Timeline (Evidence-Based, Not Assumed Order)

### Stage 0 — Foundation Idea (Owner)
- **Evidence:** S10 CLAUDE-FOUNDATION: "المشروع بدأ من فكرة جاهزة مسبقًا عند صاحب المشروع" — صفحة تجمع لقطات رياكشن يمنية نادرة ومدفونة
- **Type:** FOUNDATION
- **Confidence:** High — S10, S02
- **Artifacts:** Idea owner, not Claude

### Stage 1 — Brand Foundation & LOCK
- **Evidence:** S10: Brand v1.0 built around "الرياكشن = المثل الشعبي الرقمي" — Logo Qussasa torn corner + play hole, colors Ink/Qishr Amber/Paper/Coral, 9 category colors, fonts Lalezar/Cairo, watermark strengthened with double shadow after failure on light backgrounds, safe area guides, clip system 9:16 primary + 1:1 secondary 2-8s
- **S02:** Brand v1.0 LOCKED confirmed
- **S01:** Lists YemReact-Brand-v1.0-LOCKED.html as 🔴 Critical locked
- **S09:** tokens.css matches LOCKED HTML (but watermark spec conflict)
- **Type:** BRAND LOCK
- **Confidence:** High — LOCKED HTML exists, tested on 8 scenarios per S10
- **Date hint:** Before prototype — no explicit date in these 12, but S10 says before any real code

### Stage 2 — Content System & Launch Kit (Facebook)
- **Evidence:** S10: Content System 3 caption formats (اقتباس مباشر, لمّا... موقفي, بلا نص), 9 fixed categories, Collections admin-edit, review flow Validate→Optimize→Preview→Approve/Reject/Edit→Publish, editorial rules no intro, max 3 emoji
- **S06:** Asset inventory PNGs (Profile 720x720, Cover 1640x720, PostTemplate 1080x1350, CategoryCollection, Announcements Intro/ComingSoon/Milestone, Story RequestReaction), safe-area guides, copy deck, quality rubric 6 criteria, production checklist
- **S02:** Content System Launch Kit referenced
- **Type:** CONTENT SYSTEM
- **Confidence:** Medium-High — assets listed in S01, S06
- **Status:** READY for Facebook per S06, but no real video in prod per S09

### Stage 3 — Product Vision & MVP Directive
- **Evidence:** S02: Vision "لمكتشفون اليمنيون – مكتبة رياكشنات يمنية مصنفة مسبقاً قابلة للبحث" — Mission synthesized (searchable catalogue 30-50 clips, instant usability pre-cut 2-8s, cultural legitimacy dialect)
- **S04:** MVP Directive defines mandatory 10 features (core loop Situation→Search→Preview→Take→Use, searchable catalogue home, detail page /r/[code], save local↔cloud, submission workflow, admin CRUD, Google-only auth, watermark-gate, empty/error states, internal analytics) + explicitly excluded (infinite scroll, trending, leaderboards, comments, followers, PWA etc.)
- **S08:** Product principles انتقاء أهم من الكمية, "خذها. حطها. يمنية.", Yemeniness from spirit not cliché, mark never touches face, reaction ready to use not watched
- **Type:** PRODUCT VISION + MVP SCOPE
- **Confidence:** High for MVP mandatory list — traceable to MVP-Directive

### Stage 4 — IA & Sitemap Decisions (ACCEPTED)
- **Evidence:** S03: IA Overview — Home=library ACCEPTED, Search updates same page via ?q= ACCEPTED, Detail page /r/[code] ACCEPTED not modal, BottomNav 4 items (Library/Saved/Account/Settings), Desktop no permanent sidebar ACCEPTED, Schema cleanup (remove Session/OneTimeCode/Setting/EDITOR/SUBTITLE) ACCEPTED, Media processing managed service ACCEPTED direction
- **S08:** Confirms 4 ACCEPTED: Brand LOCKED, Detail page, No sidebar, Home=library
- **S01:** Lists 00-INDEX, 01-DECISIONS-LOG as critical
- **Type:** IA DECISIONS
- **Confidence:** High for 4 ACCEPTED items (cited as ACCEPTED in 01-DECISIONS-LOG), Medium for rest (PROPOSED)

### Stage 5 — Prototypes (JSX/HTML)
- **Evidence:** S10: YemReact-Web-Prototype.jsx — React SPA single component, 12 mock items, interactions search/filter/save/detail, no backend, no real video, labeled تجريبية — built by Claude
- **S05:** Component catalog derived from JSX/HTML prototypes (ReactionCard, ReactionDetail, SearchBar, CategoryNav, BottomNav, AccountMenu etc.)
- **S01:** Lists index.html, index (1)-(4).html, Templates-Source-Editable.html as prototypes
- **S11:** References ui-prototype/index.html as "النسخة المرجعية النهائية قبل أي تنفيذ" — but not built by Claude, external reference
- **Type:** PROTOTYPE
- **Confidence:** Medium — prototypes exist but not production, mock data only
- **Note:** S08 says 3 conflicting design references (Prototype v1/v2/v3 + Hybrid Spec + actual implementation)

### Stage 6 — Technical Foundation (Phase A)
- **Evidence:** S10: After GO, Claude wrote package.json, tsconfig.json, next.config.mjs, .env.example, prisma/schema.prisma (Category + Reaction only), lib/tokens.ts, lib/categories.ts — Phase A only, no DB connection, no deploy, no real run (Claude env no internet)
- **S09:** Later implementation Next.js 15.5.23 + React 19.2.8 + Prisma 5.22 + Neon + Auth.js v5 + Storage abstraction + Media pipeline (LocalMediaService) — 45 routes, 15 models, 7 enums, 4 migrations, 171 unit tests, 94 E2E read-only, 829 files in .storage local, 216 watermarked pairs, media=0 in prod
- **Type:** TECHNICAL FOUNDATION → IMPLEMENTATION
- **Confidence:** High for S09 technical state (CODE + DB + COMMAND OUTPUT 2026-09-02), Low for Claude's Phase A being used as base (UNKNOWN per S10)

### Stage 7 — Manus V1 React/Vite Improvements + Astro/Preact Restore
- **Evidence:** S11: Manus V1 — Header rebuilt Sidebar→Top Header Glassmorphism, Footer rebuild, Hero 520px/460px 1180px max-width, useDebounce 300ms, useRecentSearches 4, suggestions Yemeni, random reaction, Modal قريباً simplified with Focus/Escape, lazy/Suspense App.tsx, admin.css split, compression/cache, React Query staleTime, favicon SVG, SearchBar expansion, catalog error Arabic fixed + retry, Google Client ID fallback server, Settings System UserSettingsContext localStorage + SettingsPanel + themes dark/OLED/Warm Paper + Data Saver + share prefs in Astro, Mock API for prerender, public preview via Manus computer domain
- **S11:** Two stacks: React/Vite/TypeScript (tRPC 11, Express 4, Tailwind 4 raw CSS) and Astro 7 + Preact + Fastify (web/ + src/ server)
- **Type:** UI IMPROVEMENTS + SETTINGS SYSTEM (historical)
- **Confidence:** Low-Medium — local implementation claimed, no production proof, Mock API, temporary preview links
- **Date hint:** No explicit date, but after technical foundation

### Stage 8 — Manus V2 WebDev Project yemreact-deploy
- **Evidence:** S12: Manus V2 — Project WebDev full-stack React/Vite/Express/tRPC/Drizzle/MySQL, path /home/ubuntu/yemreact-deploy, checkpoint 6e9451ff, schema users/categories/reactions/submissions/saved_reactions, routers library.categories/list/byId, groups.list, submissions.create/mine/all/status/review, UI pages Home/Search/Submit/Groups/Account/Saved/Settings/Track/Reaction/Admin, BottomNav Library/Search/Submit/Account, loading/error/empty states, code-splitting lazy/Suspense manualChunks, tests 5 files 13 tests, seed 9 categories 13 reactions verified numerically, Manus OAuth + GOOGLE_CLIENT_ID server, build success, no production publish proven, Google OAuth not end-to-end
- **Type:** IMPLEMENTATION WEBDEV
- **Confidence:** Medium — checkpoint exists, build success, but production publish UNKNOWN, no video files
- **Date hint:** After V1, latest checkpoint 6e9451ff

### Stage 9 — Arena Discussion Track (Nibras ↔ User ↔ Arena)
- **Evidence:** S08: Discussion track — 13 axes, decisions by status, tensions (library discovery vs utility tool, BottomNav 4th chain Submit→Collections→Saved, Modal vs Page, 3 layers taxonomy, Featured/New/Collections rails, 3 conflicting design refs, terminology فئات vs تصنيفات, submit as growth engine chicken-egg), open questions (value vs screen record, good content rubric, acquisition channel, chicken-egg submissions, no numeric success definition, Yemeni network not measured)
- **Recent Axis C notes (referenced in S01 note):** Search top only + bottom placeholder, Collections as albums title+count, Category removal final, Admin 4 sections + 3 permissions, Footer info+map+accounts+developer no legal, Submit button tension A/B/C
- **Type:** DISCUSSION (notes only)
- **Confidence:** Medium-High for tensions — independent witness, no implementation claim
- **Date hint:** After Manus, before technical audit? Actually S08 is historical independent, but recent axis notes mention up to 1 min duration — latest in chain

### Stage 10 — Technical Audit & Handoff (2026-09-02)
- **Evidence:** S09: ARENA-TECHNICAL-HANDOFF — Date 2026-09-02, repo /home/user/yemreact-next HEAD 331c1b3 master, 1 commit 2026-08-24, no remote, 28 modified + 119 untracked, Neon prod DB counts (User=2 ADMIN hamdanaltawaf@gmail.com + USER qnasly189@gmail.com, Category=9 active, Reaction=12 published seed durationMs NULL, ReactionKeyword=62, MediaAsset=0, Collection=3, CollectionItem=8, Featured id1→YR-0001, Submission=0, SavedReaction=2 both YR-0011, Event=3 view only, AuditLog=0), routes 45, typecheck/lint/prettier clean, build 45 routes, 94/94 E2E read-only, 47 screenshots 0 overflow, curl 200/404, Google OAuth worked at least once, BottomNav has Submit, sidebar exists, /media/<key> 200, admin pages show data, Saves event not logged BUG-1 404, schema drift 3 indexes, processing stuck, seed duration null, media in prod blocked, Git dirty, env prod creds, terminology conflict, etc.
- **S07:** Gaps G1-G12 P0-P3, contradictions C1-C4, risk matrix R1-R7, roadmap P0-P8, final verdict 60% (Foundation 90, Backend 80, DB 75, Auth 80, Media 35, Admin 70, Content 10, UX 55, UI 60, Testing 60, Deployment 40)
- **Type:** TECHNICAL AUDIT — CODE-BACKED
- **Confidence:** High — best technical truth, COMMAND OUTPUT + DATABASE SELECT
- **Date:** 2026-09-02 explicit

### Stage 11 — Synthesis Packages (61 files → 7 files)
- **Evidence:** S01: 00_PROJECT_TAXONOMY_AND_FILE_MAP.md claims to prove every file read from 68 unique files, classification matrix 78 entries, de-duplication log, dependency graph, terminology unification
- **S02-S07:** Synthesis files generated from 68 files, phase 2-7, each claims fully grounded in uploaded files with inline citations
- **Type:** SYNTHESIS (analysis of previous files, not primary)
- **Confidence:** Medium — claims traceability but may mix historical with current, may resolve conflicts without explicit owner تم
- **Date hint:** After technical audit? Actually synthesis appears to be after all handoffs, attempting to unify

### Stage 12 — Current State Verifiable (as of these 12)
- **Evidence:** S09: Working tree is reference (not commit), .env.local = production, no remote, no CI, no isolated test DB, 218 integration/E2E cannot run safely, media pipeline local only, events 3 view only, saves 2, no submissions, no audit logs
- **S07:** Overall 60% weighted, blockers P0 Git hygiene + Media infra + Env separation + BUG-1
- **S08/S10:** Brand LOCKED remains high-confidence, Core Loop still DISCUSSION, BottomNav 4th not final, Categories role still questioned
- **Type:** CURRENT VERIFIABLE (only what S09 proves)
- **Confidence:** High for S09 DB counts and code existence, UNKNOWN for production URL, Vercel env vars, bucket, ffmpeg in prod, Manus relation

## Notes on Order
- Foundation → Brand LOCK → Content System → Vision/MVP → IA Decisions → Prototypes → Technical Foundation Phase A → Manus V1/V2 → Discussion Track → Technical Audit 2026-09-02 → Synthesis 7 files is the most plausible order based on evidence, but S01-S12 themselves do not give explicit timestamps for all stages except S09 date 2026-09-02 and commit 2026-08-24.
- Do not assume Manus V1/V2 happened after Arena Discussion — S11/S12 are independent handoffs with no sync claim.
- S01 taxonomy claims v2 supersedes v1 — versioned.

## Summary Counts
- Sources: 12
- Timeline stages identified: 12 (Foundation to Current Verifiable)
- High-confidence facts in timeline: Brand LOCK, Home=library, Detail page, No sidebar (ACCEPTED), Media blocked, Git dirty, etc.
- UNKNOWN periods: Manus relation to current production, exact production URL, Vercel env vars, ffmpeg in prod, real user count.
