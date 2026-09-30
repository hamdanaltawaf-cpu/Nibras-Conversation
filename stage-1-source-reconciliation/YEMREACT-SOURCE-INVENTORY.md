# YEMREACT-SOURCE-INVENTORY.md — Phase 1A — Complete Source Inventory

> Phase 1A only — No decisions, no implementation, no Git/DB changes. Only inventory and classification.
> Date: 2026-09-11
> Sources examined: 12

## Inventory Table

| ID | Source | Type | Historical Scope | Primary Subject | Reliability | Limitations |
|---|---|---|---|---|---|---|
| S01 | 00_PROJECT_TAXONOMY_AND_FILE_MAP.md | Synthesis / Master Index | Claims to cover 68-78 files from full history, Phase 1 master taxonomy | File classification, deduplication, dependency graph, terminology unification | Medium — It claims canonical versions (v2 > v1) but is itself a synthesis, not primary evidence. No code/DB check. | Does not verify content of files, only lists them. Includes duplicate handling that may be incomplete. No technical truth. |
| S02 | 01_VISION_BRAND_AND_PRODUCT_STRATEGY.md | Synthesis / Vision & Brand | Early foundation to brand-lock period, synthesized from 68 files | Vision, mission, UVP, brand identity, target audience, brand voice, core values, differentiation, pending decisions | Medium-High for vision/brand (grounded in 03-PRODUCT-VISION, MVP-Directive, LOCKED HTML), Low for mission (synthesized, not explicit in single file) | Mission not explicit in one file — inferred. No code verification. Pending decisions list is snapshot, not current. |
| S03 | 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md | Synthesis / IA & Sitemap | IA decisions period (decisions log + IA/UX docs) | IA overview, sitemap, content hierarchy, user flows, open IA questions, terminology | Medium — Cites 01-DECISIONS-LOG, 04-IA-UX, 02-OPEN-QUESTIONS but conflicts with later Axis C notes (search page) | Assumes Home=library ACCEPTED, no sidebar ACCEPTED, but does not reflect later user decision for separate /بحث page. No implementation check. |
| S04 | 04_FEATURES_MVP_AND_TECHNICAL_SPECS.md | Synthesis / Features + Technical Specs | MVP definition + technical implementation up to audit | MVP feature set (10 mandatory), technical spec (Next.js, routes, components, auth, DB, media pipeline), open tech debt (10 items) | Medium-High for feature list (traceable to MVP-Directive), High for technical debt (code-backed via audit), Medium for implementation status | Describes what must exist, not necessarily what is current. Technical debt list depends on audit file that may be outdated. No live DB check in this file itself. |
| S05 | 05_UI_DESIGN_SYSTEM_AND_COMPONENT_LIBRARY.md | Synthesis / UI Design System | UI component period, brand locked tokens | Color tokens, typography, spacing, breakpoints, component catalog (15 components), checklist | Medium for tokens (claims LOCKED but values differ from CLAUDE-FOUNDATION), Medium for components (derived from JSX prototypes, some marked PROPOSED) | Color token values (#006633) conflict with CLAUDE-FOUNDATION (#121214). Component props may be outdated vs actual code. No contrast/a11y testing evidence. |
| S06 | 06_CONTENT_ASSETS_AND_PRODUCTION_GUIDE.md | Synthesis / Content & Assets | Asset inventory + production pipeline period | PNG assets, safe-area guides, production pipeline 8 steps, copy deck, quality rubric (6 criteria), checklist, open production questions | Medium for asset inventory (lists files in uploads), Medium for pipeline (describes intended flow, not verified against production), Low for copy deck (sample only) | No video files present — pipeline not verified against real video. Quality rubric 2-8s conflicts with later note up to 60s. |
| S07 | 07_GAPS_CONTRADICTIONS_AND_EXECUTION_ROADMAP.md | Synthesis / Gaps & Roadmap | Gap analysis + contradiction log + risk matrix + roadmap | 12 gaps (G1-G12), 4 contradictions (C1-C4), risk matrix (R1-R7), execution roadmap P0-P8, final verdict 60% | High for gaps (code-backed via Technical-State-Audit), Medium for contradictions (preferred source chosen without explicit owner confirmation), Medium for roadmap (assumes owner تم) | Contradiction resolutions (C1-C4) propose preferred source — this is decision-like, not allowed in Phase 1. Final verdict % is estimate, not measured. |
| S08 | ARENA-DISCUSSION-HANDOFF.md | Handoff / Discussion | Discussion track (Nibras ↔ User ↔ Arena) historical | Product definition evolution, 13 axes discussed, decisions by status (ACCEPTED/PROPOSED/REJECTED/OPEN/DEFERRED), tensions, open questions, file inventory used in discussion | Medium-High for discussion history (independent witness, no implementation claim), High for ACCEPTED items that cite 01-DECISIONS-LOG | Does not verify code. OPEN QUESTIONS list is historical, not current. UNKNOWN section explicitly lists gaps. No direct DB/code evidence. |
| S09 | ARENA-TECHNICAL-HANDOFF.md | Handoff / Technical Audit | Technical state 2026-09-02, HEAD 331c1b3 master, Neon production read-only | Actual code (Next.js 15.5.23, React 19.2.8, Prisma 5.22, 15 models, 7 enums), routes (45), DB counts (User=2, Reaction=12, MediaAsset=0), media pipeline (829 files local, 0 prod), testing (171 unit, 94 E2E), Git (1 commit, 119 untracked), conflicts doc vs code, UNKNOWN list (20 items) | High — Best technical truth: CODE + DATABASE SELECT + COMMAND OUTPUT (tsc, lint, build, curl, playwright). Explicitly says no mutation. | Knowledge limited to working tree, not remote. No integration tests run (94 tests write to prod). No ffmpeg in env. No Vercel env vars. Manus/Nibras unknown. |
| S10 | CLAUDE-FOUNDATION-HANDOFF.md | Handoff / Foundation | Foundation period up to Claude's GO, brand lock after 8 scenarios | Foundation idea, product vision (reaction = digital proverb), product principles, brand LOCKED details (logo Qussasa, colors, fonts, watermark double-shadow + flip rule, clip system 9:16+1:1 2-8s), content system, UX original concepts, prototypes, architecture proposal, historical decisions, changes later, sources | High for Brand LOCKED (tested on 8 scenarios, HTML LOCKED), High for product principles (owner idea), Medium for UX original (evolved later), Low for current code state (no direct DB/code check after GO) | Explicitly says not current truth. Last 3 open points (save account condition, video duration, footer legal) left open. No verification of later implementation. |
| S11 | MANUS-V1-HANDOFF.md.md | Handoff / Historical UI | Manus V1 React/Vite + Astro/Preact/Fastify period | UI improvements (Header Glassmorphism, Footer, Hero 520px, debounce 300ms, recent searches 4, modal قريباً), Settings System in Astro, Mock API for prerender, bugs (DB_URL missing, Google Client ID) | Low-Medium — Historical, many IMPLEMENTED locally but not production verified. Mock API used. No DB/Auth/Media production evidence. | Two different stacks (React/Vite vs Astro) — risk of mixing. No proof of real content. No ffmpeg/watermark. Preview links temporary. Many UNKNOWN. |
| S12 | MANUS-V2-HANDOFF.md.md | Handoff / Implementation WebDev | Manus V2 WebDev project yemreact-deploy, checkpoint 6e9451ff | WebDev stack React/Vite/Express/tRPC/Drizzle, schema (users/categories/reactions/submissions/saved), routes (library/categories/search/byId/groups/submissions/review), UI pages (Home/Search/Submit/Groups/Account/Saved/Settings/Track/Reaction/Admin), content 9 categories 13 reactions, auth Manus OAuth + GOOGLE_CLIENT_ID server, build success, 13 tests | Medium — IMPLEMENTED in WebDev project with build success and checkpoint, but production publish not proven, Google OAuth not end-to-end, media no ffmpeg/watermark | No S3/storage/ffmpeg/watermark evidence. No real video files. No production URL. No rate limiting/index docs. Many UNKNOWN. Checkpoint != production. |

## Duplicate / Overlap Map (Phase 1A Section 4)

### DUPLICATE (same info, different files)

- **DUPLICATE-001 — Brand LOCKED HTML reference:** S02, S05, S08, S09, S10 all reference YemReact-Brand-v1.0-LOCKED.html as locked source.
- **DUPLICATE-002 — File taxonomy duplicates:** S01 lists duplicates (00-INDEX, 01-DECISIONS-LOG etc.) that appear twice — batch1 vs batch2 — canonical chosen.
- **DUPLICATE-003 — 30-50 initial library size:** S02, S04, S08, S10 all mention 30-50 for test, 150-300 threshold.
- **DUPLICATE-004 — Reaction Detail = Page /r/[code]:** S03, S04, S08, S10 all state page not modal.

### REINFORCED (multiple sources confirm same)

- **REINFORCED-001 — Home = Library:** S03, S04, S08, S09 (code has / as library) — multiple agree.
- **REINFORCED-002 — No permanent sidebar ACCEPTED:** S03, S08, S09 (code sidebar exists but doc says ACCEPTED no sidebar — partial reinforce with conflict)
- **REINFORCED-003 — Google-only auth direction:** S04, S07, S09, S10 (evolution from OTP to Google) — multiple confirm direction, but S11/S12 show Manus OAuth variant.
- **REINFORCED-004 — Media pipeline blocked in production:** S04 (tech debt), S07 (G1 P0 blocker), S09 (media=0, ffmpeg missing) — strong reinforce, high confidence.
- **REINFORCED-005 — Video only, no static images:** S02, S06, S10 — all agree.
- **REINFORCED-006 — Save requires account tension:** S03 (PROPOSED), S10 (historical guest-first vs later Google required) — reinforced as tension, not agreement.

### VERSIONED (evolved over time)

- **VERSIONED-001 — BottomNav 4th item:** S08 documents chain Submit → Collections → Saved (SUPERSEDED twice). S03 says Saved PROPOSED, S05 says Submit Reaction, S07 says Submit per MVP, S11/S12 say Library/Search/Submit/Account. Clear evolution.
- **VERSIONED-002 — Search route:** S03/S04 original no /search page (/?q=) → S10 originally same page then later separate /بحث page after counter-argument → S05 UI shows /search?q. Evolution from same-page to separate page.
- **VERSIONED-003 — Categories role:** S10 early fixed filter bar → later data-only + color → S03 fixed situational buckets as filter → S08 9 colors locked but role questioned. Versioned from navigation to data-only.
- **VERSIONED-004 — Collections role:** S10 editorial → S03 future rail post 150-300 → S07 post-MVP rail → S11/S12 groups.list fixed. Versioned from editorial to rail to page.
- **VERSIONED-005 — Submit form:** S10 many fields → minimal video+note → S04 caption/situation/categoryId + ignored keywords/sourceUrl → S12 trackingId flow. Versioned to minimal.
- **VERSIONED-006 — Auth:** S10 OTP + DB sessions (ADR-0001) → Google + JWT (Phase 6A) → S12 Manus OAuth + GOOGLE_CLIENT_ID server. Versioned.
- **VERSIONED-007 — Video duration:** S06/S10 2-8s → S01 note up to 60s → S09 no duration limit in code. Versioned from strict short to flexible.
- **VERSIONED-008 — Watermark:** S10 11% top-right double shadow → S09 14% bottom-right no shadow. Versioned.

### POSSIBLE CONFLICT (needs conflict register, not resolved here)

- **POSS-CONFLICT-001 — Brand colors:** S05 vs S10 (green/mustard vs ink/amber/coral)
- **POSS-CONFLICT-002 — Product definition search engine vs library:** S09 package.json vs hero text
- **POSS-CONFLICT-003 — Sidebar existence:** S03 ACCEPTED no sidebar vs S09 code has sidebar 286px
- **POSS-CONFLICT-004 — Footer legal:** S03/S07 required vs S10/C recent notes deferred vs empty
- **POSS-CONFLICT-005 — Settings built vs not built:** S03 PROPOSED vs S09 not built vs S11/S12 built in Astro
- **POSS-CONFLICT-006 — Event tracking code vs UUID:** S09 proves 404
- **POSS-CONFLICT-007 — Terminology الفئات vs التصنيفات:** S07 G10
- **POSS-CONFLICT-008 — Core Loop utility vs discovery vs hybrid:** S02, S08, S10, S11

### UNKNOWN (insufficient evidence in these 12 to determine relationship)

- **UNKNOWN-001 — Which of the 68 files in S01 is truly canonical for Brand tokens:** S01 says v2 supersedes v1 but S09 says tokens.css matches LOCKED HTML — need direct file read of LOCKED HTML which is not in these 12.
- **UNKNOWN-002 — Whether Manus V1/V2 work is part of current production:** S11/S12 checkpoints vs S09 working tree — no Git remote to link.

## Summary Counts (Phase 1A)

- Sources examined: 12
- Duplicate infos: ~4 exact duplicates
- Reinforced infos: ~6 strongly reinforced
- Versioned infos: ~8 clear version evolutions
- Possible conflicts: ~8 flagged (full list in YEMREACT-CONFLICT-REGISTER.md 38 conflicts)
