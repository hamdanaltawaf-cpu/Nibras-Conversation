# YEMREACT-OPEN-QUESTIONS.md — Product Re-Foundation Open Questions

> أسئلة مفتوحة ناتجة عن قرارات Stage 1 — لا تحسم الآن — تُحسم في مراحلها حسب REFOUNDATION-ORDER
> كل سؤال يمر بـ HISTORY → EVIDENCE → DISCUSSION → DECISION في مرحلته

---

## من DECISION-001/002/003 — Product Definition — Video + Image + Flat Saves

### OPEN-Q-01 — البحث موحد vs منفصل للصور والفيديو

- **السؤال:** هل البحث عن الصور والفيديو موحد في نفس الحقل والنتائج، أم منفصل بفلتر نوع؟
- **Stage:** Stage 3 — Content & Editorial System (Content Model)
- **Depends on:** DECISION-002 Video+Image + PD-04 Rubric + PD-09/10 Categories/Collections
- **History:** S09 Search pg_trgm + ILIKE + keyset cursor يعمل على نص فقط — لا فرق نوع — S04 search includes all reactions
- **Evidence:** Canonical Baseline T-06 Search CURRENT — searchText column + normalizeArabic — لا يوجد type filter
- **Options:**
  - A) موحد — نفس البحث يرجع صور+فيديو مختلطة في Masonry
  - B) منفصل بفلتر — تبويب "الكل / فيديو / صور" أو filter chip
  - C) موحد افتراضيًا مع إمكانية فلترة لاحقة
- **Status:** OPEN — DEFERRED to Stage 3
- **Impact:** Search UI + Search API + ReactionCard + Metrics

### OPEN-Q-02 — Reaction Card مختلفة للصورة

- **السؤال:** هل بطاقة الرياكشن للصورة مختلفة بصريًا عن الفيديو (بدون زر تشغيل، مع Qussasa فقط، مع نسبة عرض مختلفة)؟
- **Stage:** Stage 4 — Experience & Identity
- **Depends on:** DECISION-002 + DECISION-001 Pinterest-like Masonry + PD-08 Aspect
- **History:** S05 UI Design System — ReactionCard موجود للفيديو مع play hole — S10 Brand Qussasa geometry — لا يوجد كارد صورة
- **Evidence:** P-02 UPDATED Video+Image equal — لكن لا يوجد spec للصورة
- **Options:**
  - A) نفس الكارد مع اختلاف أيقونة (صورة بدون play)
  - B) كارد مخصص للصورة (تكبير عند الضغط، بدون مشغل)
  - C) نفس الكارد تمامًا — الفرق فقط في Detail Page
- **Status:** OPEN — DEFERRED to Stage 4
- **Impact:** ReactionCard component + Masonry layout + Brand application

### OPEN-Q-03 — Watermark على الصور

- **السؤال:** هل نضع واترمارك على الصور؟ وما مواصفته (11% vs 14%، أعلى-يمين vs أسفل-يمين، بظل مزدوج vs بلا ظل)؟
- **Stage:** مؤجل — لا حاليًا — Stage 4 Experience + Stage 7 Technical
- **Depends on:** DECISION-002 + PD-14 Watermark spec + B-07 Watermark concept
- **History:** S10 Watermark concept تقشّر ورقي بزاوية + شعار + نسخة مقواة بظل مزدوج — S09 watermark/qs.png 200 + processor 14% bottom-right no shadow — CONFLICT-019 watermark spec 11% vs 14%
- **Evidence:** B-07 CONFIRMED concept لكن CONFLICTED exact spec — T-04 processor 14% bottom-right
- **Options:**
  - A) لا واترمارك على الصور حاليًا — أسهل تقنيًا وأسرع تحميل
  - B) نفس واترمارك الفيديو (Qussasa 11-14% + ظل مزدوج)
  - C) واترمارك مخفف للصور (أصغر، شفافية أقل)
- **Status:** OPEN — DEFERRED — لا حاليًا per قرار حمدان
- **Impact:** Media Pipeline + Brand + Performance

