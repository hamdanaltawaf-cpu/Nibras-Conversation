# YEMREACT-CONFLICT-REGISTER-V2.md — Phase 1B — Conflict Reconciliation Audit

> Phase 1B only — No product decisions, no implementation, no Git/DB changes. Only reconciliation audit of 38 conflicts vs 12 sources.
> Sources: S01-S12 as inventoried in YEMREACT-SOURCE-INVENTORY.md
> Date: 2026-09-11

## Methodology

For each conflict from V1, checked against 12 sources, classified as:
REAL CONFLICT, VERSION DRIFT, TERMINOLOGY CONFLICT, PROTOTYPE VS IMPLEMENTATION, PROPOSED VS ACCEPTED, DUPLICATE, NOT A CONFLICT, UNRESOLVED
If evidence resolves: explain. If not: NEEDS DECISION.

---

### CONFLICT-001 — Product Definition (Search Engine vs Library)

- **Sources:** S02, S04, S09, S08
- **What A says (S09 package.json + layout.tsx):** "search engine" — محرك بحث عن رياكشنات يمنية
- **What B says (S09 hero/header + S02/S03):** "مكتبة رياكشنات يمنية" — library
- **Additional:** S08 notes tension library discovery vs utility tool
- **Evidence:** CODE (package.json description) vs DOCUMENT (hero eyebrow) — both exist in same repo
- **Type:** TERMINOLOGY CONFLICT + REAL CONFLICT
- **Can chronology resolve?** No — both present simultaneously in same commit
- **Can implementation resolve?** No — implementation contains both strings
- **Impact:** High — affects IA, messaging, metrics
- **Requires Product Decision?** YES
- **Requires Technical Decision?** NO
- **Status:** UNRESOLVED — NEEDS DECISION

### CONFLICT-002 — Brand Colors

- **A (S05):** --brand-primary #006633 deep green, secondary #B8860B mustard
- **B (S10):** Ink #121214, Qishr Amber #C1592E, Amber Light #E0824B, Paper #F3EAE0, Coral #FF5A36, Warm Grey etc.
- **Additional:** S09 says tokens.css matches LOCKED HTML, S01 lists LOCKED HTML as critical
- **Evidence:** DOCUMENT (S05 token table) vs DOCUMENT (S10 list) + IMPLEMENTATION hint (S09 tokens.css matches LOCKED)
- **Type:** VERSION DRIFT + DOCUMENT VS IMPLEMENTATION
- **Chronology?** Yes — S05 appears to be older synthesis using generic green/mustard, S10 is foundation LOCKED with Qishr concept
- **Implementation resolve?** Partial — S09 says tokens.css matches LOCKED HTML, suggests S10 colors are correct, but need direct LOCKED HTML read (not in these 12)
- **Impact:** High — brand locked violation risk
- **Requires Product?** YES (confirm LOCKED HTML as source of truth)
- **Requires Technical?** NO
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION to confirm LOCKED HTML authoritative

### CONFLICT-003 — Brand Typography

- **A (S05):** Cairo + Roboto/Inter
- **B (S10):** Lalezar ≤5 words + Cairo body + Archivo Black + Inter EN + IBM Plex Mono
- **Evidence:** DOCUMENT vs DOCUMENT
- **Type:** VERSION DRIFT
- **Chronology?** Yes — S10 more detailed, includes usage rule ≤5 words, likely newer foundation
- **Implementation?** S09 says next/font/google Lalezar, Cairo, Archivo Black, Inter, IBM Plex Mono — supports S10
- **Impact:** Medium
- **Requires Product?** YES
- **Status:** VERSION DRIFT — implementation evidence supports S10

### CONFLICT-004 — Home Definition

