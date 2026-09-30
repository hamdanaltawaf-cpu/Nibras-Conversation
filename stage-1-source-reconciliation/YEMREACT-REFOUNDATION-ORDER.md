# YEMREACT-REFOUNDATION-ORDER.md — Phase 1C — Re-foundation Order

> Order decisions to discuss later, from highest impact to lowest. No decisions made here. No technical early if depends on product not yet resolved.
> No code/Git/DB modification.

## Principle

- Product Definition / Core Loop first — everything else depends on it
- Then IA (sitemap, navigation, search route)
- Then UX/Navigation details
- Then Features (content, submissions, saves, admin)
- Then Technical implications (media infra, storage, bugs, git, env)

Do not bring technical early if it depends on product not yet resolved.

---

### Level 1 — Critical — Must First (Product Definition)

| Order | Decision ID | Topic | Why first | Depends on | Sources |
|---|---|---|---|---|---|
| 1 | PD-01 | Product Definition: search engine vs library | Defines what YemReact is — changes IA, messaging, metrics, SEO | None — root | CONFLICT-001 |
| 2 | PD-02 | Core Loop: utility vs discovery vs hybrid vs content-library-first | Defines behavior — daily habit vs mental availability, affects Home, Search, Featured/New/Collections, Save/Share, Retention | PD-01 | CONFLICT-036 |
| 3 | PD-03 | Value vs screen record from TikTok — does proposition hold? | Validates existence — if not, no need for rest | PD-01, PD-02 | S08 Q1 |
| 4 | PD-05 | Content Pipeline timing: manual 30-50 first vs simultaneous vs queue Option C — submit button tension A/B/C | Blocks growth vs quality, user trust, when submissions open | PD-02, PD-04 | CONFLICT-038 |
| 5 | PD-04 | Good content rubric operational 6 points + diversity — who decides | Blocks moderation, admin speed 40/hour | PD-02 | S08 Q2 |

### Level 2 — High — IA (depends on Level 1)

| Order | Decision ID | Topic | Why | Depends on | Sources |
|---|---|---|---|---|---|
| 6 | UX-01 / PD-08 | Search route: /?q= only vs /search page vs separate /بحث with writing bar → results page | Sitemap, SEO, shareable links, mental model — depends on product definition | PD-01, PD-02 | CONFLICT-005 |
| 7 | UX-02 / PD-09? Actually UX-02 | BottomNav 4th final: Saved vs Submit vs Collections vs placeholder will change later | Navigation core — depends on core loop (is save core? is submit growth?) | PD-02, PD-05 | CONFLICT-007 |
| 8 | UX-03 | No permanent sidebar vs persistent sidebar 286px — final | Layout complexity, 3 shells maintenance | PD-01 | CONFLICT-008 |
| 9 | UX-04 | Home composition: library only vs hero+search+CategoryNav+8 new+FeaturedStrip+≤3 collections | First impression, depends on core loop and search route | PD-01, PD-02, UX-01 | CONFLICT-004 |
| 10 | PD-09 | Categories: fixed 9 locked vs open, role filter vs data-only vs destination | Taxonomy — depends on product definition (is filtering core?) | PD-01, PD-02 | CONFLICT-009 |
| 11 | PD-10 | Collections: editorial vs rail vs page vs album title+count vs saved search | Taxonomy — depends on library size thresholds | PD-06, PD-09 | CONFLICT-010 |
| 12 | PD-07 | Video Duration: 2-8s vs up to 60s | Affects identity, rubric, performance, storage — depends on core loop and good content definition | PD-02, PD-04 | CONFLICT-020 |
| 13 | PD-08 | Video Aspect: fixed 9:16+1:1 vs any size | Affects safe area, overlays, responsive — depends on duration and brand | PD-07, B-01 | CONFLICT-021 |

### Level 3 — Medium — UX/Navigation Details (depends on Level 2)

| Order | Decision ID | Topic | Why | Depends on | Sources |
|---|---|---|---|---|---|
| 14 | UX-05 | Header: brand only mobile vs brand+search chip+groups vs glass scroll | Depends on search route and bottom nav | UX-01, UX-02 | CONFLICT-035 |
| 15 | UX-06 | Search intent segmentation single field vs visual tags | Depends on search route | UX-01 | S03 Q1 |
| 16 | UX-13 | SearchBar: debounce 300ms + recent 4 + Yemeni suggestions + random reaction final UX | Depends on search route | UX-01, UX-06 | CONFLICT-022 |
| 17 | UX-08 | Reaction Detail: page only vs modal vs intercepting route | Depends on Home and Search | UX-04, UX-01 | UX-08 |
| 18 | UX-07 | Featured/New/Collections rails priority | Depends on Home composition and Collections role | UX-04, PD-10 | S03 Q2 |
| 19 | PD-13 / UX-15? Actually PD-13 | Footer: info+map+accounts+developer no legal vs required vs deferred | Depends on legal decision | PD-11 | CONFLICT-034 |
| 20 | UX-12 | Save UI empty state copy | Depends on BottomNav and Account | UX-02 | UX-12 |
| 21 | UX-11 | Account entry consolidation (4 names for /search etc.) | Depends on IA | UX-01 to UX-04 | P2-14 |
| 22 | UX-09 | Settings timing and keys | Depends on core loop and Yemeni network reality | PD-02 | CONFLICT-014 |
| 23 | UX-14 | Error/Empty/Loading states Arabic copy | Depends on UX | UX-04 | S11 |

