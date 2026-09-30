# 07_GAPS_CONTRADICTIONS_AND_EXECUTION_ROADMAP.md

## Gap Analysis Summary

| # | Gap | Origin | Impact | Resolution | Owner |
|---|-----|--------|--------|-----------|-------|
| G1 | Media processing not runnable on Vercel – ffmpeg absent, local storage only, body‑limit 4.5 MB | `YemReact‑Technology‑State‑Audit.md §6`, `01-DECISIONS-LOG.md` | **P0 blocker** – no real videos can be published | Provision an external worker (VPS/Fly/Railway) **or** switch `STORAGE_DRIVER=s3` with presigned upload | CTO / Infra Lead |
| G2 | BUG‑1: `api.event` expects `code` but client sends UUID → save/download/share counts permanently zero | `01-DECISIONS-LOG.md` (event route), `YemReact‑Product‑UI jsx.md`, `YemReact‑Web‑Prototype.jsx.md` | Metrics unreliable; product analytics broken | Align client to send `reaction.code` **or** make route accept both; update corresponding tests | Frontend Lead |
| G3 | BUG‑2: `collectionRepository.include.media` set to `PROCESSED` but pipeline only produces `WATERMARKED`/`THUMBNAIL` → collection cards show placeholders | `03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md`, `YemReact‑Technology‑State‑Audit.md §9` | UI glitch when collections are displayed; reduces discoverability | Change `include` to `{kind: "WATERMARKED"}` or remove filter; update `collectionRepository` | Backend Lead |
| G4 | BUG‑3: Seed `duration` not written to `durationMs` → all reaction durations `null` | `YemReact‑Technology‑State‑Audit.md §9`, `prisma/seed.ts` | Duration display broken; affects UI quality rubric | Update `seed.ts` to write `durationMs: r.duration * 1000` | Data Engineer |
| G5 | Schema drift – 3 raw indexes not in Prisma schema (`Reaction_searchText_gin`, `Reaction_category_published_idx`, `Reaction_published_status_idx`) | `YemReact‑Technology‑State‑Audit.md §4.2` | Future `prisma migrate dev` may drop the GIN index → search quality degrades | Add `@@index` directives to schema or create a no‑op migration that preserves them | DB Admin |
| G6 | BUG‑5: `processingStatus = "processing"` can lock forever (no timeout/lease, retry only for `failed`) | `YemReact‑Technology‑State‑Audit.md §9` | Orphaned assets; media never finalises | Add retry path for `processing` older than X minutes; expose `?retry` endpoint | Backend Lead |
| G7 | SEC‑3: `/media/[…key]` streams submissions‑origin videos without auth check – potential leak of unreviewed content | `YemReact‑Technology‑State‑Audit.md §9` | Security risk if key becomes guessable | Restrict `/media/submissions/*` to admin only (add `requireAdmin` guard) | Security Lead |
| G8 | ENV‑1 / SEC‑2: `.env.local` contains production Neon credentials; `AUTH_SECRET` defaults insecure in dev | `YemReact‑Technology‑State‑Audit.md §9` | Accidental writes to production DB; credibility loss | Separate dev Neon branch; move secrets to Vercel dashboard; never commit `.env.local` | DevOps |
| G9 | No CI / no isolated test DB – 218 integration/E2E tests cannot run safely; `.last-run.json` does not indicate which subset executed | `YemReact‑Technology‑State‑Audit.md §12` | Inability to verify changes; risk of regressions | Set up Docker‑based dev DB or Neon branch; add GitHub Actions CI (out of current scope) | QA Engineer |
| G10 | Terminology conflict: "التصنيفات" vs "الفئات" – 20 occurrences of "التصنيفات" after decision to use "الفئات" | `01-DECISIONS-LOG.md`, `02-OPEN-QUESTIONS.md`, `03-PRODUCT-VISION.md` | UI strings mismatched with product decisions; confusion for Arabic users | Perform a mass‑replace of "التصنيفات" → "فئات" in all UI files; document the change | Localization Lead |
| G11 | Git not committed – 119 new files + 28 modified, single commit, no remote | `YemReact‑Technology‑State‑Audit.md §12` | Risk of losing Phase 6 work; no rollback | Commit + push to remote (see Phase 7 Step 1) | CTO |
| G12 | Missing Settings UI – brand voice mentions 4 toggles (autoplay, sound, data‑saving, etc.) but no UI built | `02-OPEN-QUESTIONS.md`, `03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md` | Deferred feature; does not block MVP but impacts UX completeness | Post‑MVP; can be back‑logged | Product Owner |

