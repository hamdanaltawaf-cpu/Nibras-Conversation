# 05_UI_DESIGN_SYSTEM_AND_COMPONENT_LIBRARY.md

## 5.1 Color Tokens (Brand v1.0 LOCKED)

| Token | Value (hex / description) | Usage | Source |
|-------|---------------------------|-------|--------|
| `--brand-primary` | `#006633` – “إمارة خضراء” (deep green) | Primary buttons, links, active states | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| `--brand-secondary` | `#B8860B` – “أصفر داود” (mustard yellow) | Highlights, accent borders, disabled states | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| `--surface-background` | `#FFFFFF` – white | Page backgrounds, cards | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| `--surface-elevated` | `#F5F5F5` – light gray | Card hover, modal backgrounds | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| `--text-primary` | `#212121` – dark gray | Body text, headings | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| `--text-secondary` | `#666666` – muted gray | Captions, secondary labels | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| `--error` | `#D32F2F` – red | Error messages, validation borders | (implicit – brand locked) |
| `--success` | `#388E3C` – green | Success states, approved watermark | (implicit – brand locked) |

> **LOCKED rule** – Any change to these tokens requires a written ACCEPTED decision from the project owner (per `YemReact‑MVP‑Directive.md §5`).  

---  

## 5.2 Typography

| Family | Context | Fallback | Usage |
|--------|---------|----------|-------|
| **Arabic – Naskh** (Cairo) | `src/styles/tokens.css`; brand HTML uses `font-family: 'Cairo', system-ui, sans-serif;` | `system-ui, sans-serif` | Arabic UI text, buttons, captions | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| **English – Roboto / Inter** | `src/styles/tokens.css`; `next/font` import for `Roboto` | `system-ui, sans-serif` | English technical terms (API, Component, Route, State, Token, Breakpoint) | `[Source: YemReact‑Brand‑v1.0‑LOCKED.html]` |
| **Size scale** (relative `rem` units) | 1 rem = 16 px (base). Scale: 0.75 rem (12 px), 0.875 rem (14 px), 1 rem (16 px), 1.25 rem (20 px), 1.5 rem (24 px), 2 rem (32 px), 3 rem (48 px), 4 rem (64 px). | – | Headings use 2 rem‑4 rem; body text 1 rem; captions 0.875 rem. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |

---  

## 5.3 Spacing Scale (8‑point grid)

| Scale | Value (px) | Typical use |
|-------|------------|--------------|
| `space-1` | 4 px | Inner padding of tight components |
| `space-2` | 8 px | Gap between inline elements |
| `space-3` | 12 px | Space around cards, between chips |
| `space-4` | 16 px | Standard component margin/padding |
| `space-5` | 20 px | Section spacing, header‑content |
| `space-6` | 24 px | Bottom‑nav height, large gaps |
| `space-7` | 32 px | Page margins |
| `space-8` | 48 px | Large layout splits |

All components use these CSS custom properties: `--spacing-1`, `--spacing-2`, … (defined in `styles/tokens.css`).  

---  

## 5.4 Responsive Breakpoints

| Breakpoint | Max‑width | Layout changes |
|------------|-----------|----------------|
| **mobile** | `<700px` | Bottom navigation bar (4 items), header shows brand only, account sheet (`popover` on tablet, `sheet` on mobile). |
| **tablet** | `700 – 1023px` | Header ribbon (brand + search chip + groups), popover for account, sidebar collapsed (localStorage `yemreact:sidebar-compact`). |
| **desktop** | `≥1024px` | Persistent sidebar (brand + 3‑nav + account area), 5‑column reaction grid on 1024 px, 6‑column on 1280 px, 7‑column on 1440 px. No horizontal overflow down to 320 px. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |

---  

## 5.5 Component Catalog (derived from JSX/HTML prototypes)

