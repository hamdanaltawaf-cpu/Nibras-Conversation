# YEMREACT-HISTORICAL-NOT-CURRENT.md — Phase 1C — Historical / Not Current

> Purpose: Stop re-presenting these as Current Truth. They are version drift, prototype-only, superseded, historical approach, or implementation detail no longer representing current decision.
> No code/Git/DB modification.

## 1. Version Drift — Idea evolved, old version should not be presented as current

| # | What | Old Version | Newer Version | Evidence | Why historical |
|---|---|---|---|---|---|
| VD-01 | BottomNav 4th item | Submit → Collections → Saved chain | Recent Axis C: top search only + bottom placeholder will change later + Groups in bottom | S08 SUPERSEDED chain, S03 Saved PROPOSED, S05 Submit, recent notes | Chain documented, final not decided — old items superseded |
| VD-02 | Search route | Same page /?q= ACCEPTED | Separate /search page exists 200 + recent separate /بحث page with writing bar → results | S03 ACCEPTED same page vs S09 /search 200 vs recent Axis C separate page | Evolution same-page → separate page, need product decision |
| VD-03 | Categories role | Fixed filter bar as main nav (S10/S03) — HISTORICAL — 9 category colors LOCKED B-06 | Full Removal Staged A/B — Stage A الآن بدون Migration UI Removal + Admin Hidden + Schema Kept + Brand Kept محفوظة للدراسة Stage4 + Collections+Keywords+Search — Stage B بعد P0 Git Migration آمن DROP TABLE Category + DROP categoryId + حذف 20+ موضع + تعديل Brand دراسة — CONFIRMED via DECISION-014 — P-31 + P-32 — CONFLICT-009 CLOSED | S10 Brand v1.0 LOCKED 9 colors #F4C430 #7C5CFF #C81E3A #2CB6C4 #F17FB2 #4CAF6D #6E8296 #D98E04 #E8712E vs S03 filter vs data-only vs destination VERSION DRIFT vs P-20 Rubric 6 لا يذكر فئة vs 6K Admin CRUD vs P-14 Search بالكلمات ليس بالفئة vs DECISION-014 ACCEPTED 2026-09-14 Full Removal Staged A/B | Role changed from navigation to data-only → Full Removal Staged — RESOLVED by DECISION-014 Categories Removed + Collections as Primary Taxonomy — 9 colors محفوظة للدراسة Stage4 — VD-03 HISTORICAL — CONFLICT-009 CLOSED — 62→64 facts — PD-09 CLOSED |
| VD-04 | Collections role | Editorial group managed by admin (S10) — أداة أدمن فقط تنظيم داخلي — HISTORICAL | Rail في الرئيسية + Page مستقلة — Admin-Only Curated + Manual + Multi-membership نعم + Follow نعم + SEO نعم قابل للفهرسة + 3 مجموعات عند الإطلاق طلاب قروبات بلا سياق — CONFIRMED via DECISION-015 — P-32 UPDATED + P-33 + P-34 — 64→66 facts — PD-10 CLOSED — Stage 3 CLOSED | S10 editorial → S03 future rail → recent albums title+count simple → T-03 DB Collection=3 + CollectionItem=8 + T-02 Routes /collections + /collections/[slug] existing + P-31 Categories Removed → Collections Primary + DECISION-015 ACCEPTED 2026-09-14 Admin-Only Curated + Manual + Rail+Page + Multi+Follow+SEO+3 | Role changed editorial → rail → albums → Primary Taxonomy — RESOLVED by DECISION-015 Collections as Primary Taxonomy — Rail+Page + Admin-Only Curated + Manual + Multi-membership + Follow + SEO + 3 عند الإطلاق — VD-04 HISTORICAL → RESOLVED — 64→66 facts — PD-10 CLOSED — Stage 3 CLOSED |
| VD-05 | Submit form fields | Many fields (category/situation/tags/source/rights) | Minimal video+note only (source/rights REMOVED) | S10 many → minimal, S03 ACCEPTED removal | Old many-fields superseded |
| VD-06 | Auth | OTP + DB sessions (ADR-0001 Session/OneTimeCode) | Google + JWT (Phase 6A) + Manus OAuth in WebDev | S09 CODE Google conditional, S11/S12 Manus OAuth | OTP historical, Google current in Next.js |
| VD-07 | Video duration | 2-8s strict linked to concept (S06/S10) — HISTORICAL | Up to 60s note → CONFIRMED via DECISION-012 — 2-60s + auto-reject + modal + display limit + revisable — P-27 + P-28 | S06/S10 2-8s vs S01 note up to 60s vs S09 no limit vs DECISION-012 ACCEPTED 2026-09-14 2-60s hard limits + modal rejection + "هل هي رياكشن؟" | Duration rule drifted from strict short to flexible → RESOLVED by DECISION-012 2-60s ACCEPTED — 2-8s strict HISTORICAL — up to 60s CONFIRMED — 58→60 facts — PD-07 CLOSED |
| VD-08 | Video aspect | 9:16 primary + 1:1 secondary fixed (S10/S06/S01 clip system) — HISTORICAL | Any size 9:16,1:1,16:9,4:5,3:4 أي مقاس مسموح + لا فراغ أسود + لا حد تقني + توجيه فقط Rubric 6 + Watermark+Qussasa ديناميكي + الصور أكثر مرونة — CONFIRMED via DECISION-013 — P-29 + P-30 | S10 9:16+1:1 vs S01 note not fixed size vs S09 T-04 no aspect validation + ffprobe width/height no reject + ffmpeg w=iw*0.14 works on any aspect vs DECISION-011 يوتيوب 16:9 + تيك توك 9:16 + إنستغرام 1:1/4:5 vs DECISION-013 ACCEPTED 2026-09-14 أي مقاس مسموح + لا فراغ أسود | Aspect drifted from fixed 9:16+1:1 to flexible any size → RESOLVED by DECISION-013 أي مقاس مسموح + لا فراغ أسود — 9:16+1:1 HISTORICAL — not fixed size CONFIRMED — 60→62 facts — PD-08 CLOSED — CONFLICT-021 CLOSED |
| VD-09 | Watermark | 11% top-right double shadow (arena.md §8.2) | 14% bottom-right no shadow (ffmpeg.ts) + strengthened double shadow concept | S10 vs S09 | Spec drifted, need authoritative decision |
| VD-10 | Footer | Brand description + groups link | Terms/privacy/groups → info+map+accounts+developer no legal | S03 → S05 → recent Axis C | Footer content drifted |
| VD-11 | Header | Brand only mobile + ribbon tablet | Brand+search chip+groups + Top Header glass scroll | S03 → S05 → S11 → S09 2-tier | Header composition drifted |
| VD-12 | Search suggestions | No suggestions | Recent searches 4 + Yemeni suggestions + debounce 300ms + random reaction (Manus V1) | S03 no suggestions vs S11 suggestions | Suggestions added later in separate stack |
| VD-13 | Legal pages | Required at launch | Deferred → info+map+accounts+developer no legal | S03/S07 required vs S10 deferred vs recent no legal | Legal scope drifted |
| VD-14 | Content size | 30-50 initial | 150-300 realistic threshold, DB 12 seed, WebDev 9 cat 13 reactions | S02 30-50 vs S04 150-300 vs S09 DB | Thresholds versioned, not conflict |

