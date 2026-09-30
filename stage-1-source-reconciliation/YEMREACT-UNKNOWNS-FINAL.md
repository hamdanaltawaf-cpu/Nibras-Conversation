# YEMREACT-UNKNOWNS-FINAL.md — Phase 1C — Unknowns Final Classification

> Review of 49 unknowns from YEMREACT-UNKNOWN-REGISTER.md — classified, not filled with guessing.
> No code/Git/DB modification.

## Classification Definitions

- **Must Resolve Before Product Re-foundation:** Cannot start product re-foundation without it — blocks product definition, IA, or core loop
- **Can Resolve During Product Re-foundation:** Can be discussed and decided as part of Phase 2 product re-foundation
- **Can Be Deferred to Technical Implementation:** Technical/infra detail that can wait until Arena-Agent phase, after product decisions
- **Informational / Low Impact:** Low impact, informational, does not block re-foundation

---

### Must Resolve Before Product Re-foundation (Critical)

| # | Unknown | Why must resolve before | Sources | Category |
|---|---|---|---|---|
| U-01 | Product Definition: search engine vs library — final definition | Blocks IA, sitemap, messaging, metrics — everything below depends on it | CONFLICT-001, S09, S02 | Product |
| U-02 | Core Loop: utility vs discovery vs hybrid — final loop | Critical — changes Home, Search, Featured/New/Collections, Save/Share, Retention metric | CONFLICT-036, S08 | Product |
| U-03 | Value vs screen record from TikTok — does proposition hold? | Validates product existence — if not, no need for re-foundation | S08 open Q1 | Product |
| U-04 | Definition of good content — Rubric operational vs intuition, who decides | Blocks moderation, admin speed 40/hour, quality | S08 Q2, S10 6 criteria | Product |
| U-05 | Content Pipeline timing: manual 30-50 first vs simultaneous vs queue Option C — submit button tension A/B/C | Blocks growth vs quality, user trust, when submissions open | CONFLICT-038, recent Axis C | Product |
| U-06 | Video Duration: 2-8s linked to concept vs up to 60s — final rule | Affects identity (short = genre condition), rubric, performance, storage cost | CONFLICT-020 | Product |
| U-07 | Video Aspect: fixed 9:16+1:1 vs any size — how to apply Qussasa | Affects safe area, overlays, responsive, brand application | CONFLICT-021 | Product |
| U-08 | Search route: /?q= only vs /search page vs separate /بحث with writing bar → results | Blocks sitemap, SEO, shareable links, mental model | CONFLICT-005, UX-01 | UX/IA — but Product decision |
| U-09 | BottomNav 4th final: Saved vs Submit vs Collections vs placeholder | Blocks navigation core — 4 items mobile | CONFLICT-007, UX-02 | UX/IA — Product |
| U-10 | No permanent sidebar decision vs implementation has sidebar — final? | Blocks layout complexity, maintenance of 3 shells | CONFLICT-008, UX-03 | UX/IA — Product |

### Can Resolve During Product Re-foundation (High/Medium)

