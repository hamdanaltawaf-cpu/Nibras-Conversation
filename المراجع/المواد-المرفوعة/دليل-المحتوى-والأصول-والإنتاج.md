# 06_CONTENT_ASSETS_AND_PRODUCTION_GUIDE.md

## 6.1 Asset Inventory (what exists today)

| Category | File(s) | Description | Size / Format | Source |
|----------|---------|-------------|---------------|--------|
| **PNG UI mock‑ups** | `01-Profile-Picture-720x720.png`, `02-Cover-1640x720.png`, `07-PostTemplate-1080x1350.png`, `08-CategoryCollection-1080x1350.png`, `09a‑09c‑Announcement‑*.png`, `10‑Story‑RequestReaction‑1080x1920.png`, `tablet‑768x1024.png` | Profile picture, cover banner, post‑template, category‑collection thumbnails, announcement graphics, story‑reaction visual, tablet layout reference. | PNG, dimensions as indicated. | `[Source: uploads/]` |
| **Safe‑area guides** | `06b‑ReactionClip‑SafeAreaGuide‑Default.png`, `06b‑ReactionClip‑SafeAreaGuide‑Mirrored.png`, `06‑ReactionClip‑Overlay‑1x1‑Default‑TopRight.png`, `06‑ReactionClip‑Overlay‑1x1‑Mirrored‑TopLeft.png`, `06‑ReactionClip‑Overlay‑Default‑TopRight.png`, `06‑ReactionClip‑Overlay‑Mirrored‑TopLeft.png` | 1 × 1 px safe‑area guides for reaction‑clip overlays (default & mirrored). | PNG. | `[Source: uploads/]` |
| **Illustrative brand elements** | `YemReact‑Brand‑v1.0‑LOCKED.html` (contains SVG markup for “Qussasa Mark”). | Vector‑style logo/mark that must not be altered (LOCKED). | HTML‑embedded SVG. | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| **Audio / Speech assets** | None currently uploaded. (Future: narration for onboarding, watermark‑audio.) | – | – | – |
| **JSON credentials** | `client_secret_334305269990-2r4r3laaa2h2q56pnujr8n33qriapqb3.apps.googleusercontent.com.json` | OAuth client for Google Sign‑In. | JSON. | `[Source: uploads/]` |
| **Text / policy docs** | `final_confirmation.md`, `12‑Final‑Asset‑Inventory.md`, `00‑Bio‑About‑IntroPost‑Checklist.md`, `01‑DECISIONS‑LOG.md`, `02‑OPEN‑QUESTIONS.md`, `03‑PRODUCT‑VISION.md`, `05‑ARCHITECTURE.md`, `YemReact‑MVP‑Directive.md`. | Policy, decisions, open questions, vision, tech spec, MVP scope. | Markdown / MD. | `[Source: uploads/]` |

> **Note** – All PNG assets are stored under `/home/user/uploads/` and can be referenced directly in the UI. No video files are present in the workspace; video content will be added later via the submission workflow (see §4.2).

---  

## 6.2 Content Production Pipeline (from upload to public reaction)

| Step | Action | Responsible | Output | Checks / Gates |
|------|--------|--------------|--------|----------------|
| **1️⃣ Idea & Script** | Writer defines the situation (e.g., “wedding celebration”), dialect, and short caption (≤ 8 s). | Content writer / community manager. | Plain‑text brief (Arabic/English mix). | *Must match brand voice* – see **Brand Voice** in Phase 2. |
| **2️⃣ Record / Capture** | Record a 2‑8 s vertical video (front‑facing or screen‑capture) with clear speech/acting. | Creator (or hired actor). | Raw video file (MP4, ≤ 80 MB). | *Duration check* – `validate` in `LocalMediaService`. |
| **3️⃣ Upload** | Drag‑&‑drop or “Add Reaction” button → `POST /api/submissions` (multipart). Auth: guest (local save) or signed‑in (cloud sync). | User / admin. | `Submission` row created, status **pending**. | *Auth guard* – `requireUserOrRedirect`. |
| **4️⃣ Validation** | Server runs `LocalMediaService.validate`: MIME, size, magic bytes, duration 2‑8 s. | Backend (API route). | If invalid → 400 with reason; else → **idle** MediaAsset. | *See `lib/media/validator.ts`. |
| **5️⃣ Media Processing** (off‑worker) | Worker runs `processMediaAsset`: ffprobe → dimensions/duration → ffmpeg thumbnail → ffmpeg overlay watermark → store `THUMBNAIL`, `WATERMARKED`, update `MediaAsset` status → `processingStatus = done`. | External worker / Cloud Function (not yet on Vercel). | `MediaAsset` now has `WATERMARKED` version, `durationMs` filled. | *Watermark gate* – `pickPublicVideo` prefers `WATERMARKED`. |
| **6️⃣ Admin Review** | Admin visits `/admin/submissions`, watches preview, clicks **Approve** or **Reject**. Approve triggers `nextReactionCode()` → creates `Reaction` row, sets `status = published`, links `MediaAsset`. | Admin user (role = ADMIN). | New public `Reaction` appears on home page; video becomes viewable. | *Watermark gate* returns 409 if missing. |
| **7️⃣ Publication** | Public page `/r/[code]` renders the `WATERMARKED` video (or `PROCESSED`/`ORIGINAL` fallback). | Front‑end. | User can “Take” (download/share), “Save” (add to personal list). | *Analytics* – fire `api.event(code)` (view/save/download/share). |
| **8️⃣ Post‑publish** | Optional: add to “Featured” (manual), promote via social templates (PNG post‑template), add to collections if editorial group. | Content team / admin. | Increased discoverability. | *No automatic infinite‑feed* – per MVP spec. |

