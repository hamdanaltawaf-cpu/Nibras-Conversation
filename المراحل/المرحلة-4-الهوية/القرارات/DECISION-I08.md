## DECISION-I08 — Light/Dark + Soft Depth — ACCEPTED — Stage 4 — PD-I08

**Date:** 2026-09-25
**Stage:** Stage 4 — Experience & Identity — Identity Re-Foundation
**Decided by:** حمدان (Founder)
**Status:** ACCEPTED — CLOSED
**Topic:** PD-I08 — Light / Dark System

── القرار ──

**Color Tokens (من PD-I08 الأصلي):**

| الوضع | bg | surface | ink |
|---|---|---|---|
| **Light** | `#FAFAF8` | `#FFFFFF` | `#121214` |
| **Dark** | `#18140F` | `#221C16` | `#F3ECE2` |

- **Dark دافئ** — يحفظ شخصية **Qishr** — ليس أسود نقيًا ولا أزرق غامقًا
- Base دافئ محايد في النهاري (`#FAFAF8` / `#FFFFFF`) مع حبر `#121214`

**Soft Depth (مُضاف في R2):**

- `shadow-sm: 0 1px 3px rgba(0,0,0,.04)`
- `shadow-md: 0 2px 8px rgba(0,0,0,.06)`
- `shadow-lg: 0 4px 16px rgba(0,0,0,.08)`
- `shadow-float: 0 8px 24px rgba(0,0,0,.12)`
- **Dark: .30-.50** — معايرة ضرورية في الوضع الليلي
- **Border:** `rgba(0,0,0,.04)` نهاري / `rgba(255,255,255,.06)` ليلي
- **Active:** ring + 4% surface + shadow-lg
- **Icon Containers:** دائرة 36px بخلفية `rgba(0,0,0,.03)`
- **Nested Depth:** كل طبقة بظلها

**السلوك:**

- **Auto = افتراضي** — `prefers-color-scheme`
- **200ms transitions**

── 3 تصحيحات مؤجلة — تُنفَّذ في Stage 7 ──

1. **Duration في البطاقة:** `left → right` — الصحيح: **أعلى يمين الوسائط**
2. **Duration في صفحة التفاصيل:** **يُحذف** — المشغل يعرضها
3. **Settings Modal:** حذف **«الإشعارات»** — خارج النطاق

── توضيح Related Count ──

- **P-11 يبقى كما هو** — **لا تعديل**
- Related: **10 أولية** + **Load More حتى 50 max** + **ليس Infinite Feed**
- عبارة «10 رياكشن» = **10 أولية** — ليست 10 ثابتة

── الأثر ──

- **P-42 NEW:** Light/Dark System + Soft Depth
- **P-11 CONFIRMED:** 10 أولية + Load More حتى 50 — لا تعديل
- **3 تصحيحات مؤجلة إلى Stage 7** — مسجَّلة في سجل المؤجلات
- 74→75 facts — PD-I08 CLOSED
- يفتح: PD-I09 Motion + Settings Modal Topic جديد

**Stage:** Stage 4 — PD-I08 — CLOSED — DECISION-I08 ACCEPTED 2026-09-25 — Light/Dark + Soft Depth — NEXT PD-I09 + Settings Modal

---

## Topic 18 — PD-I08 — CLOSED — DECISION-I08 ACCEPTED — Stage 4 — Light/Dark + Soft Depth

- Color Tokens: Light `#FAFAF8` / `#FFFFFF` / `#121214` — Dark `#18140F` / `#221C16` / `#F3ECE2` — Dark دافئ شخصية Qishr
- Soft Depth R2: sm .04 + md .06 + lg .08 + float .12 + Dark .30-.50 معايرة + Border .04/.06 + Active ring+4% surface+shadow-lg + Icon 36px دائرة .03 + Nested Depth كل طبقة بظلها
- Auto افتراضي prefers-color-scheme + 200ms transitions
- 3 تصحيحات مؤجلة Stage 7: Duration بطاقة left→right + Duration تفاصيل يُحذف + Settings Modal حذف الإشعارات
- Related Count: P-11 CONFIRMED — 10 أولية + Load More حتى 50 — ليس Infinite Feed — «10 رياكشن» = 10 أولية لا ثابتة — لا تعديل على P-11
- Impact: P-42 NEW — P-11 CONFIRMED — 74→75 facts — PD-I08 CLOSED
- NEXT: PD-I09 Motion + Settings Modal Topic جديد — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB

---
