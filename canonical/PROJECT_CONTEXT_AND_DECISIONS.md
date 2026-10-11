# YemReact — ملف السياق والقرارات المرجعي
> هذا الملف هو المرجع الحي الوحيد للمحادثة الحالية فقط (منذ بدايتها مع نِبراس حتى الآن). لا يحتوي على أي معلومات من محادثات كلود السابقة إلا إذا تم تأكيدها صراحة هنا. يتم تحديثه بعد كل قرار مهم.

**تاريخ الإنشاء:** 2026-09-07 | **آخر تحديث:** 2026-09-30 — DECISION-I10 UI Visual Language (Studio Seal) — Stage 4 CLOSED 100% — 79 facts
**الحالة العامة:** مرحلة DISCUSSION — تحليل وهوية وتخطيط، لا كود ولا تنفيذ UI
**المدير التنفيذي:** نِبراس | **شريك النقاش:** أرينا | **مهندس التنفيذ (لاحقًا):** أرينا كود | **حلقة الوصل:** المستخدم
**آلية العمل الجديدة:** نقاش متناوب — نِبراس يناقش مع المستخدم مرة، ثم مع أرينا مرة، ثم يعود للمستخدم — حتى حسم كل محور.




## UPDATE 2026-09-30 — DECISION-I10 — UI Visual Language (Studio Seal) — PD-I10 CLOSED — Stage 4 مكتمل 100%

- **Status:** ACCEPTED — حمدان 2026-09-30 — **LAST TOPIC**
- **الاتجاه:** **D — Hybrid «Studio Seal»** — هادئ كـLinear + دفء Qishr + ختم صارم + الشخصية في المحتوى
- **Foundation:** Spacing 4→64 · Breakpoints 640/1024/1440 · Container 1120 · Masonry 2/3/4/5
- **Buttons** 5 أنواع × 3 أحجام (40/44/48) × Radius 10 · **Inputs** 44px + Border 1px + shadow-sm + Focus ring 2px Accent
- **Cards** Reaction 14px + Collection Rail/Square + Mini 70×70 · **Modals** Desktop Center / Mobile Sheet 22px
- **States** Empty للصفحات فقط · Skeleton + Spinner 16 · Error فصحى هادئة · Toast Success+Error
- **Icons** Lucide 1.5px 16/20/24 · **Bottom Nav** 5 tabs (المكتبة · المجموعات · + · المحفوظات · الحساب)
- **Account Menu (P-45)** 3 حالات: زائر / مستخدم / أدمن (+الاستوديو) · Popover ديسكتوب · Sheet جوال
- **زر (+)** محايد+🔒 قبل الإطلاق + Sheet «قريبًا» · **Search Bar** 44px بلا فلاتر v1
- **Guest Save (P-46)** localStorage + دمج عند الدخول + Seal Motion فورًا
- **7 تصحيحات Stage 7 + قراران مؤجلان** (Search Route → Stage 5 · Scroll Restoration → مستقبلي)
- **Impact:** P-44 + P-45 + P-46 — **76→79 facts** — **PD-I10 CLOSED — Stage 4 CLOSED 100%**
- **NEXT:** Stage 5 — IA & Navigation

## UPDATE 2026-09-26 — DECISION-I09 — Motion Language — Stage 4 — PD-I09 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-26
- **الفلسفة:** Hybrid — Subtle في UI Linear/Vercel-style + Anchor مميز Seal Motion
- **Durations:** Micro 120ms · Small 180ms · Medium 240ms · Large 320ms (Seal فقط)
- **Easings:** Standard · Decelerate (دخول) · Accelerate (خروج) · Spring (Seal فقط)
- **Seal Motion:** 6 مراحل ~1.7s — ♡ → Mark → spin(Spring) → ✓ → ♡
- **Page Transitions:** ❌ None · **Progress bar:** ❌ · **Parallax/Bounce/Shake:** ❌
- **Scroll:** Desktop ثابت · Mobile يختفي down/يظهر up 250ms · Bottom Nav ثابت · لا Infinite Scroll
- **Loading:** Skeleton + Spinner 16px + Fade 150ms
- **Reduced Motion:** يُلغي Rotation/translateY/transitions/shimmer — يُبقي اللون — prefers-reduced-motion + Settings
- **Impact:** P-43 NEW — 75→76 facts — PD-I09 CLOSED — يفتح PD-I10 UI Language — آخر Topic
- **NEXT:** PD-I10 UI Language + Settings Modal Topic جديد + PD-I05-R2 بعد الإطلاق

## UPDATE 2026-09-25 — DECISION-I08 — Light/Dark + Soft Depth — Stage 4 — PD-I08 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-25
- **Color Tokens:** Light `#FAFAF8` / `#FFFFFF` / `#121214` — Dark `#18140F` / `#221C16` / `#F3ECE2` — **Dark دافئ — شخصية Qishr**
- **Soft Depth (R2):** sm `.04` + md `.06` + lg `.08` + float `.12` + Dark `.30-.50` + Border `.04/.06` + Active ring+4%+shadow-lg + Icon 36px `.03` + Nested Depth
- **السلوك:** Auto افتراضي `prefers-color-scheme` + 200ms transitions
- **3 تصحيحات مؤجلة Stage 7:** Duration بطاقة left→right · Duration تفاصيل يُحذف · Settings Modal حذف الإشعارات
- **Related Count:** P-11 CONFIRMED — 10 أولية + Load More حتى 50 — لا تعديل
- **Impact:** P-42 NEW — 74→75 facts — PD-I08 CLOSED — يفتح PD-I09 + Settings Modal
- **NEXT:** PD-I09 Motion + Settings Modal Topic جديد + PD-I05-R2 بعد الإطلاق

## UPDATE 2026-09-25 — DECISION-I07 — تفاصيل نهائية (Chip + Duration + Related/More) — PD-I07 CLOSED

- **1. Chip (PD-I07 مغلق):** **وسم بصري فقط** · **Inline قبل الوصف** · **غير قابل للنقر** · **❌ لا يظهر في البطاقة** ⚠️ تصحيح على P-35/B-09 اللذين كانا يثبتان «chips تحت بعض البطاقات اختياري»
- **2. Duration:** **في البطاقة ✅ أعلى يمين الوسائط** · **في التفاصيل ❌ يُحذف** (المشغل يعرضها progress bar + time)
- **3. Related + More (تأكيد):** Related (ذات صلة) = **10 رياكشن** · More (عشوائية) = **10-20 رياكشن** · كلاهما = **نفس بطاقة Reaction Card** — لا تصميم جديد
- **Impact:** P-39 UPDATED + P-40 UPDATED + P-35 CORRECTED + B-09 CORRECTED — **74 facts ثابتة** — PD-I07 CLOSED
- **OPEN للاستيضاح:** P-11/P-09 يثبتان «ذات صلة 10 أولًا + تحميل المزيد حتى 50» — إن كان المقصود 10 ثابتة بلا Load More يُعدَّل P-11 بقرار لاحق
- **NEXT:** PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق

## UPDATE 2026-09-25 — DECISION-I07 — PD-I07 Closed — chips الشخصية — Stage 4 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-25 — **بدون تصميم جديد**
- **1. PD-I07 (chips) = مغلق** — تُبنى على P-35 chips اختياري + P-39 الكتلة 4 «● اسم الشخصية — الوصف الأساسي — يُحذف إذا فارغ»
- **2. Duration في صفحة التفاصيل = يُحذف** — ✅ البطاقة أعلى يمين الوسائط / ❌ التفاصيل بلا Duration — P-39 CORRECTED
- **3. Related + More = نفس بطاقة Reaction Card** — لا تصميم جديد — P-40 — **لا تغيير في P-39**
- **Impact:** لا حقائق جديدة — **74 facts ثابتة** — PD-I07 CLOSED — P-40 UPDATED + P-35 UPDATED
- **NEXT:** PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق

## UPDATE 2026-09-25 — تصحيح PD-I07 (Duration Position) — التصحيح الرابع

- **في البطاقة (Card):** ✅ Duration **أعلى يمين الوسائط** — كما في PD-I06 — فيديو فقط — الصور بلا شارة
- **في صفحة التفاصيل:** ❌ **يُحذف — لا يظهر Duration**
- **السبب:** مشغل الفيديو يعرض المدة progress bar + time — التكرار = ازدحام — Pinterest-like لا يعرضها
- **التوافق:** متوافق P-27 المدة 2s-60s تبقى حقيقة بيانات + P-39 البطاقة — لا تعارض Stage 3
- **Impact:** P-39 CORRECTED — العدد ثابت 74 facts — PD-I06 يبقى CLOSED