---  

## 6.3 Copy Deck (sample copy for each asset type)

| Asset type | Example copy (Arabic / English mix) | Usage |
|------------|--------------------------------------|-------|
| **Profile picture** | “🟢 يمنية – صورة الشعار” | Header avatar. |
| **Cover banner** | “📢 مكتبة رياكت – اكتشف الرياكن يمن بسيط” | Landing‑page hero background. |
| **Post template (1080×1350)** | “🎉 فرحة بالعيدي – استخدم #يمريكية وانشر ليقَطَ” | Social‑media share image (PNG). |
| **Announcement‑Intro** | “🔍 ابحث ب الموقف – اعثر على الرياكن مناسب” | Intro banner on first‑time visit. |
| **Announcement‑ComingSoon** | “جاء الأسبوع القادم – مزيد من الرياكن القادمة” | Countdown banner. |
| **Announcement‑Milestone** | “🎯 100 رياكن مُنشَأَة – شكرًا للمُساهِمِينَ” | Milestone celebration. |
| **Story‑Reaction** | “⏱️ 2 ثانية – موقف ضحك يمني” | Short‑video teaser. |

All copy respects the **Brand Voice** (Hybrid Arabic‑English, concise, direct) and the **LOCKED** visual identity.

---  

## 6.4 Quality Rubric for a “Good” Reaction (as per **03‑PRODUCT‑VISION.md**)

| Criterion | Definition |
|-----------|------------|
| **Understandable without external context** |Viewer instantly knows the situation. |
| **Duration 2‑8 seconds** |Matches the “core loop” timing. |
| **Genuine Yemeni dialect/performance** |Tagged with dialect (Sanaa, Aden, etc.). |
| **Clear situational tag** |Not too generic; e.g., “wedding‑celebration”, “apology”. |
| **Technical cleanliness** |Audio audible, no excessive background noise, video stable. |
| **No exploitation of vulnerable moments** |Respects privacy/ethics guidelines. |
| **Consistent watermark** |Auto‑applied per pipeline; absent only if processing failed. |

A reaction that meets **all** six criteria is considered *high‑quality* and is prioritized for “Featured” or “Collections” placement.

---  

## 6.5 Production Checklist (must be completed before a reaction goes live)

- [ ] Script brief written and signed off by content lead.  
- [ ] Video recorded, ≤ 8 s, vertical orientation.  
- [ ] File format MP4, MIME = video/mp4, size ≤ 80 MB.  
- [ ] Upload via `/api/submissions` (guest or signed‑in).  
- [ ] Server validation passes (duration, magic bytes).  
- [ ] Media‑processing worker completes (ffprobe + ffmpeg watermark).  
- [ ] `MediaAsset` status = `WATERMARKED`, `durationMs` filled.  
- [ ] Admin reviews and **Approves** (watermark gate satisfied).  
- [ ] New `Reaction` row created, published status = `published`.  
- [ ] Public page `/r/[code]` renders watermarked video; “Take” and “Save” buttons functional.  
- [ ] Analytics event fired (`api.event(code)` – view/save/download/share).  
- [ ] Copy deck attached (poster image, caption).  

If any checklist item fails, the reaction stays **pending** or is **rejected** with a reason note.

---  

## 6.6 Open Production Questions (to be resolved before Phase 7)

| # | Question | Why it matters | Current stance |
|---|----------|----------------|----------------|
| 1 | **Worker deployment** – Should we provision a dedicated worker service (VPS/Fly/Railway) or outsource to Cloud Functions? | Determines whether video processing can run in production (P0 blocker). | Decision pending – see Phase 4 blocker. |
| 2 | **S3 vs local storage** – For how long should original videos be retained? | Affects cost, backup, and the watermark‑gate fallback. | Default: local `.storage`; S3 optional when `STORAGE_DRIVER=s3`. |
| 3 | **Submission‑event tracking** – Should `api.event` send `code` or `uuid`? | BUG‑1 currently makes all save/download/share counts zero. | Align client to send `code`. |
| 4 | **Featured‑reaction selection** – Who chooses which reactions become “Featured” and how often? | Influences discovery and motivates contributors. | Manual admin decision (no automated trending). |
| 5 | **Multilingual captions** – Should captions be bilingual (Arabic + English) or single‑language? | Impacts accessibility for diaspora users. | Arabic primary, optional English translation. |

---  

### 📌 Closing Statement  

The Content Assets & Production Guide consolidates every uploaded artifact (PNG mock‑ups, brand‑LOCKED HTML, policy docs, technical audit) into a single, actionable pipeline. It defines **who does what**, **what the quality bar is**, and **what must be checked** before a reaction becomes publicly visible. The open production questions are the remaining sign‑posts that must be answered (particularly the media‑processing infrastructure) before the project can move from its current ≈ 60 % state to a launch‑ready ≈ 90 % state.  

--- ✅ PHASE 6 COMPLETE. Type "المرحلة التالية" to proceed to Phase 7.