### OPEN-Q-04 — Media Pipeline للصور

- **السؤال:** كيف نعالج الصور تقنيًا (resize, compress, thumbnail, storage, delivery)؟
- **Stage:** Stage 7 — Technical Foundation
- **Depends on:** DECISION-002 + TD-01 Media infra + TD-04 Processing
- **History:** S09 Media pipeline local: validate MIME/size/magic bytes, storage.put LocalStorage ./storage, processor ffprobe/ffmpeg للفيديو فقط — لا يوجد pipeline للصور — S07 G1 media infra blocked prod
- **Evidence:** T-04 CURRENT local video pipeline + T-05 Media in production blocked — لا يوجد evidence للصور
- **Options:**
  - A) نفس pipeline الفيديو مع إضافة sharp للصور (resize ≤1080, WebP, thumbnail 480)
  - B) pipeline منفصل للصور (أبسط، بدون ffprobe)
  - C) استخدام خدمة مُدارة (Cloudflare Images / R2 + resizing)
- **Status:** OPEN — DEFERRED to Stage 7
- **Impact:** TD-01 + TD-04 + Storage + Cost

### OPEN-Q-05 — هل الصور تدخل نفس الفئات التسع؟

- **السؤال:** هل الصور تدخل نفس الفئات التسع (ضحك، صدمة، غضب، استغراب، إحراج/صمت، موافقة، رفض، سخرية، حماس) أم فئات منفصلة أو فرعية؟
- **Stage:** Stage 3 — Content & Editorial System
- **Depends on:** DECISION-002 + PD-09 Categories role + B-06 Category colors
- **History:** B-06 9 category colors CONFIRMED — S02/S10 Categories = Data Only 9 fixed — S03 Categories role filter vs data-only VERSION DRIFT — لا يوجد ذكر للصور في الفئات
- **Evidence:** B-06 CONFIRMED 9 colors — P-02 UPDATED Video+Image — لكن لا يوجد قرار هل الفئات تنطبق على الصور
- **Options:**
  - A) نفس الفئات التسع للصور والفيديو — موحد
  - B) فئات منفصلة للصور (ميمات، بوسترات، لقطات شاشة)
  - C) نفس الفئات + نوع محتوى كـ طبقة ثانية (فئة + نوع: فيديو/صورة)
- **Status:** OPEN — DEFERRED to Stage 3
- **Impact:** Content Model + Taxonomy + Search + Admin

### OPEN-Q-06 — الصور في نفس الشبكة أم قسم منفصل؟

- **السؤال:** هل الصور والفيديو في نفس شبكة Masonry أم في قسمين منفصلين أو تبويبين؟
- **Stage:** Stage 5 — Information Architecture & Navigation
- **Depends on:** DECISION-001 Pinterest-like Masonry + DECISION-002 Video+Image + IA-01 Home=Library
- **History:** IA-01 Home=Library ACCEPTED — S03 Home = library itself — S05 Masonry Mixed Aspect — لا يوجد فصل نوع في التاريخ
- **Evidence:** IA-01 CONFIRMED Home=Library — DECISION-001 Presentation Pinterest-like Masonry Grid visual only — لكن لا يوجد spec للخلط
- **Options:**
  - A) نفس الشبكة — صور وفيديو مختلطة — Pinterest الحقيقي
  - B) قسمين منفصلين — "فيديوهات" + "صور" — rail أو تبويب
  - C) نفس الشبكة افتراضيًا مع فلتر نوع اختياري
- **Status:** OPEN — DEFERRED to Stage 5
- **Impact:** IA + Navigation + Home composition + Search

### OPEN-Q-07 — طبيعة البحث في YemReact — البحث ليس "بالموقف" فقط