## UPDATE 2026-09-25 — تصحيح PD-I06 (Detail Page Layout) — التصحيح الثالث

- **التصحيح 1 — موضع الأزرار:** الأزرار (حفظ + تنزيل + مشاركة + [...]) **بجانب العنوان — في اليسار (RTL) — نفس السطر — ليست سطرًا منفصلًا**
- **التصحيح 2 — إلغاء Empty States:** لا رسائل فارغة — لا اسم شخصية → لا شيء — لا وصف → لا شيء — لا وصف ثنائي → لا زر ▼ — لا مجموعات → لا قسم — **الحقل يُحذف من DOM إذا كان فارغًا** — لا placeholder — لا empty message — الصفحة نظيفة
- **التوافق:** P-09 «إن وجد» + P-35 chips اختياري + P-34 «إن وُجدت» + P-06 حفظ CTA دائم — لا تعارض
- **Impact:** P-39 CORRECTED — العدد ثابت 74 facts — PD-I06 يبقى CLOSED

## UPDATE 2026-09-25 — DECISION-I04 — Typography System — Stage 4 — PD-I04 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-25
- **الخطوط (4):** Display Lalezar (الـLogo فقط + عناوين التسويق) + Primary Arabic IBM Plex Sans Arabic 400/500/600/700 + Latin Inter 400/500/600/700 + Mono IBM Plex Mono 400/500
- **Type Scale:** H1 32/700/1.2 — H2 24/600/1.3 — H3 20/600/1.3 — Body L 16/400/1.5 — Body 14/400/1.5 — Body S 13/400/1.5 — Caption 12/400/1.4 — Micro 11/500/1.4 Mono
- **RTL:** كامل — أرقام Western — Letter Spacing: عربي 0 / لاتيني H1-H2 -0.01em / Mono 0
- **مؤجل:** Micro 11px يُختبر Stage 7 قد يُرفع 12px — Settings Modal Topic مستقبلي
- **Rejected:** خطوط عربية تقليدية Amiri+Reem Kufi+Aref Ruqaa + خط يد + Lalezar في UI + أكثر من 4 خطوط
- **Impact:** P-41 NEW Typography System — 73→74 facts — PD-I04 CLOSED — يفتح PD-I07 + PD-I08 + PD-I09
- **NEXT:** PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق

## UPDATE 2026-09-24 — DECISION-I05 — Watermark Deferred — Stage 4 — PD-I05 — DEFERRED

- **Status:** DEFERRED — مُجمّد مؤقتًا — ليس CLOSED — حمدان 2026-09-24
- **القرار:** تجميد Watermark مؤقتًا — لا يُنفّذ الآن
- **السبب:** 1) يحتاج دراسة أعمق تأثير على صناع المحتوى+التكاليف+القانوني 2) يمكن إضافته بعد الإطلاق ليس حرجًا للنسخة الأولى 3) Direction C الختم يبقى صالحًا مع 2 Anchors Motion + chips 4) صفر مخاطرة تقنية قابل للتراجع
- **ما تم تجميده:** Watermark على الفيديو + الصور + البطاقات + صفحة التفاصيل + معالجة FFmpeg
- **ما يبقى فعّالًا:** Qussasa Mark PD-I02 كـLogo في الهيدر فقط + Motion Signature PD-I09 + chips الشخصية PD-I06+PD-I07
- **إعادة الفتح:** بعد الإطلاق — PD-I05-R2 — ببيانات حقيقية سلوك المستخدم
- **Impact:** P-38 NEW Watermark Deferred — B-07 FROZEN — B-09 UPDATED 2 Anchors — P-35 UPDATED 2 Anchors — 70→71 facts

## UPDATE 2026-09-24 — DECISION-I06 — Reaction Card & Detail Page — Stage 4 — PD-I06 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-24
- **البطاقة:** الوسائط بدون فراغ أسود + Duration badge أعلى يمين فيديو فقط + العنوان + ⋮ ثلاث نقاط + نقرة → /r/[code] — بدون Watermark
- **صفحة التفاصيل /r/[code] — 8 كتل:** رجوع / الوسائط+Duration / العنوان كبير+[حفظ][تنزيل][مشاركة][...] / ● اسم الشخصية — الوصف الأساسي / الوصف الثنائي المطوي ▼ / المجموعات إن وُجدت / رياكشنات ذات صلة / رياكشنات عشوائية (محدودة 10-20)
- **الأزرار:** رئيسية حفظ + تنزيل + مشاركة — ⋮ **نسخ الرابط + إبلاغ فقط** — CORRECTED 2026-09-24 ❌ حُذف تعديل Admin فقط
- **التصحيح 2026-09-24:** 1) رياكشنات عشوائية P-40 — قسم **محدود 10-20 رياكشن — تصحيح ثان 2026-09-25: كان 20-40 → أصبح 10-20** — ليس Infinite Scroll — لا Load More — يتوقف عند 10-20 — يتوافق P-03 No Infinite Feed + DECISION-006 2) P-23 — عنصران فقط نسخ الرابط + إبلاغ — لا أزرار Admin في المكتبة — الأدمن يعدّل من /admin فقط — قرار حمدان «مثل المستخدم تمامًا + الصلاحيات في صفحة الأدمن فقط»
- **Impact:** P-39 NEW Reaction Card & Detail Page Spec — P-40 NEW ذات صلة + عشوائية — P-11 UPDATED — P-23 UPDATED — 71→73 facts — PD-I06 CLOSED
- **NEXT:** PD-I04 Typography + PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد + PD-I05-R2 بعد الإطلاق

## UPDATE 2026-09-23 — DECISION-I03 — Multi-Accent Color System — ACCEPTED — Stage 4 OPEN — PD-I03 CLOSED — 70 facts

- DECISION-I03 Multi-Accent Color System ACCEPTED 2026-09-23 Stage 4 Identity Re-Foundation PD-I03 Color System CLOSED
- Palette الأساسي: Base Ink/Paper/Grey Monochrome + Accent افتراضي قهري/كهرماني Qussasa-derived Qishr Amber + Success/Warning/Error قياسية
- Accents اختيارية من الإعدادات Settings Modal على ذوقك: كهرماني Amber افتراضي دافئ يمني + بنفسجي Purple حديث مميز + تيل Teal بارد هادئ
- Theme: نهاري Day افتراضي + ليلي Night + تلقائي Auto يتبع النظام prefers-color-scheme
- Reduce Motion: On/Off — يحترم prefers-reduced-motion — تفاصيل PD-I09
- Settings Modal: موجود UI على ذوقك عنوان أنيق بلهجة يمنية + 3 Accents + Theme + Motion + زر استعادة الإعدادات Reset — Topic جديد يُفتح لاحقًا
- المرجع البصري Prototype موقع تجريبي: Home Pinterest-like Masonry + Settings Modal + Qussasa Mark في Header + Captions بلهجة يمنية + Flat Saves Bookmark + Duration badge — موقع تجريبي ليس نهائي — الاستوديو اسم مؤقت أدمن — البحث لاحقًا — تفاصيل نهائية مع بناء فعلي
- Rejected: النظام 1 كهرماني فقط محدود + النظام 2 نيلي يفقد الدفء + النظام 4 رمادي فقط بلا شخصية + 3 Accents ثابتة نستخدم متعدد — كلها REJECTED per DECISION-I03
- Impact: P-37 Multi-Accent Color System — B-05 UPDATED Brand colors foundation → Multi-Accent — B-06 9 colors محفوظ للدراسة — 69→70 facts — PD-I03 CLOSED يفتح PD-I04+PD-I05+PD-I06+PD-I08+PD-I09+Settings Modal — Prototype مرجع بصري ليس نهائي — ملاحظة موقع تجريبي + الاستوديو اسم مؤقت + البحث لاحقًا
- No code/Git/DB — documentation only — No conflict Stage 3 — Multi-Accent يبني فوق Brand Direction + Qussasa Mark — Direction C + Qussasa + Qussasa-derived Amber



## UPDATE 2026-09-23 — DECISION-I02 — Qussasa Mark v1.0 Adopted As-Is — ACCEPTED — Stage 4 OPEN — PD-I02 CLOSED — 69 facts

