## DECISION-I03 — Multi-Accent Color System — ACCEPTED — Stage 4 — PD-I03

- **Status:** ACCEPTED — CLOSED — PD-I03 CLOSED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-23 — Stage 4 — Identity Re-Foundation — PD-I03 Color System
- **Topic:** نظام ألوان متعدد + إعدادات المستخدم

**Context — رحلة الاختيار:**

1. DECISION-I01 Brand Direction الختم Direction C ACCEPTED 2026-09-21 — Modern Product First — 3 Anchors — Modern UI Pinterest-like
2. DECISION-I02 Qussasa Mark v1.0 Adopted As-Is ACCEPTED 2026-09-23 — مربع بزاوية مشطوفة + مثلث سالب — 16-512px — اجتاز 8 سيناريوهات
3. Claude أنتج 4 أنظمة ألوان في H1-R2/H1-R3: النظام 1 كهرماني فقط + النظام 2 نيلي + النظام 3 متعدد Accents + النظام 4 رمادي فقط — مع 3 Accents ثابتة مقترحة
4. Prototype موقع تجريبي يُظهر: Home Pinterest-like Masonry + Settings Modal (3 accents + theme + motion) + Qussasa Mark في Header + Captions بلهجة يمنية + Flat Saves Bookmark + Duration badge — المرجع البصري
5. حمدان اختار: نظام ألوان متعدد + إعدادات المستخدم — Multi-Accent Color System

**Previous → New:**