- **السؤال:** ما طبيعة البحث الحقيقية؟ هل المستخدم يبحث بالموقف فقط أم بأنواع أخرى؟
- **Stage:** Stage 5 — البحث والتنقل — DEFERRED per DECISION-007
- **Depends on:** DECISION-007 Value + DECISION-001 Search equal + T-06 Search pg_trgm + keywords
- **History:** افتراض سابق: "المستخدم يجي بموقف محدد مثل: لما صاحبي يكذب" — مصحح في DECISION-007 تصحيح 1 — المستخدم يبحث عن: اسم الرياكشن نفسه (مثال: مصطفى المومري)، اسم الشخص (مثال: هديل مانع)، جملة محددة (مثال: "اقرب اقرب لو انت رجال")، وصف المشهد (مثال: فيديو الذي يعد الرز)، الكلام المضمّن في الفيديو
- **Evidence:** DECISION-007 ACCEPTED — Value = منتقاة + قابلة للبحث + جاهزة — البحث ليس بالموقف فقط — لكن لا يوجد spec تفصيلي — T-06 Search pg_trgm + similarity + normalizeArabic + searchText + keywords 62 موجود
- **Options:**
  - A) بحث موقفي فقط — "لما صاحبك يقول بكرة" — ضيق
  - B) بحث متعدد الأنواع — اسم رياكشن + اسم شخص + جملة + وصف مشهد + كلام مضمن — واسع — يطابق تصحيح DECISION-007
  - C) بحث متعدد الأنواع مع أولوية — موقف أولًا، ثم اسم، ثم جملة، ثم وصف — يحتاج scoring
- **Status:** OPEN — DEFERRED to Stage 5 (البحث والتنقل) per DECISION-007
- **Impact:** Search UI + Search API + searchText + keywords + related + Collections + Metrics
- **Source:** DECISION-007 تصحيح 1

---

## من DECISION-007 — Value — تصحيحات وتأكيدات

### CONFIRMED — Library Size Target at Launch

- **Target:** 300-500 رياكشن قبل الإطلاق
- **Status:** CONFIRMED per DECISION-007 تصحيح 2
- **Stage:** Stage 3 Content — لكنه CONFIRMED كهدف إطلاق
- **Reason:** يلغي مشكلة "12 رياكشن" كعائق تقييم — لا نحتاج نعالج مشكلة مؤقتة — DB 12 كانت مؤقتة
- **Impact:** Content Pipeline + Admin + Media Pipeline + Search coverage + Launch threshold
- **Source:** DECISION-007

### DEFERRED — Keyword Tool

- **السؤال:** هل نحتاج Keyword Tool مرن يتطور لاحقًا إلى بنية خوارزمية؟ — S1 Axis B clarification
- **Stage:** Stage 3 (المحتوى) — DEFERRED per DECISION-007
- **Note:** لا تعتبر موافقة على C موافقة على Keyword Tool — قرار منفصل Content/Search Architecture
- **Status:** DEFERRED

### DEFERRED — Search Architecture التفصيلي

- **Stage:** Stage 5 (البحث والتنقل) — DEFERRED per DECISION-007
- **Includes:** OPEN-Q-07 + UX-01 Search route /?q= vs /search vs /بحث منفصلة + اقتراحات بنترست عند الكتابة فقط

### REJECTED — Percentages 70%/80%

- **Status:** سُحبت، لا نستخدمها — لا أساس موثق — REJECTED per DECISION-007

### REJECTED — Validation Framework 4 أسابيع

- **Status:** لا نحتاجها — نحن في مرحلة إعادة تأسيس نبني الأفضل ثم نطلق — REJECTED per DECISION-007

---

## ملاحظات عامة

- كل هذه الأسئلة ناتجة عن DECISION-002 Video+Image + DECISION-007 Value — لا تحسم الآن حتى لا نقفز
- كل سؤال سيمر بقالب البروتوكول كاملًا في مرحلته: HISTORY → EVIDENCE → DISCUSSION → DECISION
- لا شيء يصبح قرارًا إلا بتم صريح من حمدان
- DECISION-007 أغلق PD-03 — Value = منتقاة + قابلة للبحث + جاهزة للاستخدام الفوري — OPEN-Q-07 جديد — Library Size Target 300-500 CONFIRMED
- DECISION-008 أغلق PD-20 — Audience أي شخص في موقف + Signals 3 + Acquisition مراقبة فقط + Trial Phase + Team Structure — Stage 2 CLOSED
- DECISION-009 أغلق PD-04 — Rubric 6 معايير نهائية — OPEN-Q-08 Keyword Tool منفصل + OPEN-Q-09 استخراج كلام + DECISION-010 Report Button