- DECISION-I02 Qussasa Mark v1.0 Adopted As-Is ACCEPTED 2026-09-23 Stage 4 Identity Re-Foundation PD-I02 Logo/Mark CLOSED
- Decision: اعتماد Qussasa Mark v1.0 كما هو — بدون تحسين — مربع بزاوية علوية يمنى مشطوفة/ممزقة بتسنين + ثقب تشغيل مثلث كفراغ سالب fill-rule evenodd — اجتاز 8 سيناريوهات — يعمل 16-512px — متوافق Direction C الختم تقشير=بصمة بصرية — يوفر وقت Stage 4
- Reason: 1) اجتاز 8 سيناريوهات Brand v1.0 LOCKED S10 2) متوافق Direction C الختم تقشير=بصمة 3) يعمل 16-512px 4) يوفر وقت للمواضيع الأكثر تأثيرًا PD-I03+PD-I05
- Rejected: Direction A الزاوية + B الحرف + C الختم الجديد + D الإيقاع + كل النسخ المحسّنة H1-R2 + Qussasa Improvement H1-R3 لم يُنفذ — كلها REJECTED per DECISION-I02
- Impact: P-36 Qussasa Mark v1.0 adopted — B-04 UPDATED HISTORICAL→ACCEPTED — B-07 Watermark سيُبنى على Qussasa Mark Qussasa-based — PD-I02 CLOSED — يفتح PD-I03 Color System + PD-I05 Watermark Qussasa-based — 68→69 facts — Revisable إذا احتجنا تحسين → PD جديد — لا يمنع التطوير — مرن — CONFLICT-019 partially resolved Qussasa-based — No conflict Stage 3
- No code/Git/DB — documentation only — No conflict with Stage 3 — Qussasa Mark v1.0 يبني فوق Brand Direction الختم — Direction C + Qussasa



## UPDATE 2026-09-21 — DECISION-I01 — Brand Direction — الختم — ACCEPTED — Stage 4 OPEN — PD-I01 CLOSED — 67 facts

- DECISION-I01 Brand Direction Direction C الختم Al-Khatm ACCEPTED 2026-09-21 Stage 4 Identity Re-Foundation PD-I01 CLOSED
- Persona منهجي واثق الشخصيات هي البطل — Mood بصمة استوديو لا زخرفة — Modern Product First, Yemeni Character Second — DeepSeek + ChatGPT
- 3 Signature Anchors: 1) Watermark موحد شكل هندسي مجرد صغير جدًا ليس رمز ثقافي زاوية ثابتة كل رياكشن مكان يُحدد PD-I05 — 2) Motion Signature حركة ختم/قلب 150-200ms عند الحفظ/الإضافة لـCollection — 3) chips اسم الشخصية تحت بعض البطاقات اختياري مصطفى المومري هديل مانع تصنيف موازٍ للـCollections
- Modern UI Foundation Pinterest-like Masonry + Search فوري + Spacing Linear + نظام واحد صارم + Account flows قياسية + لا تراث في UI
- Content Art Direction thumbnails إطار موحد بدون فراغ أسود + Captions قصيرة لهجة يمنية + تصنيف شخصيات كطبقة اكتشاف + تركيز مين قالها
- Tests: Hide/Show + Museum + Modernity passed — Pinterest+Linear+Superhuman حديث 100%
- Rejected: Direction A الزاوية بصمة 2-3px + B الحرف خط عربي فقط + D الإيقاع بصمة ضعيفة + 4 الأولى متحف (ترانزستور، قمرية، السوق، المثل) + رموز مباشرة + متحف فلسفة
- Impact: P-35 Brand Direction — 66→67 — B-07 peel+Qussasa → HISTORICAL → abstract geometric — B-04 Qussasa → HISTORICAL — CONFLICT-019 partially resolved — Old 11% vs 14% → New abstract — Details PD-I05 — P-06 Save+Motion متوافق — P-14 Search+chips متوافق — P-32 Collections+chips طبقة ثانية — P-29 Aspect+Watermark موحد+thumbnails مقصوصة — Stage3 CLOSED لا تعارض — Stage4 OPEN PD-I01 CLOSED يفتح PD-I02+I03+I04+I05+I06+I09
- No code/Git/DB — documentation only — No conflict with Stage 3 — Brand Direction builds on top — لا يلغيه


---

## 1. وصف مختصر للمشروع والهدف النهائي

**YemReact — يمن رياكت:** مكتبة رياكشنات يمنية (فيديو فقط، مقتطعة من مواقف يمنية حقيقية، تُفهم بذاتها بدون سياق).

> **ملاحظة للمناقشة فقط (ليست معتمدة):** المستخدم نبه أن الافتراض السابق "9:16 أساسي + 1:1" و "2-8 ثوانٍ" قد يكون غير دقيق. طرح فكرة: الفيديو ليس بمقاس محدد، والمدة قد تصل لدقيقة كحد أقصى. هذه نقطة للملاحظات والنقاش فقط، ليست قرارًا معتمدًا.

**الفكرة المركزية:** الرياكشن = المثل الشعبي الرقمي. لقطة قصيرة تُستخدم كإجابة جاهزة لموقف يومي، تُؤخذ وتُوضع في مكانها (تعليق، ميم، حالة، رد).

**الشعار التشغيلي:** "خذها. حطها. يمنية."

**الهدف النهائي للمرحلة الحالية:** إطلاق صفحة Facebook بمحتوى حقيقي (30-50 كحد أدنى للاختبار، 150-300 كعتبة فائدة حقيقية) + تثبيت هوية Brand v1.0 + إعداد خطة منتج قابلة للتسليم لمصمم ومطور بدون إعادة اختراع الهوية.

**الهدف المستقبلي:** موقع/مكتبة قابلة للبحث بالموقف ("لما صاحبك يقول بكرة") وليس بالمشاعر المجردة، مع حفظ ومشاركة وتنزيل، ومساهمات بمراجعة يدوية.

---

## 2. المتطلبات الأساسية والتعليمات التي يجب الالتزام بها

1.  **الهوية البصرية مقفلة:** لا إعادة تصميم للشعار، الألوان، الخطوط، القُصاصة. التعديل الوحيد المسموح هو تطبيقها داخل الصفحات.
    - الشعار: القُصاصة (إطار ممزق + زر تشغيل).
    - الألوان الأساسية: الحبر الداكن، الكهرمان، الكهرمان الفاتح، الورق، المرجان، الرمادي.
    - ألوان التصنيف (9 فئات): ضحك، صدمة، غضب، استغراب، إحراج/صمت، موافقة، رفض، سخرية، حماس.
    - الخطوط: لاليزار للعناوين القصيرة، القاهرة للنصوص.
    - العلامة المائية: نسخة مُقوّاة بظل.
    - قاعدة قلب الكتلة: إذا انشغلت الزاوية الافتراضية، تُقلب الكتلة كاملة للجهة المقابلة.
    - **ملاحظة فقط:** موضوع مقاسات الفيديو والمدة (هل هي ثابتة أم مرنة، حتى دقيقة) هو نقطة ملاحظات قيد النقاش، ليس قرارًا معتمدًا، ولن نناقش كيفية بنائه تقنيًا في هذه المرحلة.

2.  **الفيديو فقط:** الصور الثابتة كمنتج مرفوضة. المنتج هو الفيديو فقط.

3.  **ملاحظة عن المقاس والمدة (ليست معتمدة):** كانت هناك ملاحظة سابقة أن المقاس ثابت والمدة قصيرة. الآن هناك ملاحظة جديدة تطرح أن المقاس قد يكون مرنًا والمدة قد تصل لدقيقة. هذه ملاحظة للنقاش فقط، ليست قرارًا معتمدًا، ولن نناقش كيفية تنفيذها تقنيًا الآن.

4.  **طريقة العمل:** محور واحد في كل مرة، مرحلة نقاش وتوثيق فقط حتى اعتماد الخطة النهائية. لا كود، لا بناء تقني، لا واجهات جديدة قبل اعتماد الهوية والهيكلية.

4.  **التمييز الواضح في التوثيق:** ACCEPTED (معتمد), PROPOSED (مقترح واضح لم يُعتمد), DISCUSSION (قيد النقاش), OPEN (سؤال مفتوح), REJECTED (مرفوض), DEFERRED (مؤجل), SUPERSEDED (كان معتمد واستُبدل).

5.  **لا افتراضات خارج الملفات الحالية:** المرجع هو الملفات المرفوعة في هذه المحادثة + ملفات القرارات (01-DECISIONS-LOG.md, 02-OPEN-QUESTIONS.md, إلخ). أي وثيقة قديمة تعتبر تاريخ لا حقيقة عند التعارض.

6.  **فلسفة المنتج الحاكمة (من MVP Directive):** YemReact يساعد المستخدم يلاقي الرياكشن اليمني المناسب للموقف بأسرع طريقة، ويعطيه إياه جاهزًا. أي ميزة لا تخدم مباشرة: الاكتشاف + الوصول + الحفظ + الأخذ + المشاركة + بناء المكتبة — تُرفض افتراضيًا.