- **A (S03/S08):** Home = library only, ACCEPTED
- **B (S02/S05/S11):** Home = hero + search + rails (featured/new/collections)
- **Evidence:** DOCUMENT (01-DECISIONS-LOG ACCEPTED) vs PROTOTYPE (index.html) vs IMPLEMENTATION (S09 / has hero + CategoryNav + 8 new + FeaturedStrip + ≤3 collections)
- **Type:** PROTOTYPE VS IMPLEMENTATION + PROPOSED VS ACCEPTED
- **Chronology?** Yes — ACCEPTED no-rail decision, but implementation includes rails (FeaturedStrip etc.)
- **Implementation resolve?** No — code has rails, decision says no rails — conflict between decision and implementation
- **Impact:** High — sitemap
- **Requires Product?** YES (reaffirm Home=library or accept rails)
- **Status:** REAL CONFLICT — NEEDS PRODUCT DECISION

### CONFLICT-005 — Search Route

- **A (S03/S07 C1):** No separate /search page, only /?q= — ACCEPTED, single-page mental model
- **B (S04/S05/S09/S10 recent):** /search exists (rewrite) or separate /بحث page
- **Evidence:** DOCUMENT ACCEPTED vs IMPLEMENTATION /search 200 + SSR 24 results
- **Type:** VERSION DRIFT + PROPOSED VS ACCEPTED
- **Chronology?** Yes — original same page, later separate page after counter-argument (S10 says Claude revised after argument), recent Axis C notes separate /بحث page
- **Implementation?** Yes — S09 proves /search exists and works
- **Impact:** High — SEO, shareable links
- **Requires Product?** YES
- **Requires Technical?** YES (routing)
- **Status:** VERSION DRIFT — implementation has /search, decision says no /search — NEEDS PRODUCT DECISION

### CONFLICT-006 — Reaction Detail

- **A (S03/S04/S08/S10):** Page /r/[code] ACCEPTED, SEO/shareable
- **B (Prototypes):** Modal (v1/v2)
- **Evidence:** DOCUMENT ACCEPTED + IMPLEMENTATION /r/[code] 200 vs DOCUMENT prototype modal
- **Type:** PROTOTYPE VS IMPLEMENTATION
- **Chronology?** Yes — modal early, page later ACCEPTED
- **Implementation?** Yes — S09 proves page exists, no modal
- **Impact:** Medium
- **Status:** NOT A CONFLICT now — ACCEPTED page is current, modal is HISTORICAL

### CONFLICT-007 — BottomNav 4th Item

- **A (S03):** Saved PROPOSED
- **B (S05/S07):** Submit Reaction per MVP
- **C (S03 history):** Collections as rail
- **D (S11/S12):** Library/Search/Submit/Account
- **Evidence:** DOCUMENT chain SUPERSEDED twice (Submit → Collections → Saved)
- **Type:** VERSION DRIFT
- **Chronology?** Yes — clear chain documented in S08
- **Implementation?** Partial — S09 BottomNav has Submit (docblock Home/Search/Submit/Account), S05 says Submit instead of Collections
- **Impact:** High — navigation core
- **Requires Product?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION to finalize 4th item

### CONFLICT-008 — Sidebar

- **A (S03/S08):** No permanent sidebar ACCEPTED
- **B (S05/S09):** Persistent sidebar 286px exists, hidden via !important in admin
- **Evidence:** DOCUMENT ACCEPTED vs IMPLEMENTATION sidebar exists
- **Type:** PROTOTYPE VS IMPLEMENTATION + PROPOSED VS ACCEPTED
- **Chronology?** Yes — decision to remove, but code still has sidebar
- **Implementation?** Yes — S09 proves sidebar exists and 0 overflow 320-1440
- **Impact:** Medium
- **Requires Product?** YES
- **Requires Technical?** YES
- **Status:** REAL CONFLICT — decision vs implementation

### CONFLICT-009 — Categories Role

- **A (S03):** Fixed situational buckets as filter
- **B (S10):** 9 colors locked but later data-only
- **C (S08):** Category vs Collection vs Tags 3 layers questioned
- **Evidence:** DOCUMENT versioned
- **Type:** VERSION DRIFT + TERMINOLOGY CONFLICT
- **Chronology?** Yes — early filter bar, later data-only + color
- **Impact:** Medium
- **Requires Product?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION

### CONFLICT-010 — Collections Role

- **A (S03):** Editorial collection PROPOSED not built until 150-300
- **B (S05):** CollectionCard text only
- **C (S07):** Post-MVP rail
- **D (Recent Axis C):** Albums simple title+count
- **Evidence:** DOCUMENT multiple
- **Type:** VERSION DRIFT
- **Chronology?** Yes — editorial → future rail → albums
- **Implementation?** Partial — S09 Collection=3, CollectionItem=8, but media include bug
- **Impact:** Medium
- **Requires Product?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION

### CONFLICT-011 — Saved Implementation

- **A (S04):** local ↔ cloud
- **B (S09):** localStorage yr:saved + cloud union optimistic
- **Evidence:** DOCUMENT + IMPLEMENTATION — both agree on union logic
- **Type:** DUPLICATE / REINFORCED
- **Chronology?** No conflict, evolution to detailed implementation
- **Implementation?** Yes — S09 proves union logic works
- **Impact:** Low
- **Status:** NOT A CONFLICT — REINFORCED

### CONFLICT-012 — Submit Form Fields

- **A (S06/S10):** video + optional note minimal
- **B (S04):** caption/situation/categoryId + source/keywords ignored
- **Evidence:** DOCUMENT minimal vs CODE many fields but some ignored
- **Type:** VERSION DRIFT + PROPOSED VS ACCEPTED
- **Chronology?** Yes — many fields → minimal
- **Implementation?** Partial — S09 shows keywords/sourceUrl validated then ignored (no columns)
- **Impact:** Medium
- **Requires Product?** YES (what fields allowed)
- **Requires Technical?** YES (columns)
- **Status:** VERSION DRIFT — NEEDS DECISION

### CONFLICT-013 — Account UI

- **A (S03/S05/S08):** Menu/Sheet not full page ACCEPTED
- **B (S11):** Account page
- **Evidence:** DOCUMENT ACCEPTED vs historical page
- **Type:** PROTOTYPE VS IMPLEMENTATION
- **Chronology?** Yes — page early, sheet later ACCEPTED
- **Implementation?** Yes — S09 AccountMenu popover/sheet exists
- **Status:** NOT A CONFLICT — sheet is current

### CONFLICT-014 — Settings

- **A (S03):** 4 toggles PROPOSED priority raised
- **B (S09):** Not built
- **C (S11/S12):** Built in Astro (UserSettingsContext, themes, data saver)
- **Evidence:** DOCUMENT PROPOSED vs IMPLEMENTATION not built in Next.js vs built in Astro
- **Type:** PROTOTYPE VS IMPLEMENTATION + VERSION DRIFT
- **Chronology?** Yes — proposed, not built in Next.js, built in separate Astro stack
- **Implementation?** Yes — S09 proves not built in Next.js
- **Impact:** Medium
- **Requires Product?** YES (timing)
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION on timing

### CONFLICT-015 — Admin Sections

- **A (S03):** Admin area
- **B (S04):** CRUD categories & collections
- **C (S09):** 4 cards Reactions/Categories/Collections/Submissions, no Featured/Users/Audit
- **Evidence:** DOCUMENT + IMPLEMENTATION — S09 proves 4 cards
- **Type:** VERSION DRIFT
- **Chronology?** Yes — basic CRUD → 4 cards
- **Implementation?** Yes — S09 curl 200
- **Status:** VERSIONED — current is 4 cards, not full

### CONFLICT-016 — Auth Method