---

## من DECISION-008 — Audience + Signals + Trial Phase + Team — Stage 2 CLOSED

### CONFIRMED — Audience

- **الأساسي:** أي شخص في موقف يحتاج رياكشن يرد به — أول فكرة YemReact — العمر تركيز شباب غير محدد — المنصة ما نحدد — اللغة لهجة يمنية — الجهاز جوال متوسط 30% قوي 10% ضعيف
- **الثانوي:** صناع ميمز، طلاب، أصحاب صفحات
- **Status:** ACCEPTED — DECISION-008 — Stage 2 CLOSED
- **Rejected:** "واتساب يمني" كوصف وحيد — استُبدل بـ "أي شخص في موقف" — REJECTED per DECISION-008
- **Source:** DECISION-008

### CONFIRMED — Directional Signals 3 فقط

- **Signals:** 1) هل لقى اللي يدور عليه؟ (بحث وجد vs فاضي) 2) هل استخدمه؟ (نزّل/نسخ/شارك/حفظ) 3) هل رجع؟ (كوكي مجهول خلال أسبوعين) — مؤشرات اتجاه وليست أهداف — بدون أرقام — بدون KPIs رسمية — بدون Validation Framework 4 أسابيع
- **Status:** ACCEPTED — DECISION-008 — Stage 2 CLOSED
- **Rejected:** 7 مؤشرات → 3 فقط — "المكتبة تكبر" كمؤشر منتج → مؤشر إنتاج — Percentages 70%/80% → REJECTED — Validation 4 أسابيع → REJECTED
- **Source:** DECISION-008

### CONFIRMED — Acquisition

- **Details:** ما نفترض قناة — نراقب فقط: مباشر + مشاركة /r/[code] + بحث جوجل + موقع آخر (فيسبوك، تويتر، الخ) — لا نفترض SEO/Facebook هي القناة النهائية
- **Status:** ACCEPTED — DECISION-008
- **Source:** DECISION-008

### CONFIRMED — Trial Phase قبل الإطلاق — Arena-Agent

- **Details:** Arena-Agent يتولاها — إصلاح BUG-1 Event tracking + رفع 300-500 رياكشن + اختبار داخلي شامل + ثم الإطلاق الرسمي — لن تكون هناك مرحلة إصلاح BUG-1 منفصلة
- **Status:** CONFIRMED — DECISION-008
- **Source:** DECISION-008 — P-18

### CONFIRMED — Team Structure

- **Details:** 👑 حمدان Founder → 🧠 نِبراس Product Discussion → 📜 Blueprint → 🏗️ Arena-Agent Implementation
- **Status:** CONFIRMED — DECISION-008 — P-19
- **Source:** DECISION-008

---

## من DECISION-009 — Rubric — Stage 3 — PD-04 — 6 معايير + OPEN-Q-08/09 + Report Button

### DECISION-009 — Rubric 6 معايير نهائية — ACCEPTED — CLOSED

- **المعايير:**
  1) نظافة فنية: وضوح كامل + صوت نظيف (فيديو) + صورة نقية (صورة) + أول إطار=بداية + لا Bumper/لوجو غريب
  2) هوية يمنية: لهجة يمنية أو سياق يمني أو شخص يمني معروف
  3) أخلاقي: لا إساءة، لا تحقير، لا تنمر، لا محتوى غير لائق
  4) بياناته جاهزة: اسم لو معروف + اسم شخص + جملة/كلام مضمن + وصف مشهد + كلمات مفتاحية أساسية + استخراج تلقائي OPEN-Q-09
  5) تنوع: جديد ليس متكرر
  6) جاهز للاستخدام: بدون قص/تحرير — خذها. حطها.