---

## 3. القرارات التي اتُّخذت (مع السبب)

### ACCEPTED (معتمدة ومقفلة)

- **Brand v1.0 LOCKED:** اجتاز اختبار 8 نماذج واقعية، Watermark مُقوّى، قاعدة قلب الكتلة مضافة. السبب: اختبار بصري كامل + لا حاجة لتغيير جمالي. لا يُعاد فتحها بصريًا.
- **Main = Library:** الرئيسية هي المكتبة نفسها. لا صفحة /search منفصلة مفهوميًا. البحث يحدّث نفس الصفحة عبر ?q=. السبب: نموذج ذهني واحد + رابط قابل للمشاركة (/?q=خبر).
- **Reaction Detail = Page /r/[code]:** لا Modal. السبب: رابط حقيقي قابل للمشاركة والفهرسة (OG/SEO) أهم من استمرارية بصرية.
- **Sidebar REMOVED:** لا Sidebar دائم على Desktop. السبب: يتعارض مع "الرئيسية = المكتبة لا Dashboard" + 3 أشكال Shell مختلفة = تعقيد صيانة.
- **Account = Menu/Sheet لا صفحة كاملة:** يطابق وزنه الفعلي بالمنتج.
- **Schema Cleanup — اتجاه معتمد:** حذف Session, OneTimeCode, Setting (بقايا OTP), دور EDITOR, MediaKind.SUBTITLE. السبب: بقايا بلا منطق حالي = عبء فهم. (التنفيذ لم يبدأ بعد)
- **Media Processing — اتجاه معتمد:** منطق Validate/Extract/Watermark يُعاد استخدامه لكن مكان تشغيله ينتقل لخدمة/Worker مُدارة (Cloudflare Stream أو معادل) خارج عملية Next.js/Vercel. السبب: تشغيل ffmpeg داخل Serverless غير موثوق بنيويًا + فشل فعلي (0 فيديو في الإنتاج).
- **Source/Rights REMOVED من مبادئ Submissions:** محذوفة كليًا من النموذج.
- **Performance Rating REJECTED:** لا تقييم أداء من المُرسِل.

### PROPOSED (مقترحة بانتظار اعتماد)

- **BottomNav الخانة الرابعة = Saved:** تاريخ القرار: أولًا Submit (SUPERSEDED لأنه يضع إنشاء محتوى بنفس مستوى الاكتشاف)، ثم Collections (SUPERSEDED لأن 3 مجموعات لا تبرر مقعد تنقل دائم)، حاليًا Saved لأنه أقرب فعل شخصي متكرر لـ"خذها. حطها.".
- **Categories = Data Only:** 9 فئات كبيانات/لون فقط، لا فلترة بارزة كوجهة مستقلة.
- **Collections = Rail داخلي:** لا BottomNav Destination. Rail داخل تجربة المكتبة يكفي حتى يكبر العدد.
- **Masonry Mixed Aspect:** فيديو فقط، لا Pinterest صور ثابتة.
- **Content 3 Types ثابتة:** Daily (قُصاصة واحدة اقتباس مباشر), When Need (لما... + جواب جاهز), Library Week (Carousel 4-6 لقطات لفئة واحدة).
- **Speech Extraction = Binary + Expandable Window:** نص مستخرج تلقائيًا بجوار الوصف الأساسي، نافذة قابلة للتوسيع عند دخول الرياكشن. الخدمة لم تُختر بعد.
- **Core Loop = Hybrid Utility (PROPOSED → DISCUSSION حاليًا):** كان PROPOSED كـUtility خالص (أداة عند الحاجة)، ثم اقترح نِبراس Hybrid Utility: "Find the right reaction, discover the next one, and share it naturally" / "اعثر على رد الفعل المناسب، واكتشف المزيد، وشاركه بسهولة." ترتيب الأولويات: 1) العثور، 2) فهم واختيار، 3) حفظ/مشاركة/استخدام، 4) اكتشاف مشابه، 5) العودة عند الحاجة. لكن نِبراس تراجع عن اعتماده الفوري وطلب جلسة فهم مفتوحة، لذلك حالته الآن DISCUSSION بميول لـHybrid.
- **Library Size:** 30-50 كافية لاختبار التصميم فقط، 150-300 عتبة واقعية لتغطية موقفية تجعل البحث نادرًا ما يرجع فارغًا.
- **middleware.ts كطبقة حماية إضافية:** فوق الحراس الحاليين بـ38 موضعًا.
- **Content Rubric 6 نقاط (مقترح — يحتاج تعديل بسبب المدة الجديدة):** 1) يُفهم فورًا بلا سياق، 2) قصير سابقًا 2-8ث — الآن حتى 60ث كحد أقصى، لكن الأفضلية للأقصر (هل نفرّق بين Clip سريع ≤8ث و Clip سردي حتى 60ث؟)، 3) أصالة لهجية يمنية، 4) تحديد موقفي كافٍ لا عام، 5) نظافة تقنية، 6) راحة مصدر (لا استغلال لحظة ضعف شخص عادي). — OPEN: كيف نطبق Rubric على فيديو 45ث لا يزال رياكشن؟

### REJECTED (مرفوضة نهائيًا)

- صور ثابتة كمنتج (Pinterest).
- Trending كواجهة أساسية / عداد "الأكثر إعجابًا" ظاهر للمستخدم / لايكات / تعليقات عامة / متابعين / رسائل بين المستخدمين / Leaderboard / نقاط / Feed لا نهائي بأسلوب TikTok / إشعارات اجتماعية "فلان أعجب بـ...".
- Video Intro/Outro Bumper قبل اللقطة (أول فريم = بداية الرياكشن).
- Ad Creative في مرحلة الإطلاق العضوي.

### SUPERSEDED (مستبدلة مع تاريخ)

- BottomNav: Submit → Collections → Saved (كما موضح أعلاه).
- انبهار كفئة عاشرة بلون مستقل → أُلحقت بعائلة استغراب (نفس التركواز) لتفادي تضخم التصنيف.

### OPEN / DISCUSSION (مفتوحة)

- Core Loop النهائي: Utility-first أم Social/Discovery-first أم Hybrid أم Content-library-first؟
- Speech Service: Whisper؟ Cloudflare؟ Storage DB Field أم Search Index فقط؟ UI Expandable Window أين (بجوار الفيديو؟ تحت العنوان؟ بجوار Save؟).
- Content Pipeline: Manual 30-50 كيف يُجمع Raw؟ من أي مصادر؟ من يجمع؟ متى تُفعّل Submissions كمصدر أول (بعد 150؟ 300؟).
- Taxonomy: هل نحتاج Tags كطبقة ثالثة؟ هل Collections تصبح "بحث محفوظ" بدل كيان مُدار يدويًا؟
- Search: أنواع النية (كلمة حرفية، موقف، مزاج، شخص) — هل حقل واحد يكفي؟
- Admin Experience: Bulk Approve/Reject/Categorize، Keyboard Shortcuts، Needs Review حالة جديدة؟
- Settings (autoplay/صوت/توفير بيانات) — أولويتها ارتفعت بسبب واقع الشبكة اليمنية لكن توقيتها؟
- Submission كـGrowth Engine — فقدان النموذج بعد تسجيل الدخول عبر Google (فجوة موثقة).
- Git: 147 ملف بلا Remote — Critical، فروع، CI، حماية إنتاج.
- Observability: لو تعطّل الموقع غدًا كيف نعرف؟ لا سجلات مركزية حاليًا.
- Performance Budget: لا أرقام حقيقية لشبكة/جهاز يمني فعلي (3G بطيء افتراض غير مقاس).
- Accessibility / RTL edge cases.
- Metrics: 5 مؤشرات فقط — Search Success Rate؟ Save Rate؟ Share Rate؟ Submission Conversion؟ Retention (Mental Availability vs Engagement Loop)؟
- Video Identity Responsive: كيف تُطبق Qussasa / Peel / Duration Tag / Category Dot على أي مقاس (16:9 أفقي، 9:16 عمودي، 1:1 مربع، 4:5، 3:4)؟ Safe Area نسبي كيف يُحسب؟ هل Overlays الحالية (06-... Default/Mirrored) تبقى كمرجع فقط أم نحتاج نظام توليد ديناميكي؟
- Duration up to 60s: هل 60ث لا يزال "رياكشن" أم يصبح "مقطع"؟ كيف نفرّق في UI بين سريع ≤8ث وطويل حتى 60ث؟ هل نضيف فلتر مدة؟ هل يؤثر على الأداء (تحميل، توفير بيانات) وعلى تكلفة المعالجة والتخزين؟
- Monetization: DEFERRED — لا قرار الآن لكن هل أي قرار تقني يمنعها مستقبلًا؟