### Level 4 — Medium — Features (depends on Level 1-3)

| Order | Decision ID | Topic | Why | Depends on | Sources |
|---|---|---|---|---|---|
| 24 | PD-15 | Submission fields minimal vs full + admin edit? | Depends on pipeline timing and good content rubric | PD-05, PD-04 | CONFLICT-012 |
| 25 | PD-16 | Privacy of submissions raw hidden until approved, sender preview, /media/submissions/* public? | Depends on pipeline + legal | PD-05, PD-11 | CONFLICT-030 |
| 26 | PD-11 | Legal pages required vs deferred | Depends on submissions open timing | PD-05 | CONFLICT-023 |
| 27 | PD-17 | Original master retention for rejected | Depends on legal + storage | PD-11 | PD-17 |
| 28 | PD-18 | Featured selection manual vs SQL | Depends on editorial and home composition | UX-04 | CONFLICT-024 |
| 29 | PD-20 | Success metrics numeric definition | Depends on core loop and product definition | PD-01, PD-02 | PD-20 |
| 30 | PD-12 | Terminology الفئات vs التصنيفات dictionary mass replace | Can be done during features as copy deck | PD-09 | CONFLICT-033 |
| 31 | UX-10 | Submission as Growth Engine low-friction vs chicken-egg break | Depends on pipeline timing | PD-05 | S08 |

### Level 5 — Low/Deferred — Technical Implications (depends on product, after Level 4)

| Order | Decision ID | Topic | Why deferred | Depends on | Sources |
|---|---|---|---|---|---|
| 32 | TD-01 | Media infrastructure worker vs S3 presigned vs managed service (cost) | Cost choice, depends on duration/aspect and collections | PD-07, PD-08, PD-10 | P0-2 |
| 33 | TD-02 | Storage driver Local vs S3, ensureWatermarkFile path, S3_PUBLIC_URL | Depends on TD-01 | TD-01 | S09 |
| 34 | TD-03 | FFmpeg details, thumbnail scale, watermark generation | Depends on TD-01 + watermark spec | TD-01, PD-14 | S09 |
| 35 | TD-04 | Upload arrayBuffer vs streaming, body limit | Depends on TD-01 | TD-01 | P1-8 |
| 36 | TD-05 | Delivery Range/206, Content-Disposition, auth for submissions/* | Depends on privacy + infra | PD-16, TD-01 | SEC-3 |
| 37 | TD-06 | Worker void promise vs real queue + retry + lease | Depends on infra | TD-01 | P1-4 |
| 38 | TD-12 | Git hygiene commit + remote | Independent P0 but should be first technical after product | None | P0-1 |
| 39 | TD-13 | Env separation prod vs dev, AUTH_SECRET defaults | Independent P0-3 | None | P0-3 |
| 40 | TD-07 | Schema drift 3 indexes | Independent but no migrate dev before fix | None | G5 |
| 41 | TD-08 | BUG-1 code vs UUID | Independent small fix | None | BUG-1 |
| 42 | TD-09 | BUG-2 collection include | Independent | None | BUG-2 |
| 43 | TD-10 | BUG-3 seed durationMs NULL | Independent | None | BUG-3 |
| 44 | TD-11 | Other bugs double fetch, /saved N requests, getCurrentUser 3x, etc. | Independent UX debt | None | P2-5 to P2-14 |
| 45 | TD-14 | Testing isolation no CI | Depends on env separation | TD-13 | G9 |
| 46 | TD-15 | Auth defaults insecure, 403 HTTP 200 etc. | Partially product + technical | None | S09 |
| 47 | TD-16 | Prisma format, migration_lock.toml, tooling | Deferrable | None | S09 |
| 48 | TD-17 | CSS monolithic, SVG duplicated | Deferrable post-MVP polish | None | P3 |
| 49 | TD-18 | SEO generateMetadata OG per reaction, favicon/robots/sitemap | Depends on product definition | PD-01 | P2-7 |

## Order Summary

- Level 1 Critical Product: 5 decisions (PD-01 to PD-05)
- Level 2 High IA: 8 decisions (UX-01 to PD-08)
- Level 3 Medium UX: 10 decisions (UX-05 to UX-14)
- Level 4 Medium Features: 8 decisions (PD-15 to UX-10)
- Level 5 Technical: 18 decisions (TD-01 to TD-18)
- Total ordered: 49 decisions — matches unknowns + conflicts
- Rule enforced: No technical early if depends on product not yet resolved — e.g., TD-01 media infra deferred until PD-07/PD-08 duration/aspect decided