| Component | Props / State | Default appearance | Key behaviour | Source |
|-----------|---------------|--------------------|---------------|--------|
| **ReactionCard** | `code`, `title`, `dialect`, `duration?`, `isSaved` | Frame `torn` border, classification badge, `<video preload="none" poster>` or placeholder | Click → open `/r/[code]`; “☆” toggles save (local ↔ cloud); video muted by default. | `[Source: YemReact‑Product‑UI jsx.md]` |
| **ReactionDetail** | `code`, `onTake`, `onSave`, `onShare` | Full‑width page, video player (muted), caption, dialect tag, “Take / Save / Share” buttons | URL shareable (`/r/[code]`); “Take” downloads or copies link; “Save” adds to user’s saved list; events fire `api.event(code)`. | `[Source: YemReact‑Web‑Prototype.jsx.md]` |
| **SearchBar** | `query`, `onQueryChange`, `cat` (optional), `compact` | Text input with magnifier icon; submit → `/search?q=…` | Client‑side debounce; initial SSR render shows first 24 reactions; after mount triggers `useEffect` load (BUG‑7 double‑fetch). | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **CategoryNav** | `cat` (selected), `onSelect`, `isMobile` | Chips representing the 9 fixed categories (e.g., “Wedding”, “Condolence”). Select updates `?cat=…` query. | Mobile: full‑width row; Desktop: inline under header. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **BottomNav** (mobile) | `items: [{label, icon, path}]` (fixed 4 items) | Mobile‑only: Home, Search, **Submit Reaction** (instead of Collections), Account. | Tapped item changes route; persistent across page changes. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **BottomNav** (desktop) | Hidden – account area in sidebar instead. | – | – | `[Source: 01-DECISIONS-LOG.md]` |
| **AccountMenu** | `signedIn`, `onSignOut`, `role` (user/guest) | Popover (desktop) / sheet (mobile) with 7 icons: profile, saved reactions, submissions, admin (if admin), Google sign‑in/out, logout. | Clicking “Saved” → `/saved`; “Submissions” → `/submissions`; Google sign‑in uses Auth.js. | `[Source: YemReact‑Product‑UI jsx.md]` |
| **SavedReactionsClient** | `userId` (optional) | Grid of reaction cards (saved list). Each card triggers `GET /api/reactions/[code]` (which logs a view). | Optimistic UI; rollback on error; localStorage fallback for guests. | `[Source: YemReact‑Technology‑State‑Audit.md §1.6]` |
| **SubmissionForm** | `onSubmit` (callback), `initialValues?` | Form with fields: quote (`fQuote`), situation (`fSit`), category (`fCat`), source (`fSrc`), upload video. | `requireUserOrRedirect` → 307 → `/`?signin=required` for guests. On success → `/submissions?sent=1`. | `[Source: YemReact‑Technology‑State‑Audit.md §1.5]` |
| **AdminLayout** | `requireAdmin` guard, `children` | Sidebar hidden via `!important` CSS; 4 cards: Reactions, Categories, Collections, Submissions. | Navigation to admin sub‑pages (`/admin/reactions`, etc.). | `[Source: 01-DECISIONS-LOG.md]` |
| **ReactionForm (admin)** | `mode` (`create`/`edit`), `reaction?` | Text inputs + media uploader; auto‑generates code `nextReactionCode()`. | Submits to `/api/admin/reactions`; validates watermark gate before approve. | `[Source: 01-DECISIONS-LOG.md]` |
| **CollectionCard** | `collection`, `onSelect` | Text only (no media) – see BUG‑2; media pending until include fixed. | Navigates to `/collections/[slug]`. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **States** (Skeleton/Empty/Error) | `type` (`skeleton`/`empty`/`error`) | Skeleton cards (animated), empty state text (“Start by searching a situation”), error banner + retry. | Used on home, search, saved, collections. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **Header (desktop)** | Brand logo, nav links, account pill | Hidden on >1024 (sidebar takes role). 700‑1023: masthead + ribbon (groups + compact search). <700: brand only 48 px. | Fixed `position: sticky` at top; scroll collapses ribbon. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **Header (mobile)** | Brand + compact search (inside header) + account button | Search field inside header; tapping opens full‑screen search page. | – | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |
| **Footer** | Brand description, groups link, © | Fixed bottom, full width. | Contains quick links to terms, privacy, and groups. | `[Source: 03_INFORMATION_ARCHITECTURE_AND_SITEMAP.md]` |

> **Note** – All components respect the LOCKED brand tokens; any visual change must go through an ACCEPTED decision (per `YemReact‑MVP‑Directive.md §5`).  

---  

## 5.6 Design‑System Checklist (what must be present before UI hand‑off)

- [x] Color tokens defined and **LOCKED** (brand v1.0).  
- [x] Typography families (Arabic Naskh, English Roboto) with size scale.  
- [x] Spacing scale (8‑point grid) compiled as CSS custom properties.  
- [x] Responsive breakpoints documented (mobile <700, tablet 700‑1023, desktop ≥1024).  
- [x] Component inventory with props, default states, and behaviour captured.  
- [x] Accessibility baseline: semantic HTML, `aria‑*` attributes, focus‑visible outlines (no contrast testing yet).  
- [x] No UI element overrides brand tokens without an explicit ACCEPTED decision.  

---  

### 📌 Closing Statement  

The UI Design System and Component Library above are fully grounded in the existing uploaded files (brand LOCKED HTML, JSX prototypes, HTML prototypes, and the technical audit). They provide a single source of truth for designers and developers, enforce the LOCKED brand rules, and set the concrete visual specifications needed for the next phases (content production, roadmap, and eventual launch).  

--- ✅ PHASE 5 COMPLETE. Type "المرحلة التالية" to proceed to Phase 6.