---

## 4. ما تم إنجازه حتى الآن

- تحليل كامل لملف Yem React.md الأصلي + كل ملفات uploads (Brand LOCKED, Identity System, Social Design System, Content System Launch Kit, MVP Directive, Production Guide, Asset Inventory, Product UI jsx, Web Prototype jsx, Project Story).
- إنشاء هيكل المرجع الحي: 00-INDEX.md, 01-DECISIONS-LOG.md, 02-OPEN-QUESTIONS.md, 03-PRODUCT-VISION.md, 04-IA-UX.md, 05-ARCHITECTURE.md (6 ملفات، مبدأ: من يحتاج يقرأ هذا أولًا؟).
- توثيق كل القرارات بحالة ACCEPTED/PROPOSED/REJECTED/SUPERSEDED/OPEN مع السبب والبدائل.
- إنشاء phase_01_analysis_plan.md: 7 محاور منطقية A→G (A Core/هوية، B Content/تحرير، C IA/تنقل، D UX/تفاعل، E Architecture/تقنية، F Growth/أعمال، G Operations/صيانة) + ترتيب منطقي Product→UX→Technical→Growth.
- جلسة تحليل مفتوح (Open Session) غطت 20 نقطة (جوهر المشروع، المشكلة، الهدف، المنتج، الجمهور، القيمة، ما حُسم، ما اقتُرح، ما رُفض، التعارضات، الافتراضات، نقاط القوة/الضعف، ما أُغفل، ما يحتاج حسم قبل التصميم، العلاقة بين المكونات، التصور، الاتجاهات المحتملة، أسئلة).
- تجهيز حزمة أصول Facebook كاملة وجاهزة: Profile 720x720, Cover 1640x720 (2x), Overlays 9:16 و1:1 (Default + Mirrored), Safe Area Guides x4, Post Template 1080x1350, Category Collection, Announcements (Intro/ComingSoon/Milestone), Story RequestReaction — كلها READY.
- لا كود جديد، لا تنفيذ UI جديد، لا بناء تقني — التزام بمرحلة DISCUSSION فقط.

---

## 5. ما لم يتم إنجازه بعد

- حسم Core Loop نهائيًا (القرار الأكثر تأثيرًا).
- جمع محتوى حقيقي (0 فيديو منشور في الإنتاج حاليًا).
- اختيار Speech Service وتصميم Expandable Window.
- تنظيف Schema (تنفيذ الحذف).
- نقل Media Processing لخدمة مُدارة (تنفيذ).
- إضافة middleware.ts وتنفيذ Rate Limiting وFile Validation.
- حل Git Critical (Remote, Branch, CI).
- بناء Observability (Logs, Health Check, Metrics Dashboard).
- تحديد Performance Budget بأرقام حقيقية.
- تصميم تفصيلي لـ Reaction Detail Sequence (Video → Title → Window → Category → Collections → Save → Share → Related؟).
- تصميم Account Menu (Saved Sync Mechanism, My Submissions Status, Settings Keep/Remove).
- تصميم Admin List/Single Review مع Rubric Checkboxes + Bulk + Keyboard.
- تحديد Metrics الخمسة النهائية وSEO وSocial Embeds وViral Loop.
- تنفيذ أول 10 منشورات إطلاق حسب Content System.

---

## 6. المشكلات والأخطاء والملاحظات المهمة

1.  **Content = 0 Real:** كل UI (Featured, New, Trending, Masonry) نظري بدون Reaction حقيقي يُحكم عليه. خطر بناء واجهة على فراغ.
2.  **Git هش:** 147 ملف غير ملتزم بلا Remote — خطر فقدان بيانات Critical.
3.  **Protection متفرقة:** 38 موضع حماية بلا ضمان بنيوي — أي Route جديد قد ينسى الحارس.
4.  **Media داخل Serverless:** ffmpeg كوعد بلا انتظار داخل دالة Serverless = فشل وظيفي محتوم (حدود وقت تنفيذ).
5.  **Observability = Blind:** لا كشف لو تعطّل الموقع.
6.  **Performance = No Numbers:** افتراض "3G بطيء، هاتف ضعيف" صحيح غالبًا لكن بلا رقم يوجّه ميزانية.
7.  **افتراض القيمة غير مُختبر:** هل البحث الموقفي والانتقاء والواترمارك أسرع/أنظف فعلًا من تسجيل الشاشة من TikTok؟ بلا دليل استخدام حقيقي.
8.  **تعريف "محتوى جيد" حدسي:** بلا Rubric تشغيلي ثابت يطبقه أي أدمن بثبات.
9.  **قناة الاكتساب غير معروفة:** SEO + روابط قابلة للمشاركة مفترضة كقناة نمو بلا اختبار (Facebook؟ كلام متناقل؟ Google؟).
10. **مشكلة الدجاجة والبيضة في Submissions:** المساهمات تحل ندرة المحتوى لكنها تحتاج جمهورًا موجودًا ليساهم.
11. **تناقض ضمني:** Core Loop المقترح كـUtility يتعارض مع Social Features المفترضة في Launch Kit (Featured/New/Trending) إذا اعتُبرت أساسية.
12. **تعقيد Taxonomy:** 3 طبقات متوازية (Category ثابتة 9، Collection تحريرية، Tags مفتوحة) — هل الثلاث ضرورية؟

---

## 7. الافتراضات التي بُني عليها العمل

- المستخدم يدخل لأنه يحتاج رياكشنًا لموقف محدد، ليس للتصفح المستمر بلا سبب (افتراض Utility — يحتاج اختبار).
- 150-300 رياكشن كافية لتغطية موقفية واقعية (تقاطع رقمين مستقلين من زاويتين: تغطية موقفية + عتبة بحث دلالي — إشارة جيدة لا يقين).
- الجمهور الأساسي: صناع ميمز 16-30، صناع محتوى يبحثون عن بديل محلي لـGiphy/Tenor، مستخدم عادي يريد تعبير سريع، صفحات يمنية/عربية.
- الشبكة/الجهاز اليمني: 3G بطيء + هاتف منخفض المواصفات (غير مقاس).
- Watermark كقناة توزيع (تعرض العلامة عند المشاركة) — فعال.
- Save هو CTA الأساسي (يطابق "خذها. حطها.") وليس المتابعة.
- البحث بالموقف ("لما...") أقوى من البحث بالمشاعر المجردة ("صدمة").

---

## 8. الملفات الموجودة ووظيفة كل ملف وعلاقته بالمشروع

