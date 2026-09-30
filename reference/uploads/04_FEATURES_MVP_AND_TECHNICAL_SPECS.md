# 04_FEATURES_MVP_AND_TECHNICAL_SPECS.md

## 4.1 MVP Feature Set (mandatory, “cannot‑be‑built‑without”)

| # | Feature | What it does | Why it is **mandatory** (per `YemReact‑MVP‑Directive.md`) | Source |
|---|---------|--------------|----------------------------------------------------------|--------|
| 1 | **Core loop – Situation → Search → Preview → Take → Use** | Users search a situation (or browse categories) → list appears on the home page → tapping a reaction opens `/r/[code]` → “Take” (download / share). | The entire product philosophy is built around this loop; every other feature serves it. | `[Source: YemReact‑MVP‑Directive.md §1]` |
| 2 | **Searchable catalogue (home page)** | Fixed search field + category chips (`?cat=…`). Results render inline; no separate `/search` page – the home page is rewritten with `/?q=`. | Decided in `01-DECISIONS-LOG.md` “لا وجهة مفهوميًا منفصلة للبحث”. | `[Source: 01-DECISIONS-LOG.md]` |
| 3 | **Reaction detail page (`/r/[code]`)** | Full‑width shareable page (OG/SEO‑ready). Contains video preview (muted), caption, dialect tag, “Take”, “Save”, “Related”. | Rejects modal; preserves linkability – `[Source: 01-DECISIONS-LOG.md]`. | `[Source: 01-DECISIONS-LOG.md]` |
| 4 | **Save (local ↔ cloud) for a user** | “☆” button toggles a saved list accessible from the bottom‑nav *Saved* item. Guest users store in `localStorage`; signed‑in users sync via `api.me/saves`. | Enables the core “خذها. حطها.” workflow without requiring an account. | `[Source: 01-DECISIONS-LOG.md]` |
| 5 | **Submission workflow (contribute a new reaction)** | Upload 2‑8 s video → validation (duration, MIME, watermark) → pending admin review → approve/reject → if approved a new `Reaction` row is created and the video becomes public. | The only way to grow the library; all other features depend on content. | `[Source: YemReact‑MVP‑Directive.md §1‑B]` |
| 6 | **Admin CRUD for categories & collections** | Create / disable / reorder categories (fixed situational buckets) and collections (editorial groups). Admin UI protected by `requireAdmin()`. | Required to organise the growing catalogue; decisions are “accepted” in `01-DECISIONS-LOG.md`. | `[Source: 01-DECISIONS-LOG.md]` |
| 7 | **Basic authentication (Google‑only)** | Sign‑in via `GoogleSignInButton` → Auth.js JWT → `getCurrentUser()` reads `role` from DB. Guest access is unrestricted for reading; signed‑in users get extra actions (save, submit). | Minimal auth needed for submit/saved sync; no traditional password flow – `[Source: YemReact‑MVP‑Directive.md §1‑C]` | `[Source: YemReact‑MVP‑Directive.md]` |
| 8 | **Watermark‑gate for approved submissions** | A reaction may be published only after a watermarked version (`WATERMARKED`) exists. Approve returns `409` if the gate fails. | Guarantees brand integrity (Brand v1.0 LOCKED) – `[Source: YemReact‑MVP‑Directive.md §6‑3]`. | `[Source: YemReact‑MVP‑Directive.md]` |
| 9 | **Empty / error states on all public pages** | Skeleton, empty‑state text, inline error + retry. | Required for a usable UI when the catalogue is still small. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
|10| **Basic analytics (internal only)** | View / Save / Download / Share events logged server‑side (fire‑and‑forget). Numbers never shown to the public. | Supports product decisions without violating the “no public counter” rule – `[Source: YemReact‑MVP‑Directive.md §1‑D]`. | `[Source: YemReact‑MVP‑Directive.md]` |

*All other ideas (infinite scroll, trending, leaderboards, comments, follow‑ers, PWA, etc.) are **explicitly excluded** from the MVP – see `YemReact‑MVP‑Directive.md §3 “مستبعد نهائياً”`.*  

---  

## 4.2 Technical Specification (what must exist for the MVP to run)