| # | Unknown | Why during | Sources | Category |
|---|---|---|---|---|
| U-11 | Categories role: filter bar vs data-only color vs destination, fixed 9 locked vs open | Can be discussed during IA | CONFLICT-009, PD-09 | Product |
| U-12 | Collections role: editorial vs rail vs page vs album title+count vs saved search | Can be discussed during IA | CONFLICT-010, PD-10 | Product |
| U-13 | Legal pages required vs deferred vs footer info+map+accounts+developer | Can be discussed during IA/Footer | CONFLICT-023, PD-11 | Product |
| U-14 | Terminology الفئات vs التصنيفات + library/search/new/عرض الكل dictionary | Can be resolved during product re-foundation as part of copy deck | CONFLICT-033, PD-12 | Product |
| U-15 | Footer content final | Can be resolved during IA | CONFLICT-034, PD-13 | UX/IA |
| U-16 | Header content final (brand only vs brand+search chip+groups vs glass) | Can be resolved during IA | CONFLICT-035, UX-05 | UX/IA |
| U-17 | Home composition: library only vs hero+search+CategoryNav+8 new+FeaturedStrip+≤3 collections | Can be resolved during IA/Home | CONFLICT-004, UX-04 | UX/IA |
| U-18 | Search intent segmentation single field vs visual tags | Can be resolved during UX Search | S03 Q1, UX-06 | UX/IA |
| U-19 | Featured/New/Collections rails priority | Can be resolved during IA | S03 Q2, UX-07 | UX/IA |
| U-20 | Reaction Detail page only vs modal vs intercepting route | Can be resolved during UX Detail | UX-08, S08 | UX/IA |
| U-21 | Settings timing and keys (autoplay/sound/data-saving/motion) | Can be resolved during UX, priority raised due to Yemeni network | UX-09, CONFLICT-014 | UX/IA |
| U-22 | Submission as Growth Engine low-friction vs chicken-egg break | Can be resolved during Growth | UX-10, S08 | Product/Growth |
| U-23 | Account entry consolidation (4 names for /search, 4 entries for /collections) | Can be resolved during IA | UX-11, P2-14 | UX/IA |
| U-24 | Save UI empty state copy | Can be resolved during UX | UX-12 | UX/IA |
| U-25 | SearchBar debounce 300ms + recent searches 4 + Yemeni suggestions + random reaction final UX | Can be resolved during UX Search | UX-13, CONFLICT-022 | UX/IA |
| U-26 | Watermark spec authoritative 11% vs 14% | Can be resolved during Brand audit (but needs LOCKED HTML read) | CONFLICT-019, PD-14, BD-01 | Brand/Product |
| U-27 | Submission fields video+note minimal vs caption/situation/category + keywords/sourceUrl, admin edit? | Can be resolved during Features | CONFLICT-012, PD-15 | Product/Features |
| U-28 | Privacy of submissions raw hidden until approved, sender preview, /media/submissions/* public? | Can be resolved during Features/Policy | CONFLICT-030, PD-16 | Product/Features |
| U-29 | Original master retention for rejected | Can be resolved during Features | PD-17 | Product |
| U-30 | Featured selection manual vs SQL | Can be resolved during Editorial | CONFLICT-024, PD-18 | Product |
| U-31 | Success metrics numeric definition | Can be resolved during Product Re-foundation as part of metrics | PD-20 | Product |

### Can Be Deferred to Technical Implementation (Arena-Agent)

| # | Unknown | Why deferrable | Sources | Category |
|---|---|---|---|---|
| U-32 | Production URL on Vercel + current deploy status | Technical, needs Vercel dashboard — does not block product definition | BD-03, S09 | Technical |
| U-33 | Vercel env vars actual (AUTH_SECRET, GOOGLE_ID/SECRET, IP_SALT, STORAGE_DRIVER, S3_*) | Technical, needs dashboard | BD-03, S09 | Technical |
| U-34 | Bucket R2/S3/MinIO existence | Technical, infra choice | BD-03, S09 | Technical |
| U-35 | S3Storage real test vs mocks only | Technical, needs bucket | BD-03, S09 | Technical |
| U-36 | Integration tests 94 + E2E 30 results (not run because writes to prod) | Needs isolated test DB — technical | BD-04, S09 | Technical |
| U-37 | ffmpeg now in any env besides local .storage 216 outputs | Needs real build logs | BD-05, S09 | Technical |
| U-38 | Media infrastructure choice worker vs S3 presigned vs managed service (cost) | Depends on product duration/aspect decisions — deferrable after product | TD-01, S07 | Technical |
| U-39 | Storage driver Local vs S3, ensureWatermarkFile writes to ./storage even with S3 | Depends on TD-01 | TD-02 | Technical |
| U-40 | FFmpeg details thumbnail scale, watermark generation | Depends on TD-01 + watermark spec | TD-03 | Technical |
| U-41 | Upload arrayBuffer 80MB in memory vs streaming, body limit 4.5MB | Depends on TD-01 | TD-04, P1-8 | Technical |
| U-42 | Delivery Range/206, Content-Disposition, auth for submissions/* | Depends on privacy + infra | TD-05 | Technical |
| U-43 | Worker void promise vs real queue + retry + lease | Depends on infra | TD-06 | Technical |
| U-44 | Schema drift 3 indexes add @@index or no-op migration | Independent technical, but should not run migrate dev before fix | TD-07 | Technical |
| U-45 | BUG-1/2/3/5 etc. fixes (code vs UUID, PROCESSED vs WATERMARKED, durationMs NULL, double fetch, /saved N requests, getCurrentUser 3x) | Independent technical fixes | TD-08 to TD-11 | Technical |
| U-46 | Git hygiene 1 commit no remote dirty, agent/ .agents/ inside repo | Independent P0 | TD-12 | Technical |
| U-47 | Env separation .env.local prod creds, defaults insecure, E2E helper forges JWT | Independent P0-3 | TD-13 | Technical |
| U-48 | Testing isolation no CI, no isolated DB | Depends on env separation | TD-14 | Technical |

### Informational / Low Impact

| # | Unknown | Why low impact | Sources | Category |
|---|---|---|---|---|
| U-49 | Manus relation to current production — is WebDev yemreact-deploy related to Next.js yemreact-next? + Who wrote Phase 0→6L + Who is Manus/Nibras + qnasly189@gmail.com role + mtimes unified + error.tsx behavior + performance under load + a11y axe + Google OAuth Testing vs Production mode + other branches outside box | Informational, does not block product re-foundation, but useful for history | BD-06 to BD-08, S09, S11, S12 | Historical/Informational |

## Summary

- Must Resolve Before: 10 unknowns — all product definition, core loop, pipeline timing, duration/aspect, search route, bottom nav, sidebar
- Can Resolve During: 21 unknowns — categories, collections, legal, terminology, footer, header, home composition, search intent, rails, detail modal, settings, growth, save UI, watermark spec, submission fields, privacy, retention, featured, metrics
- Can Be Deferred to Technical: 17 unknowns — production URL, Vercel env, bucket, S3 test, integration tests, ffmpeg now, media infra, storage, upload, delivery, worker, schema drift, bugs, git, env separation, testing isolation
- Informational/Low: 1 group (7 sub-items) — Manus relation, who wrote phases, etc.
- Total: 49