| الملف | الوظيفة | الحالة |
|---|---|---|
| 00-INDEX.md | خريطة المجلد وحالة المرحلة DISCUSSION | مرجع حي |
| 01-DECISIONS-LOG.md | كل قرار: السبب، البدائل المرفوضة، الحالة، تاريخ التغيير | مرجع حي |
| 02-OPEN-QUESTIONS.md | كل سؤال بلا جواب + تعارضات + توترات Product/UX/Architecture | مرجع حي |
| 03-PRODUCT-VISION.md | تعريف المنتج، Core Loop، حدود MVP، استراتيجية محتوى | مرجع حي |
| 04-IA-UX.md | البنية المعلوماتية، التنقل، كل شاشة ووظيفتها | مرجع حي |
| 05-ARCHITECTURE.md | التقني: DB, Media, Security, Deployment, Testing | مرجع حي |
| YemReact-Brand-v1.0-LOCKED.html | الهوية المقفلة نهائيًا بعد اختبار 8 نماذج — Watermark مُقوّى + قاعدة قلب الكتلة | LOCKED |
| YemReact-identity-system.html / YemReact-دليل-الهوية.md | دليل الهوية الأصلي (قبل LOCKED) — مفهوم القُصاصة = المثل الشعبي الرقمي، لوحة القشر، Lalezar/Cairo | تاريخي، يُلغى عند التعارض مع LOCKED |
| YemReact-Social-Design-System.html / Templates-Source-Editable.html | نظام تصميم السوشال + قوالب قابلة للتعديل | مرجع بصري |
| 01-Profile-Picture-720x720.png, 01b-SizeTest, 02-Cover-1640x720 | أصول إطلاق Facebook | READY |
| 06-ReactionClip-Overlay-... (x4) + 06b-SafeAreaGuide (x4) | Overlays للفيديو 9:16 و1:1 (Default + Mirrored) + أدلة Safe Area | READY |
| 07-PostTemplate-1080x1350, 08-CategoryCollection, 09a/b/c-Announcement, 10-Story-RequestReaction | قوالب منشورات وإعلانات وقصص | READY |
| 11-Reaction-Production-Guide.md | دليل تنفيذي 10 خطوات لإنتاج رياكشن من الصفر حتى النشر بدون رجوع لأي مرجع | READY |
| 12-Final-Asset-Inventory.md | جرد نهائي للأصول — لا يوجد أصل بصري ناقص لإطلاق Facebook | COMPLETE |
| 00-Bio-About-IntroPost-Checklist.md | نصوص Bio/About + كابشن أول منشور + Checklist إطلاق | READY |
| YemReact-Content-System-Launch-Kit.md | نظام تشغيل المحتوى: 9 خطوات ثابتة، نظام تسمية 3 طبقات، هوية المنشور، 3 أنواع ثابتة + ثانوية، 3 صيغ كتابة (لما... / اقتباس / نداء مباشر)، Hashtag 3 طبقات، أول 10 منشورات | مرجع تشغيلي |
| YemReact-MVP-Directive.md | نطاق MVP المعتمد + مؤجل بعد MVP + مستبعد نهائيًا + قرارات معمارية نهائية + 3 نقاط معلقة (تسلسل خط الفيديو، نطاق صفحات قانونية، مدة احتفاظ Original المرفوض) | مرجع نطاق |
| YemReact-Product-UI jsx.md / YemReact-Web-Prototype.jsx.md | بروتوتايب واجهة (Mock Data، لا Backend) — شبكة بطاقات، بحث، تفاصيل، حفظ، تصنيفات، حالات فارغة | بروتوتايب نظري، لا يُعتبر محتوى حقيقي |
| YemReact-Project-Story.html | قصة المشروع من الفكرة حتى الحلم — المثل الشعبي الرقمي، "خذها. حطها. يمنية."، رحلة الهوية | مرجع سردي |
| نبراس.md | نص المحادثة الكاملة مع نِبراس وأرينا منذ البداية + جميع البرومبتات المتبادلة + قرارات المحور A المقترحة ثم الملغاة + خطة 7 محاور | المصدر الأساسي لهذا الملف |
| مستند نصي جديد (2).md | فارغ 0 بايت | لا قيمة |

---

## 9. آخر نقطة وصلنا إليها في المحادثة

- نِبراس كان قد اعتمد مبدئيًا: الإطار A→G، Brand LOCKED، Core Loop Hybrid Utility، Value Prop موسعة، Audience كما هو بترتيب أولويات.
- ثم قرر نِبراس **عدم إرسال** قرار المحور A كأمر مغلق، والعودة لجلسة فهم وتحليل مفتوحة.
- أرسل نِبراس برومبت يطلب من أرينا قراءة كل الملفات ومحادثة كلود وتحليل 20 نقطة بدون اعتماد قرارات جديدة أو تحديث ملف القرارات أو كتابة كود.
- أرينا سلّم session_analysis_open.md (20 نقطة، A→G، ACCEPTED/PROPOSED/REJECTED/OPEN مميزة، لا تنفيذ).
- نِبراس حضّر برومبت جديد يطلب من أرينا نقاشًا عميقًا ومفتوحًا حول جوهر المنتج: تحليل 4 اتجاهات لـCore Loop (Utility-first, Social/Discovery-first, Hybrid, Content-library-first) مع تحليل توافق كل اتجاه مع الهوية، مفهوم المثل الشعبي، المحتوى عند الإطلاق، أثره على Home/Library/Search/Categories/Collections/Save/Share/Submissions، أنواع المحتوى Daily/When Need/Library Week، مؤشرات النجاح، مخاطره، ماذا لو 30-50 فقط، أي اتجاه يُختبر بسرعة وأقل تكلفة، وأسئلة حاسمة عن سلوك البحث، هل الصفحة الرئيسية تبدأ ببحث أم مكتبة أم مزيج، هل Daily/Trending/New تخدم المنتج أم تدفعه لتقليد السوشال، هل Collections ضرورية منذ البداية، هل Save/Share أساسية أم ثانوية، هل Submit أساسي أم قناة مستقبلية، ما الحد الأدنى الذي يثبت الفكرة.
- **التوقف الفعلي:** عند هذا البرومبت الأخير — بانتظار رد أرينا التحليلي العميق قبل حسم المحور A.

---

## 10. الخطوات التالية المقترحة أو المطلوبة

**المرحلة الحالية: محور A — الهوية والفكرة (Core) — نقاش مفتوح**

1.  **أرينا يقدّم تحليله العميق لـ4 اتجاهات Core Loop** مع فصل واضح بين: معلومات مؤكدة من الملفات، استنتاجاته من ربط المعلومات، اقتراحاته المهنية، أسئلة تحتاج تأكيد من نِبراس. لا اعتماد Core Loop، لا تحديث ملف القرارات بقرارات جديدة، لا انتقال لـB.
2.  **نِبراس يراجع ويصحح ويعترض ويضيف** — حوار حقيقي، ليس تنفيذ أوامر.
3.  **حسم Core Loop بصيغة Hybrid Utility أو بديل مبرر** — مع صياغة مختصرة عربية وإنجليزية + ترتيب أولويات داخل الحلقة + أثره على القرارات القادمة.
4.  **تحديث PROJECT_CONTEXT_AND_DECISIONS.md** بـCore Loop كـACCEPTED مع نقل الصيغة السابقة إلى SUPERSEDED.
5.  **الانتقال لمحور B فقط بعد حسم A:** Content and Editorial System — أنواع المحتوى، Rubric 6 نقاط (ACCEPTED أم Modified؟)، Taxonomy (Tags NEW؟ Collections Rail FINAL؟)، Pipeline (Manual 30-50 كيف يُجمع Raw؟ متى تُفعّل Submissions؟)، Speech Extraction (Service Choice + Storage + UI Window).
6.  **ثم C→D→E→F→G محورًا بمحور** بانتظار موافقة بعد كل محور، مع تلخيص قرارات مؤكدة ونقاط مفتوحة وما يحتاج مراجعة، وتحديث الملف المرجعي بعد كل مجموعة قرارات.

**قواعد التحديث المستقبلية للملف:**
- حدّث بعد كل قرار مهم أو تغيير متطلبات أو تقدم جوهري.
- لا تحذف معلومات سابقة مهمة، انقلها لـSUPERSEDED مع سبب التغيير.
- ميّز بوضوح بين قرارات مؤكدة، اقتراحات، نقاط قيد النقاش، نقاط لم تُحسم.
- لا تضع حوارًا كاملًا — معلومات لازمة فقط لفهم المشروع ومتابعته من قبل نموذج آخر.
- عند تعارض قرار جديد مع سابق، وضّح التعارض والقرار الأحدث.

---

## 11. أي تغييرات أو تحديثات طرأت على القرارات السابقة

- Core Loop: من PROPOSED Utility (أداة عند الحاجة) → مقترح Hybrid Utility (Find right reaction, discover next, share naturally) → **حاليًا DISCUSSION** بانتظار تحليل أرينا المفتوح. الصيغة السابقة محفوظة كـSUPERSEDED إذا اعتمد الجديد.
- BottomNav الرابعة: Submit (SUPERSEDED) → Collections (SUPERSEDED) → Saved (PROPOSED حاليًا).
- انبهار: من لون عاشر مستقل → أُلحقت بعائلة استغراب (SUPERSEDED).
- Brand v1.0: من دليل هوية أولي (YemReact-دليل-الهوية.md) → نسخة LOCKED نهائية (YemReact-Brand-v1.0-LOCKED.html) مع Watermark مُقوّى وقاعدة قلب الكتلة — النسخة الأولى تعتبر تاريخية عند التعارض.
- طريقة العمل: من تنفيذ مباشر (افتراض سابق) → مرحلة DISCUSSION محور بمحور، لا كود قبل اعتماد الخطة (ACCEPTED).

---

## 12. سجل زمني مختصر لأهم التطورات