- **Previous:**
  - B-05 Brand colors foundation: Ink, Qishr Amber, Paper, Coral, Warm Grey etc. — Qishr from Yemeni coffee, not flag — CONFIRMED as foundation intent — S10 explicit list + rationale avoiding cliché — S09 tokens.css matches LOCKED — High for intent, Medium for exact hex (conflict S05 #006633 vs S10 #121214)
  - B-06 9 category colors: ضحك #F4C430, صدمة #7C5CFF, غضب #C81E3A, استغراب #2CB6C4, إحراج/صمت #F17FB2, موافقة #4CAF6D, رفض #6E8296, سخرية #D98E04, حماس #E8712E — انبهار merged into استغراب — CONFIRMED — S10 explicit list — محفوظة للدراسة Stage4 per DECISION-014 — الآن لا تُستخدم كفلتر — Categories Removed — تبقى للدراسة Visual Accents/Mood Tags
  - B-01 Brand v1.0 LOCKED — Ink #121214 + Qishr Amber + Paper — S10 — 8 scenarios test
  - P-08 Presentation Pinterest-like Masonry Grid visual only — P-35 Brand Direction الختم Modern UI Foundation — P-36 Qussasa Mark v1.0 Header
  - PD-I03 Color System كان OPEN — HISTORY+EVIDENCE done — يحتاج قرار
  - Settings Modal لم يكن موجود — الآن موجود — UI "على ذوقك" — عنوان أنيق بلهجة يمنية — زر استعادة الإعدادات

- **New:**

  **Multi-Accent Color System — ACCEPTED**

  ```
  Palette الأساسي:

  1. Base: Ink / Paper / Grey (Monochrome)
     - Ink: الأساس الداكن — Qussasa Mark — Header — Text
     - Paper: الخلفية الفاتحة — Masonry background — Cards
     - Grey: المحايد — Borders — Secondary text —  Warm Grey

  2. Accent الافتراضي: قهري/كهرماني (Qussasa-derived)
     - مستمد من Qussasa Mark — Qishr Amber — Brand v1.0 LOCKED
     - يمثل الدفء اليمني بدون ألوان علم مباشرة
     - افتراضي — Default accent

  3. Success / Warning / Error (قياسية)
     - ألوان نظام قياسية — لا يمنية — وظيفية
     - Success: حفظ/متابعة
     - Warning: تنبيه
     - Error: خطأ/حذف

  Accents اختيارية (من الإعدادات — Settings Modal):

  - كهرماني (Amber) — افتراضي — Default
    - دافئ — Qussasa-derived — Qishr — يمني بدون علم
    - يمثل القهوة اليمنية — Qishr — Brand v1.0

  - بنفسجي (Purple)
    - حديث — مميز — يمثل الإبداع
    - بديل للكهرماني — يعطي شخصية مختلفة

  - تيل (Teal)
    - بارد — هادئ — يمثل التوازن
    - بديل — يعطي هدوء

  Theme:

  - نهاري (Day) — افتراضي — Default
    - Paper فاتح — Ink داكن — Qussasa Mark واضح

  - ليلي (Night)
    - Ink داكن خلفية — Paper فاتح نص — Qussasa Mark مضيء
    - يحترم تفضيل المستخدم الليلي

  - تلقائي (Auto — يتبع النظام)
    - يتبع prefers-color-scheme — System preference
    - تلقائي — لا يحتاج تدخل

  Reduce Motion:

  - خيار (On/Off) — Settings Modal
    - On: تقليل الحركة — يحترم prefers-reduced-motion
    - Off: حركة كاملة — Motion Signature 150-200ms ختم/قلب
    - تفاصيل الحركة → PD-I09 Motion

  Settings Modal:

  - موجود — UI: "على ذوقك" — عنوان أنيق بلهجة يمنية
  - يحتوي:
    - 3 Accents: كهرماني (افتراضي) + بنفسجي + تيل
    - Theme: نهاري (افتراضي) + ليلي + تلقائي
    - Reduce Motion: On/Off
    - زر "استعادة الإعدادات" — Reset to defaults
  - Prototype يُظهر Modal — مرجع بصري — ليس نهائي
  - Topic جديد — Settings Modal — يُفتح لاحقًا — Stage 4/5

  المرجع البصري — Prototype موقع تجريبي:

  - Home: Pinterest-like Masonry — P-08 — Masonry Grid visual only
  - Settings Modal: 3 accents + theme + motion — "على ذوقك" — استعادة الإعدادات
  - Qussasa Mark في Header — B-04 ACCEPTED — 16-512px
  - Captions بلهجة يمنية — P-35 Content Art Direction — قصيرة بلهجة يمنية
  - Flat Saves (Bookmark) — P-07 Flat Saves — Bookmark icon
  - Duration badge — P-27 Duration 2-60s — badge على البطاقة
  - البحث سيُضاف لاحقًا — OPEN — Search
  - "الاستوديو" = اسم مؤقت لصفحة الأدمن — Admin page temporary name
  - الموقع المُعروض = نموذج تجريبي، ليس نهائيًا — Prototype not final
  - التفاصيل النهائية تأتي مع بناء الموقع الفعلي — Final details with actual build

  ملاحظة:
  - الموقع المُعروض = نموذج تجريبي، ليس نهائيًا
  - "الاستوديو" = اسم مؤقت لصفحة الأدمن
  - البحث سيُضاف لاحقًا
  - التفاصيل النهائية تأتي مع بناء الموقع الفعلي
  ```

**Reason:**

1) يحل PD-I03 Color System — Stage 4 Identity Re-Foundation — رحلة: Claude 4 أنظمة ألوان — Prototype تجريبي يُظهر Home+Masonry+Settings Modal+Qussasa Mark+Captions+Flat Saves+Duration badge — حمدان اختار Multi-Accent — قرار مؤسس
2) يتوافق مع DECISION-I01 Brand Direction الختم — Modern Product First, Yemeni Character Second — Modern UI Foundation Pinterest-like Masonry + Search فوري + Spacing Linear + نظام واحد صارم + Account flows قياسية + لا تراث في UI — Multi-Accent يعطي شخصية بدون تراث — حديث 100%
3) يتوافق مع DECISION-I02 Qussasa Mark v1.0 Adopted As-Is — Qussasa Mark في Header — Accent الافتراضي قهري/كهرماني Qussasa-derived — مستمد من Qussasa — Qishr Amber — Brand v1.0 LOCKED — B-05 + B-04 — Ink/Paper/Grey Monochrome + Qussasa Amber
4) يعطي تحكم للمستخدم — Settings Modal "على ذوقك" — 3 Accents اختيارية + Theme نهاري/ليلي/تلقائي + Reduce Motion On/Off + زر استعادة الإعدادات — يحترم تفضيلات — P-15 Audience أي شخص في موقف — Device جوال متوسط 30% قوي 10% ضعيف — Theme ليلي/تلقائي يحسن تجربة — Reduce Motion يحترم Accessibility
5) يرفض الأنظمة المحدودة — النظام 1 كهرماني فقط محدود — النظام 2 نيلي يفقد الدفء اليمني — النظام 4 رمادي فقط بلا شخصية — 3 Accents ثابتة نستخدم متعدد — Multi-Accent مرن — Base Monochrome + Accent افتراضي Qussasa + Accents اختيارية Amber/Purple/Teal — يعطي دفء + شخصية + مرونة
6) يفتح Stage 4 — PD-I04 Typography + PD-I05 Watermark Qussasa-based + PD-I06 Reaction Card + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد — تفاصيل لاحقة — هذا القرار يحدد Palette العامة لا التفاصيل الدقيقة hex
7) يتوافق مع Stage 3 CLOSED — P-12 Value منتقاة + قابلة للبحث + جاهزة + P-13 300-500 + P-20 Rubric 6 + P-25 Pipeline + P-27 Duration 2-60s badge + P-29 Aspect أي مقاس + P-31 Categories Removed + P-32 Collections Primary — لا تعارض — Color System يبني فوق Content & Editorial System