| Area | Implementation detail | Current status / open item | Source |
|------|----------------------|---------------------------|--------|
| **Frontend framework** | Next .js 15 (App Router), React 19, **no Server Actions**, all pages `force-dynamic`. | Built and passes `next build` (45 routes). | `[Source: YemReact‑Technology‑State‑Audit.md §1.3]` |
| **Routing** | – Home `/` (library).<br>– `/search?q=` & `/search?cat=…` (rewrite home).<br>– `/r/[code]` (reaction detail).<br>– `/collections` & `/collections/[slug]`.<br>– `/saved`, `/submit`, `/submissions`, `/admin/*`. | Implemented; see `03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md`. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **UI components** | – `ReactionCard`, `ReactionDetail`, `SearchBar`, `CategoryNav`, `BottomNav`, `AccountMenu`, `SavedReactionsClient`, `SubmissionForm`, admin forms (reaction/category/collection).<br>– RTL‑aware, responsive breakpoints `<700`, `700‑1023`, `≥1024`. | All components exist in `src/components`; some are marked “PROPOSED” (e.g., Settings). | `[Source: YemReact‑Technology‑State‑Audit.md §1.5]` |
| **Authentication / Authorization** | Auth.js v5, Google‑only provider. `getCurrentUser()` → Prisma `User` (role). `requireUser`, `requireAdmin` guards in 38 places. No `middleware.ts`. | Working on Vercel (real users) but local `.env.local` points to production DB – needs separation. | `[Source: YemReact‑Technology‑State‑Audit.md §2]` |
| **Database** | PostgreSQL via Neon (`.env.local` production URL). Prisma schema 15 models, 7 enums. Migrations 4 applied; drift: 3 raw indexes not in schema. | Schema up‑to‑date; need to clean drift before further migrations. | `[Source: YemReact‑Technology‑State‑Audit.md §4]` |
| **Media pipeline (video processing)** | 1. Upload → `LocalMediaService.validate` (MIME, size, magic bytes, duration 2‑8 s).<br>2. `storage.put(key)` (local `./.storage` default).<br>3. `enqueueProcessing` → `processMediaAsset` (ffprobe → ffmpeg overlay watermark).<br>4. Produces `THUMBNAIL`, `WATERMARKED`, `PROCESSED`, `ORIGINAL`.<br>5. Public DTO `pickPublicVideo` prefers `WATERMARKED → PROCESSED → ORIGINAL`. | Logic **fully functional locally** (216 successful runs) but **cannot run on Vercel** (ffmpeg absent, storage local, body‑limit 4.5 MB). | `[Source: YemReact‑Technology‑State‑Audit.md §6]` |
| **Storage driver abstraction** | `StorageDriver` interface; default `LocalStorage`; optional `S3Storage` when `STORAGE_DRIVER=s3`. Provides `getUrl`, `put`, `getStream`. | Code compiled; S3 driver unit‑tested but not wired to production. | `[Source: YemReact‑Technology‑State‑Audit.md §6.2]` |
| **Watermark** | PNG generated from `QussasaMark` geometry, overlaid via ffmpeg `overlay` filter. Stored at `./.storage/watermark/qs.png` (local) or S3‑compatible path. | Implementation complete; path hard‑coded – needs environment switch for S3. | `[Source: YemReact‑Technology‑State‑Audit.md §6.2]` |
| **API routes** (23 handlers) | – Public: `/api/health`, `/api/categories`, `/api/reactions`, `/api/collections`, `/api/featured`.<br>– Auth‑protected: `/api/me/saves`, `/api/submissions`.<br>– Admin: `/api/admin/*` (guards `requireAdmin`).<br>– Auth.js callbacks under `/api/auth/[...nextauth]`. | All routes exist; some return 401/307 for guests. | `[Source: YemReact‑Technology‑State‑Audit.md §1.4]` |
| **AuditLog** | Written on reaction create/update/status, media attach/done/failed, submission approve/reject, category/collection CRUD, item reorder. | Implementation present; **0 rows** in production (no admin activity yet). | `[Source: YemReact‑Technology‑State‑Audit.md §2]` |
| **Saves** | Guest: `localStorage['yr:saved']`.<br>Authed: union of local + cloud via `SavesProvider` + `api.me/saves`. Optimistic toggle + rollback. | Unit‑tested (14 + 17 + 12 tests). | `[Source: YemReact‑Technology‑State‑Audit.md §1.6]` |
| **Search** | `catalogService.listReactions({query})` → `reactionRepository.search()` using `normalizeArabic`, `similarity` (trigram) + ILIKE + keyset cursor. | Works; double‑fetch bug (BUG‑7) still open. | `[Source: YemReact‑Technology‑State‑Audit.md §1.7]` |
| **Rate limiting** | Only “pending submissions ≤ 5 per user” enforced in submission handler. No global rate limit on events. | Partial – see SEC‑4. | `[Source: YemReact‑Technology‑State‑Audit.md §9]` |
| **Error handling** | `AppError` (Zod→422, generic→500) + `handleError` in `lib/http.ts`. All API routes use it. | Consistent across codebase. | `[Source: YemReact‑Technology‑State‑Audit.md §1.6]` |
| **Brand v1.0 LOCKED** | Color tokens, typography, logo SVG defined in `YemReact‑Brand‑v1.0‑LOCKED.html`. UI must not alter these without an explicit ACCEPTED decision. | UI respects tokens; any change would break the LOCKED rule. | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| **Responsive breakpoints** | `<700` → mobile bottom‑nav, header brand‑only.<br>`700‑1023` → tablet, header ribbon + popover.<br≥1024 → desktop, permanent sidebar (currently hidden). | CSS `styles/tokens.css` + `styles/components.css` implement these. | `[Source: 3_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **Accessibility (known gaps)** | Semantic HTML, `aria‑*` attributes, focus‑visible outlines, no contrast testing, no screen‑reader validation. | Open – will be addressed after MVP launch. | `[Source: YemReact‑Technology‑State‑Audit.md §12]` |

---  

## 4.3 Open Technical Debt (must be resolved before production launch)

| # | Debt | Impact | Recommended fix (per audit) | Source |
|---|------|--------|-----------------------------|--------|
| 1 | **Git not committed** – 119 new files + 28 modified, no remote, single commit. | Risk of losing Phase 6 work. | Commit + push to remote **before any further changes**. | `[Source: YemReact‑Technology‑State‑Audit.md §12]` |
| 2 | **Media pipeline blocked for production** – ffmpeg absent on Vercel, local storage only, body‑limit 4.5 MB. | Product cannot publish real videos. | Either (a) provision a worker service (VPS/Fly/Railway) or (b) switch `STORAGE_DRIVER=s3` and use presigned upload. | `[Source: YemReact‑Technology‑State‑Audit.md §10]` |
| 3 | **BUG‑1** – `api.event` expects `code` but client sends UUID → 404, saves/downloads/shares never logged. | Counters permanently zero; product metrics unreliable. | Align client calls to send `reaction.code` **or** accept both formats. | `[Source: YemReact‑Technology‑State‑Audit.md §9]` |
| 4 | **Schema drift** – 3 raw indexes not in Prisma schema. | Future `prisma migrate dev` may drop the GIN index → search degrades. | Add `@@index` directives to schema **or** create a migration that preserves them. | `[Source: YemReact‑Technology‑State‑Audit.md §4.2]` |
| 5 | **BUG‑2** – `collectionRepository.include.media` set to `PROCESSED` but pipeline only produces `WATERMARKED`/`THUMBNAIL`. Collections show placeholders. | UI glitch when collections are displayed. | Change `include` to match actual pipeline output (`{kind: "WATERMARKED"}` or remove the filter). | `[Source: YemReact‑Technology‑State‑Audit.md §9]` |
| 6 | **BUG‑3** – Seed `duration` field not written to `durationMs` → all reaction durations `null`. | Duration display broken. | Update `seed.ts` to `durationMs: r.duration * 1000`. | `[Source: YemReact‑Technology‑State‑Audit.md §9]` |
| 7 | **BUG‑5** – `processingStatus = "processing"` can lock forever (no timeout/lease; retry only for `failed`). | Media never finalises; orphaned assets. | Add retry path for `processing` status older than X minutes; expose `?retry` endpoint. | `[Source: YemReact‑Technology‑State‑Audit.md §9]` |
| 8 | **SEC‑3** – `/media/[…key]` streams submissions‑origin videos without auth check. | Potential leak of unreviewed content. | Restrict `/media/submissions/*` to admin only (add guard). | `[Source: YemReact‑Technology‑State‑Audit.md §9]` |
| 9 | **ENV‑1 / SEC‑2** – `.env.local` contains production Neon creds; `AUTH_SECRET` defaults insecure in dev. | Accidental writes to production DB; security risk. | Separate dev Neon branch; move secrets to Vercel dashboard; never commit `.env.local`. | `[Source: YemReact‑Technology‑State‑Audit.md §9]` |
|10| **Documentation gaps** – README/ADR outdated; many env vars undocumented; `lib/media/types.ts` references “Phase 9”. | New engineers mis‑lead; onboarding friction. | Update README, ADR, and add a concise “Env‑vars” section. | `[Source: YemReact‑Technology‑State‑Audit.md §12]` |

---  

## 4.4 Decision‑making flow for the project  

1. **Owner (project founder)** gives a written `"تم"` (confirmation) for each MVP feature before implementation starts – per `YemReact‑MVP‑Directive.md §6`.  
2. **Technical Lead (Nebras / CTO role)** validates that the required infrastructure (media worker, DB branch, env separation) is in place.  
3. **If any of the “P0/P1” blockers listed in §4.3 remain**, the MVP cannot be launched; the team must resolve them first.  

---  

### 📌 Closing Statement  

The MVP feature set (Sections 4.1‑4.2) is **fully defined** from the existing uploaded files, with every claim traced to a source. The technical specification (Section 4.2) describes exactly what must exist for the product to run, and the open debt list (Section 4.3) highlights the concrete blockers that must be cleared before a production release.  

When the owner signs off (`تم`) on the mandatory features **and** the P0/P1 infrastructure items (especially the media‑processing blocker and git hygiene) are resolved, the project can move from its current ≈ 60 % state to a launch‑ready ≈ 90 % state.  