- **البداية:** فكرة YemReact كـ"مكتبة رياكشنات يمنية" بديل محلي لـGiphy/Tenor، مع مفهوم "المثل الشعبي الرقمي" و"القُصاصة".
- **الهوية:** تطوير دليل هوية أولي → اختبار على 8 نماذج واقعية → تثبيت Brand v1.0 LOCKED (Qussasa, ألوان القشر, Lalezar/Cairo, Watermark مُقوّى).
- **المحتوى:** بناء Content System Launch Kit (9 خطوات، 3 طبقات تسمية، 3 أنواع ثابتة، 3 صيغ كتابة، Hashtag Strategy، أول 10 منشورات) + Production Guide + Asset Inventory + Bio/About Checklist — كلها READY.
- **المنتج:** كتابة Product Vision (مقارنة بدائل: مجلد شخصي/تيك توك/تيليجرام/Google-Giphy، تفوق أكيد مقابل Giphy فقط، الباقي مشروط بمكتبة كبيرة) + MVP Directive (نطاق إلزامي أ→د، مؤجل، مستبعد نهائيًا، قرارات معمارية نهائية Next.js+PostgreSQL+Prisma+R2+Stream+Vercel+Google Only، 3 نقاط معلقة).
- **التنظيم:** إنشاء هيكل 6 ملفات مرجعية (00-INDEX إلى 05-ARCHITECTURE) + Decisions Log + Open Questions.
- **التحليل:** كتابة phase_01_analysis_plan.md (7 محاور A-G، ترتيب منطقي، لا تنفيذ قبل حسم A→B→C).
- **جلسة مفتوحة:** تسليم session_analysis_open.md (20 نقطة، لا قرارات جديدة معتمدة).
- **قرار محور A (ثم إلغاؤه كأمر مغلق):** اقتراح Hybrid Utility + Brand LOCKED + Value Prop موسعة + Audience مرتب — ثم التراجع لطلب جلسة فهم مفتوحة أعمق.
- **التوقف الحالي:** بانتظار تحليل أرينا العميق لـ4 اتجاهات Core Loop (Utility-first, Social/Discovery-first, Hybrid, Content-library-first) مع أسئلة حاسمة، بدون اعتماد قرارات أو تحديث ملفات أو انتقال لمحور B.

---

## 13. ملاحظات جولة النقاش المتناوب — مع المستخدم (ليست معتمدة بعد)

**تاريخ:** 2026-09-07 — دورة مع المستخدم بعد دورة أرينا

**الجولة الأولى — إجابات المستخدم كملاحظات:**

- **س1 البحث:** المستخدم يعرف بنفسه ماذا يكتب. شريط البحث يكون مثل طريقة بنترست — تظهر اقتراحات تصحيح كلمات أو بحث ذو صلة أو مشابه عندما يكتب فقط.
- **س2 البحث أساسي أم جانبي:** جانبي — ليس الطريقة الأساسية للوصول.
- **س3 بداية الرئيسية:** مكتبة مرئية، ونجعل البحث ثنائي نفس طريقة بنترست.
- **س4 المجموعات:** ليست أساسية من البداية. يمكن للمسؤول إنشاء مجموعة وتبدأ بالظهور، وعندما ينشر رياكشن يظهر خيار اختياري لإضافته للمجموعات الموجودة.
- **س5 أقل شيء لإثبات الفكرة:** على نِبراس — اقترح مكتبة 30-50 + بحث جانبي + حفظ بدون حساب + صفحة تفاصيل برابط.
- **ملاحظة المقاس والمدة:** تبقى كملاحظة فقط — نكتبها الآن ونطبقها لاحقًا.
- **جوهر الفكرة:** مزيج — العثور والتصفح والاكتشاف معًا.

**الجولة الثانية — إجابات المستخدم الجديدة كملاحظات (بعد رد أرينا الثاني):**

- **س1 توجيه الزيارة الأولى:** سنفعل مثل كل المنصات فيسبوك وبنترست وغيرها — يكون هناك زر بحث بدون أن نفعل توجيه، هذا شيء معروف لا يحتاج توجيه، عندما أدخل أتصفح المكتبة أو إذا كنت فاهم ماذا أريد سوف أبحث بدون توجيه. (لا حاجة لعنصر توجيهي).
- **س2 المجموعات:** اتفق مع الملاحظة — المجموعات أداة للمسؤول فقط، تحتاج وقت حتى ينشئ أول مجموعة.
- **س3 المقاييس للمزيج:** اتفق مع الملاحظة — نحتاج أكثر من مقياس (تصفح، نجاح بحث، حفظ) كملاحظة.
- **س4 الهوية مع أي مقاس وأي مدة:** اتفق مع الملاحظة — الهوية ستبقى متماسكة لكن تحتاج مراجعة بصرية لاحقًا بدون تغييرها.
- **س5 الحد الأدنى والحفظ:** اتفق مع الملاحظة، ولكن مع تعديل مهم: عندما يضغط حفظ يلزمه تسجيل الحساب (مفتاح ربط تسجيل دخول جوجل فقط — سوف نناقش لاحقًا طريقة الحساب). أي الحفظ لم يعد بدون حساب، بل بحساب جوجل فقط.

**خلاصة المحور الأول (أ) كملاحظات مجمعة بعد موافقة المستخدم — مغلق كملاحظات:**

- جوهر الفكرة: مزيج — المكتبة المرئية أساس، البحث جانبي مساعد، الاكتشاف محدود.
- البحث: جانبي، المستخدم يعرف ماذا يكتب، نساعده باقتراحات مثل بنترست عند الكتابة فقط، بدون توجيه إضافي — زر بحث معروف مثل فيسبوك وبنترست.
- الرئيسية: مكتبة مرئية، البحث ثنائي بنفس طريقة بنترست.
- المجموعات: ليست أساسية، ينشئها المسؤول وتبدأ بالظهور، وعند النشر خيار اختياري للإضافة.
- الحد الأدنى: 30-50 فيديو حقيقي متنوع، مع بحث جانبي باقتراحات، مع حفظ يتطلب حساب جوجل فقط، وصفحة تفاصيل برابط حقيقي.
- المقاس والمدة: ملاحظة فقط — الفيديو ليس بمقاس محدد والمدة قد تصل لدقيقة — للمناقشة لاحقًا.
- الحساب: تسجيل دخول جوجل فقط — سنناقش لاحقًا.
- التوجيه: لا حاجة لتوجيه في الزيارة الأولى — زر البحث معروف.

**خلاصة المحور الثاني (ب) كملاحظات مجمعة بعد موافقة المستخدم — مغلق كملاحظات:**

- معنى المحتوى الجيد: الإبقاء على الستة معايير (تعبير واضح، مفهوم بذاته، موقف واضح، أصالة يمنية، جودة مقبولة، ملاءمة) + نقطة داخلية للتنوع + أداة قابلة للتطوير لهيكلة خوارزمية مستقبلًا.
- أنواع المحتوى: الإبقاء على الثلاثة مع تغيير الأولوية: عند الحاجة أولًا، مكتبة الأسبوع ثانيًا، اليومي ثالثًا ويمكن تأجيله.
- التصنيف: 9 فئات ثابتة كبيانات داخلية + كلمات مفتاحية مفتوحة كبيانات داخلية فقط للبحث الجانبي، بدون عرضها كفلتر للمستخدم. المجموعات أداة تنظيم للمسؤول فقط.
- مصدر المحتوى: جمع يدوي من المسؤول أولًا 30-50، ثم فتح المساهمات لاحقًا عند وجود دليل سلوكي (تم الاتفاق على المبدأ، التفاصيل الرقمية لم تُحسم بعد — ملاحظة).
- التنوع: تتبع داخلي فقط للتوازن، بدون فلتر للمستخدم.
- التكرار: تكرار الملف نفسه = رفض، نفس الموقف بأداء مختلف = قبول بشرط الأصالة.

**خلاصة المحور الثالث (ج) كملاحظات مجمعة بعد 3 جولات مع المستخدم وأرينا — مغلق كملاحظات مع تأجيل نقطة د:**

**أ) التنقل — تم:**
- البحث علوي فقط (زر عدسة في الشريط العلوي -> يظهر شريط كتابة -> عند البحث تظهر النتائج في صفحة منفردة /بحث)
- الشريط السفلي: الرئيسية، [زر مؤقت مكان البحث السفلي سيتغير لاحقًا لزر آخر]، المجموعات، الحساب — البحث السفلي ملغى ويستبدل لاحقًا
- زر مساهمة (+) للمستخدم يظهر الآن للجميع في الشريط العلوي — عند الضغط إذا لم يكن مسجلاً يطلب تسجيل جوجل فقط ثم يفتح نموذج مساهمة

**ب) المجموعات — تم:**
- أبسط شكل: قائمة بالمجموعات، كل مجموعة عنوان + عدد لقطات، عند الضغط تظهر لقطات المجموعة بنفس تنسيق المكتبة
- المجموعات أداة تنظيم للمسؤول فقط، المستخدم لا ينشئها، تظهر في التفاصيل كـ "موجود في: ..." إن وجدت فقط