- **من يقرر:** حمدان أساسي + أي أدمن لاحقًا — نفس المعايير في الحالتين (أدمن يرفع بنفسه أو مستخدم يرسل مساهمة → قبول/رفض)
- **Status:** ACCEPTED — PD-04 CLOSED
- **Source:** DECISION-009

### OPEN-Q-08 — Keyword Tool منفصل — DEFERRED

- **Topic:** أداة كلمات مفتاحية مرنة تتطور لخوارزمية — S1 Axis B clarification — أداة حتى نكون قادرين على تطويره فيما بعد حتى نكون هيكله خوارزميه للموقع كامل
- **Status:** DEFERRED → Stage 3 (Topic لاحق) أو Stage 5 (IA/Search) — منفصل تمامًا عن PD-04 per DECISION-009 تعديل 4
- **Depends on:** DECISION-009 Rubric + P-14 Search Nature + OPEN-Q-07 + S1 Axis B
- **Impact:** Content Model + Search + Related + Collections + Admin
- **Source:** DECISION-009 + S1 Axis B

### OPEN-Q-09 — استخراج الكلام تلقائي — DEFERRED — Flow معتمد خيار 2

- **Topic:** أداة تلقائية تستخرج الكلام من الفيديو — مجانية إلزامي — تخدم اللهجة اليمنية (تحدي قد نحتاج هجين)
- **Flow المعتمد (خيار 2):**
  1. الأدمن يرفع الفيديو
  2. يظهر خيار "استخراج الكلام"
  3. الأدمن يضغط → المعالجة تشتغل
  4. النص يظهر للأدمن قبل النشر
  5. الأدمن يعدّل ويصحّح
  6. ثم ينشر
- **متطلبات:** مجانية إلزامي + تخدم لهجة يمنية + اختيار الأداة المحددة → Stage 7
- **المخرجات:** النص يظهر في "الوصف الثنائي" + يُستخدم في البحث + قابل للتعديل
- **Status:** DEFERRED → Stage 3 (البيانات) / Stage 7 (الأداة)
- **Depends on:** DECISION-009 Rubric معيار 4 + P-14 Search Nature + OPEN-Q-07 + T-04 Media pipeline
- **Impact:** Content + Search + Reaction Detail + Admin + Media Pipeline + Cost
- **Source:** DECISION-009

### DECISION-010 — Report Button — إضافة زر "إبلاغ" — ACCEPTED

- **Topic:** إضافة زر "إبلاغ" داخل قائمة الثلاث نقاط في الرياكشن
- **قائمة الثلاث نقاط النهائية:** حفظ + تنزيل + نسخ رابط + مشاركة + إبلاغ (جديد) — CONFIRMED
- **كيف يشتغل:** يضغط "إبلاغ" → يختار السبب (محتوى غير لائق، إساءة لشخص، حقوق ملكية، محتوى مضلل، سبب آخر نص حر) → يُرسل للأدمن → الأدمن يراجع → يقرر (إبقاء/حذف/تعديل)
- **التنفيذ:** UI الزر → يُسجل الآن، يُنفذ Stage 4/6 — Backend → Stage 8 Legal & Compliance
- **Status:** ACCEPTED — CONFIRMED — UI Stage 4/6 + Backend Stage 8
- **Source:** DECISION-009 + DECISION-010

### CONFIRMED — حذف "قانوني" من Rubric

- **Status:** Legal تم إخراجه من Rubric — المسؤولية القانونية تُعالج في Stage 8 — آلية إبلاغ (Report) + Takedown + شروط — CONFIRMED per DECISION-009

### REJECTED — من PD-04

- "قانوني" كمعيار في Rubric — REJECTED per DECISION-009
- "40 في الساعة" كرقم مستهدف — REJECTED per DECISION-009 — لا أرقام مستهدفة
- "7 معايير" — نبقى 6 — REJECTED per DECISION-009
- Keyword Tool داخل Rubric — REJECTED per DECISION-009 — منفصل OPEN-Q-08
- "تنوع بقواعد معقدة" — REJECTED per DECISION-009 — مبسط: جديد ليس متكرر