**Alternative rejected:**

- النظام 1 (الكهرماني فقط) — محدود — REJECTED per DECISION-I03 — كهرماني فقط محدود — لا يعطي خيارات للمستخدم — يفقد مرونة
- النظام 2 (النيلي) — يفقد الدفء — REJECTED per DECISION-I03 — نيلي يفقد الدفء اليمني — Qishr Amber دافئ يمني — نيلي بارد لا يمثل
- النظام 4 (رمادي فقط) — بلا شخصية — REJECTED per DECISION-I03 — رمادي فقط بلا شخصية — Monochrome Base موجود لكن يحتاج Accent — رمادي فقط ممل
- 3 Accents ثابتة — نستخدم متعدد — REJECTED per DECISION-I03 — 3 Accents ثابتة = لا اختيار للمستخدم — Multi-Accent = Base + Default Qussasa + Optional Amber/Purple/Teal + Theme + Motion + Settings Modal "على ذوقك" — مرن

**Impact:**

- PD-I03 CLOSED — Stage 4 Identity Re-Foundation — PD-I03 Color System — ACCEPTED 2026-09-23 — 69 → 70 facts
- P-37 NEW: Multi-Accent Color System — Base Ink/Paper/Grey Monochrome + Accent افتراضي قهري/كهرماني Qussasa-derived + Success/Warning/Error قياسية + Accents اختيارية Amber افتراضي + Purple + Teal + Theme Day افتراضي + Night + Auto + Reduce Motion On/Off + Settings Modal "على ذوقك" + زر استعادة الإعدادات — Prototype مرجع بصري Home Masonry + Settings Modal + Qussasa Mark Header + Captions لهجة يمنية + Flat Saves Bookmark + Duration badge — ملاحظة موقع تجريبي ليس نهائي — "الاستوديو" اسم مؤقت أدمن — البحث لاحقًا — تفاصيل نهائية مع بناء فعلي
- B-05 UPDATED: Brand colors foundation — من CONFIRMED as foundation intent → ACCEPTED — DECISION-I03 — Base Ink/Paper/Grey Monochrome + Accent Qussasa-derived Qishr Amber + Success/Warning/Error قياسية + Optional Amber/Purple/Teal + Theme Day/Night/Auto + Reduce Motion — Settings Modal "على ذوقك" — B-04 Qussasa Mark Header — B-09 Brand Direction الختم
- B-06 9 category colors: يبقى محفوظ للدراسة — لا يُستخدم كفلتر — Categories Removed per DECISION-014 — يبقى للدراسة Visual Accents/Mood Tags — لا علاقة مباشرة بـ Multi-Accent — لكن Purple/Teal/Amber قد تُستلهم منه مستقبلًا — للدراسة Stage4
- Canonical Facts: 69 → 70 (9 brand + 37 product? Actually 9 brand + 37 product? Let's recalc: 9 brand + 36 product =45+24=69 → 9+37=46+24=70) — B-05 UPDATED — P-37 NEW
- B-01 to B-09 — Brand v1.0 LOCKED — الآن B-04 Qussasa Mark v1.0 ACCEPTED — B-05 Multi-Accent ACCEPTED — B-07 Watermark Qussasa-based — B-09 Brand Direction الختم — كلها متوافقة — Direction C الختم + Qussasa Mark + Multi-Accent Qussasa-derived
- P-35 Brand Direction الختم + P-36 Qussasa Mark v1.0 + P-37 Multi-Accent Color System — متوافق — Brand Direction + Mark + Colors — Direction C + Qussasa + Qussasa-derived Amber
- P-07 Flat Saves Bookmark + P-27 Duration badge — متوافق — Prototype يُظهر Flat Saves + Duration badge — P-07 + P-27
- P-08 Pinterest-like Masonry — متوافق — Prototype Home Masonry — P-08
- P-15 Audience أي شخص في موقف — متوافق — Settings Modal "على ذوقك" + Theme Day/Night/Auto + Reduce Motion — يحترم تفضيلات
- Stage 3 CLOSED — 66 facts — لا تعارض مع Stage 4 PD-I03 — Multi-Accent Color System يبني فوق Content & Editorial System — لا يلغيه
- Stage 4 — Experience & Identity — الآن OPEN — PD-I01 CLOSED Brand Direction + PD-I02 CLOSED Qussasa Mark + PD-I03 CLOSED Multi-Accent — يفتح PD-I04 Typography + PD-I05 Watermark Qussasa-based + PD-I06 Reaction Card + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد
- YEMREACT-HISTORICAL-NOT-CURRENT.md: B-05 Brand colors foundation → UPDATED ACCEPTED — DECISION-I03 Multi-Accent — B-06 9 category colors → يبقى محفوظ للدراسة — لا يُستخدم كفلتر — PD-I03 CLOSED
- YEMREACT-REFORMATION-MASTER-PLAN.md + PROJECT_CONTEXT_AND_DECISIONS.md + Roadmap — يحتاج تحديث — PD-I03 مغلق — Multi-Accent Color System — يفتح PD-I04+PD-I05+PD-I06+PD-I08+PD-I09+Settings Modal
- NEXT: Stage 4 — PD-I04 Typography + PD-I05 Watermark Qussasa-based + PD-I06 Reaction Card + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان

**Stage:** Stage 4 — PD-I03 — CLOSED — DECISION-I03 ACCEPTED 2026-09-23 — Multi-Accent Color System — NEXT PD-I04 + PD-I05 + PD-I06 + PD-I08 + PD-I09 + Settings Modal

**Evidence:** B-05 Brand colors foundation Ink/Qishr Amber/Paper/Coral/Warm Grey Qishr from Yemeni coffee not flag, B-06 9 category colors #F4C430 #7C5CFF #C81E3A #2CB6C4 #F17FB2 #4CAF6D #6E8296 #D98E04 #E8712E, B-01 Brand v1.0 LOCKED, B-04 Qussasa Mark v1.0 Adopted As-Is, B-09 Brand Direction الختم Direction C, P-08 Pinterest-like Masonry, P-07 Flat Saves Bookmark, P-27 Duration 2-60s badge, P-35 Brand Direction + P-36 Qussasa Mark, Claude 4 color systems 1 Amber only + 2 Indigo + 3 Multi-Accent + 4 Grey only + 3 Accents fixed, Prototype موقع تجريبي Home Masonry + Settings Modal 3 accents + theme + motion + Qussasa Mark Header + Captions لهجة يمنية + Flat Saves + Duration badge, Hamdan chose Multi-Accent Color System — Base Ink/Paper/Grey + Accent Qussasa-derived Amber + Success/Warning/Error + Optional Amber/Purple/Teal + Theme Day/Night/Auto + Reduce Motion + Settings Modal "على ذوقك" + Reset, Stage 4 OPEN PD-I01 CLOSED PD-I02 CLOSED 69 facts

---

## Topic 13 — PD-I03 — CLOSED — DECISION-I03 ACCEPTED — Stage 4 — Multi-Accent Color System

- Multi-Accent Color System — Base Ink/Paper/Grey Monochrome + Accent افتراضي قهري/كهرماني Qussasa-derived + Success/Warning/Error قياسية + Accents اختيارية Amber افتراضي + Purple + Teal + Theme Day افتراضي + Night + Auto + Reduce Motion On/Off + Settings Modal "على ذوقك" + زر استعادة الإعدادات
- Palette: Base Ink/Paper/Grey + Accent Qussasa-derived + Success/Warning/Error — Accents اختيارية Amber/Purple/Teal — Theme Day/Night/Auto — Reduce Motion On/Off — Settings Modal "على ذوقك"
- Prototype مرجع بصري: Home Pinterest-like Masonry + Settings Modal 3 accents + theme + motion + Qussasa Mark Header + Captions لهجة يمنية + Flat Saves Bookmark + Duration badge — موقع تجريبي ليس نهائي — "الاستوديو" اسم مؤقت أدمن — البحث لاحقًا — تفاصيل نهائية مع بناء فعلي
- Reason: 1) يحل PD-I03 2) متوافق Direction C الختم Modern Product First 3) متوافق Qussasa Mark v1.0 Qussasa-derived 4) تحكم للمستخدم Settings Modal 5) يرفض أنظمة محدودة 1/2/4 + 3 Accents ثابتة 6) يفتح PD-I04+I05+I06+I08+I09+Settings Modal 7) لا تعارض Stage3
- Rejected: النظام 1 كهرماني فقط محدود + النظام 2 نيلي يفقد الدفء + النظام 4 رمادي فقط بلا شخصية + 3 Accents ثابتة نستخدم متعدد
- Impact: P-37 Multi-Accent — B-05 UPDATED — B-06 محفوظ للدراسة — 69→70 facts — PD-I03 CLOSED يفتح PD-I04 Typography + PD-I05 Watermark Qussasa-based + PD-I06 Reaction Card + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد — Prototype مرجع بصري
- NEXT: PD-I04 + PD-I05 + PD-I06 + PD-I08 + PD-I09 + Settings Modal — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB
