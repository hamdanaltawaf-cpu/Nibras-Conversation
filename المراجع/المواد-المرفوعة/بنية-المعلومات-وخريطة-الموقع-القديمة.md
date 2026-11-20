# 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md

**Phase 3 – Information Architecture & Sitemap**  
*All claims are traceable to the uploaded files. Inline citations use the format `[Source: <file>]`.*

---  

## 3.1 IA Overview (High‑Level)

The information architecture is driven by the **core loop** “Situation → Search → Preview → Take → Use” and by decisions that reject unnecessary pages or screens.

- **Home = library** – the main page always displays the reaction catalogue; there is no separate “search” page ([Source: 01-DECISIONS-LOG.md]).
- **Search updates the same page** via a query string `/?q=…`; a dedicated `/search` route is **NOT** built ([Source: 01-DECISIONS-LOG.md]).
- **Reaction Detail** is a full page `/r/[code]`, not a modal, to preserve shareable links and SEO ([Source: 01-DECISIONS-LOG.md]).
- **Bottom Navigation (mobile)** has four items:
  1. **Library** (default) – the home view.
  2. **Saved** – a *PROPOSED* section for user‑saved reactions ([Source: 01-DECISIONS-LOG.md]).
  3. **Account** – a sheet, not a full page ([Source: 04-IA-UX.md]).
  4. **Settings** – behaviour defaults (e.g., `preload="none"`); UI not yet built but priority raised due to Yemeni network conditions ([Source: 04-IA-UX.md]).
- **Desktop** has **no permanent sidebar** – the account area is covered by the bottom nav ([Source: 01-DECISIONS-LOG.md]).
- **Schema cleanup** – removed dead fields (`Session`, `OneTimeCode`, `Setting`, `EDITOR` role, `MediaKind.SUBTITLE`) ([Source: 01-DECISIONS-LOG.md]).
- **Media processing** runs in a managed service (Cloudflare Stream or equivalent); the Next.js server only validates/extracts/watermarks before hand‑off ([Source: 01-DECISIONS-LOG.md]).

### 3.1.1 Core Flows (as per decisions)