## Contradiction Resolution Log

| Contradiction | Involved Files | Decision (preferred source) | Reason |
|---|---|---|---|
| **C1** – Search page vs home‑page query string – some docs propose a dedicated `/search` route; `01-DECISIONS-LOG.md` explicitly rejects it | `01-DECISIONS-LOG.md`, `03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md` | Keep home page as the only search entry point (`/?q=…`) | Maintains single‑page mental model & SEO; avoids duplicate content |
| **C2** – Bottom‑nav item: “Collections” vs “Submit Reaction” – `03‑IA` lists “Collections” as a rail; `01‑DECISIONS‑LOG.md` (mobile bottom nav) proposes “Submit Reaction” | `03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md`, `01-DECISIONS-LOG.md` | Retain **Submit Reaction** as the 3rd mobile bottom‑nav item (per MVP directive). Collections become a future rail (post‑MVP). | MVP must prioritize content growth over browsing; submit drives library expansion |
| **C3** – Brand token LOCKED vs UI prototype using different colors – `YemReact‑Brand‑v1.0‑LOCKED.html` locks primary/secondary; prototype HTML uses `#006633` and `#B8860B` (same) but some JSX overrides with hard‑coded values | `YemReact‑Brand‑v1.0‑LOCKED.html`, `src/components/*` | Enforce LOCKED tokens via CSS custom properties; any override must go through an ACCEPTED decision | Prevents accidental brand drift; simplifies future redesigns |
| **C4** – Auth flow: Google‑only vs optional email/password – `YemReact‑MVP‑Directive.md §1‑C` says Google‑only; `01‑DECISIONS‑LOG.md` mentions “Google Sign‑In optional” | `YemReact‑MVP‑Directive.md`, `01-DECISIONS-LOG.md` | Adopt Google‑only as the **canonical** auth method for MVP; any password flow is deferred | Keeps auth surface minimal; aligns with “guest” use‑case |

## Risk Matrix (Likelihood × Impact)

| Risk ID | Description | Likelihood (1‑5) | Impact (1‑5) | Score (L × I) | Mitigation |
|---|---|---|---|---|---|
| R1 | Media pipeline remains blocked on Vercel | 5 | 5 | 25 | Provision external worker (Step 3‑4 in roadmap) |
| R2 | BUG‑1 not fixed → analytics blind | 4 | 4 | 16 | Align client‑side code + test (Phase 7‑Step 2) |
| R3 | Schema drift causes search collapse | 3 | 5 | 15 | Add `@@index` to schema (Phase 7‑Step 3) |
| R4 | Security leak via unprotected `/media` endpoint | 2 | 5 | 10 | Add `requireAdmin` guard (Phase 7‑Step 4) |
| R5 | `.env.local` exposure → prod DB writes | 3 | 5 | 15 | Separate env (Phase 7‑Step 5) |
| R6 | Terminology conflict leads to UI confusion | 2 | 3 | 6 | Mass‑replace & docs update (Phase 7‑Step 6) |
| R7 | Missing Settings UI → UX debt (post‑MVP) | 4 | 2 | 8 | Back‑log for Phase 8 |

## Execution Roadmap (next steps after Phase 7)

| Phase | Objective | Key Deliverables | Dependencies | Owner |
|---|---|---|---|---|
| **P0‑Git hygiene** | Stabilise source‑code history | • Commit all Phase 6 changes (excluding `agent/`, `.agents/`, `skills-lock.json`)<br>• Add remote (GitHub/GitLab)<br>• Verify `git log` shows two commits; `git remote -v` non‑empty | None (immediate) | CTO |
| **P1‑Env separation** | Isolate development Neon branch from production | • Create Neon branch or local Postgres Docker instance<br>• Move production credentials out of `.env.local`; document env mapping<br>• Run `npm run test:integration` and `npm run test:e2e` against the dev DB without touching production | P0 completed | DevOps |
| **P2‑Media infrastructure** | Enable video processing in production | • Decide between (a) external worker service or (b) `STORAGE_DRIVER=s3` + presigned upload<br>• Refactor `processMediaAsset` to be worker‑friendly (no in‑process spawn)<br>• Update `STORAGE_DRIVER` env, `ensureWatermarkFile` path, and `/media` route guards<br>• Perform a successful end‑to‑end upload → approved reaction on a staging Neon branch | P1 completed; access to a worker VM or S3 bucket | CTO / Infra Lead |
| **P3‑Bug‑1 fix** | Restore save/download/share metrics | • Change `ReactionCard`/`ReactionDetail` to send `reaction.code` in `api.event()` call<br>• Update `tests/unit/reaction-save.test.ts` and `tests/e2e/save-sync.spec.ts` accordingly<br>• Verify that POST `/api/reactions/YR-0001/event` returns 200 and increments `events` counter | P0‑P1 done; front‑end access | Frontend Lead |
| **P4‑Bug‑2/3/5 fixes** | Fix collection media, seed duration, processing lock | • Adjust `collectionRepository.include` to `{kind: "WATERMARKED"}`<br>• Edit `prisma/seed.ts` to write `durationMs`<br>• Add retry logic for `processing` status older than X min; expose `?retry` endpoint<br>• Run unit tests to confirm | P0‑P2 done; backend access | Backend Lead |
| **P5‑Security hardening** | Protect `/media/submissions/*` | • Add `requireAdmin` guard in `media/[...key]/route.ts`<br>• Ensure only admin‑generated keys are streamable<br>• Run a manual penetration test (or automated security scan) | P2 done; admin credentials available | Security Lead |
| **P6‑Env & CI setup** | Enable safe test execution | • Add `.env.example` with only non‑sensitive vars<br>• Configure GitHub Actions to spin a temporary Neon branch for each PR<br>• Ensure `prisma migrate diff` does not drop the GIN index (add `@@index`)<br>• Verify that 94 integration + 124 E2E tests pass on the CI | P1‑P5 done; CI access | QA Engineer |
| **P7‑Terminology cleanup** | Resolve “التصنيفات” vs “فئات” | • Perform a global search‑replace of “التصنيفات” → “فئات” in all UI/MD files<br>• Update documentation and user‑facing strings<br>• Communicate the change to all stakeholders | P0‑P6 done; translators if needed | Localization Lead |
| **P8‑Post‑MVP polish** | Add non‑blocking enhancements | • Implement Settings UI (autoplay, data‑saving toggles)<br>• Add “Featured” selection UI<br>• Polish onboarding walkthrough<br>• Conduct accessibility audit (contrast, screen‑reader) | All P0‑P7 completed | Product Owner |

> **Note** – The roadmap assumes the owner will provide the written `" تم "` confirmations for each mandatory MVP feature (as per `YemReact‑MVP‑Directive.md §6`). Without those confirmations, no implementation may start.

## Final Verdict (Current Project Status)

| Category | % Complete | Rationale |
|---|---|---|
| Foundation | 90 | strict TS, lint/prettier zero, build clean, unified AppError/env/http |
| Backend (API) | 80 | 23 route handlers with zod + guards + audit; missing service layer, rate limit, batch endpoints |
| Database | 75 | schema clear, 4 migrations applied, search trgm, drift indexes, 3 dead models |
| Auth | 80 | Google+JWT+DB role works (real users); no role mgmt, insecure defaults |
| Media | 35 | full logic locally (216 runs) but **zero** production capability (ffmpeg missing, storage local, body‑limit) |
| Admin | 70 | CRUD for reactions/categories/collections/submissions; no Featured/Users/Audit UI, no pagination |
| Content | 10 | 12 seed reactions, no video in production |
| UX | 55 | flows for visitor/user/admin exist; no Settings, no suggestions, TTL groups, 3 nav shells |
| UI | 60 | Brand v1.0 applied, RTL, responsive no overflow, CSS monolithic, admin raw, differs from prototype |
| Testing | 60 | 171 unit + 94 E2E now pass; 94 integration + 30 E2E not runnable (DB/ffmpeg) |
| Deployment | 40 | Vercel+Neon read+auth ok; media impossible, env unclear, no `vercel.json` |

**Overall Project Status:** ≈ 60 % (weighted average).  
**Key Blockers:** Media pipeline (P0), Git hygiene (P0), Env separation (P1), BUG‑1 (P1).  

When the owner signs off (` تم `) on the mandatory MVP features **and** the P0/P1 infrastructure items (especially media worker & env split) are resolved, the project can move to a launch‑ready ≈ 90 % state.

--- ✅ PHASE 7 COMPLETE. Type "المرحلة التالية" to proceed (or type "إنهاء" to stop).