- **A (S04/S07):** Google-only canonical
- **B (S08):** OTP vs Google debate
- **C (S11/S12):** Manus OAuth + GOOGLE_CLIENT_ID server
- **D (S09):** Google provider conditional, 2 users in DB
- **Evidence:** DOCUMENT ADR-0001 OTP vs CODE Google + JWT
- **Type:** VERSION DRIFT
- **Chronology?** Yes — OTP historical (ADR-0001) → Google + JWT Phase 6A → Manus OAuth in WebDev
- **Implementation?** Yes — S09 proves Google conditional, works in prod at least once
- **Impact:** High
- **Requires Product?** YES (Google-only vs OTP)
- **Requires Technical?** YES
- **Status:** VERSION DRIFT — Google-only is current in Next.js, Manus OAuth is separate stack

### CONFLICT-017 — Media Pipeline Blocked

- **A (S04/S06):** Pipeline described as working
- **B (S09/S07):** Blocked in production, ffmpeg missing, local storage only, body limit 4.5MB, media=0 in prod
- **Evidence:** IMPLEMENTATION + DATABASE — S09 .storage 829 files local, 216 pairs, media=0 prod, 0 ffmpeg
- **Type:** PROTOTYPE VS IMPLEMENTATION
- **Chronology?** No — local works, prod blocked from start
- **Implementation?** Yes — DB proves 0 MediaAsset in prod
- **Impact:** P0 blocker
- **Requires Technical?** YES
- **Status:** REAL CONFLICT — CONFIRMED as blocked, NEEDS TECHNICAL DECISION

### CONFLICT-018 — Storage Driver

- **A (S04):** Local default, S3 optional
- **B (S09):** Local ./storage + S3 via minio, interface exists
- **Evidence:** IMPLEMENTATION interface exists
- **Type:** DUPLICATE / REINFORCED
- **Chronology?** No conflict
- **Implementation?** Yes — code has interface, S3 tested with mocks only
- **Status:** NOT A CONFLICT — REINFORCED, but S3 not verified against real bucket

### CONFLICT-019 — Watermark Spec

- **A (S10):** 11% top-right double shadow
- **B (S09):** 14% bottom-right no shadow #f3eae0 Qussasa
- **Evidence:** DOCUMENT vs IMPLEMENTATION ffmpeg.ts
- **Type:** VERSION DRIFT + REAL CONFLICT
- **Chronology?** Yes — v1 failed on light backgrounds, v2 double shadow, then code 14% bottom-right
- **Implementation?** Partial — need LOCKED HTML to confirm which spec is authoritative
- **Impact:** Medium — brand locked
- **Requires Product?** YES
- **Requires Technical?** YES
- **Status:** CONFLICTED — NEEDS PRODUCT DECISION

### CONFLICT-020 — Video Duration

- **A (S06/S10):** 2-8s linked to concept (short = genre condition)
- **B (S01 note):** Not fixed, up to 60s
- **C (S09):** No duration limit in code, default 80MB
- **Evidence:** DOCUMENT 2-8s vs NOTE up to 60s vs CODE no limit
- **Type:** VERSION DRIFT
- **Chronology?** Yes — strict short → flexible up to 60s
- **Implementation?** Yes — code has no limit
- **Impact:** High — affects rubric, identity
- **Requires Product?** YES
- **Requires Technical?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION

### CONFLICT-021 — Video Aspect

- **A (S10):** 9:16 primary, 1:1 secondary
- **B (S01 note):** Not fixed size
- **C (S06):** Vertical
- **Evidence:** DOCUMENT vs NOTE
- **Type:** VERSION DRIFT
- **Chronology?** Yes — fixed aspect → flexible
- **Implementation?** Partial — safe-area guides exist for 9:16 and 1:1
- **Impact:** Medium
- **Requires Product?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION

### CONFLICT-022 — Search Suggestions

- **A (S03):** No suggestions
- **B (S11):** Recent searches 4, Yemeni suggestions, debounce 300ms, random reaction
- **C (S08):** Intent segmentation open
- **Evidence:** DOCUMENT no suggestions vs IMPLEMENTATION in React/Vite path
- **Type:** PROTOTYPE VS IMPLEMENTATION + VERSION DRIFT
- **Chronology?** Yes — no suggestions early, added later in Manus V1
- **Impact:** Medium
- **Requires Product?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION

### CONFLICT-023 — Legal Pages

- **A (S03/S07):** Terms/Privacy required at launch
- **B (S10 recent + Axis C):** Footer simplified, legal deferred, then info+map+accounts+developer no legal
- **Evidence:** DOCUMENT required vs DOCUMENT deferred vs NOTE empty
- **Type:** VERSION DRIFT
- **Chronology?** Yes — required → deferred → info/map/accounts/developer
- **Impact:** Medium — compliance
- **Requires Product?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION

### CONFLICT-024 — Featured

- **A (S04):** Featured exists
- **B (S09):** Featured id1→YR-0001, no admin UI, no API
- **C (S03):** Featured/New rails open
- **Evidence:** IMPLEMENTATION single row vs DOCUMENT no UI
- **Type:** PROPOSED VS ACCEPTED + IMPLEMENTATION gap
- **Chronology?** Yes — featured displayed, no way to change except SQL/seed
- **Impact:** Low
- **Requires Product?** YES (manual vs auto)
- **Requires Technical?** YES
- **Status:** VERSIONED — exists but not manageable

### CONFLICT-025 — Event Tracking Code vs UUID (BUG-1)

- **A (S09 client):** ReactionCard sends id UUID
- **B (S09 route):** /api/reactions/[id]/event expects code → 404
- **Evidence:** IMPLEMENTATION — COMMAND OUTPUT POST UUID → 404 + DB events=3 view only + unit tests prove both sides
- **Type:** REAL CONFLICT — BUG
- **Chronology?** No — bug from start
- **Implementation?** Yes — proves broken
- **Impact:** High — metrics blind
- **Requires Technical?** YES
- **Status:** CONFIRMED BUG — NEEDS TECHNICAL FIX

### CONFLICT-026 — Collection Media Include (BUG-2)

- **A (S09 repo):** include.media kind=PROCESSED only
- **B (Pipeline):** Produces WATERMARKED/THUMBNAIL
- **Evidence:** IMPLEMENTATION code L7 vs pipeline output
- **Type:** REAL CONFLICT — BUG
- **Impact:** Medium — collection cards placeholder
- **Requires Technical?** YES
- **Status:** CONFIRMED BUG

### CONFLICT-027 — Seed DurationMs Null (BUG-3)

- **A (S09 seed):** duration defined in REACTIONS[] not written to durationMs
- **B (DB):** durationMs NULL
- **Evidence:** IMPLEMENTATION code + DATABASE NULL
- **Type:** REAL CONFLICT — BUG
- **Impact:** Low
- **Requires Technical?** YES
- **Status:** CONFIRMED BUG

### CONFLICT-028 — Schema Drift 3 Indexes (G5)

- **A (DB):** Reaction_searchText_gin, Reaction_category_published_idx, Reaction_published_status_idx exist
- **B (Schema):** Not in schema.prisma
- **Evidence:** IMPLEMENTATION migrate diff DROP INDEX
- **Type:** REAL CONFLICT — DRIFT
- **Impact:** Medium — future migrate may drop GIN
- **Requires Technical?** YES
- **Status:** CONFIRMED DRIFT

### CONFLICT-029 — Processing Status Stuck (BUG-5)

- **A (Code):** processingStatus=processing no timeout, retry only failed
- **Evidence:** IMPLEMENTATION processor.ts L40
- **Type:** REAL CONFLICT — BUG
- **Impact:** Medium — orphaned assets
- **Requires Technical?** YES
- **Status:** CONFIRMED BUG

### CONFLICT-030 — Media Submissions Leak (SEC-3)