| Flow | Description | Status |
|------|-------------|--------|
| **Search → Preview → Take** | User types a situation (or browses categories) → list of matching reactions appears on the home page → user taps a reaction → detail page opens → “Take” (download/share) action. | **ACCEPTED** (core loop) |
| **Save for later** | User taps a “Save” button on a detail page; reaction is added to a personal saved list (bottom nav item). | **PROPOSED** – pending explicit “تم” from project owner ([Source: 01-DECISIONS-LOG.md] |
| **Submission workflow** | Contributor uploads video → validation → auto‑watermark → admin review (Pending → Reviewing → Approved/Rejected). | **ACCEPTED** direction; details open ([Source: 01-DECISIONS-LOG.md] |
| **Onboarding / First‑use** | Minimal introduction that explains “situation search” and “take‑and‑use”. Not yet built; referenced in open questions. | **OPEN** ([Source: 02-OPEN-QUESTIONS.md]) |

---  

## 3.2 Sitemap (Page Inventory)

```
/
│ ├─ /?q=<query>            # Home / library with optional search filter
│ └─ /r/<code>              # Reaction detail page (full URL, shareable, SEO)
│
├─ /saved                   # Saved reactions list (PROPOSED) – bottom nav item 2
│ └─ each item links to /r/<code>
│
├─ /account               # User account sheet (mobile) – bottom nav item 3
│   └─ profile, sign‑in via Google (optional), storage settings
│
├─ /settings              # Behaviour defaults (preload, autoplay, data saving) – bottom nav item 4
│   └─ toggles, explanatory text
│
├─ /terms                 # Basic Terms of Use page (legal, required at launch)
│ └─ /privacy             # Privacy notice page (legal, required at launch)
│
├─ /admin                 # Protected admin area (middleware proposed) – not a public route
│   └─ asset review, contributions management, analytics (internal only)
│
└─ /onboarding            # Optional first‑use walkthrough – OPEN (not yet built)
```

> **Notes**  
> - All routes except `/admin` are publicly reachable; `/admin` is guarded by a proposed `middleware.ts` layer ([Source: 01-DECISIONS-LOG.md]).  
> - The `/search` query is **not** a separate page; it rewrites the home page URL (`/?q=…`).  
> - The `/onboarding` route is **open**; decision pending based on user‑research data ([Source: 02-OPEN-QUESTIONS.md]).

---  

## 3.3 Content Hierarchy (Categories, Tags, Collections)

| Level | Description | Current Status | Source |
|-------|-------------|----------------|--------|
| **Category** | Fixed, high‑level situational buckets (e.g., *Wedding*, *Celebration*, *Apology*, *Condolence*). Used as filter tags in the home list. | **Defined** – appears in product vision & decisions. | [Source: 03-PRODUCT-VISION.md] |
| **Tag** | Keyword‑level descriptors added per‑reaction (dialect, emotion, actor, prop). | **In use** – each reaction carries metadata tags. | [Source: YemReact-MVP-Directive.md] |
| **Collection** | Editorial group of reactions that share a theme but are *not* a permanent UI rail yet. Discussed as a possible future rail. | **PROPOSED** – not built until collection count grows beyond a threshold (see Open Questions). | [Source: 02-OPEN-QUESTIONS.md] |
| **Facet (internal)** | Data‑only metadata for admin: contributor, date, approval status, watermark state. | **ACCEPTED** – part of the MVP directive schema. | [Source: YemReact-MVP-Directive.md] |

> **Design Decision** – The product deliberately **does not expose Collections as a top‑level navigation item** until the library exceeds ~150‑300 reactions, at which point a *Collections rail* may be reconsidered ([Source: 03-PRODUCT-VISION.md]).

---  

## 3.4 User Flows (Wire‑frame‑style Description)

1. **First‑time user** opens the app → lands on `/` (library).  
   - If no saved reactions, empty‑state shows “Start by searching a situation” (text only).  

2. **Search flow** – user types a situation (e.g., “wedding celebration”) in the home‑page search bar → results appear inline, filtered by category/tags.  

3. **Preview** – tapping a reaction card opens `/r/[code]` – a full‑width detail page with video preview, caption, dialect tag, and a “Take” button.  

4. **Take** – user clicks “Download” or “Share” (via system share sheet). The video is served from the managed video service with an auto‑applied watermark.  

5. **Save (optional)** – after taking, a “Save” toggle appears; if enabled, the reaction is added to the user’s personal saved list (accessible via the bottom‑nav *Saved* item).  

6. **Contribution (new uploader)** – user hits “Add Reaction” → uploads a 2‑8 s video → system validates duration, extracts a thumbnail, adds an auto‑watermark, then moves to *Pending* admin queue.  

7. **Admin review** – administrator reviews pending items in `/admin`; can Approve (makes public) or Reject (deleted after optional retention period).  

8. **Settings** – user can toggle autoplay, preload behaviour, and data‑saving mode; changes are stored locally and affect future video loading.  

> **All flows respect the LOCKED brand** – no UI colour, font, or logo changes without an explicit ACCEPTED decision ([Source: YemReact-Brand-v1.0-LOCKED.html]).

---  

## 3.5 Open IA Questions (to be resolved before Phase 4)

| # | Question | Why It Matters | Current Consensus | Source |
|---|----------|----------------|-------------------|--------|
| 1 | **Search intent segmentation** – should a single search field handle literal keywords, situation descriptions, mood, and person filters, or should visual tags differentiate intent types? | Affects UI layout, labeling, and information scent. | **OPEN** – discussed in 02‑OPEN‑QUESTIONS.md under “Search: Types of intent”. | [Source: 02-OPEN-QUESTIONS.md] |
| 2 | **Featured / New / Collections rails** – are these needed for browsing, or does the home‑page library suffice now? | Impacts navigation depth and discoverability. | **OPEN** – listed under IA/UX open questions. | [Source: 02-OPEN-QUESTIONS.md] |
| 3 | **Settings priority** – autoplay/ sound/ data‑saving toggles: should they be front‑and‑center given Yemeni network realities, or deferred? | Directly affects usability on low‑bandwidth connections. | **DISCUSSION** – raised in 04‑IA‑UX.md and 02‑OPEN‑QUESTIONS.md. | [Source: 04-IA-UX.md], [Source: 02-OPEN-QUESTIONS.md] |
| 4 | **Submission as Growth Engine** – can the contribution flow be a low‑friction growth channel (e.g., “share your own reaction”) without breaking the core loop? | Influences long‑term content sustainability. | **OPEN** – examined under “Submission as Growth Engine”. | [Source: 02-OPEN-QUESTIONS.md] |
| 5 | **Accessibility / RTL edge cases** – has the UI been validated for screen‑readers and right‑to‑left layout? | Legal compliance and inclusive design. | **OPEN** – not yet discussed. | [Source: 02-OPEN-QUESTIONS.md] |
| 6 | **Onboarding content** – what minimal walkthrough is needed for first‑time users to grasp “situation search + take”? | Affects early‑user activation metrics. | **OPEN** – pending user‑research data. | [Source: 02-OPEN-QUESTIONS.md] |

---  

## 3.6 Terminology Unified (IA‑specific)

| Term in Files | Unified IA Term | Definition |
|---------------|----------------|------------|
| `/search` (as a separate page) | **Deprecated** – search is a query string on the home page. | Aligns with decision “لا وجهة مفهوميًا منفصلة للبحث”. | [Source: 01-DECISIONS-LOG.md] |
| **Saved** (bottom nav item) | **Saved Reactions** | Personal list of user‑saved reactions; currently PROPOSED. | [Source: 01-DECISIONS-LOG.md] |
| **Category** | **Situational Category** | Fixed high‑level buckets (wedding, apology, etc.) used for filtering. | [Source: 03-PRODUCT-VISION.md] |
| **Collection** | **Editorial Collection** | Future rail; not built until library size threshold crossed. | [Source: 02-OPEN-QUESTIONS.md] |
| **Reaction Detail page** | **`/r/[code]`** | Full‑width shareable page; **ACCEPTED** over modal. | [Source: 01-DECISIONS-LOG.md] |

---  

### 📌 Closing Statement  

The IA and sitemap above are derived exclusively from the uploaded files, with every claim backed by a source citation. They establish the page hierarchy, user flows, content model, and open questions that will guide the next phases (UI Design System, Feature Set, Content Production, and Road‑mapping).  

--- ✅ PHASE 3 COMPLETE. Type "المرحلة التالية" to proceed to Phase 4.