## 2. Prototype-Only — Should not be presented as production

| # | What | Evidence | Why not current |
|---|---|---|---|
| PO-01 | YemReact-Web-Prototype.jsx — React SPA single component 12 mock items | S10, S01 — labeled تجريبية, no backend, no real video | Prototype for visual system, not product |
| PO-02 | index.html, index (1)-(4).html, Templates-Source-Editable.html | S01 — prototypes | HTML prototypes, not current |
| PO-03 | ui-prototype/index.html v4 Library-First — 78KB 4 views + modal + sheets + settings + role switcher, declares itself final reference before any implementation | S11, S08 — "النسخة المرجعية النهائية قبل أي تنفيذ" | Reference design, conflicts with implementation (no sidebar vs sidebar, modal vs page, search in place vs page) — not current truth |
| PO-04 | Hybrid Technical Specification React 19 + Vite + Tailwind 4 + wouter + tRPC client/src/* | S09 — project different, S01 lists as reference | Not this repo (Next.js), separate project |
| PO-05 | uploads/*.tsx.txt, *.css, sha256sums.txt extracted from client/src/* wouter/tRPC | S09 — reference to other project | Not in yemreact-next, reference only |
| PO-06 | Modal "قريباً" for Images/People locked sections | S11 — temporary solution | Temporary, not product decision |
| PO-07 | Mock API for Astro prerender (local API to enable build without DB) | S11, S12 — Mock API | Build tool, not production data |
| PO-08 | Public preview via Manus computer domain https://3000-...manus.computer | S11, S12 — temporary preview | Temporary, not permanent hosting |

## 3. Superseded — Explicitly superseded by newer decision

| # | What | Superseded By | Evidence |
|---|---|---|---|
| SUP-01 | BottomNav Submit (first) | Collections (second) | S08 SUPERSEDED chain |
| SUP-02 | BottomNav Collections (second) | Saved (third) PROPOSED | S08 SUPERSEDED |
| SUP-03 | Brand identity system early (YemReact-identity-system.html / دليل-الهوية.md) before lock | Brand v1.0 LOCKED HTML | S10, S01 — early is historical when conflict with LOCKED |
| SUP-04 | OTP auth + Session/OneTimeCode models + ADMIN_EMAIL/SMTP_* env | Google + JWT | S09 models exist but 0 rows, ADR-0001 vs CODE |
| SUP-05 | Enبهار as 10th color independent | Merged into استغراب family same turquoise | S08, S10 |
| SUP-06 | YemReact-Unified-Context-Reference.md v1 | v2 supersedes v1 | S01 de-duplication log |

## 4. Historical Approach — Old architecture/process no longer used

| # | What | Evidence | Why historical |
|---|---|---|---|
| HA-01 | yemreact-app MVP: Node pure, JSON DB data/mock-db.json, OTP, admin password, no ffmpeg, Termux version, docs arena.md 855 lines | S09 /home/user/yemreact-app OLD — reference decisions/lessons only | Old MVP, not current Next.js |
| HA-02 | yemreact-web prototype static HTML/CSS/JS + data.js 12 mock reactions, local fonts | S09 OLD prototype | Archive |
| HA-03 | README.md repo says Phase 0 + Foundation not implemented yet: auth/admin/submissions/FFmpeg/R2 | S09 — all implemented | OUTDATED |
| HA-04 | docs/ADR-0001 signed DB-backed sessions OTP, ADR-0002 aggregation job, docs/ARCHITECTURE.md public routes cacheable revalidate | S09 — Google+JWT, no aggregation job, 0 revalidate 44 force-dynamic | OUTDATED/CONFLICT |
| HA-05 | lib/media/types.ts docblock "FFmpeg lands in Phase 9", lib/media/index.ts "real service replaces in Phase 9", lib/session.ts "Auth lands in Phase 6" | S09 — implemented in 6H | OUTDATED comments |
| HA-06 | package.json description "search engine" vs hero "library" — old description | S09 CONFLICT | Old description not updated |
| HA-07 | fonts/ Cairo/Lalezar ttf+woff2 local — app uses next/font/google | S09 — fonts not used | Unused assets |
| HA-08 | agent/, .agents/, skills-lock.json inside repo | S09 — not part of product | Not product |

## 5. Implementation Detail No Longer Representing Current Decision

| # | What | Decision says | Implementation has | Why not current truth |
|---|---|---|---|---|
| ID-01 | Home = library only, no rails | No Featured/New/Collections rails | Has hero + CategoryNav + 8 new + FeaturedStrip + ≤3 collections (S09 /) | Implementation includes rails despite ACCEPTED no rails — decision is product truth, implementation is historical artifact until Blueprint |
| ID-02 | No permanent sidebar | No sidebar | Has sidebar 286px, hidden via !important in admin (S09) | Decision ACCEPTED no sidebar vs code has sidebar |
| ID-03 | Search = /?q= only | No separate /search | Has /search 200 SSR 24 results + double fetch (S09) | Implementation has /search despite decision |
| ID-04 | Categories counts active only | Active only | Includes draft/archived (S09 CODE categoryRepository.findActive) | Bug, not decision |
| ID-05 | Collection media WATERMARKED/THUMBNAIL | Should show watermarked | Loads PROCESSED only → placeholder (BUG-2) | Bug, not decision |
| ID-06 | Event tracking code | Should log save/download/share | Sends UUID → 404 (BUG-1) | Bug, not decision |
| ID-07 | BottomNav docblock says Home/Search/Saved/Account but code has Submit | Saved vs Submit | Docblock outdated inside same batch | Docblock historical |

## Summary

- Version Drift: 14 items
- Prototype-Only: 8 items
- Superseded: 6 items
- Historical Approach: 8 items
- Implementation Detail Not Current: 7 items
- Total historical/not current: 43 items — should not be presented as Current Truth in Phase 2
