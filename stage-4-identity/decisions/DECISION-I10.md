## DECISION-I10 — UI Visual Language (Studio Seal) — ACCEPTED — Stage 4 — PD-I10 — LAST TOPIC

**Date:** 2026-09-30
**Stage:** Stage 4 — Experience & Identity — Identity Re-Foundation — **LAST TOPIC**
**Decided by:** حمدان (Founder)
**Status:** ACCEPTED — CLOSED
**Topic:** PD-I10 — UI Visual Language

── الاتجاه المعتمد ──

**Direction D — Hybrid «Studio Seal»**

نظام هادئ كـLinear + دفء Qishr في الأسطح والظلال + نظام ختم صارم: حدود رقيقة + ظل ناعم + Seal Motion + الشخصية اليمنية في **المحتوى** لا في الواجهة

── المكونات المعتمدة ──

**1. Foundation:** Spacing `4/8/12/16/24/32/48/64` · Breakpoints `640 / 1024 / 1440` · Container `1120px` · Masonry `2 / 3 / 4 / 5` أعمدة

**2. Buttons:** 5 أنواع — Primary · Secondary · Ghost · Icon · Destructive · 3 أحجام `S=40 · M=44 · L=48` · Radius `10px` · 5 حالات — Default · Hover · Active · Disabled · Loading

**3. Inputs:** Text · Search · Select · Textarea · Height `44px` · Radius `10px` · Border `1px` + `shadow-sm` · Focus ring `2px Accent`

**4. Cards:** Reaction `radius 14px` · Collection `Rail + Square` · Mini `70×70`

**5. Modals:** Desktop = Center Modal · Mobile = Bottom Sheet `radius 22px top`

**6. Menus:** Dropdown (نسخ الرابط + إبلاغ) · Account

**7. States:** Empty **للصفحات فقط** (Lucide icon + عنوان + إجراء) · Loading = Skeleton + Spinner 16px · Error = نبرة فصحى هادئة · **Toast: Success + Error** (ليس Success فقط)

**8. Icons:** **Lucide** · `1.5px` · `16/20/24px` · Bottom Nav: `layout-grid` · `layers` · `plus` · `bookmark` · `circle-user`

**9. Navigation:**
- Header Desktop: Mark + Logo + Nav + **Search Bar كامل** + Account
- Header Mobile: Mark + **Search Bar كامل** (بلا Avatar)
- Header Mobile: يختفي عند scroll down / يظهر عند scroll up
- **Bottom Nav: 5 tabs** — المكتبة · المجموعات · **+** · المحفوظات · الحساب

**10. Account Menu — 3 حالات:**
- **الزائر:** Google Login + الإعدادات + المساعدة
- **المستخدم:** Identity + الإعدادات + المساعدة + Logout
- **الأدمن:** نفس المستخدم + **الاستوديو** (مجموعة منفصلة)
- Desktop = Popover · Mobile = Bottom Sheet
- ❌ لا «المحفوظات» (مكررة) · ❌ لا «مساهماتي» (ميتة قبل الإطلاق)

**11. زر (+):** محايد قبل الإطلاق + 🔒 · Bottom Sheet «الرفع يُفتح قريبًا» · Accent بعد الإطلاق · Desktop: زر «+ رفع» في Header **بعد الإطلاق فقط**

**12. Search Bar:** Desktop حقل `44px` بعرض `420-480px` · Mobile حقل كامل في Header · Placeholder «ابحث عن رياكشن أو موقف...» · **بلا فلاتر في v1**

**13. Guest Save:** حفظ محلي `localStorage` للزائر · دمج عند الدخول · **Seal Motion يعمل فورًا**

**14. Mobile Video Preview:** لا معاينة تلقائية · Tap يفتح التفاصيل

**15. Report Flow:** Sheet بأسباب radio — **5 أسباب**

── 7 تصحيحات مؤجَّلة إلى Stage 7 ──

1. Duration في البطاقة: `left → right`
2. Duration في التفاصيل: **يُحذف**
3. Bottom Nav Icons: **Lucide** (لا Emojis)
4. خط **Inter**: تحميل في الـHTML
5. Aspect Ratio في التفاصيل: `aspect-ratio:${r.ratio}`
6. حذف متغير `tabs` الميت
7. **Qussasa قابل للنقر في Header**

