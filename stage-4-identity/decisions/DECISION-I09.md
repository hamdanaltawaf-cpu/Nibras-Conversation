## DECISION-I09 — Motion Language — ACCEPTED — Stage 4 — PD-I09

**Date:** 2026-09-26
**Stage:** Stage 4 — Experience & Identity — Identity Re-Foundation
**Decided by:** حمدان (Founder)
**Status:** ACCEPTED — CLOSED
**Topic:** PD-I09 — Motion Language

── القرار ──

**1. الفلسفة: Hybrid**

- **Subtle في UI** — هادئ — Linear / Vercel-style
- **Anchor مميز** — Seal Motion

**2. Motion Tokens — Durations:**

| الاسم | المدة | الاستخدام |
|---|---|---|
| Micro | 120ms | hover / focus / click |
| Small | 180ms | بطاقة، chip |
| Medium | 240ms | modal، menu |
| Large | 320ms | **Seal Motion — استثناء** |

**Easings:**

- **Standard** — `cubic-bezier(.4,0,.2,1)`
- **Decelerate** — `cubic-bezier(0,0,.2,1)` — دخول
- **Accelerate** — `cubic-bezier(.4,0,1,1)` — خروج
- **Spring** — `cubic-bezier(.34,1.56,.64,1)` — **Seal فقط**

**3. Seal Motion (Anchor):**

- **6 مراحل — ~1.7 ثانية**
- `♡ → Mark → spin(Spring) → ✓ → ♡`
- **Spring محجوز له** — لا يُستخدم في أي مكان آخر

**4. Page Transitions:** ❌ **None** — Pinterest-style — أداء أولًا

**5. Scroll Behaviors:**

- Header Desktop: **ثابت**
- Header Mobile: **يختفي عند scroll down — يظهر عند scroll up** — 250ms
- Bottom Nav: **ثابت دائمًا**
- **لا Infinite Scroll** — P-03

**6. Loading States:**

- **Skeleton (shimmer)** — للبطاقات
- **Spinner 16px** — للأزرار
- **Fade In 150ms** — للصور/الفيديو
- **لا Progress Bar**

**7. Reduced Motion:**

- **يُلغي:** Rotation · translateY · Page transitions · Skeleton shimmer
- **يُبقي:** التحول اللوني — وظيفي
- **التنفيذ:** `prefers-reduced-motion` + خيار Settings

── المرفوضات ──

- حركة **> 320ms** — باستثناء Seal
- **Spring في أماكن أخرى**
- **Page transitions** — slide, shared element
- **Progress bar**
- **Scroll animations معقدة** — parallax
- **Bounce / Shake / Wobble**

── الأثر ──

- **P-43 NEW:** Motion Language
- 75→76 facts
- **PD-I09 CLOSED**
- يفتح: **PD-I10 (UI Language)** — آخر Topic

**Stage:** Stage 4 — PD-I09 — CLOSED — DECISION-I09 ACCEPTED 2026-09-26 — Motion Language — NEXT PD-I10

---

## Topic 19 — PD-I09 — CLOSED — DECISION-I09 ACCEPTED — Stage 4 — Motion Language

- الفلسفة Hybrid — Subtle في UI Linear/Vercel-style + Anchor مميز Seal Motion
- Durations: Micro 120ms + Small 180ms + Medium 240ms + Large 320ms Seal فقط
- Easings: Standard `.4,0,.2,1` + Decelerate `0,0,.2,1` دخول + Accelerate `.4,0,1,1` خروج + Spring `.34,1.56,.64,1` Seal فقط
- Seal Motion: 6 مراحل ~1.7s — ♡ → Mark → spin(Spring) → ✓ → ♡ — Spring محجوز له
- Page Transitions ❌ None — Pinterest-style أداء أولًا
- Scroll: Header Desktop ثابت + Mobile يختفي down/يظهر up 250ms + Bottom Nav ثابت دائمًا + لا Infinite Scroll P-03
- Loading: Skeleton shimmer للبطاقات + Spinner 16px للأزرار + Fade In 150ms للصور/الفيديو + لا Progress Bar
- Reduced Motion: يُلغي Rotation/translateY/Page transitions/shimmer — يُبقي التحول اللوني — prefers-reduced-motion + خيار Settings
- Rejected: حركة >320ms + Spring elsewhere + Page transitions + Progress bar + Parallax + Bounce/Shake/Wobble
- Impact: P-43 NEW — 75→76 facts — PD-I09 CLOSED — يفتح PD-I10 UI Language آخر Topic
- NEXT: PD-I10 UI Language — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB

---