- **A (Code):** /media/[...key] streams submissions/* without auth
- **Evidence:** IMPLEMENTATION media/[...key]/route.ts no guard
- **Type:** REAL CONFLICT — SECURITY
- **Impact:** High — unreviewed leak
- **Requires Product?** YES (privacy policy)
- **Requires Technical?** YES
- **Status:** CONFIRMED SECURITY ISSUE

### CONFLICT-031 — Git State (P0-1)

- **A (Git):** 1 commit 331c1b3 2026-08-24, 28 modified, 119 untracked, no remote
- **Evidence:** IMPLEMENTATION git status
- **Type:** REAL CONFLICT — HYGIENE
- **Impact:** P0 — loss risk
- **Requires Technical?** YES
- **Status:** CONFIRMED

### CONFLICT-032 — Env Production Leak (P0-3)

- **A (.env.local):** Production Neon creds, AUTH_SECRET default insecure
- **Evidence:** IMPLEMENTATION .env.local + env.ts defaults
- **Type:** REAL CONFLICT — SECURITY
- **Impact:** High — prod writes
- **Requires Technical?** YES
- **Status:** CONFIRMED

### CONFLICT-033 — Terminology الفئات vs التصنيفات

- **A (Decision):** الفئات
- **B (Code/UI):** 20 occurrences التصنيفات
- **Evidence:** IMPLEMENTATION grep + DOCUMENT decision
- **Type:** TERMINOLOGY CONFLICT
- **Chronology?** Yes — decision to use فئات after التصنيفات used
- **Impact:** Low — UI mismatch
- **Requires Product?** YES (dictionary)
- **Status:** CONFIRMED — NEEDS PRODUCT DECISION to enforce

### CONFLICT-034 — Footer Content

- **A (S03):** brand description + groups link
- **B (S05):** terms, privacy, groups
- **C (Recent Axis C):** info+map+accounts+developer no legal
- **Evidence:** DOCUMENT multiple
- **Type:** VERSION DRIFT
- **Chronology?** Yes — groups → terms/privacy → info/map
- **Impact:** Low
- **Requires Product?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION

### CONFLICT-035 — Header Content

- **A (S03):** brand only mobile, ribbon tablet
- **B (S05):** brand+search chip+groups
- **C (S11):** Top Header glass
- **Evidence:** DOCUMENT + IMPLEMENTATION S09 header 2-tier
- **Type:** VERSION DRIFT + PROTOTYPE VS IMPLEMENTATION
- **Impact:** Medium
- **Requires Product?** YES
- **Status:** VERSION DRIFT — NEEDS PRODUCT DECISION

### CONFLICT-036 — Core Loop

- **A (S02):** searchable catalogue + discovery without feed
- **B (S08):** library discovery vs utility tool tension
- **C (S10):** tool at need → hybrid
- **D (S11):** hybrid library/search/share
- **Evidence:** DOCUMENT multiple definitions
- **Type:** REAL CONFLICT — PRODUCT DEFINITION
- **Chronology?** Yes — utility → hybrid
- **Impact:** Critical — changes everything below
- **Requires Product?** YES
- **Status:** UNRESOLVED — NEEDS PRODUCT DECISION

### CONFLICT-037 — Content Size

- **A (S02):** 30-50 initial
- **B (S04):** 150-300 realistic threshold
- **C (S09 DB):** 12 reactions seed
- **D (S12):** 9 categories 13 reactions
- **Evidence:** DOCUMENT + IMPLEMENTATION DB counts
- **Type:** VERSIONED
- **Chronology?** Yes — 30-50 test, 150-300 realistic
- **Impact:** Medium
- **Requires Product?** YES
- **Status:** VERSIONED — not conflict, different thresholds

### CONFLICT-038 — Submit Button Tension (Axis C d)

- **A:** Show but not enter until 30-50
- **B:** Enter after review simultaneous
- **C:** Queue with message "review after 30-50"
- **Evidence:** DOCUMENT recent Axis C notes + S08 chicken-egg + S04 workflow
- **Type:** REAL CONFLICT — PRODUCT + TECHNICAL
- **Chronology?** No — new tension from recent notes
- **Implementation?** No — needs decision
- **Impact:** High — growth vs quality
- **Requires Product?** YES
- **Requires Technical?** YES
- **Status:** OPEN — NEEDS PRODUCT DECISION (owner chooses A/B/C)