── قرارات مؤجَّلة ──

1. **Search Route** (صفحة منفصلة vs `?q=`) → **Stage 5** — IA & Navigation
2. **Scroll Restoration** (استعادة موضع التمرير) → **محسّن مستقبلي** — يحتاج session storage

── ما تم رفضه ──

- Avatar في Header Mobile
- «المحفوظات» و«مساهماتي» في Account Menu
- Toast للـ«قريبًا» — **Bottom Sheet بدلًا**
- **Emojis في UI**
- Infinite Scroll
- Qussasa في Empty States
- **Linear** في الـEmpty States (النبرة: فصحى هادئة)

── الأثر ──

- **P-44 NEW:** UI Visual Language (Studio Seal)
- **P-45 NEW:** Account Menu (3 حالات)
- **P-46 NEW:** Guest Save (local + sync)
- **76 → 79 facts**
- **PD-I10 CLOSED**
- **Stage 4 — Identity Re-Foundation مكتمل 100%**

**Stage:** Stage 4 — PD-I10 — CLOSED — DECISION-I10 ACCEPTED 2026-09-30 — UI Visual Language Studio Seal — **Stage 4 CLOSED 100%** — NEXT Stage 5

---

## Topic 20 — PD-I10 — CLOSED — DECISION-I10 ACCEPTED — Stage 4 — UI Visual Language (Studio Seal)

- الاتجاه: **Direction D — Hybrid «Studio Seal»** — نظام هادئ كـLinear + دفء Qishr + نظام ختم صارم + الشخصية في المحتوى لا الواجهة
- Foundation: Spacing 4/8/12/16/24/32/48/64 + Breakpoints 640/1024/1440 + Container 1120px + Masonry 2/3/4/5
- Buttons 5 أنواع × 3 أحجام (40/44/48) × Radius 10px × 5 حالات — Inputs 44px + Radius 10 + Border 1px + shadow-sm + Focus ring 2px Accent
- Cards: Reaction 14px + Collection Rail/Square + Mini 70×70 — Modals: Desktop Center + Mobile Bottom Sheet 22px
- States: Empty للصفحات فقط Lucide + عنوان + إجراء — Loading Skeleton + Spinner 16px — Error فصحى هادئة — Toast Success + Error
- Icons: Lucide 1.5px 16/20/24 — Bottom Nav 5 tabs: layout-grid/layers/plus/bookmark/circle-user
- Navigation: Header Desktop Mark+Logo+Nav+Search+Account — Mobile Mark+Search بلا Avatar + يختفي↓/يظهر↑
- Account Menu 3 حالات: زائر (Google+الإعدادات+المساعدة) · مستخدم (Identity+الإعدادات+المساعدة+Logout) · أدمن (+الاستوديو مجموعة منفصلة) — Popover ديسكتوب / Sheet جوال
- زر (+): محايد+🔒 قبل الإطلاق + Sheet «قريبًا» + Accent بعد الإطلاق + «+ رفع» في Header بعد الإطلاق فقط
- Search Bar: 44px عرض 420-480px ديسكتوب + حقل كامل جوال + Placeholder «ابحث عن رياكشن أو موقف...» + بلا فلاتر v1
- Guest Save: localStorage + دمج عند الدخول + Seal Motion فورًا — Mobile: لا معاينة تلقائية + Tap يفتح التفاصيل — Report Flow: Sheet radio 5 أسباب
- 7 تصحيحات مؤجلة Stage 7 + قراران مؤجلان (Search Route → Stage 5 · Scroll Restoration → مستقبلي)
- Rejected: Avatar جوال + المحفوظات/مساهماتي في Account + Toast للقريبًا + Emojis في UI + Infinite Scroll + Qussasa في Empty States + Linear نبرة Empty
- Impact: P-44 + P-45 + P-46 NEW — 76→79 facts — PD-I10 CLOSED — **Stage 4 CLOSED 100%**
- NEXT: **Stage 5 — IA & Navigation** — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB

---