**ج) إزالة الفئة نهائيًا من التفاصيل — تم:**
- الفئة مزالة نهائيًا من صفحة التفاصيل حتى كنقطة زينة — تبقى بيانات داخلية فقط للبحث الجانبي وتنظيم المسؤول

**د) توتر زر المساهمة — مؤجل للمحور التالي:**
- الخيار أ (زر يظهر لكن المحتوى لا يدخل حتى 30-50) = مرفوض من المستخدم — لا اتفق
- الخيار ب (زر يظهر + المحتوى يدخل بعد المراجعة + يدوي + مساهمات متزامنة) = قيد النقاش
- الحالة: مؤجل للمحور التالي (د) — تجربة التفاعل — مع اقتراح ثالث (ج): زر يظهر الآن + قائمة انتظار مبكرة + رسالة واضحة "ستبدأ المراجعة بعد اكتمال الأساسي 30-50" + حالة المساهمة في حساب المستخدم

**هـ) لوحة المسؤول — نعم:**
- 4 أقسام: رياكشنات (عرض وإدارة)، مجموعات (عرض وإدارة كألبومات: اسم + عدد + غلاف)، مساهمات (مراجعة 40/ساعة بنفس أداة 6 معايير + تنوع + كلمات مفتاحية قابلة للتطوير)، مسؤولين (إضافة مسؤول بصلاحيات محدودة: مراجعة مساهمات فقط، إدارة مجموعات فقط، إدارة كاملة بدون إضافة مسؤولين) — 3 صلاحيات

**و) التذييل — تعديل جديد:**
- خالي من القانونية (الشروط والخصوصية والأسئلة مؤجلة/ملغاة حسب طلب المستخدم)
- يحتوي: معلومات الموقع + خريطة الموقع + حسابات الموقع الاجتماعية + معلومات المطور — كملاحظة نهائية

**تفاصيل إضافية مؤكدة للمحور ج:**
- صفحة البحث المنفصلة: حقل كبير + اقتراحات عند الكتابة مثل بنترست + شبكة نتائج + حالة فارغة مشجعة — بدون فلاتر الآن (مؤجلة)
- صفحة تفاصيل الرياكشن: فيديو، عنوان + زر ثلاث نقاط على يسار الصفحة محاذاة العنوان (ترتيب داخلي: حفظ أولًا ثم تنزيل ثم نسخ رابط ثم مشاركة)، وصف أساسي، زر مطوي للوصف الثنائي يظهر فقط إذا وجد، مجموعات مرتبطة إن وجدت ثم فيديوهات قريبة — بدون فئة نهائيًا
- قائمة الحساب: منبثقة، صورة واسم من جوجل، محفوظات مع عدد ظاهر، مساهماتي بحالتها، تسجيل خروج — بدون إعدادات الآن
- الشريط العلوي: شعار + بحث + مساهمة (+) للمستخدم
- الشريط السفلي: الرئيسية، [زر مؤقت سيتغير]، المجموعات، الحساب

**الحالة الحالية:**
- المحور أ: مغلق كملاحظات (ليس قرارًا معتمدًا نهائيًا)
- المحور ب: مغلق كملاحظات (ليس قرارًا معتمدًا نهائيًا)
- المحور ج: مغلق كملاحظات (أ، ب، ج، هـ، و تم — د مؤجل للمحور التالي) — ليس قرارًا معتمدًا نهائيًا
- المحور د: التالي — تجربة التفاعل + نقطة د المؤجلة (توتر زر المساهمة)

---

## Stage 4R — Identity Compression — DECISION-4R01 — 2026-10-02

- **DECISION-4R01 — Identity Compression — Scope Correction — ACCEPTED 2026-10-02 — حمدان — 79 facts**
- Stage 4 تبقى CLOSED — Stage 4R مرحلة مستقلة — 5 محاور: Content · Quick Use · Search · Discovery · Visual
- Categories REJECTED (إزالة كاملة لا Staged A/B) + B-06 9 ألوان REJECTED معها — P-31 SUPERSEDED by P-47
- Watermark FROZEN حتى إغلاق Stage 8 (B-07 + P-38) — ليس DEFERRED
- Qussasa Mark (B-04/P-36) و Chip الشخصية (B-09/P-35) **ACTIVE بلا تغيير** — ظهورهما على البطاقة REMOVED / RE-AFFIRMED
- STATUS VOCABULARY (قاموس الحالات) أُضيف إلى CANONICAL-BASELINE — REJECTED-FINAL و STOPPED-UNTIL-COMPLETE مرفوضان
- العدّ: 79 → -1 (B-06) → +1 (P-47) → **79 facts**
- NEXT: انتظار إشارة فتح Stage 4R — Stage 5 / 5.1 Search Route لا يزال OPEN

## C-02 — Search Nature — DECISION-C02 — 2026-10-09

- **DECISION-C02 — Search Nature — Known-Item Only — ACCEPTED 2026-10-09 — حمدان — 80 facts**
- افتتاح سلسلة **C-xx — Content Axis (محور المحتوى)** — C-01 تعريف المحتوى اليمني (التالي) · C-02 CLOSED
- البحث = **بالتعرّف فقط** — 5 مداخل: العنوان · اسم الشخص · جملة محددة · وصف المشهد · الكلام المضمن
- **Situational Search (البحث بالموقف) مُلغى** كأسلوب مستقل — «الموقف» = Intent لا Mechanism
- ❌ لا حقل Use Case جديد — الوصف الأساسي + الثنائي (P-39)
- **P-48 NEW** · **P-14 SUPERSEDED** · **OPEN-Q-07 CLOSED**
- ⚠️ **P-01/P-09** («Search equal to browsing») تحت المراجعة → تُحسم في 5.1
- ⏸️ **P-20 #6** توسيع «يكتمل معناه بلا شرح» → DEFERRED to C-01
- العدّ: 79 → **80 facts**
- **5.1 Search Route** محسوم اتجاهًا: `?q=` — يبقى توثيقه الرسمي مطلوبًا
- NEXT: **C-01** · ثم استكمال Stage 5

## Stage 5 / 5.1 — Search Route — DECISION-5.1 — 2026-10-09 — CLOSED

- **DECISION-5.1 — Search Route — ACCEPTED 2026-10-09 — حمدان — 80 facts (لا فكت جديد)**
- سطح البحث = المكتبة: `/` المكتبة · **`/?q=` نفس المكتبة + فلتر** — البحث فلتر لا سطح مستقل
- `/search` → **redirect** إلى `/?q=` — لا صفحة منفصلة ولا محتوى مكرر
- **`noindex,follow`** عند وجود `q` — حماية من سيناريو Giphy (210,843 رابط محذوف) — SEO في IA-02 + P-34
- التنفيذ عند **Submit/Enter** لا as-you-type (P-15 — 10% جوال ضعيف) — Autocomplete محلي → **C-04**
- بحث **عالمي** من أي صفحة عدا `/admin` · `q` يبقى عند الرجوع من `/r/[code]` · Scroll Restoration → **Stage 7**
- **P-01 + P-09 → ✅ RESOLVED** — «Search equal to browsing» = **نفس السطح، نقطتا دخول** لا نفس الآلية
- ذيول: P-01 · P-09 · P-48 · T-02
- **5.1 CLOSED** — NEXT: 5.2 Bottom Nav أو C-01 (Stage 4R متوقف مؤقتًا عند C-01)

**ملاحظة لنموذج جديد يستلم هذا الملف:** اقرأ هذا الملف أولًا كاملًا قبل أي ملف آخر. إذا تعارض مع أي ملف قديم، هذا الملف هو الحقيقة الحالية. لا تعتبر أي PROPOSED كـACCEPTED إلا بعد تأكيد صريح من نِبراس عبر المستخدم. لا تكتب كودًا قبل اعتماد الخطة النهائية A→G. الملاحظات في القسم 13 ليست معتمدة بعد.


---

## CURRENT STATUS UPDATE — 2026-10-11 — Founder-approved

- **Stage 5.2:** CLOSED **for documentation only**, by explicit founder approval.
- **Next topic:** **C-01 — تعريف المحتوى اليمني (Content Axis)**. The deferred P-20 criterion #6 (“يكتمل معناه بلا شرح”) remains assigned to C-01.
- **Scope:** documentation and decision history only. No code, build, database changes, or claims of runtime verification.
- **Security:** SEC-06 was not audited as part of this closure and remains separate.
- **History:** earlier “Stage 5.2 OPEN / awaiting founder approval” statements remain as historical records and are superseded for current status by this dated update and the closure decision in YEMREACT-DECISIONS-LOG.md.
- Do not invent a Stage 5.3. Continue with C-01 unless Hamdan directs otherwise.
