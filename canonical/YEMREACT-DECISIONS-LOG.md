# YEMREACT-DECISIONS-LOG.md — Product Re-Foundation Decisions Log

> سجل القرارات النهائية المعتمدة من حمدان — كل قرار يمر بـ Previous → New → Reason → Alternative → Impact → Stage
> مصدر السلطة الوحيد: حمدان (Founder) — رأي نِبراس أو أي وكيل ليس قرارًا
> الحالة: ACCEPTED فقط بعد كلمة "تم" صريحة

---

## DECISION-001 — Product Definition — ACCEPTED

- **Status:** ACCEPTED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-12 — Stage 1 — Product Definition
- **Topic:** ما هو YemReact؟

**Previous → New:**

- **Previous:** Product = تعريف متعارض في الكود نفسه:
  - package.json / layout metadata: "Yemeni visual reaction search engine" (محرك بحث)
  - hero eyebrow / header caption: "مكتبة رياكشنات يمنية" (مكتبة)
  - Vision Synthesis S02: "مكتبة رياكشنات يمنية مصنفة مسبقاً قابلة للبحث، جاهزة للاستخدام الفوري"
  - Core Loop متعارض: utility vs discovery vs hybrid (CONFLICT-001, CONFLICT-036)

- **New:** 
  ```
  YemReact = مكتبة رياكشنات يمنية مصنفة مسبقًا، قابلة للبحث وللاستخدام الفوري.
  - المحتوى: فيديو + صور — متكافئان
  - العرض: Pinterest-like (Masonry Grid) — الشكل فقط
  - الحفظ: Flat Saves — قائمة موحدة بدون Boards
  - الشبكة الاجتماعية: مرفوضة
  - البحث: متكافئ الأهمية مع التصفح
  - الاكتشاف: محدود (رياكشنات قريبة + مجموعات الأدمن إن وُجدت)
  - الاسم: "يمن رياكت / YemReact" يبقى كما هو
  English: A curated, searchable Yemeni reaction library — ready to use.
  Content: Video + Image — equal. Presentation: Pinterest-like Masonry Grid (visual only).
  Saves: Flat Saves — no user Boards. Social: Rejected. Search: Equal to browsing. Discovery: Limited.
  ```

- **Reason:**
  1) يحل CONFLICT-001 (search engine vs library) و CONFLICT-036 (utility vs discovery) بقرار واحد
  2) يطابق ملاحظات Axis A الأخيرة: "المكتبة المرئية أساس، البحث جانبي مساعد، مزيج العثور والتصفح والاكتشاف"
  3) يطابق سلوك المستخدم اليمني: يعرف ما يريد فيبحث بدون توجيه، أو يتصفح ليكتشف
  4) يعمل مع 30-50 فيديو/صورة (مكتبة صغيرة قابلة للتصفح) ويتحسن مع 150-300
  5) يحافظ على P-03 No social feed REJECTED و B-02 Reaction = المثل الشعبي الرقمي و B-03 "خذها. حطها. يمنية."

- **Alternative rejected:**
  - A) Search Engine First فقط — يفشل مع 30-50 (نتائج فارغة كثيرة)، يتجاهل سلوك التصفح
  - B) Library First فقط — يضعف وعد السرعة "ألاقي المناسب بأسرع طريقة"
  - D) Pinterest كامل (شبكة اجتماعية) — مخالف P-03 صريح

- **Impact:**
  - Product: يعيد تعريف PD-01 + PD-02 Core Loop + PD-03 Value + PD-20 Metrics
  - IA: يؤكد IA-01 Home=Library، يفتح UX-01 Search route و UX-02 BottomNav و PD-09/10 Categories/Collections
  - Content: يفتح PD-04 Rubric + PD-07 Duration + PD-08 Aspect + PD-09/10 + DECISION-002 Video+Image
  - Technical: يؤثر على TD-01 Media infra + TD-02 Storage + Search pg_trgm + Watermark
  - Brand: لا يغير Brand v1.0 LOCKED كأساس، لكن يوسع تطبيق الهوية على نوعين محتوى

- **Stage:** Stage 1 — Product Definition — يفتح كل المراحل 2-8
- **Evidence:** CONFLICT-001, CONFLICT-036, U-01, U-02, S02 Vision, S10 Brand, S08 Discussion, Axis A notes
- **Status in Canonical:** سيدخل كـ P-01 UPDATED + B-08 Name stays

---

## DECISION-002 — Video + Image — ACCEPTED

- **Status:** ACCEPTED
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 1

**Previous → New:**

- **Previous:** P-02 (Video only — static images rejected) — CONFIRMED في Canonical Baseline القديم:
  - S02, S06, S10 explicitly reject Pinterest static
  - S04 MVP excludes static
  - 12 مصدر تاريخي تعتبر الصور مرفوضة كمنتج

- **New:** فيديو + صور — نوعا محتوى متكافئان — كلاهما منتج أساسي

**Reason:**
1) "رياكشن" في الوعي اليمني يشمل الصور والفيديو معًا (ميمات ثابتة، بوسترات رياكشن، لقطات شاشة)
2) جمهور Pinterest-like يتوقع رؤية صور — الشكل البصري Masonry يتطلب تنوع أطوال
3) UX: المستخدم يفهم المحتوى بسرعة من الصور (أخف، أسرع تحميل في شبكة يمنية بطيئة)
4) لا يخالف P-03 No social feed — الصور كمحتوى لا تعني شبكة اجتماعية
5) يفتح قيمة جديدة: تغطية مواقف أكثر بدون الحاجة لتصوير فيديو

**Alternative rejected:**
1) الفيديو فقط — مقيد، يخالف طبيعة Pinterest-like ويقلل التغطية الموقفية
2) الصور فقط — يضيع قيمة الفيديو (الحركة والصوت هي جوهر الرياكشن اليمني)
3) الصور كـ thumbnails فقط — مؤجل للدراسة، لكنه يقلل من قيمة الصور كرياكشن مستقل
4) Pinterest كامل (شبكة اجتماعية مع Boards و Follow) — مرفوض، يخالف P-03 صريح

**Impact:**
- Product Definition: يوسع تعريف المنتج من video library إلى visual library
- Content Model: يفتح OPEN-Q-01/05/06 — هل الصور تدخل نفس الفئات التسع؟ هل البحث موحد؟ هل الشبكة واحدة؟
- Reaction Card: يحتاج تصميم مختلف للصورة (بدون play button، مع Qussasa فقط؟) → Stage 4
- Reaction Detail: فيديو مع مشغل vs صورة ثابتة مع تكبير → Stage 6
- Media Pipeline: فيديو يحتاج ffprobe/ffmpeg/watermark 14% vs صورة تحتاج resize/compress/watermark مختلف → Stage 7 TD-04
- Search: pg_trgm + similarity يعمل على نص فقط، لكن الصور تحتاج نفس البحث الموقفي → Stage 3
- Categories: هل الصور تدخل نفس 9 فئات أم فئات فرعية؟ → Stage 3
- Watermark: واترمارك الفيديو معتمد 11% vs 14%، لكن واترمارك الصور غير محدد → OPEN-Q-03 مؤجل
- Admin: مراجعة صور أسرع من فيديو، لكن نفس Rubric 6 معايير → Stage 6

**Stage:** Stage 1 — Product Definition — يؤثر على Stage 3 Content & Stage 4 Experience & Stage 5 IA & Stage 7 Technical

**Supersedes:** P-02 القديم (Video only) — يصبح P-02 UPDATED: Video + Image equal

---

## DECISION-003 — Flat Saves — ACCEPTED

- **Status:** ACCEPTED
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 1

**Previous → New:**

- **Previous:** لا يوجد نظام حفظ ثابت كقرار منتج — 6D بنى Flat Saves في الكود (SavesProvider + localStorage yr:saved + union مع /api/me/saves) لكن لم يُحسم كقرار منتج — كان PROPOSED في S03/S08 مع توتر Saved vs Submit vs Collections في BottomNav

- **New:** Flat Saves — قائمة موحدة لكل مستخدم، بدون Boards — كل رياكشن محفوظ يذهب لقائمة واحدة مرتبة زمنيًا

**Reason:**
1) 30-50 رياكشن لا يحتاج تنظيمًا — Boards over-engineering في المرحلة الحالية
2) UVP = "خذها. حطها." ليس تنظيم — القيمة هي الأخذ السريع والاستخدام، لا التصنيف الشخصي
3) لا التباس مع Collections (admin-scoped) — Collections هي مجموعات الأدمن (طلاب، قروب، بلا سياق) وليست Boards شخصية
4) لا Schema change — SavedReaction موجود (2 rows YR-0011) + localStorage union يعمل — لا حاجة لـ Board table جديدة
5) لا خطر Social Creep — Boards قد تتحول لـ Profile public + Follow + Likes → يخالف P-03
6) Pinterest-like = الشكل البصري فقط (Masonry Grid) وليس الشبكة الاجتماعية

**Alternative rejected:**
- A+Boards — over-engineering في المرحلة الحالية — يحتاج Board table + BoardItem + UI إنشاء/تعديل/حذف + مشاركة Boards → يعقد MVP بدون قيمة مثبتة — مؤجل لما بعد إثبات Product-Market Fit مع Flat Saves

**Impact:**
- Product: يؤكد P-06 Save is core CTA — "خذها. حطها." — بدون تعقيد
- IA: يوضح أن Collections ≠ Saves — Collections = مجموعات أدمن في /مجموعات كألبومات، Saves = قائمة شخصية في /saved أو Account sheet
- Technical: لا تغيير على 6D، لا Schema change، فقط توثيق — SavesProvider الحالي يبقى
- UX: AccountMenu يظهر عدد المحفوظات بجانب الكلمة — بسيط
- Growth: Flat Saves أسرع للاستخدام المتكرر — mental availability بدون تنظيم

**Stage:** Stage 1 — Product Definition — يؤكد قرار سابق في الكود كقرار منتج نهائي

---

## REJECTED — مرفوضات مؤكدة في هذا الموضوع

- Pinterest كامل (D) — شبكة اجتماعية مع Boards شخصية + Follow + Feed خوارزمي — مخالف P-03 (No social feed) — REJECTED
- Boards الشخصية للمستخدم — over-engineering — REJECTED في المرحلة الحالية (قد يُعاد النظر بعد PMF)
- Trending / Likes / Comments / Followers / Infinite Feed / Leaderboard / Notifications "فلان أعجب" — كما في P-03 — REJECTED
- Video Intro/Outro Bumper — REJECTED كما في P-04

## CONFIRMED — مؤكدات في هذا الموضوع

- B-XX (جديد): اسم المنتج "يمن رياكت / YemReact" يبقى كما هو رغم توسعة المحتوى من فيديو فقط إلى فيديو+صورة — CONFIRMED
- IA-01: Home = Library — يبقى مؤكدًا ضمن التعريف الجديد — CONFIRMED
- P-06: Save is core CTA — يبقى مؤكدًا — CONFIRMED
- B-01 to B-07: Brand v1.0 LOCKED + Qussasa + Reaction=مثل شعبي رقمي + "خذها. حطها. يمنية." — تبقى CONFIRMED (لا شيء مقدس مطلقًا لكن لم يُقترح تغييرها في هذا الموضوع)

---

---

## DECISION-004 — Core Loop — ACCEPTED

- **Status:** ACCEPTED
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 1 — PD-02
- **Topic:** ما هي الحلقة الأساسية؟

**Previous → New:**

- **Previous:** Core Loop متعارض:
  - S10 PROPOSED Utility-first (أداة عند الحاجة، mental availability)
  - S08 tension: Utility-first "ادعاء كبير يستاهل اعتراضًا صريحًا" vs Discovery-first vs Hybrid Utility "Find right reaction, discover next, share naturally" DISCUSSION
  - S02 Search→Preview→Take
  - S11/S12 Hybrid library/search/share

- **New:** Hybrid — 5 خطوات داخل الجلسة + Outcome خارج الحلقة:
  ```
  Core Loop (in-session):
  1) Open — يفتح المستخدم YemReact
  2) Enter — نقطة دخول مزدوجة متكافئة:
     - Browse: تصفح المكتبة المرئية (Masonry) — للزيارة الأولى
     - Search: بحث موقفي — عند وجود حاجة
     الاثنان متكافئان — لا أحدهما مهيمن
  3) Understand & Choose — صفحة التفاصيل /r/[code]:
     - فيديو/صورة + وصف أساسي
     - وصف ثنائي مطوي (يظهر فقط إن وُجد)
  4) Save / Share / Use — Flat Saves + تنزيل + نسخ رابط + مشاركة
  5) Discover similar — محدود:
     - رياكشنات قريبة: 10 initial، + Load More 10، الحد الأقصى 50 حسب الصلة
     - مجموعات الأدمن إن وُجدت كبطاقة واحدة
     - بدون feed لا نهائي

  OUTCOME (post-session):
  → Return when need (mental availability)

  English:
  1) Open
  2) Enter — Browse OR Search — equal
  3) Understand & Choose — /r/[code]
  4) Save / Share / Use — Flat Saves + download + copy + share
  5) Discover similar — limited (10 initial, Load More, max 50 by relevance)
  Outcome: Return when need

  DEFERRED DETAILS (ليست جزءًا من Core Loop، تُحسم لاحقًا):
  - "حفظ بـ Google فقط" — تفصيل Auth/Save → Stage 6
  - "بدون تصنيف ظاهر" — تفصيل وصف/تصنيف → Stage 3/6
  ```

**Reason — القرار النهائي vs رأي المراجعة:**

- **قرار نهائي مدعوم:** 
  1) DECISION-001 ACCEPTED — Product Definition هو Hybrid (Library + Search equal + Discovery limited + Flat Saves + Pinterest visual only) — Core Loop يجب أن يتماشى معه
  2) يحل CONFLICT-036 (Core Loop) — توتر S08 بين utility vs discovery vs hybrid
  3) يحل CONFLICT-001 جزئيًا — Product Definition Hybrid يحتاج Core Loop Hybrid

- **رأي/تحليل المراجعة (ليس قرارًا):**
  - "مزيج العثور والتصفح والاكتشاف" — من Axis A الأخير — تحليل يدعم Hybrid لكنه ليس دليلًا نهائيًا
  - يعمل مع 30-50 و150-300 — تقدير حجم مكتبة — يحتاج قرار PD-06 لاحقًا
  - ملاحظة: لا infinite feed — مستند إلى P-03 REJECTED Infinite Feed + DECISION-001 Discovery limited — لكن P-03 يرفض Infinite Feed كميزة، لا يرفض Discovery-first كمفهوم كامل — التمييز مهم

**Alternative rejected — مصحح:**

- A) Utility-first الخالص — PROPOSED سابقًا في S10 — تم رفضه كحل وحيد لأن Product Definition اعتُمد Hybrid في DECISION-001 — Utility-first وحده لا يحقق نقطتي دخول متكافئتين (Browse + Search) اللتين اعتمدتا في DECISION-004 — ليس لأنه "لا يبرر Flat Saves" — Flat Saves قرار مستقل DECISION-003
- B) Discovery-first الخالص — كان مطروحًا في S08 — تم رفضه كحل وحيد لأنه يركز على التصفح فقط بدون مساواة البحث — DECISION-001 اعتمد Search equal to browsing — Discovery-first وحده لا يحقق المساواة — أما مسألة مخالفة P-03، فـ P-03 يرفض Trending/Likes/Comments/Followers/Infinite Feed كميزات محددة، وليس فكرة التصفح نفسها — لذا لا نسجل "يخالف P-03" كادعاء عام بدون تفصيل

**Impact:**
- Product: يحسم PD-02 + يفتح PD-03 Value vs Screen Record + PD-20 Metrics مزيج Search Success Rate + Save Rate
- IA: Home = مكتبة مرئية + بحث في الهيدر متكافئ — Search route Stage 5 — BottomNav Stage 5
- Content: Rubric 6 معايير + تنوع + كلمات مفتاحية مرنة تتطور لخوارزمية (S1 Axis B) — Pipeline Option C 30-50 أولًا
- Technical: Search pg_trgm يبقى + اقتراحات بنترست عند الكتابة فقط — Media Pipeline فيديو+صورة — Event tracking يحتاج إصلاح BUG-1 لقياس Metrics — Flat Saves union يبقى
- Growth: Facebook launch 30-50 + بحث جانبي + حفظ بجوجل فقط + تفاصيل برابط — لا Viral Loop حقيقي — Watermark كقناة توزيع

**Stage:** Stage 1 — PD-02 — يفتح Stage 2 Audience & Value و Stage 3 Content
**Evidence:** DECISION-001, DECISION-002, DECISION-003, P-06 Save core CTA, IA-01 Home=Library, P-03 No social feed, CONFLICT-036, U-02, Axis A notes

---

## DECISION-005 — Return as Outcome — ACCEPTED

- **Status:** ACCEPTED
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 1 — PD-02

**Previous → New:**

- **Previous:** Return when need كان يُعتبر خطوة داخل Core Loop في بعض المصادر (S10 utility: Open → Search → Take → Return) — غير واضح هل هو خطوة أم نتيجة

- **New:** Return when need خارج Core Loop — هو Outcome (post-session) — نتيجة الحلقة، ليست خطوة داخلها
  - Core Loop = داخل الجلسة فقط (5 خطوات قابلة للقياس)
  - Return = نتيجة — تقاس على مستوى أسابيع/أشهر — Metric منفصل: Retention (mental availability)

**Reason:**
1) Core Loop يجب أن يكون قابلًا للقياس داخل الجلسة (Open → Enter → Understand → Save/Share/Use → Discover) — Return لا يمكن قياسه داخل نفس الجلسة
2) يتوافق مع مفهوم mental availability vs daily habit — المستخدم لا يعود يوميًا، يعود عند الحاجة — هذا Retention وليس Engagement Loop
3) يفصل Metrics: In-session Metrics (Search Success Rate, Save Rate, Share Rate) vs Post-session Metrics (Return Rate, Mental Availability)

**Alternative rejected:**
- Return كخطوة داخل Core Loop — يخلط بين ما يحدث داخل الجلسة وما يحدث بعدها — يصعب قياسه

**Impact:**
- Metrics: PD-20 يصبح مزيج In-session (Search Success + Save + Share) + Post-session (Return when need)
- Product: يوضح أن YemReact ليس تطبيق عادة يومية — هو أداة تذكر وقت الحاجة
- Growth: لا نحتاج Daily Active Users — نحتاج Mental Availability — "هل تذكرت YemReact عندما احتجت رياكشن؟"

**Stage:** Stage 1 — PD-02

---

## DECISION-006 — Discover similar محدود — ACCEPTED

- **Status:** ACCEPTED
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 1 — PD-02

**Previous → New:**

- **Previous:** "رياكشنات قريبة" غير محددة العدد في S03/S04/S10 — "مجموعات مرتبطة إن وجدت فقط ثم فيديوهات قريبة" في Axis C — لا يوجد حد

- **New:** Discover similar محدود:
  - Initial load: 10 رياكشن قريب حسب الصلة
  - Load More: 10 إضافية عند الضغط
  - Max: 50 — الحد الأقصى حسب الصلة
  - الترتيب: حسب الصلة (similarity + keywords + category + collections)
  - مجموعات الأدمن إن وُجدت تظهر كبطاقة واحدة (ليست re-feed) — عنوان+عدد
  - بدون feed لا نهائي — لا infinite scroll

**Reason:**
1) أداء على 3G — 10 أخف من 50 — يمني مع شبكة بطيئة
2) UX — لا يشتت المستخدم — 10 كافية للاختيار، 50 لمن يريد التعمق
3) يتوافق مع "الاكتشاف المحدود" في DECISION-001 — Discovery limited
4) يسمح للمستخدم بالتعمق حسب رغبته (Load More) بدون إجباره على feed لا نهائي
5) يحافظ على P-03 No infinite feed REJECTED

**Alternative rejected:**
- Discover similar غير محدود (Infinite Feed) — يخالف P-03 + DECISION-001 Discovery limited — يشتت المستخدم — أداء سيء على 3G
- مسار مختلف للصور vs الفيديو داخل Discover — REJECTED — DECISION: مسار موحد للصور والفيديو في Core Loop (CONFIRMED)

**Impact:**
- IA: صفحة التفاصيل /r/[code] — فيديو/صورة + وصف + ثلاث نقاط + مجموعات إن وجدت + قريبة 10 + Load More حتى 50
- Technical: Related query يحتاج limit 10 + offset + max 50 — similarity scoring — لا infinite scroll
- Content: يحتاج كلمات مفتاحية + فئات + مجموعات لحساب الصلة — يفتح OPEN-Q-01/05/06
- Performance: 10 initial أفضل لـ 3G — Load More اختياري

**Stage:** Stage 1 — PD-02 — يؤثر على Stage 5 IA و Stage 6 Core Flows

---

## REJECTED — مرفوضات Topic 2 — مصحح

- Utility-first الخالص كحل وحيد — رُفض لأن DECISION-001 اعتمد Hybrid (Library + Search متكافئان) — Utility-first وحده لا يحقق نقطتي دخول متكافئتين — ليس لأنه "لا يبرر Flat Saves" — Flat Saves قرار مستقل DECISION-003
- Discovery-first الخالص كحل وحيد — رُفض لأنه يركز على التصفح فقط بدون مساواة البحث — DECISION-001 اعتمد Search equal — أما P-03 فيرفض ميزات محددة (Trending/Likes/Comments/Followers/Infinite Feed) وليس فكرة التصفح نفسها — لذا لا نسجل مخالفة عامة لـ P-03
- Return كخطوة داخل Core Loop — أصبح Outcome خارج الحلقة — DECISION-005
- Discover similar غير محدود (Infinite Feed) — رُفض لأن DECISION-001 اعتمد Discovery limited + DECISION-006 حدد 10 initial + Load More max 50 — يتوافق مع P-03 REJECTED Infinite Feed كميزة محددة
- مسار مختلف للصور vs الفيديو داخل Core Loop — REJECTED — مسار موحد CONFIRMED — جزء من DECISION-004

## CONFIRMED — مؤكدات Topic 2 — مصحح

- مسار موحد للصور والفيديو في Core Loop — CONFIRMED — DECISION-004
- Flat Saves يبقى core CTA (P-06) — CONFIRMED — DECISION-003
- Search + Browse متكافئان — نقطتا دخول مزدوجة — CONFIRMED — DECISION-004
- Home = Library يبقى مؤكدًا ضمن Hybrid — CONFIRMED — IA-01 + DECISION-001
- Name stays "يمن رياكت / YemReact" — CONFIRMED — DECISION-001
- DEFERRED DETAILS: "حفظ بـ Google فقط" و "بدون تصنيف ظاهر" — ليست جزءًا من Core Loop — تُحسم في Stage 3/6

## Topic 2 — CLOSED — نهائي

- DECISION-004/005/006 ACCEPTED كما هي — مع تصحيح توثيقي يحذف تفاصيل لم تعتمد كقرار Product
- النتيجة النهائية المحفوظة:
  - Hybrid
  - Browse + Search كنقطتي دخول متكافئتين
  - Understand & Choose
  - Save / Share / Use
  - Discover Similar محدود: 10 أولية + Load More حتى 50
  - Return when need = Outcome وليس خطوة

## التالي — بعد Topic 2 — CLOSED

- تحديث Canonical Baseline بـ DECISION-004/005/006 مع التصحيح
- فتح Topic 3: PD-03 — Value vs Screen Record — Stage 2

---

## DECISION-007 — Value — ACCEPTED — Stage 2 — PD-03

- **Status:** ACCEPTED — CLOSED
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 2 — PD-03 — Value vs Screen Record
- **Topic:** ما القيمة الأساسية التي تجعل المستخدم يختار YemReact بدل Screen Record؟

**Previous → New:**

- **Previous:** 
  - S08 Open Question: Value Proposition vs Screen Record — does situational search + curation + watermark beat screen recording? — no real usage evidence — OPEN
  - S02 differentiation matrix: situational search + dialect authenticity + pre-processed ready-to-use + discovery without feed + LOCKED brand — PROPOSED
  - S10 Reaction = المثل الشعبي الرقمي — "خذها. حطها. يمنية." — ready-to-use — PROPOSED
  - PD-03 كان مخلوطًا مع Keyword Tool architecture — CONFLATED

- **New:**
  ```
  YemReact = مكتبة رياكشنات يمنية منتقاة، قابلة للبحث، جاهزة للاستخدام الفوري.

  الوعد:
  - تلاقي الرياكشن المناسب
  - بجودة عالية (انتقاء بشري)
  - بهوية يمنية
  - بدون قص أو تحرير

  English: YemReact = A curated, searchable Yemeni reaction library — ready to use.
  Promise: Find the right reaction — high-quality human curation — Yemeni identity — no editing needed.

  Note: الصياغة النهائية (تاغلاين، وصف، عنوان الموقع) مؤجلة لمرحلة الهوية — وليست جزءًا من PD-03
  ```

**Reason:**

1) يحل PD-03 — Value vs Screen Record — كقرار قيمة جوهرية — المعنى الجوهري للمنتج — ليس فرضية تحتاج إثبات قبل المتابعة — نحن في مرحلة إعادة تأسيس نبني الأفضل ثم نطلق — Validation Framework بـ 4 أسابيع قياس مرفوض per قرار حمدان
2) يتوافق مع DECISION-001 Product Definition Hybrid (مكتبة مصنفة مسبقًا قابلة للبحث جاهزة للاستخدام الفوري) + DECISION-004 Core Loop Hybrid — القيمة = منتقاة + قابلة للبحث + جاهزة
3) يميز عن البدائل:
   - vs Screen Record TikTok: انتقاء بشري + جودة عالية + هوية يمنية + بدون قص — Screen Record يحتاج قص وإزالة واجهة
   - vs حفظ في واتساب/المعرض: قابل للبحث — واتساب غير قابل للبحث — مكتبة منظمة
   - vs Giphy/Tenor: هوية يمنية — Giphy غير يمني
4) لا يحسم Keyword Tool — Keyword Tool مؤجل Stage 3 — لا يعتبر موافقة على C موافقة على Keyword Tool
5) لا يحسم Search Architecture — البحث ليس "بالموقف" فقط — يشمل اسم الرياكشن، اسم الشخص، جملة، وصف مشهد، كلام مضمن — OPEN-Q-07 جديد — مؤجل Stage 5

**Alternative rejected:**

- A) Utility Value فقط "أسرع طريقة" — ضيق — لا يبرر Curation + هوية يمنية
- B) Discovery/Curated Value فقط "تتصفح وتكتشف" — ضيق — لا يبرر Search equal
- C) Hybrid Value مع Keyword Tool كجزء من القرار — مرفوض كخلط — Keyword Tool قرار منفصل Content/Search Architecture — مؤجل
- D) Value Hypothesis تحتاج إثبات قبل اعتمادها كقرار — مرفوض per قرار حمدان — REJECTED: "Validation Framework بـ 4 أسابيع قياس — لا نحتاجها. نحن في مرحلة إعادة تأسيس — نبني الأفضل، ثم نطلق." + "افتراض أن Value مثبتة تجريبيًا — القيمة مقبولة كقرار منتج، وليست بحاجة إلى إثبات قبل المتابعة."

**Impact:**

- Product: يحسم PD-03 — Value = منتقاة + قابلة للبحث + جاهزة للاستخدام الفوري — يفتح PD-20 Metrics + Audience
- Content: يفتح PD-04 Rubric (ما هو "جودة عالية"؟) + PD-06 Library Size Target 300-500 CONFIRMED
- Search: يفتح OPEN-Q-07 — البحث ليس بالموقف فقط — يشمل اسم الرياكشن، اسم الشخص، جملة، وصف مشهد، كلام مضمن — مؤجل Stage 5
- IA: Home = مكتبة منتقاة قابلة للبحث — يتوافق مع IA-01
- Technical: لا يحسم Search Architecture — مؤجل Stage 5 + Stage 7 — لا يحسم Media Pipeline
- Growth: Facebook launch + بحث + حفظ — مع قيمة واضحة: منتقاة + قابلة للبحث + جاهزة

**Corrections recorded in this decision:**

- **تصحيح 1 — البحث ليس "بالموقف" فقط:** الافتراض السابق "المستخدم يجي بموقف محدد مثل: لما صاحبي يكذب" مصحح — المستخدم يبحث عن: اسم الرياكشن نفسه (مصطفى المومري)، اسم الشخص (هديل مانع)، جملة محددة ("اقرب اقرب لو انت رجال")، وصف المشهد (فيديو الذي يعد الرز)، الكلام المضمن في الفيديو — يُسجل في OPEN-Q-07 — مؤجل Stage 5
- **تصحيح 2 — حجم المكتبة المستهدف:** Target 300-500 رياكشن قبل الإطلاق — CONFIRMED — يلغي مشكلة "12 رياكشن" كعائق تقييم — لا نحتاج نعالج مشكلة مؤقتة

**Deferred (يبقى مؤجلًا):**

- Keyword Tool → Stage 3 (المحتوى)
- Library Size النهائي → Stage 3 (لكن Target 300-500 CONFIRMED كهدف إطلاق)
- Search Architecture التفصيلي → Stage 5
- Media Pipeline → Stage 7
- Percentages 70%/80% → سُحبت، لا نستخدمها — لا أساس موثق

**Rejected in this topic:**

- Validation Framework بـ "4 أسابيع قياس" — لا نحتاجها — نحن في مرحلة إعادة تأسيس نبني الأفضل ثم نطلق — REJECTED
- افتراض أن Value مثبتة تجريبيًا — القيمة مقبولة كقرار منتج وليست بحاجة لإثبات قبل المتابعة — REJECTED

**Stage:** Stage 2 — PD-03 — Value — CLOSED

**Evidence:** DECISION-001, DECISION-004, P-06, B-02, B-03, S02 differentiation, S10 Reaction=مثل شعبي رقمي

---

## OPEN — NEXT QUESTION FROM FOUNDER

- السؤال 1: هل نكمل Stage 2 (Audience & Value) — الذي بقي فيه: PD-20 (مقاييس النجاح) + الجمهور؟
- السؤال 2: أم تفضل الانتقال مباشرة إلى Stage 3 (المحتوى ونظام التحرير)؟

بانتظار قرار حمدان — لا انتقال تلقائي

---

## Topic 3 — PD-03 — CLOSED — DECISION-007 ACCEPTED

- Value = مكتبة يمنية منتقاة + قابلة للبحث + جاهزة للاستخدام الفوري
- الوعد: تلاقي الرياكشن المناسب — بجودة عالية — بهوية يمنية — بدون قص أو تحرير
- OPEN-Q-07 جديد: البحث ليس بالموقف فقط — اسم، شخص، جملة، وصف مشهد، كلام مضمن — DEFERRED Stage 5
- Library Size Target 300-500 CONFIRMED
- Keyword Tool DEFERRED Stage 3 — لا يعتبر موافقة على C موافقة على Keyword Tool
- Percentages 70%/80% سُحبت
- Validation Framework مرفوض
- NEXT: قرار حمدان — نكمل Stage 2 أولًا Topic واحد PD-20 ثم Stage 3 — الترتيب ملزم

---

## DECISION-008 — Directional Signals + Audience — ACCEPTED — Stage 2 — PD-20

- **Status:** ACCEPTED — CLOSED — Stage 2 CLOSED
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 2 — PD-20 Metrics + Audience
- **Topic:** ما الذي نراقبه لنعرف أننا نسير في الاتجاه الصحيح؟ ومن هو الجمهور؟

**Previous → New:**

- **Previous:**
  - S08 Open Question 5: Success metrics: Search Success Rate? Save Rate? Share Rate? Submission Conversion? Retention mental availability vs engagement loop? — no numeric success definition — OPEN — كان يطرح أرقام 70%/80% + Validation Framework 4 أسابيع — PROPOSED
  - S02 Vision: Audience "صناع ميمز 16-30" + differentiation WhatsApp personal collections vs TikTok — PROPOSED
  - S09: Event tracking معطل BUG-1 UUID vs code → 404 — savesCount=0 — لا قياس — CONFIRMED BUG
  - S07: لا سجلات مركزية — Observability مفقودة
  - DECISION-005: Return as Outcome — Return when need خارج Core Loop — Metric منفصل Retention mental availability
  - DECISION-007: Percentages 70%/80% REJECTED — Validation Framework 4 أسابيع REJECTED — لا نحول Metrics لأهداف رقمية

- **New:**

  ```
  Audience (الجمهور):

  الأساسي:
  - أي شخص في موقف يحتاج رياكشن يرد به
  - أول فكرة تجيه: YemReact
  - العمر: التركيز على الشباب (غير محدد برقم)
  - المنصة: ما نحدد منصة — أي منصة تواصل
  - اللغة: لهجة يمنية
  - الجهاز: جوال، متوسط القوة — 30% قوي، 10% ضعيف

  الثانوي:
  - صناع ميمز، طلاب، أصحاب صفحات

  Directional Signals (3 فقط — بدون أرقام — مؤشرات اتجاه وليست أهداف):

  1) هل لقى اللي يدور عليه؟
     → عدد البحوث اللي رجعت نتيجة vs فاضية — بدون هدف رقمي — مجرد اتجاه: هل نحن نتحسن مع 300-500؟

  2) هل استخدمه؟
     → أي فعل بعد ما لقى (نزّل / نسخ / شارك / حفظ) — بدون هدف رقمي

  3) هل رجع؟
     → كوكي مجهول — نشوف إذا رجع خلال أسبوعين — بدون DAU — هل تذكر YemReact عندما احتاج رياكشن؟

  Acquisition — ما نفترض قناة — نراقب فقط:
  - مباشر (كتب الرابط)
  - من مشاركة (رابط /r/[code])
  - من بحث (جوجل)
  - من موقع آخر (فيسبوك، تويتر، الخ)
  - لا نفترض SEO أو Facebook هي القناة النهائية — نترك البيانات تقول

  CONFIRMED — المرحلة التجريبية قبل الإطلاق:
  - Arena-Agent يتولاها
  - إصلاح BUG-1 (Event tracking)
  - رفع 300-500 رياكشن
  - اختبار داخلي شامل
  - ثم الإطلاق الرسمي

  CONFIRMED — هيكل الفريق:
  👑 حمدان (Founder)
     │
     ▼
  🧠 نِبراس — Product Discussion
     │
     ▼
  📜 Blueprint
     │
     ▼
  🏗️ Arena-Agent — Implementation
  ```

**Reason:**

1) يحل PD-20 — Metrics + Audience — كقرار Stage 2 — يغلق Stage 2 — الترتيب ملزم per قرار حمدان — Stage 2 أولًا ثم Stage 3
2) يصحح Audience: ليس "مستخدم واتساب" فقط — الأساسي أي شخص في موقف يحتاج رياكشن — أول فكرة YemReact — العمر تركيز شباب غير محدد — المنصة ما نحدد — اللغة لهجة يمنية — الجهاز جوال متوسط — 30% قوي 10% ضعيف — الثانوي صناع ميمز/طلاب/أصحاب صفحات — يطابق Collections الحالية students/group-chat/no-context hint + S02 differentiation WhatsApp personal collections كبديل
3) يصحح Signals: "المكتبة تكبر" ليست مؤشر منتج — هي مؤشر إنتاج — لا نراقبها كمؤشر — 300-500 خطوة إطلاق بعدها نمو تدريجي بدون توقف — 7 مؤشرات السابقة استُبدلت بـ 3 فقط — بدون أرقام مستهدفة — مؤشرات اتجاه وليست أهداف — يطابق قاعدة حمدان: "ما الذي يجب أن نراقبه لنعرف إن كنا نسير في الاتجاه الصحيح؟ كيف نعرف أن المنتج ينجح أو يفشل؟ لكن بدون أرقام مخترعة وبدون تحويلها لالتزامات"
4) يصحح Acquisition: ما نفترض قناة — نراقب فقط مباشر/مشاركة/بحث/موقع آخر — لا نفترض SEO أو Facebook هي القناة — نترك البيانات تقول
5) يثبت المرحلة التجريبية: Arena-Agent يتولى إصلاح BUG-1 + رفع 300-500 + اختبار داخلي شامل + ثم الإطلاق الرسمي — لن تكون هناك "مرحلة إصلاح BUG-1" منفصلة — هي جزء من المرحلة التجريبية قبل الإطلاق
6) يثبت هيكل الفريق: حمدان → نِبراس Product Discussion → Blueprint → Arena-Agent Implementation — واضح

**Alternative rejected:**

- A) Utility Signals + جمهور واتساب يمني عام فقط — 4 Signals — رُفض لأن الجمهور ليس "مستخدم واتساب" فقط — استُبدل بـ "أي شخص في موقف" — و Signals استُبدلت بـ 3 فقط
- B) Discovery/Curated Signals + جمهور صناع ميمز 16-30 فقط — رُفض لأنه يخالف تصحيح "ليس صناع ميمز فقط" + يركز على Discovery فقط بدون Utility
- C) Hybrid Signals 7 مؤشرات + جمهور هجين واتساب عام أساسي + صناع ميمز ثانوي + Library growth كمؤشر — رُفض جزئيًا — "المكتبة تكبر" ليست مؤشر منتج — هي مؤشر إنتاج — استُبدلت بـ 3 Signals فقط — و Audience استُبدل بـ "أي شخص في موقف"
- أرقام مستهدفة 70%/80% — مرفوضة per DECISION-007 + DECISION-008 — لا أساس موثق
- Validation Framework 4 أسابيع — مرفوض per DECISION-007 + DECISION-008
- "واتساب يمني" كوصف الجمهور — استُبدل بـ "أي شخص في موقف" — REJECTED
- "المكتبة تكبر" كمؤشر منتج — REJECTED — هي مؤشر إنتاج

**Impact:**

- Product: يحسم PD-20 + Audience — يغلق Stage 2 — يفتح Stage 3 Content & Editorial System — PD-04 Rubric
- Content: Library Size Target 300-500 CONFIRMED كهدف إطلاق — لكن "المكتبة تكبر" ليست مؤشر منتج — هي مؤشر إنتاج — 300-500 خطوة إطلاق بعدها نمو تدريجي بدون توقف
- Search: OPEN-Q-07 أنواع البحث — مؤجل Stage 5 — لكن Signals تراقب هل البحث وجد نتيجة
- IA: Home = مكتبة منتقاة قابلة للبحث — يطابق Audience أي شخص في موقف
- Technical: BUG-1 Event tracking يُحل في المرحلة التجريبية قبل الإطلاق — Arena-Agent يتولاها — لا مرحلة منفصلة — مع رفع 300-500 + اختبار داخلي شامل
- Team: هيكل الفريق CONFIRMED — حمدان → نِبراس → Blueprint → Arena-Agent
- Growth: Acquisition ما نفترض قناة — نراقب مباشر/مشاركة/بحث/موقع آخر — Watermark كقناة توزيع محتملة لكن لا نفترضها

**Stage:** Stage 2 — PD-20 — CLOSED — Stage 2 CLOSED — NEXT Stage 3 Content

**Evidence:** DECISION-001 to 007, P-06 Save CTA, P-09 Core Loop Hybrid, P-12 Value, P-13 Library Size Target 300-500 CONFIRMED, T-06 Search, T-07 Saves, T-03 DB 12, SEC-01 BUG-1, Collections students/group-chat/no-context, S02 Audience, S08 Metrics, S08 Acquisition unknown

---

## Topic 4 — PD-20 — CLOSED — DECISION-008 ACCEPTED — Stage 2 CLOSED

- Audience الأساسي: أي شخص في موقف يحتاج رياكشن — أول فكرة YemReact — تركيز شباب غير محدد — ما نحدد منصة — لهجة يمنية — جوال متوسط — 30% قوي 10% ضعيف — الثانوي صناع ميمز/طلاب/أصحاب صفحات
- Directional Signals 3 فقط بدون أرقام: 1) هل لقى اللي يدور عليه؟ (بحث وجد vs فاضي) 2) هل استخدمه؟ (نزّل/نسخ/شارك/حفظ) 3) هل رجع؟ (كوكي مجهول خلال أسبوعين)
- Acquisition: ما نفترض قناة — نراقب مباشر/مشاركة/بحث/موقع آخر — لا نفترض SEO/Facebook
- "المكتبة تكبر" ليست مؤشر منتج — مؤشر إنتاج — 300-500 خطوة إطلاق بعدها نمو تدريجي
- المرحلة التجريبية قبل الإطلاق: Arena-Agent — إصلاح BUG-1 + رفع 300-500 + اختبار داخلي شامل + ثم الإطلاق
- هيكل الفريق: حمدان → نِبراس → Blueprint → Arena-Agent — CONFIRMED
- NEXT: Stage 3 Content & Editorial System — PD-04 Rubric — ما معنى "محتوى جيد"؟

## NEXT — بانتظار فتح Stage 3

- Stage 2 مغلق
- Stage 3 — Content & Editorial System — Topic الأول PD-04 Rubric — السؤال المتوقع: ما معنى "محتوى جيد"؟ كيف نعرف أن رياكشن يستحق أن يدخل المكتبة؟

---

## DECISION-009 — Rubric — 6 معايير نهائية — ACCEPTED — Stage 3 — PD-04

- **Status:** ACCEPTED — CLOSED — PD-04 CLOSED
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 3 — PD-04 Rubric
- **Topic:** ما معنى "محتوى جيد"؟ كيف نعرف أن رياكشن يستحق أن يدخل المكتبة؟

**Previous → New:**

- **Previous:**
  - S10 6 معايير بدون تفصيل — PROPOSED
  - S08 Open Question 2: Rubric operational 6 points vs intuition? Who decides? — OPEN — VERSION DRIFT
  - S06 pipeline 8 steps + quality rubric + checklist بدون تفصيل
  - S1 Axis B: flexible keyword tool evolving to algorithmic structure — PROPOSED
  - PD-04 كان يخلط بين "قانوني" + Keyword Tool + استخراج كلام + 40/ساعة + 7 معايير

- **New — 6 معايير نهائية:**

  ```
  1) نظافة فنية
     - وضوح كامل
     - صوت نظيف (فيديو)
     - صورة نقية (صورة)
     - أول إطار = بداية الرياكشن
     - لا Bumper / لا لوجو غريب

  2) هوية يمنية
     - لهجة يمنية، أو سياق يمني، أو شخص يمني معروف

  3) أخلاقي
     - لا إساءة، لا تحقير، لا تنمر، لا محتوى غير لائق

  4) بياناته جاهزة
     - اسم الرياكشن لو له اسم معروف
     - اسم الشخص
     - جملة / كلام مضمن
     - وصف مشهد
     - كلمات مفتاحية أساسية
     - + استخراج تلقائي للكلام من الفيديو (OPEN-Q-09)

  5) تنوع
     - رياكشن جديد، ليس متكرر

  6) جاهز للاستخدام
     - بدون قص، بدون تحرير — خذها. حطها.

  من يقرر؟
  - حمدان (أساسي)
  - أي شخص له صلاحية أدمن (لاحقًا)

  في أي حالة؟
  - الأدمن يرفع بنفسه → يطبّق Rubric قبل النشر
  - المستخدم يرسل مساهمة → الأدمن يطبّق Rubric → قبول/رفض
  نفس المعايير، نفس الشخص (أو الفريق)، في الحالتين
  ```

**Corrections / Modifications from proposal:**

1) حذف "قانوني" من Rubric — السبب: المنصة حرة تجمع رياكشنات عشوائية — المسؤولية القانونية تُنقل إلى Stage 8 — CONFIRMED
2) "بياناته جاهزة" يتوسع: اسم الرياكشن لو له اسم معروف + اسم الشخص + جملة/كلام مضمن + وصف مشهد + كلمات مفتاحية أساسية + استخراج تلقائي للكلام من الفيديو — OPEN-Q-09
3) "تنوع" يبسط: رياكشن جديد، ليس متكرر — بدون قواعد معقدة
4) Keyword Tool منفصل تمامًا → OPEN-Q-08 — DEFERRED
5) استخراج الكلام تلقائي → OPEN-Q-09 — DEFERRED Stage 3/7

**Reason:**

1) يحل PD-04 Rubric — ما معنى "محتوى جيد"؟ — 6 معايير واضحة قابلة للتطبيق على 300-500 Target CONFIRMED — P-13
2) يتوافق مع DECISION-007 Value منتقاة + بجودة عالية + هوية يمنية + بدون قص — Rubric يحقق Value — P-12
3) يتوافق مع P-04 first frame = reaction start — نظافة فنية أول إطار = بداية
4) يتوافق مع B-02 مثل شعبي رقمي + P-15 Audience أي شخص في موقف + OPEN-Q-07 أنواع البحث (اسم، شخص، جملة، وصف مشهد، كلام مضمن) — "بياناته جاهزة" يغطي أنواع البحث
5) يفصل Legal عن Rubric — Legal يُعالج في Stage 8 مع Report Button + Takedown + شروط — لا يخلط
6) يفصل Keyword Tool عن Rubric — Keyword Tool أداة منفصلة تتطور لخوارزمية — S1 Axis B — OPEN-Q-08
7) يفصل استخراج الكلام تلقائي عن Rubric — أداة تلقائية مجانية تخدم لهجة يمنية — OPEN-Q-09 — Flow معتمد خيار 2: رفع → خيار استخراج → معالجة → نص يظهر للأدمن قبل النشر → تعديل → نشر — المخرجات: النص في الوصف الثنائي + يُستخدم في البحث + قابل للتعديل

**Alternative rejected:**

- "قانوني" كمعيار في Rubric — REJECTED — Legal منفصل Stage 8
- "40 في الساعة" كرقم مستهدف — REJECTED — لا أرقام مستهدفة per قاعدة حمدان
- "7 معايير" — نبقى 6 — REJECTED
- Keyword Tool داخل Rubric — REJECTED — منفصل OPEN-Q-08
- "تنوع بقواعد معقدة" — REJECTED — مبسط: جديد ليس متكرر

**Impact:**

- Content: يحسم PD-04 — Rubric 6 معايير نهائية — يفتح PD-05 Pipeline كيف نجمع 300-500؟ + PD-06 Library Size + PD-07 Duration + PD-08 Aspect + PD-09/10 Categories/Collections
- Search: "بياناته جاهزة" يغطي OPEN-Q-07 أنواع البحث — اسم، شخص، جملة، وصف مشهد، كلام مضمن + كلمات مفتاحية أساسية + استخراج تلقائي OPEN-Q-09 — النص في الوصف الثنائي + يُستخدم في البحث
- IA: Reaction Detail /r/[code] — فيديو/صورة + وصف أساسي + وصف ثنائي مطوي (يظهر فقط إن وجد) + كلام مستخرج تلقائي — Stage 6
- Technical: OPEN-Q-09 استخراج كلام تلقائي مجانية تخدم لهجة يمنية — اختيار الأداة Stage 7 — OPEN-Q-08 Keyword Tool منفصل Stage 3/5
- Legal: حذف "قانوني" من Rubric — Legal Stage 8 مع Report Button DECISION-010 + Takedown + شروط
- Team: من يقرر حمدان أساسي + أي أدمن لاحقًا — نفس المعايير في الحالتين (أدمن يرفع بنفسه أو مستخدم يرسل مساهمة)

**Stage:** Stage 3 — PD-04 — CLOSED — NEXT PD-05 Pipeline

**Evidence:** DECISION-007 Value, P-04 first frame, P-05 human decision, B-02 مثل شعبي, P-13 300-500 Target, P-15 Audience, OPEN-Q-07, S10 6 criteria, S08 Rubric vs intuition, S1 Axis B

---

## OPEN-Q-08 — Keyword Tool منفصل — DEFERRED

- **Topic:** أداة كلمات مفتاحية مرنة تتطور لخوارزمية — S1 Axis B clarification
- **Details:** أداة حتى نكون قادرين على تطويره فيما بعد حتى نكون هيكله خوارزميه للموقع كامل — requires flexible keyword tool that can evolve into algorithmic structure for whole site
- **Previous:** كان داخل Rubric — تم فصله per DECISION-009 تعديل 4 — منفصل تمامًا عن PD-04
- **Status:** DEFERRED → Stage 3 (Topic لاحق) أو Stage 5 (IA/Search)
- **Depends on:** DECISION-009 Rubric + P-14 Search Nature + OPEN-Q-07 + S1 Axis B
- **Impact:** Content Model + Search + Related + Collections + Admin
- **Source:** DECISION-009 — S1 Axis B

---

## OPEN-Q-09 — استخراج الكلام تلقائي — DEFERRED — Flow معتمد خيار 2

- **Topic:** أداة تلقائية تستخرج الكلام من الفيديو — مجانية إلزامي — تخدم لهجة يمنية (تحدي قد نحتاج هجين)
- **Details:**
  - Flow المعتمد (خيار 2):
    1. الأدمن يرفع الفيديو
    2. يظهر خيار "استخراج الكلام"
    3. الأدمن يضغط → المعالجة تشتغل
    4. النص يظهر للأدمن قبل النشر
    5. الأدمن يعدّل ويصحّح
    6. ثم ينشر
  - متطلبات الأداة: مجانية (إلزامي) — تخدم اللهجة اليمنية (تحدي قد نحتاج هجين) — اختيار الأداة المحددة → Stage 7
  - المخرجات: النص يظهر في "الوصف الثنائي" — النص يُستخدم في البحث — النص قابل للتعديل من الأدمن
- **Previous:** كان داخل "بياناته جاهزة" — تم فصله كأداة منفصلة per DECISION-009 تعديل 5 + توسع 2
- **Status:** DEFERRED → Stage 3 (البيانات) / Stage 7 (الأداة)
- **Depends on:** DECISION-009 Rubric معيار 4 "بياناته جاهزة" + P-14 Search Nature + OPEN-Q-07 + T-04 Media pipeline
- **Impact:** Content + Search + Reaction Detail + Admin + Media Pipeline + Cost (مجانية إلزامي)
- **Source:** DECISION-009

---

## DECISION-010 — Report Button — إضافة زر "إبلاغ" — ACCEPTED — Stage 3

- **Status:** ACCEPTED — CONFIRMED — Topic منفصل لاحقًا
- **Decided by:** حمدان
- **Date:** 2026-09-12 — Stage 3 — PD-04 Rubric — Report Button جديد
- **Topic:** إضافة زر "إبلاغ" داخل قائمة الثلاث نقاط في الرياكشن

**Previous → New:**

- **Previous:**
  - قائمة الثلاث نقاط النهائية كانت: حفظ + تنزيل + نسخ رابط + مشاركة — من Axis C notes — PROPOSED
  - لا يوجد زر إبلاغ — OPEN
  - Legal كان داخل Rubric — ثم حُذف — REJECTED كمعيار

- **New:**
  ```
  قائمة الثلاث نقاط النهائية:
  - حفظ
  - تنزيل
  - نسخ رابط
  - مشاركة
  - إبلاغ (جديد) — CONFIRMED

  كيف يشتغل:
  - المستخدم يضغط "إبلاغ"
  - يختار السبب:
    - محتوى غير لائق
    - إساءة لشخص
    - حقوق ملكية
    - محتوى مضلل
    - سبب آخر (نص حر)
  - يُرسل للأدمن
  - الأدمن يراجع → يقرر (إبقاء / حذف / تعديل)

  التنفيذ:
  - UI الزر → يُسجّل الآن، يُنفّذ في Stage 4 (Experience) أو Stage 6 (Flows)
  - Backend الإبلاغ → Stage 8 (Legal & Compliance)

  Legal:
  - آلية إبلاغ (Report) — الآن معتمد كزر
  - آلية Takedown
  - شروط استخدام
  - كلها Stage 8
  ```

**Reason:**

1) يحل Legal الذي حُذف من Rubric — Legal يُعالج في Stage 8 مع آلية إبلاغ + Takedown + شروط — Report Button جزء من Legal
2) يتوافق مع P-05 No automatic publishing + DECISION-009 Rubric أخلاقي (لا إساءة، لا تحقير، لا تنمر، لا محتوى غير لائق) — المستخدم يمكنه الإبلاغ إذا خالف Rubric
3) يتوافق مع DECISION-007 Value منتقاة + بجودة عالية — الإبلاغ يساعد الحفاظ على الجودة بعد الإطلاق
4) يفصل UI عن Backend — UI يُسجل الآن ويُنفذ Stage 4/6 — Backend Stage 8 Legal & Compliance

**Alternative rejected:**

- لا يوجد زر إبلاغ — REJECTED — نحتاج آلية إبلاغ
- إبلاغ بدون أسباب محددة — REJECTED — نحتاج أسباب: غير لائق، إساءة، حقوق ملكية، مضلل، آخر

**Impact:**

- IA: قائمة الثلاث نقاط في /r/[code] — حفظ + تنزيل + نسخ رابط + مشاركة + إبلاغ — Stage 6 Core Flows
- UX: Experience زر إبلاغ — Stage 4/6
- Legal: Backend إبلاغ + Takedown + شروط — Stage 8 — اقتراح 3 من حمدان Legal & Compliance
- Content: يساعد الحفاظ على Rubric بعد الإطلاق — 300-500 + نمو تدريجي

**Stage:** Stage 3 — Report Button — CONFIRMED — UI Stage 4/6 + Backend Stage 8

**Evidence:** DECISION-009 Rubric أخلاقي, P-05 human decision, DECISION-007 Value, P-15 Audience, S08 open questions, اقتراح 3 Legal

---

## Topic 5 — PD-04 — CLOSED — DECISION-009 ACCEPTED — Stage 3

- Rubric 6 معايير نهائية: 1) نظافة فنية (وضوح كامل + صوت نظيف + صورة نقية + أول إطار=بداية + لا Bumper/لوجو غريب) 2) هوية يمنية (لهجة/سياق/شخص يمني معروف) 3) أخلاقي (لا إساءة/تحقير/تنمر/غير لائق) 4) بياناته جاهزة (اسم لو معروف + اسم شخص + جملة/كلام مضمن + وصف مشهد + كلمات مفتاحية أساسية + استخراج تلقائي OPEN-Q-09) 5) تنوع (جديد ليس متكرر) 6) جاهز للاستخدام (بدون قص/تحرير خذها حطها) — من يقرر حمدان أساسي + أي أدمن لاحقًا — نفس المعايير في الحالتين (أدمن يرفع بنفسه أو مستخدم يرسل مساهمة)
- تعديلات: حذف "قانوني" من Rubric → Stage 8 Legal — "بياناته جاهزة" توسع + استخراج تلقائي OPEN-Q-09 Flow خيار 2 — "تنوع" مبسط — Keyword Tool منفصل OPEN-Q-08 — استخراج كلام OPEN-Q-09 مجانية تخدم لهجة يمنية — Report Button جديد في ثلاث نقاط: حفظ+تنزيل+نسخ رابط+مشاركة+إبلاغ — UI Stage 4/6 + Backend Stage 8
- REJECTED: "قانوني" كمعيار + "40/ساعة" كرقم مستهدف + "7 معايير" + Keyword Tool داخل Rubric + تنوع بقواعد معقدة
- NEXT: PD-05 Pipeline — كيف نجمع 300-500؟ هل نسجلها بأنفسنا؟ هل نفتح مساهمات فورًا؟ هل نستورد من مصادر؟ حقوق النشر؟

## NEXT — Stage 3 — PD-05 Pipeline — CLOSED per DECISION-011

- Stage 3 — Content & Editorial System — PD-05 Pipeline CLOSED — DECISION-011 ACCEPTED 2026-09-14

---

## DECISION-011 — Pipeline — Open Sourcing + Blur Before Launch — ACCEPTED — Stage 3 — PD-05

- **Status:** ACCEPTED — CLOSED — PD-05 CLOSED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-14 — Stage 3 — PD-05 Pipeline
- **Topic:** كيف نجمع 300-500 رياكشن؟

**Previous → New:**

- **Previous:**
  - PD-05 Pipeline كان OPEN — DISCUSSION — 3 خيارات: A Admin-only Manual / B Open from Day 1 / C Hybrid Sourcing + Queue — PROPOSED
  - P-18 قال "Arena-Agent يرفع 300-500" — يحتاج تصحيح — كان CONFIRMED في DECISION-008 لكنه خلط بين بناء النظام ورفع المحتوى
  - Submit tension A/B/C من Axis C — لم يُحسم — CONFLICT-038
  - Content Sourcing Plan اقتراح 1: من أين نأتي بـ300-500؟ حقوق النشر؟ — OPEN

- **New:**

  ```
  1. Source — المصدر:
  - لقطات قصيرة من مواقع التواصل الاجتماعي (يوتيوب/تيك توك/إنستغرام)
  - ليست رياكشنات ذاتية
  - القص المناسب فقط — لا فيديوهات كاملة
  - المنصة حرة — لا حقوق
  - Reason: YemReact منصة رياكشنات، ليست تجارة. المحتوى لقطة قصيرة عشوائية.

  2. Who Uploads — من يرفع:
  - Arena-Agent: يبني النظام كاملًا (كود + بنية + اختبار + BUG-1 + نشر)
  - حمدان (الأساسي): بعد اكتمال البناء والنشر → يرفع 300-500 بنفسه
  - Arena-Agent لا يرفع محتوى — فقط يجهّز النظام
  - Reason: Arena-Agent دوره برمجي/هندسي. الرفع عملية تحريرية تحتاج عين بشرية.
  ⚠️ هذا يُعدّل P-18 جزئيًا:
    - P-18 القديم: "Arena-Agent يرفع 300-500"
    - P-18 المُعدّل: "Arena-Agent يبني ويجهّز وينشر. حمدان يرفع 300-500."

  3. Submissions Timing — توقيت المساهمات:
  - قبل الإطلاق: زر (+) يظهر لكنه مقفل فعليًا — blur + "قريبًا"
  - عند الإطلاق: حذف كود بسيط → الزر يعمل
  - بعد الإطلاق: المساهمات مفتوحة من أول إطلاق
  - Reason: حماية الجودة أثناء مرحلة البناء. الإطلاق يفتح الباب.

  4. Rights — الحقوق:
  - المنصة حرة — لا حقوق على المحتوى
  - Report Button (DECISION-010) يحمي بعد النشر
  - Legal كامل في Stage 8: Terms + Privacy + Takedown + Content Policy
  - Reason: المحتوى لقطات قصيرة، ليست تجارة. الإبلاغ يحمي.

  5. Quality / Speed:
  - لا يهم — التنوع والتغطية أهم من السرعة
  - Rubric 6 معايير (DECISION-009) يُطبَّق على كل لقطة من حمدان
  - Reason: 300-500 هدف إطلاق. الجودة تُطبَّق عبر Rubric، لكن التنوع أولاً.

  6. نمو تدريجي:
  - 300-500 خطوة إطلاق
  - بعدها نمو تدريجي بدون توقف (DECISION-008)
  - "المكتبة تكبر" ليست مؤشر منتج — مؤشر إنتاج
  ```

**Reason:**

1) يحل PD-05 Pipeline — CONFLICT-038 — Submit tension A/B/C — كيف نجمع 300-500؟ — Source لقطات قصيرة من مواقع التواصل + ليست ذاتية + قص مناسب فقط + منصة حرة لا حقوق — يطابق DECISION-009 تعديل 1 المنصة حرة تجمع رياكشنات عشوائية + P-24 حذف قانوني → Stage8
2) يصحح P-18 — Arena-Agent يبني النظام كاملًا (كود + بنية + اختبار + BUG-1 + نشر) — حمدان يرفع 300-500 بنفسه بعد اكتمال البناء والنشر — Arena-Agent لا يرفع محتوى — فقط يجهّز — دوره برمجي/هندسي — الرفع تحريري يحتاج عين بشرية — P-18 القديم "Arena-Agent يرفع 300-500" → P-18 المُعدّل "Arena-Agent يبني ويجهّز وينشر. حمدان يرفع 300-500." — تعديل جزئي CONFIRMED
3) يحل Submissions Timing — قبل الإطلاق زر (+) يظهر لكنه مقفل فعليًا blur + "قريبًا" — عند الإطلاق حذف كود بسيط → يعمل — بعد الإطلاق مفتوحة من أول إطلاق — حماية الجودة أثناء البناء — الإطلاق يفتح الباب — يطابق Recent Axis C "زر المساهمة (+) يظهر الآن للجميع" لكن مع blur قبل الإطلاق
4) يحل Rights — المنصة حرة لا حقوق — Report Button DECISION-010 يحمي بعد النشر — Legal كامل Stage 8 Terms + Privacy + Takedown + Content Policy — المحتوى لقطات قصيرة ليست تجارة — الإبلاغ يحمي
5) يوضح Quality/Speed — لا يهم — التنوع والتغطية أهم من السرعة — Rubric 6 يُطبق على كل لقطة — 300-500 هدف إطلاق — الجودة عبر Rubric لكن التنوع أولاً — يطابق DECISION-009 Rubric 6 + DECISION-008 "المكتبة تكبر ليست مؤشر منتج"
6) يثبت نمو تدريجي — 300-500 خطوة إطلاق بعدها نمو تدريجي بدون توقف per DECISION-008 — P-13 يبقى CONFIRMED

**Alternative rejected:**

- A) Admin-only Manual: حمدان يسجل 300-500 بنفسه — مرفوض (بطيء جدًا، غير عملي) — per DECISION-011
- B) Open from Day 1 بلا قيود: مرفوض (جودة متغيرة + لا حماية قبل الإطلاق) — per DECISION-011
- C) Hybrid Sourcing + Queue: مرفوض (Queue يبطئ النمو — حمدان يرفع بنفسه أولًا) — per DECISION-011 — كان PROPOSED في Topic PD-05 لكنه رُفض كـ Queue

**Impact:**

- PD-05 CLOSED — Stage 3 PD-05 CLOSED
- P-18 يُعدّل جزئيًا: Arena-Agent يبني + ينشر، لا يرفع محتوى — P-18 Modified → P-26
- P-13 300-500 يبقى CONFIRMED — Target إطلاق
- DECISION-009 Rubric 6 يبقى — يُطبق على كل لقطة من حمدان
- DECISION-010 Report Button يبقى — يحمي بعد النشر
- يفتح: PD-06 Library Size Details (كيف تُطبق Rubric على 300-500؟ كيف يتم التنوع؟) + PD-07 Duration + PD-08 Aspect
- Content Sourcing Plan اقتراح 1: من أين نأتي بـ300-500؟ — حُسم: لقطات قصيرة من مواقع التواصل (يوتيوب/تيك توك/إنستغرام) — ليست ذاتية — قص مناسب فقط — منصة حرة لا حقوق — Rights Stage 8
- Submissions Timing: blur + "قريبًا" قبل الإطلاق — حذف كود بسيط عند الإطلاق → يعمل — مفتوحة بعد الإطلاق

**Stage:** Stage 3 — PD-05 — CLOSED — DECISION-011 ACCEPTED 2026-09-14 — NEXT PD-06 Library Size Details

**Evidence:** DECISION-007 Value, DECISION-008 Audience/Signals/Trial Phase, DECISION-009 Rubric 6, DECISION-010 Report Button, P-13 300-500 Target, P-18 Trial Phase old, P-24 حذف قانوني → Stage8, Recent Axis C زر (+) يظهر للجميع, CONFLICT-038 Pipeline, اقتراح1 Content Sourcing Plan

---

## Topic 6 — PD-05 — CLOSED — DECISION-011 ACCEPTED — Stage 3

- Source: لقطات قصيرة من مواقع التواصل (يوتيوب/تيك توك/إنستغرام) — ليست ذاتية — قص مناسب فقط — منصة حرة لا حقوق — YemReact منصة رياكشنات ليست تجارة
- Who Uploads: Arena-Agent يبني النظام كاملًا (كود+بنية+اختبار+BUG-1+نشر) — حمدان بعد اكتمال البناء والنشر → يرفع 300-500 بنفسه — Arena-Agent لا يرفع محتوى — فقط يجهّز — يُعدّل P-18 جزئيًا
- Submissions Timing: قبل الإطلاق زر (+) مقفل فعليًا blur + "قريبًا" — عند الإطلاق حذف كود بسيط → يعمل — بعد الإطلاق مفتوحة من أول إطلاق — حماية الجودة
- Rights: منصة حرة لا حقوق — Report Button DECISION-010 يحمي بعد النشر — Legal كامل Stage8 Terms+Privacy+Takedown+Content Policy
- Quality/Speed: لا يهم — التنوع والتغطية أهم — Rubric 6 يُطبق
- نمو تدريجي: 300-500 خطوة إطلاق بعدها نمو تدريجي بدون توقف — "المكتبة تكبر" ليست مؤشر منتج
- REJECTED: A Admin-only Manual بطيء غير عملي + B Open from Day1 بلا قيود جودة متغيرة + C Hybrid Sourcing+Queue Queue يبطئ النمو
- P-18 Modified: Arena-Agent يبني ويجهّز وينشر — حمدان يرفع 300-500 — P-26
- NEXT: PD-06 Library Size Details — كيف تُطبق Rubric على 300-500؟ كيف يتم التنوع؟

## DECISION-012 — Video Duration — ACCEPTED — Stage 3 — PD-07

- **Status:** ACCEPTED — CLOSED — PD-07 CLOSED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-14 — Stage 3 — PD-07 Video Duration
- **Topic:** ما هي المدة المسموحة للرياكشن؟

**Previous → New:**

- **Previous:**
  - VERSION DRIFT — CONFLICT-020
  - S10/S06/S01: 2-8s strict linked to concept — Reaction = مثل شعبي رقمي كلمة بصرية جاهزة — أول إطار = بداية
  - S01 note: up to 60s flexible note — not fixed
  - S09 T-04: no limit in code — Media pipeline local validate MIME/size/magic bytes only — durationMs NULL 12 seed — DB Reaction.durationMs NULL — no duration limit
  - S08 Open Question: Video Duration 2-8s vs 60s — High impact — affects identity, rubric, performance, storage cost — OPEN
  - S09 T-05: Media in production blocked — no ffmpeg on Vercel — LocalStorage ephemeral — body limit 4.5MB vs 80MB — 60s heavier than 8s
  - PD-07 كان OPEN — CONFLICT-020 — HISTORY + EVIDENCE done 2026-09-14

- **New:**

  ```
  1. النطاق:
  - الحد الأدنى: 2 ثانية
  - الحد الأقصى: 60 ثانية
  - المرونة كاملة من 2s إلى 60s — أي لقطة ثواني عشوائية مثل Pinterest

  2. رفض تلقائي:
  - ما يزيد عن 60s → رفض تلقائي
  - ما يقل عن 2s → رفض تلقائي
  - للجميع بنفس القاعدة — مستخدم + أدمن (لا استثناء)

  3. طريقة الرفض (Modal — ليس error تقني):
  - عند تجاوز الحد (أعلى أو أدنى):
    ┌──────────────────────────────────┐
    │   ⚠️  المدة خارج النطاق المسموح │
    │                                  │
    │   المقطع الذي حاولت رفعه مدته    │
    │   [XX] ثانية.                    │
    │                                  │
    │   المدة المسموحة: من 2s إلى 60s  │
    │                                  │
    │   يرجى قص المقطع ثم المحاولة.    │
    │                                  │
    │         [ حسناً ]                │
    └──────────────────────────────────┘
  - ليست error page حمراء — modal واضح
  - وصف واضح + ذكر المدة الفعلية [XX] + ذكر الحد 2s-60s
  - اقتراح الحل (القص)
  - زر واحد بسيط [حسناً]
  - RTL + عربي + متوافق مع Brand v1.0 LOCKED (B-01 to B-07)
  - UX محترمة — ليست رسالة تقنية

  4. عرض الحد قبل الرفع:
  - في نموذج الرفع (SubmissionForm + AdminForm)
  - سطر واضح: "المدة: من 2s حتى 60s"
  - يظهر دائماً — ليس tooltip — يمنع المفاجأة

  5. معيار القبول:
  - "هل هي رياكشن؟" — وليس "كم مدتها؟"
  - لقطة 45s مقبولة إذا كانت رياكشن
  - Rubric 6 (خاصة "نظافة فنية" + "جاهز للاستخدام") هو الفيصل
  - 60s لا تعني فيديو كامل — لا فيديوهات كاملة per DECISION-011 — القص المناسب فقط

  6. الصور:
  - validation المدة للفيديو فقط
  - الصور مستثناة تماماً
  - الصور لها validation آخر (حجم فقط) — لا علاقة بالمدة

  7. قابلية المراجعة:
  - الحد 60s قابل للتعديل لاحقاً بقرار جديد
  - إذا احتجنا 90s بعد سنة → PD جديد
  - لا نغلق الباب — revisable

  8. التوافق:
  - P-04 Video Intro/Outro Bumper REJECTED — أول إطار = بداية الرياكشن — متوافق مع 60s — أول إطار = بداية بغض النظر عن المدة
  - P-20 Rubric 6 — المدة حد تقني منفصل — لا يُضاف للمعايير — "نظافة فنية" تُطبّق على كل لقطة بغض النظر عن المدة
  - P-25 Pipeline DECISION-011 — لقطات قصيرة من مواقع التواصل — القص المناسب فقط — لا فيديوهات كاملة — 2-60s يحقق "قصيرة" + "قص مناسب"
  - P-13 Library Size 300-500 — 60s × 300-500 أثقل من 8s — لكن لا يمنع الإطلاق — يُراقب Storage/Bandwidth/Processing cost
  ```

**Reason:**

1) يتوافق مع DECISION-011 Pipeline — Source لقطات قصيرة من مواقع التواصل يوتيوب/تيك توك/إنستغرام — ليست ذاتية — قص مناسب فقط — لا فيديوهات كاملة — منصة حرة لا حقوق — YemReact منصة رياكشنات ليست تجارة — محتوى لقطة قصيرة عشوائية — "أي لقطة عشوائية مثل الرياكشنات في بنترست — أي لقطة ثواني" — 2-60s يحقق "ثواني" + "قصيرة" + "قص مناسب"
2) يحل VERSION DRIFT + CONFLICT-020 — S10/S06/S01 2-8s strict vs S01 note up to 60s vs S09 T-04 no limit — الآن 2-60s CONFIRMED hard limits
3) الحد 60s يحمي:
   - Storage — 60s × 300-500 أثقل من 8s — لكن لا يمنع الإطلاق
   - Bandwidth — 3G يمني — 60s أثقل لكن مقبول كحد أقصى
   - Processing cost — ffmpeg thumbnail + watermark 14% — يدعم 60s — لا تغيير
   - يمنع فيديوهات كاملة — DECISION-011 "لا فيديوهات كاملة" — 60s حد يمنع 5 دقائق
4) الحد الأدنى 2s يمنع:
   - مقاطع فارغة — 0-1s بلا معنى
   - GIFs بلا معنى — أقل من 2s ليست رياكشن
   - أخطاء رفع — ملف تالف
5) Modal يمنح تجربة UX محترمة — ليست رسالة تقنية — وصف واضح + ذكر المدة الفعلية [XX] + ذكر الحد + اقتراح الحل (القص) + زر واحد بسيط — RTL + عربي + متوافق Brand v1.0 — يظهر في SubmissionForm + AdminForm — سطر "المدة: من 2s حتى 60s" يظهر دائماً قبل الرفع — ليس tooltip
6) "هل هي رياكشن؟" كمعيار قبول — يسمح بمرونة إبداعية — لقطة 45s مقبولة إذا كانت رياكشن — Rubric 6 هو الفيصل — "نظافة فنية" + "جاهز للاستخدام" — لا نحكم بالمدة بل بالمحتوى
7) قابلية المراجعة — الحد 60s قابل للتعديل لاحقاً بقرار جديد — إذا احتجنا 90s بعد سنة → PD جديد — لا نغلق الباب — revisable
8) يتوافق مع P-04 — أول إطار = بداية الرياكشن بغض النظر عن المدة — 60s لا تعني Intro/Outro Bumper — REJECTED يبقى
9) يتوافق مع P-20 Rubric 6 — المدة حد تقني منفصل — لا يُضاف للمعايير — "نظافة فنية" تُطبّق على كل لقطة بغض النظر عن المدة — وضوح كامل + صوت نظيف + صورة نقية + أول إطار=بداية + لا Bumper/لوجو غريب — كلها مستقلة عن المدة

**Alternative rejected:**

- A) 2-8s strict linked to concept — REJECTED per DECISION-012 — 60s مقبول كرياكشن إذا كان "هل هي رياكشن؟" — 2-8s كان PROPOSED في S10/S06/S01 لكنه ضيق — لا يغطي لقطات قصيرة عشوائية مثل Pinterest — REJECTED
- B) up to 60s بدون حد أدنى — REJECTED — 2s مطلوب لمنع مقاطع فارغة/GIFs بلا معنى — REJECTED
- D) لا حد صارم — توجيه فقط عبر Rubric — REJECTED per DECISION-012 — الحد صارم + رفض تلقائي + modal — لا توجيه فقط — نحتاج حد تقني يحمي Storage/Bandwidth/Processing + يمنع فيديوهات كاملة — REJECTED

**Impact:**

- PD-07 CLOSED — Stage 3 PD-07 CLOSED — DECISION-012 ACCEPTED 2026-09-14 — 58 → 60 facts
- P-27 NEW: Video Duration 2-60s + auto-reject >60s/<2s + modal rejection + display limit in forms + revisable
- P-28 NEW: Reaction Criterion vs Duration — "هل هي رياكشن؟" وليس "كم مدتها؟" — لقطة 45s مقبولة إذا كانت رياكشن — Rubric 6 هو الفيصل
- P-20 Rubric 6: المدة حد تقني منفصل — لا يُضاف للمعايير — "نظافة فنية" تُطبّق بغض النظر عن المدة
- P-04 Video Intro/Outro Bumper REJECTED: متوافق — أول إطار = بداية الرياكشن بغض النظر عن المدة — 60s لا تعني Bumper
- P-25 Pipeline DECISION-011: متوافق — لقطات قصيرة من مواقع التواصل — قص مناسب فقط — لا فيديوهات كاملة — 2-60s يحقق "قصيرة" + "قص مناسب"
- P-13 Library Size 300-500: 60s × 300-500 أثقل لكن لا يمنع الإطلاق — يُراقب
- Technical Stage 7: MediaService.validate — إضافة الحد 2s-60s + auto-reject — modal واضح ليس error تقني — معالجة ffmpeg لا تغيير (يدعم 60s) — Storage 60s × 300-500 قد يكون أثقل لكن لا يمنع الإطلاق — T-04 CURRENT local + T-05 blocked production
- YEMREACT-HISTORICAL-NOT-CURRENT.md: VD-07 Video duration 2-8s strict → HISTORICAL CONFIRMED as old — S01 note up to 60s → CONFIRMED as new — DECISION-012
- NEXT: PD-08 Video Aspect — HISTORY + EVIDENCE فقط — بانتظار أمر حمدان — PD-06 Library Size thresholds 30-50 vs 150-300 SKIPPED — حُسم في DECISION-007 = 300-500 CONFIRMED

**Stage:** Stage 3 — PD-07 — CLOSED — DECISION-012 ACCEPTED 2026-09-14 — NEXT PD-08 Video Aspect

**Evidence:** S10 Brand v1.0 2-8s strict, S06 Content pipeline 8 steps, S01 Taxonomy clip system, S09 T-04 no limit + T-03 durationMs NULL + T-05 blocked, S08 CONFLICT-020 VERSION DRIFT, DECISION-011 Pipeline لقطات قصيرة عشوائية, DECISION-009 Rubric 6 نظافة فنية, P-04 Bumper REJECTED, P-13 300-500 Target, CORRECTION duration NOT 8s max up to 60s max, Note "أي لقطة عشوائية مثل الرياكشنات في بنترست — أي لقطة ثواني"

---

## Topic 7 — PD-07 — CLOSED — DECISION-012 ACCEPTED — Stage 3

- Video Duration: 2-60s — الحد الأدنى 2s — الحد الأقصى 60s — المرونة كاملة 2s→60s — أي لقطة ثواني عشوائية مثل Pinterest
- رفض تلقائي: >60s → رفض — <2s → رفض — للجميع مستخدم+أدمن لا استثناء — hard limits
- طريقة الرفض: Modal ليس error تقني — ⚠️ المدة خارج النطاق المسموح — المقطع مدته [XX] ثانية — المدة المسموحة من 2s إلى 60s — يرجى قص المقطع ثم المحاولة — [حسناً] — RTL عربي Brand v1.0 — وصف واضح + مدة فعلية + حد + اقتراح حل
- عرض الحد قبل الرفع: SubmissionForm + AdminForm سطر واضح "المدة: من 2s حتى 60s" يظهر دائماً ليس tooltip
- معيار القبول: "هل هي رياكشن؟" وليس "كم مدتها؟" — لقطة 45s مقبولة إذا كانت رياكشن — Rubric 6 هو الفيصل — 60s لا تعني فيديو كامل — لا فيديوهات كاملة per DECISION-011
- الصور: مستثناة تماماً — validation المدة للفيديو فقط — الصور حجم فقط
- قابلية المراجعة: 60s قابل للتعديل لاحقاً بقرار جديد — 90s بعد سنة → PD جديد — لا نغلق الباب
- التوافق: P-04 Bumper REJECTED متوافق أول إطار=بداية بغض النظر عن المدة — P-20 Rubric 6 المدة حد تقني منفصل لا يُضاف — P-25 Pipeline متوافق قصيرة+قص مناسب — P-13 300-500 أثقل لكن لا يمنع
- REJECTED: A 2-8s strict ضيق — B up to 60s بدون حد أدنى يسمح فارغ — D لا حد صارم توجيه فقط لا يحمي Storage
- P-27 Video Duration + P-28 Reaction Criterion — 58 → 60 facts — Stage 3 PD-07 CLOSED
- NEXT: PD-08 Video Aspect — HISTORY + EVIDENCE فقط — PD-06 SKIPPED حُسم في DECISION-007 300-500

## DECISION-013 — Aspect Ratio — ACCEPTED — Stage 3 — PD-08

- **Status:** ACCEPTED — CLOSED — PD-08 CLOSED — CONFLICT-021 CLOSED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-14 — Stage 3 — PD-08 Video Aspect
- **Topic:** ما هو المقاس المسموح للفيديو؟

**Previous → New:**

- **Previous:**
  - VERSION DRIFT — CONFLICT-021
  - S10/S06/S01: 9:16 primary + 1:1 secondary — clip system — Overlays 9:16 + 1:1 + Safe Area Guides x4 Default/Mirrored ×2
  - S01 note: not fixed size — flexible note
  - S09 T-04: no aspect validation in code — MediaService.validate MIME/size/magic bytes only — ffprobe reads width/height but no reject — ffmpeg watermark w=iw*0.14 works on any aspect — thumbnail scale=480:-2 keeps ratio
  - S08 Open Question: Video Aspect 9:16+1:1 vs any size — affects Brand, Overlays, Watermark, Safe Area, Masonry Grid — OPEN
  - S09 T-05 blocked production — no ffmpeg on Vercel — MediaAsset 0 prod
  - PD-08 كان OPEN — CONFLICT-021 — HISTORY + EVIDENCE done 2026-09-14
  - DECISION-011 Pipeline: Source لقطات قصيرة من مواقع التواصل يوتيوب/تيك توك/إنستغرام — يوتيوب 16:9 + تيك توك 9:16 + إنستغرام 1:1 و 4:5 — لا يهم المصدر — تعارض جديد: يوتيوب 16:9 vs Brand 9:16 primary
  - DECISION-012 Duration 2-60s + auto-reject + modal + Reaction Criterion "هل هي رياكشن؟" — ACCEPTED

- **New:**

  ```
  1. المقاس:
  - أي مقاس مسموح — 9:16, 1:1, 16:9, 4:5, 3:4, أي مقاس آخر
  - لا حد تقني على المقاس — لا رفض تلقائي — MediaService.validate لا يضيف فحص مقاس
  - المهم: الفيديو يعمل بدون فراغ أسود (no black bars)

  2. القيد الوحيد — بدون فراغ أسود:
  - الفيديو يجب أن يملأ الإطار الذي يظهر فيه
  - لا letterboxing (أشرطة سوداء أفقية)
  - لا pillarboxing (أشرطة سوداء عمودية)
  - إذا كان الفيديو 16:9 ويعرض في بطاقة 9:16 — يجب أن يملأها (crop أو scale)
  - هذا توجيه — ليس رفض تقني (لا حد صارم في MediaService.validate) — Rubric 6 يقرر

  3. المصدر:
  - لا يهم المصدر (يوتيوب 16:9 + تيك توك 9:16 + إنستغرام 1:1 و 4:5)
  - نأخذ الرياكشن بأي مقاس يكون
  - لا نقص حسب المقاس — نقبل كما هو — لا نقص 16:9 لـ 9:16

  4. Watermark + Qussasa:
  - تطبيق ديناميكي على أي مقاس
  - Watermark: نسبة من عرض الفيديو (14% تقنيًا حاليًا — CONFLICT-019 يُحل في Stage 4/7 — 11% vs 14%)
  - Qussasa: في الزاوية دائمًا — قاعدة قلب الكتلة Default/Mirrored
  - يعملان على 9:16, 1:1, 16:9, 4:5 — بغض النظر عن المقاس — scale2ref يحافظ على النسبة

  5. حد صارم أم توجيه:
  - توجيه فقط — Rubric 6 يقرر — P-20 نظافة فنية تشمل الآن "بدون فراغ أسود"
  - لا رفض تلقائي على المقاس (بخلاف Duration 2-60s hard limits)
  - إذا كان المقاس غريبًا أو غير مناسب — Rubric 6 (نظافة فنية) يقرر
  - القاعدة: "هل هي رياكشن؟" — وليس "ما مقاسها؟" — P-30

  6. الصور:
  - قواعد مختلفة — أكثر مرونة
  - أي مقاس للصور
  - لا قيد فراغ أسود على الصور (الصور بطبيعتها لا تمتد)
  - Rubric 6 يُطبّق (نظافة فنية — صورة نقية) — P-02 Video+Image equal

  7. التفاصيل المؤجلة — Stage 4 + Stage 7:
  - كيفية تطبيق "بدون فراغ أسود" تقنيًا:
    - Option A: Crop — نأخذ مركز الفيديو ونملأ البطاقة
    - Option B: Scale + Pad — نُوسّع الفيديو ونضيف padding
    - Option C: Masonry يتكيف مع المقاس الأصلي — لا crop ولا pad — Pinterest-like
  - Qussasa في الزاوية: يحتاج مراجعة لـ 16:9 (الزاوية مختلفة؟) — Stage 4
  - Safe Area Guides لكل مقاس: يحتاج تصميم — Stage 4 — Brand v1.0 Safe Area لـ 9:16 فقط (أعلى 6% أسفل 20% يمين 14% يسار 6%)
  - Overlays جديدة: إذا احتجنا لـ 16:9/4:5/3:4 — Stage 4 — الحالية 9:16+1:1 تبقى كمرجع بصري ليست حد
  - ffmpeg watermark: مراجعة لـ "بدون فراغ أسود" — aspect fill vs fit — Stage 7

  8. التوافق:
  - P-04 Bumper REJECTED — أول إطار=بداية بغض النظر عن المقاس — متوافق
  - P-20 Rubric 6 — نظافة فنية تشمل الآن "بدون فراغ أسود" — P-20 UPDATED
  - P-27 Duration 2-60s — متوافق — لا تعارض — حد تقني للمدة + توجيه للمقاس
  - P-25 Pipeline — لقطات قصيرة من مواقع التواصل — قص مناسب فقط — لا فيديوهات كاملة — أي مقاس يحقق "قصيرة" + "قص مناسب"
  - P-13 Library Size 300-500 — أي مقاس × 300-500 — لا يمنع الإطلاق
  - B-04 Qussasa + B-07 Watermark LOCKED concept — تطبيق ديناميكي — متوافق
  - CONFLICT-019 Watermark 11% vs 14% — لم يُحل بعد — يبقى لـ Stage 4/7 — PD-08 لم يحسمه
  ```

**Reason:**

1) يتوافق مع DECISION-011 Pipeline — Source لقطات قصيرة من مواقع التواصل يوتيوب/تيك توك/إنستغرام — ليست ذاتية — قص مناسب فقط — لا فيديوهات كاملة — منصة حرة — يوتيوب 16:9 + تيك توك 9:16 + إنستغرام 1:1 و 4:5 — أي مقاس مسموح يحقق "لقطات عشوائية من مصادر متعددة المقاسات" — لا نقص حسب المقاس
2) يتوافق مع DECISION-012 Duration — معيار "هل هي رياكشن؟" وليس "كم مدتها؟" — الآن "هل هي رياكشن؟" وليس "ما مقاسها؟" — مرونة إبداعية — Rubric 6 هو الفيصل — 60s مقبولة إذا كانت رياكشن + أي مقاس مقبول إذا كان رياكشن
3) Pinterest-like Masonry = مرونة مقاسات — الشكل الأساسي — Masonry Grid يعرض أي مقاس — 9:16, 1:1, 4:5, 3:4, 16:9 — كلها مقبولة في Pinterest — YemReact presentation = Pinterest-like visual only — P-08
4) رفض الحد الصارم = حرية إبداعية أكبر — لا رفض تلقائي على المقاس — توجيه فقط — Rubric 6 يقرر — إذا كان المقاس غريبًا أو غير مناسب — نظافة فنية — يختلف عن Duration 2-60s hard limits الذي يحمي Storage/Bandwidth/Processing — المقاس لا يحتاج حماية بنفس الدرجة
5) "بدون فراغ أسود" = تجربة بصرية نظيفة — لا letterboxing + لا pillarboxing — الفيديو يملأ الإطار — توجيه — ليس رفض تقني — يضاف لـ P-20 نظافة فنية — يحل مشكلة 16:9 في بطاقة 9:16 — يجب أن يملأها (crop أو scale) — Stage 4/7 يقرر كيفية التطبيق تقنيًا
6) Watermark + Qussasa ديناميكيان = لا حاجة لـ Overlays جديدة لكل مقاس — w=iw*0.14 نسبة من عرض الفيديو — scale2ref يحافظ على النسبة — overlay (W-w-16:H-h-16) أسفل-يمين — يعمل على أي مقاس — Qussasa في الزاوية دائمًا — قاعدة قلب الكتلة Default/Mirrored — B-04 + B-07 LOCKED concept — متوافق — Overlays الحالية 9:16+1:1 تبقى كمرجع بصري ليست حد
7) الصور أكثر مرونة = Pinterest يقبل أي مقاس للصور — DECISION-002 Video+Image equal — لكن الصور بطبيعتها لا تمتد — لا قيد فراغ أسود على الصور — Rubric 6 صورة نقية — أكثر مرونة
8) يحل CONFLICT-021 — 9:16+1:1 vs not fixed size — VERSION DRIFT — الآن أي مقاس مسموح + لا فراغ أسود + توجيه فقط — CONFLICT-021 CLOSED
9) يحل تعارض جديد بعد DECISION-011 — يوتيوب 16:9 vs Brand 9:16 primary — الآن أي مقاس مقبول — لا نقص 16:9 لـ 9:16 — يفقد محتوى — REJECTED قص 16:9 لـ 9:16

**Alternative rejected:**

- B) 9:16+1:1+4:5 فقط — REJECTED per DECISION-013 — نريد مرونة كاملة — أي مقاس مسموح — لا نحدد 3 فقط — REJECTED
- C) 9:16+1:1 فقط (S10 الأصلي) — REJECTED per DECISION-013 — قيد على التنوع — S10 كان PROPOSED لكنه ضيق — لا يغطي يوتيوب 16:9 — REJECTED
- D) 9:16 فقط — REJECTED per DECISION-013 — قيد صارم — REJECTED
- B) قص 16:9 لـ 9:16 — REJECTED per DECISION-013 — يفقد محتوى — نأخذ الرياكشن بأي مقاس يكون — لا نقص حسب المقاس — REJECTED
- C) نمط موحد على كل مقاس — REJECTED per DECISION-013 — نريد ديناميكية — Watermark + Qussasa ديناميكيان — REJECTED
- A) رفض تقني (مثل Duration) — REJECTED per DECISION-013 — توجيه فقط — لا رفض تلقائي على المقاس — يختلف عن Duration 2-60s — المقاس توجيه فقط Rubric 6 يقرر — REJECTED

**Impact:**

- PD-08 CLOSED — Stage 3 PD-08 CLOSED — CONFLICT-021 CLOSED — DECISION-013 ACCEPTED 2026-09-14 — 60 → 62 facts
- P-29 NEW: Aspect Ratio — أي مقاس مسموح (9:16, 1:1, 16:9, 4:5, 3:4, أي مقاس) + لا حد تقني + لا رفض تلقائي + بدون فراغ أسود (no black bars — لا letterboxing + لا pillarboxing — يملأ الإطار) + توجيه فقط Rubric 6 يقرر + المصدر لا يهم + لا نقص حسب المقاس + Watermark+Qussasa ديناميكي + الصور أكثر مرونة أي مقاس
- P-30 NEW: Aspect Criterion vs Size — "هل هي رياكشن؟" وليس "ما مقاسها؟" — Rubric 6 نظافة فنية تشمل "بدون فراغ أسود" — إذا كان المقاس غريبًا Rubric يقرر
- P-20 Rubric 6 UPDATED: نظافة فنية تشمل الآن "بدون فراغ أسود" — وضوح كامل + صوت نظيف + صورة نقية + أول إطار=بداية + لا Bumper/لوجو غريب + بدون فراغ أسود (لا letterboxing/pillarboxing) — لا يُضاف "المقاس" صريحًا كمعيار منفصل — Rubric 6 يقرر
- P-04 Bumper REJECTED: متوافق — أول إطار=بداية بغض النظر عن المقاس — 60s + أي مقاس لا يعني Bumper
- P-27 Duration 2-60s: متوافق — لا تعارض — حد صارم للمدة + توجيه للمقاس — 2-60s + أي مقاس
- P-25 Pipeline DECISION-011: متوافق — لقطات قصيرة من مواقع التواصل — قص مناسب فقط — لا فيديوهات كاملة — أي مقاس يحقق "قصيرة" + "قص مناسب" — يوتيوب 16:9 مقبول
- P-13 Library Size 300-500: أي مقاس × 300-500 — لا يمنع الإطلاق
- B-04 Qussasa + B-07 Watermark LOCKED concept: متوافق — تطبيق ديناميكي على أي مقاس — w=iw*0.14 — scale2ref — قاعدة قلب الكتلة
- CONFLICT-019 Watermark 11% vs 14%: لم يُحل بعد — يبقى لـ Stage 4 (Experience) أو Stage 7 (Technical) — PD-08 لم يحسمه — VD-09 يبقى OPEN
- CONFLICT-021 Video Aspect: يُغلق الآن — DECISION-013 يحسمه — 9:16+1:1 vs any size → أي مقاس مسموح + لا فراغ أسود — CLOSED
- Overlays 9:16 + 1:1: تبقى كمرجع بصري — ليست حد — Stage 4 يقرر هل نحتاج Overlays جديدة لـ 16:9/4:5/3:4 — VD-08 HISTORICAL
- Stage 4 (Experience): يُفتح — Safe Area Guides لكل مقاس + Overlays جديدة؟ + Qussasa في الزاوية مراجعة لـ 16:9 + كيفية تطبيق "بدون فراغ أسود" (Crop vs Scale+Pad vs Masonry يتكيف)
- Stage 7 (Technical): MediaService.validate — لا يضيف فحص مقاس (لا حد صارم) — T-04 يبقى لا يفرض مقاس — ffmpeg watermark يحتاج مراجعة لـ "بدون فراغ أسود" (aspect fill vs fit) — T-04 CURRENT local
- NEXT: PD-09 Categories — HISTORY + EVIDENCE فقط — بانتظار أمر حمدان — لا تعارض مع PD-08

**Stage:** Stage 3 — PD-08 — CLOSED — DECISION-013 ACCEPTED 2026-09-14 — NEXT PD-09 Categories — CONFLICT-021 CLOSED

**Evidence:** S10 Brand v1.0 LOCKED 9:16 Safe Area 6% top 20% bottom 14% right 6% left + Qussasa 6-15% + Watermark 9-15% double shadow, S06 Content Pipeline Overlays 9:16+1:1 + Safe Area Guides x4 + Step2 vertical vs S01 note not fixed size, S01 Asset Inventory clip system 9:16+1:1 vs note not fixed, S09 T-04 no aspect validation + ffprobe width/height no reject + ffmpeg watermark w=iw*0.14 + thumbnail scale=480:-2 keeps ratio + DB no aspect column, S08 CONFLICT-021 VERSION DRIFT 9:16+1:1 vs not fixed size NEEDS PRODUCT DECISION, DECISION-011 Pipeline يوتيوب 16:9 + تيك توك 9:16 + إنستغرام 1:1 و 4:5 لقطات عشوائية قص مناسب, DECISION-012 Duration 2-60s + auto-reject + modal + Reaction Criterion هل هي رياكشن, P-04 Bumper REJECTED أول إطار=بداية, P-20 Rubric 6 نظافة فنية, P-02 Video+Image equal, B-04 Qussasa + B-07 Watermark LOCKED concept, CONFLICT-019 Watermark 11% vs 14% remains, CONFLICT-021 Video Aspect

---

## Topic 8 — PD-08 — CLOSED — DECISION-013 ACCEPTED — Stage 3 — CONFLICT-021 CLOSED

- Aspect Ratio: أي مقاس مسموح — 9:16, 1:1, 16:9, 4:5, 3:4, أي مقاس آخر — لا حد تقني — لا رفض تلقائي — MediaService.validate لا يضيف فحص مقاس
- القيد الوحيد — بدون فراغ أسود: الفيديو يملأ الإطار — لا letterboxing (أشرطة سوداء أفقية) — لا pillarboxing (أشرطة سوداء عمودية) — إذا كان 16:9 في بطاقة 9:16 يجب أن يملأها (crop أو scale) — توجيه ليس رفض تقني — Rubric 6 يقرر — نظافة فنية تشمل "بدون فراغ أسود"
- المصدر: لا يهم — يوتيوب 16:9 + تيك توك 9:16 + إنستغرام 1:1 و 4:5 — نأخذ الرياكشن بأي مقاس — لا نقص حسب المقاس — لا نقص 16:9 لـ 9:16 يفقد محتوى
- Watermark + Qussasa: تطبيق ديناميكي على أي مقاس — Watermark نسبة من عرض الفيديو 14% تقنيًا — Qussasa في الزاوية دائمًا — قاعدة قلب الكتلة Default/Mirrored — يعملان على 9:16,1:1,16:9,4:5 — لا حاجة Overlays جديدة لكل مقاس — Overlays الحالية 9:16+1:1 تبقى مرجع بصري ليست حد
- حد صارم أم توجيه: توجيه فقط — Rubric 6 يقرر — لا رفض تلقائي على المقاس بخلاف Duration 2-60s — القاعدة "هل هي رياكشن؟" وليس "ما مقاسها؟" — P-30
- الصور: قواعد مختلفة أكثر مرونة — أي مقاس للصور — لا قيد فراغ أسود — Rubric 6 صورة نقية
- التفاصيل المؤجلة Stage 4/7: كيفية تطبيق "بدون فراغ أسود" — Option A Crop مركز + Option B Scale+Pad + Option C Masonry يتكيف مع المقاس الأصلي — Qussasa مراجعة لـ 16:9 — Safe Area Guides لكل مقاس — Overlays جديدة إذا احتجنا — ffmpeg watermark مراجعة aspect fill vs fit
- التوافق: P-04 Bumper REJECTED متوافق أول إطار=بداية — P-20 Rubric 6 UPDATED نظافة فنية تشمل بدون فراغ أسود — P-27 Duration متوافق لا تعارض — P-25 Pipeline متوافق — P-13 300-500 لا يمنع — B-04+B-07 LOCKED متوافق ديناميكي
- CONFLICT-019 Watermark 11% vs 14% لم يُحل بعد — يبقى Stage 4/7 — VD-09 OPEN
- CONFLICT-021 Video Aspect يُغلق الآن — DECISION-013 يحسمه — 60→62 facts
- REJECTED: B 9:16+1:1+4:5 فقط مرونة جزئية — C 9:16+1:1 فقط قيد تنوع — D 9:16 فقط قيد صارم — B قص 16:9 لـ 9:16 يفقد محتوى — C نمط موحد — A رفض تقني مثل Duration توجيه فقط
- P-29 Aspect Ratio + P-30 Aspect Criterion — 60 → 62 facts — Stage 3 PD-08 CLOSED — CONFLICT-021 CLOSED
- NEXT: PD-09 Categories — HISTORY + EVIDENCE فقط — بانتظار أمر حمدان — لا تعارض مع PD-08

## DECISION-014 — Categories Full Removal (Staged) — ACCEPTED — Stage 3 — PD-09

- **Status:** ACCEPTED — CLOSED — PD-09 CLOSED — CONFLICT-009 CLOSED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-14 — Stage 3 — PD-09 Categories
- **Topic:** إزالة الفئات نهائيًا — مسار آمن من مرحلتين

**Previous → New:**

- **Previous:**
  - CONFLICT-009 Categories Role — لم يُحسم منذ Phase 1 — VERSION DRIFT
  - S10 Brand v1.0: 9 category colors LOCKED — ضحك #F4C430, صدمة #7C5CFF, غضب #C81E3A, استغراب #2CB6C4, إحراج/صمت #F17FB2, موافقة #4CAF6D, رفض #6E8296, سخرية #D98E04, حماس #E8712E
  - S03: Categories filter vs data-only vs destination — VERSION DRIFT — Fixed filter bar as main nav vs data-only + color internal
  - P-20 Rubric 6: لا يذكر فئة صريحًا — 6 معايير نهائية نظافة فنية + هوية يمنية + أخلاقي + بياناته جاهزة + تنوع + جاهز للاستخدام — لا فئة
  - 6K: Admin CRUD للفئات (بُني حديثًا) — T-03 DB Category=9 active — Reaction=12 published seed — Category model موجود — Reaction.categoryId موجود
  - P-14 Search Nature DECISION-007: البحث بالكلمات — ليس بالفئة — اسم الرياكشن، اسم الشخص، جملة، وصف مشهد، كلام مضمن — OPEN-Q-07
  - S09 T-04: Media pipeline local — لا علاقة بالفئات
  - PD-09 كان OPEN — HISTORY + EVIDENCE done 2026-09-14 — Categories role filter vs data-only

- **New:**

  **القرار:** إزالة كاملة للفئات (Full Removal) على مرحلتين — مسار آمن — مصيري Pivotal — لا يُنفَّذ فورًا — توثيق فقط الآن.

  ```
  STAGE A — الآن (بدون Migration / ترحيل) — آمنة — قابلة للتراجع:

  1. UI Removal (إزالة من الواجهة):
  - حذف CategoryNav (شريط الفئات) من الرئيسية
  - حذف ?cat= من البحث
  - حذف اختيار الفئة من نموذج الرفع (SubmissionForm + ReactionForm)
  - حذف "الفئة" من صفحة التفاصيل /r/[code]
  - حذف لون الفئة من البطاقة (ReactionCard) — B-06 يبقى لكن لا يُعرض

  2. Admin Hidden (إخفاء الإدارة):
  - صفحة إدارة الفئات تُخفى من القائمة — لا رابط في Admin menu
  - كود 6K يبقى (يمكن استرجاعه) — لا حذف كود الآن
  - الـ route /admin/categories يبقى (لكن لا يظهر رابط) — hidden not deleted

  3. Schema Kept (البنية محفوظة):
  - Category model (جدول الفئات) يبقى — Prisma schema.prisma يبقى
  - Reaction.categoryId (المفتاح الأجنبي) يبقى — 12 رياكشن seed مرتبطة
  - لا Migration الآن — لا DROP TABLE — لا ALTER TABLE — آمن

  4. Brand Kept (الهوية محفوظة):
  - 9 ألوان الفئات تبقى في Brand v1.0 LOCKED — B-06
  - نحتفظ بها للدراسة — لا تعديل الآن
  - لا تعديل tokens.css الآن

  5. البديل — Collections + Keywords + Search:
  - Collections (المجموعات) = التصنيف الأساسي — موضوعي: طلاب، قروبات، بلا سياق — P-32
  - Keywords (الكلمات المفتاحية) = البحث — يغطي أوسع — OPEN-Q-08
  - Search = حر بالكلمات (بدون فلتر) — P-14 — DECISION-007 — OPEN-Q-07

  STAGE B — بعد P0 Git (Stage 7 / Stage 4) — خطير — يُنفَّذ فقط بعد أن يُحسم P0 Git:
  - P0 Git = commit كامل + remote (نسخة بعيدة) + backup (نسخة احتياطية) — P0-1 Git branch master only 1 commit 331c1b3 + 28 modified + 119 untracked — خطر فقدان — SEC-04 Schema drift — يجب حسمه أولًا

  عندها يُنفَّذ:

  1. Migration (ترحيل) آمن:
  ```sql
  DROP TABLE Category;              -- حذف 9 فئات
  ALTER TABLE Reaction              -- حذف المفتاح الأجنبي
    DROP COLUMN categoryId;         -- من 12 رياكشن seed + 300-500 لاحقًا
  ```

  2. حذف 20+ موضع في الكود:
  - CategoryNav component — شريط الفئات
  - Admin Categories page (6K كامل) — CRUD categories + /new + /[slug]/edit
  - CategoryDTO في API — /api/categories + /api/admin/categories
  - Category references في ReactionForm — اختيار الفئة
  - Category filtering في Search — ?cat= + categoryId filter + CategoryNav logic
  - Category colors usage في ReactionCard — B-06 usage (لكن B-06 نفسه يبقى للدراسة Stage 4)
  - categoryRepository.findActive — counts active only — bug includes draft/archived

  3. تعديل Brand v1.0 — دراسة الاستخدام النهائي لـ9 ألوان:
  - Visual Accents (لمسات بصرية)? — استخدام الألوان كلمسات بصرية عامة
  - Mood Tags (وسوم مزاجية)? — تحويلها لوسوم مزاجية بدل فئات
  - حذف نهائي? — حذف الألوان إذا لم نحتاجها
  - القرار في Stage 4 (Experience) مع تفاصيل التنفيذ في Stage 7 (Technical)
  - B-06 يبقى Stage A → يُعدّل Stage B — محفوظ للدراسة

  Revisable — مرن — قابل للتراجع:
  - Stage A قابل للتراجع (لا Migration) — إرجاع CategoryNav + ?cat= + Admin link — سهل
  - Stage B قابل للتراجع (قبل Migration) — إذا لم ننفذ Migration بعد — يمكن التراجع
  - إذا احتجنا Categories لاحقًا → نستعيد من Stage A — لا Migration = سهل الاسترجاع
  - القرار مرن — ليس نهائي لا رجعة فيه

  Terminology — المصطلحات:
  - Categories → الفئات (تصنيف عاطفي: ضحك، صدمة، غضب، استغراب، إحراج/صمت، موافقة، رفض، سخرية، حماس)
  - Collections → المجموعات (تصنيف موضوعي: طلاب، قروبات، بلا سياق) — التصنيف الأساسي الجديد
  - Keywords → الكلمات المفتاحية (للبحث) — البحث الأساسي
  - Migration → الترحيل / الهجرة (تغيير بنية قاعدة البيانات)
  - Schema → المخطط / البنية (بنية قاعدة البيانات)
  - DROP TABLE → حذف الجدول
  - ALTER TABLE → تعديل الجدول
  - UI → واجهة المستخدم
  ```

**Reason:**

1) DECISION-007 Value + P-14 Search Nature — البحث بالكلمات — ليس بالفئة — اسم الرياكشن نفسه (مصطفى المومري)، اسم الشخص (هديل مانع)، جملة محددة ("اقرب اقرب لو انت رجال")، وصف المشهد (فيديو الذي يعد الرز)، الكلام المضمن في الفيديو — OPEN-Q-07 — البحث ليس "بالموقف" فقط — يشمل اسم، شخص، جملة، وصف مشهد، كلام مضمن — DECISION-007 تصحيح 1 — الفئة لا تغطي هذا — Keywords تغطي أوسع
2) Pinterest-like — لا يعتمد على Categories في الصفحة الأولى — P-08 Presentation Pinterest-like Masonry Grid visual only — Pinterest يعرض صور بدون فلتر فئات في الرئيسية — البحث + التصفح + Collections كافية — لا نحتاج CategoryNav
3) Collections (المجموعات) أقوى للسياق — موضوعي: طلاب، قروبات، بلا سياق — P-32 Collections as Primary Taxonomy — Collections = مجموعات الأدمن (طلاب، قروب، بلا سياق) — أقوى للسياق من الفئات العاطفية — DECISION-008 Audience أي شخص في موقف — Collections تغطي السياق الاجتماعي (طلاب، قروب) — أفضل من الفئات العاطفية فقط
4) Keywords (الكلمات المفتاحية) تغطي البحث بشكل أوسع — OPEN-Q-08 Keyword Tool منفصل — أداة كلمات مفتاحية مرنة تتطور لخوارزمية — S1 Axis B — Keywords = البحث الأساسي — تغطي مواقف أكثر بدون الحاجة لتصنيف عاطفي — P-20 بياناته جاهزة + كلمات مفتاحية أساسية + استخراج تلقائي OPEN-Q-09
5) الأمان أولًا — P0 Git محجوب — Migration خطير — T-10 Git branch master only 1 commit 331c1b3 2026-08-24 + 28 modified + 119 untracked + no remote — خطر فقدان 147 ملفًا — لا نقطة رجوع — P0-1 — SEC-04 Schema drift 3 indexes not in schema.prisma → next migrate dev proposes DROP — Migration الآن = مخاطرة عالية — Stage A بدون Migration = آمن
6) قابلية التراجع — Stage A يمكن التراجع عنه بسهولة — لا Migration — إرجاع CategoryNav + ?cat= + Admin link — سهل — Stage B قابل للتراجع قبل Migration — إذا احتجنا Categories لاحقًا → نستعيد من Stage A
7) 6K لا يُهدر — يُخفى (قابل للاسترجاع) بدل الحذف الفوري — Admin CRUD للفئات بُني حديثًا — لا نحذف كود 6K الآن — نخفيه من القائمة — يمكن استرجاعه إذا احتجنا — يحمي جهد 6K
8) Brand محفوظ — للتعديل المدروس لاحقًا — B-06 9 category colors LOCKED — ضحك #F4C430، صدمة #7C5CFF، غضب #C81E3A، استغراب #2CB6C4، إحراج/صمت #F17FB2، موافقة #4CAF6D، رفض #6E8296، سخرية #D98E04، حماس #E8712E — نحتفظ بها للدراسة Stage 4 — لا تعديل الآن — دراسة: Visual Accents؟ Mood Tags؟ حذف نهائي؟ — القرار في Stage 4 مع تنفيذ Stage 7
9) قرار مصيري Pivotal — يحتاج مسار آمن، ليس قرار متسرع — إزالة كاملة للفئات = قرار كبير — يؤثر على IA، Search، Admin، Brand، DB — يحتاج مرحلتين — Stage A الآن آمنة + Stage B بعد P0 Git — لا ننفذ أي شيء الآن — فقط نوثق — التنفيذ الفعلي يبدأ بعد اكتمال Stage 3 + Stage 4 + P0 Git — يحمي من خطأ Migration + فقدان بيانات + تعديل Brand قبل وقت مناسب

**Alternative rejected:**

- الخيار 1 (الحد الأدنى — إبقاء الفئات كـ data-only + color internal، لا filter bar) — REJECTED per DECISION-014 — لا يصل للإزالة الكاملة — نريد Full Removal — لا يلبي طلب الإزالة — REJECTED
- الخيار 3 (دمج ذكي — Categories + Collections + Keywords هجين — Categories كـ mood tags + Collections كـ context + Keywords كـ search) — REJECTED per DECISION-014 — لا يُلبي طلب الإزالة — نريد إزالة كاملة — Collections كتصنيف أساسي + Keywords كبحث يكفي — لا نحتاج دمج — REJECTED
- التنفيذ الفوري (بدون مرحلتين — DROP TABLE Category + ALTER TABLE Reaction DROP categoryId الآن + حذف 20+ موضع + تعديل Brand الآن) — REJECTED per DECISION-014 — مخاطرة عالية — P0 Git محجوب — T-10 Git dirty + no remote + SEC-04 drift — Migration خطير — يحتاج مسار آمن Stage A/B — REJECTED

**Impact:**

- PD-09 CLOSED — Stage 3 PD-09 CLOSED — CONFLICT-009 CLOSED — DECISION-014 ACCEPTED 2026-09-14 — 62 → 64 facts
- P-31 NEW: Categories Removed (Staged A/B — إزالة على مرحلتين — Stage A الآن بدون Migration آمنة قابلة للتراجع — UI Removal CategoryNav + ?cat= + اختيار الفئة من نموذج الرفع + الفئة من /r/[code] + لون الفئة من البطاقة + Admin Hidden صفحة إدارة الفئات تُخفى من القائمة كود 6K يبقى route يبقى + Schema Kept Category model + Reaction.categoryId يبقى لا Migration + Brand Kept 9 ألوان B-06 تبقى للدراسة + البديل Collections=التصنيف الأساسي + Keywords=البحث + Search حر بالكلمات — Stage B بعد P0 Git — commit كامل + remote + backup — Migration آمن DROP TABLE Category + ALTER TABLE Reaction DROP categoryId + حذف 20+ موضع CategoryNav + Admin Categories 6K + CategoryDTO + Category refs + Category filtering + Category colors usage + تعديل Brand v1.0 دراسة 9 ألوان Visual Accents/Mood Tags/حذف نهائي Stage4/7 — Revisable مرن Stage A قابل للتراجع Stage B قابل للتراجع قبل Migration — إذا احتجنا Categories نستعيد من Stage A)
- P-32 NEW: Collections as Primary Taxonomy (المجموعات كتصنيف أساسي — موضوعي: طلاب، قروبات، بلا سياق — أقوى للسياق من الفئات العاطفية — البديل الأساسي بعد إزالة الفئات — Pinterest-like لا يعتمد على Categories — Collections + Keywords + Search تكفي — PD-10 سيُوسَّع HISTORY+EVIDENCE)
- Canonical Facts: 62 → 64 (8 brand + 32 product + 6 IA + 10 technical + 8 security)
- CONFLICT-009 Categories Role: يُغلق بـ DECISION-014 — Fixed filter bar vs data-only vs destination → Full Removal Staged — CLOSED
- 6K Admin CRUD: يبقى مخفيًا Stage A (قابل للاسترجاع) → يُحذف Stage B (بعد P0 Git) — لا يُهدر
- Brand v1.0 B-06 9 colors: يبقى Stage A (محفوظ للدراسة) → يُعدّل Stage B (Visual Accents/Mood Tags/حذف) — دراسة Stage4/7
- P-20 Rubric 6: لا يذكر فئة صريحًا — لا يحتاج حذف — "هوية يمنية" تبقى — لا تعتمد على الفئة — متوافق
- P-04 Bumper REJECTED: لا علاقة — يبقى REJECTED
- P-27+P-28 Duration 2-60s + Reaction Criterion: لا علاقة — يبقيان ACCEPTED
- P-29+P-30 Aspect أي مقاس + لا فراغ أسود + هل هي رياكشن؟: لا علاقة — يبقيان ACCEPTED
- Stage 4 (Experience): دراسة استخدام 9 ألوان B-06 — Visual Accents؟ Mood Tags؟ حذف نهائي؟ — كيفية تطبيق "بدون فراغ أسود" + Safe Area Guides لكل مقاس + Qussasa مراجعة لـ 16:9
- Stage 7 (Technical): تنفيذ Migration + حذف 20+ موضع — CategoryNav + Admin Categories 6K + CategoryDTO + Category refs + filtering + colors usage — بعد P0 Git commit+remote+backup — آمن — T-10 + SEC-04
- Admin: يفقد فلتر سريع Category — لكن Collections + Keywords تكفي — P-32 Collections as Primary Taxonomy
- Search: ?cat= يُحذف — Search حر بالكلمات بدون فلتر — P-14 + DECISION-007 + OPEN-Q-07 + OPEN-Q-08
- YEMREACT-HISTORICAL-NOT-CURRENT.md: VD-03 Categories role → HISTORICAL — S10 9 category colors → MOVED TO "محفوظة للدراسة Stage 4" — B-06 محفوظ للدراسة
- NEXT: PD-10 Collections — HISTORY + EVIDENCE فقط — بانتظار أمر حمدان — Collections الآن لها دور أكبر — التصنيف الأساسي — PD-10 سيُوسَّع

**Stage:** Stage 3 — PD-09 — CLOSED — DECISION-014 ACCEPTED 2026-09-14 — NEXT PD-10 Collections — CONFLICT-009 CLOSED — 62 → 64 facts

**Evidence:** S10 Brand v1.0 LOCKED B-06 9 category colors #F4C430 #7C5CFF #C81E3A #2CB6C4 #F17FB2 #4CAF6D #6E8296 #D98E04 #E8712E, S03 Categories filter vs data-only vs destination VERSION DRIFT, CONFLICT-009 Categories Role OPEN since Phase1, P-20 Rubric 6 لا يذكر فئة, 6K Admin CRUD للفئات built, P-14 Search Nature DECISION-007 البحث بالكلمات ليس بالفئة + OPEN-Q-07 اسم شخص جملة وصف مشهد كلام مضمن, S09 T-03 DB Category=9 active Reaction=12 categoryId exists, S09 T-10 Git P0-1 1 commit + dirty + no remote + SEC-04 drift 3 indexes, DECISION-007 Value منتقاة + قابلة للبحث + جاهزة, DECISION-011 Pipeline لقطات قصيرة عشوائية, DECISION-012 Duration 2-60s + Reaction Criterion هل هي رياكشن, DECISION-013 Aspect أي مقاس + لا فراغ أسود + هل هي رياكشن, P-08 Pinterest-like visual only لا يعتمد Categories, P-32 Collections as Primary Taxonomy

---

## Topic 9 — PD-09 — CLOSED — DECISION-014 ACCEPTED — Stage 3 — CONFLICT-009 CLOSED

- Categories Full Removal (Staged A/B) — إزالة كاملة للفئات على مرحلتين — مسار آمن — مصيري Pivotal — لا يُنفَّذ فورًا — توثيق فقط الآن — لا كود/Git/DB
- Stage A الآن بدون Migration آمنة قابلة للتراجع: UI Removal حذف CategoryNav من الرئيسية + حذف ?cat= من البحث + حذف اختيار الفئة من نموذج الرفع + حذف الفئة من /r/[code] + حذف لون الفئة من البطاقة — Admin Hidden صفحة إدارة الفئات تُخفى من القائمة كود 6K يبقى route يبقى — Schema Kept Category model + Reaction.categoryId يبقى لا Migration — Brand Kept 9 ألوان B-06 تبقى للدراسة لا تعديل — البديل Collections=التصنيف الأساسي + Keywords=البحث + Search حر بالكلمات بدون فلتر
- Stage B بعد P0 Git Stage7/4: يُنفَّذ فقط بعد حسم P0 Git commit كامل + remote + backup — Migration آمن DROP TABLE Category + ALTER TABLE Reaction DROP categoryId من 12 رياكشن + 300-500 لاحقًا — حذف 20+ موضع CategoryNav + Admin Categories 6K كامل + CategoryDTO + Category refs + filtering + colors usage + تعديل Brand v1.0 دراسة 9 ألوان Visual Accents/Mood Tags/حذف نهائي Stage4/7
- Revisable مرن: Stage A قابل للتراجع لا Migration + Stage B قابل للتراجع قبل Migration + إذا احتجنا Categories نستعيد من Stage A
- Reason: DECISION-007 البحث بالكلمات ليس بالفئة + Pinterest-like لا يعتمد Categories + Collections أقوى للسياق موضوعي طلاب قروبات بلا سياق + Keywords تغطي أوسع + الأمان أولًا P0 Git محجوب Migration خطير + قابلية التراجع Stage A سهل + 6K لا يُهدر يُخفى قابل للاسترجاع + Brand محفوظ للدراسة + قرار مصيري يحتاج مسار آمن ليس متسرع
- REJECTED: الخيار 1 الحد الأدنى data-only لا يصل للإزالة الكاملة + الخيار 3 دمج ذكي Categories+Collections+Keywords لا يلبي طلب الإزالة + التنفيذ الفوري بدون مرحلتين مخاطرة عالية P0 Git محجوب
- Impact: P-31 Categories Removed Staged A/B + P-32 Collections as Primary Taxonomy — 62→64 facts — CONFLICT-009 CLOSED — 6K يبقى مخفيًا Stage A → يُحذف Stage B — Brand v1.0 B-06 يبقى Stage A → يُعدّل Stage B — P-20 Rubric لا يذكر فئة متوافق — P-04 Bumper لا علاقة — P-27+P-28 Duration لا علاقة — P-29+P-30 Aspect لا علاقة — Stage4 دراسة 9 ألوان + Stage7 Migration+حذف 20+ موضع بعد P0 Git — Admin يفقد فلتر سريع لكن Collections+Keywords تكفي — Search ?cat= يُحذف حر بالكلمات — YEMREACT-HISTORICAL-NOT-CURRENT VD-03 HISTORICAL + B-06 محفوظ للدراسة
- NEXT: PD-10 Collections — HISTORY + EVIDENCE فقط — Collections الآن لها دور أكبر التصنيف الأساسي — PD-10 سيُوسَّع — بانتظار أمر حمدان — لا كود/Git/DB — لا Migration — لا حذف Schema — لا تعديل Brand

## DECISION-015 — Collections as Primary Taxonomy — ACCEPTED — Stage 3 — PD-10

- **Status:** ACCEPTED — CLOSED — PD-10 CLOSED — Stage 3 CLOSED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-14 — Stage 3 — PD-10 Collections
- **Topic:** المجموعات كتصنيف أساسي بعد إزالة الفئات

**Previous → New:**

- **Previous:**
  - Collections كانت "أداة أدمن فقط" (S03 + Axis C) — تنظيم داخلي، ليست وجهة مستقلة
  - الدور: تنظيم داخلي — 3 مجموعات موجودة (طلاب، قروبات، بلا سياق) — T-03 DB Collection=3 students 3 group-chat 3 no-context 2 CollectionItem=8 — T-02 Routes /collections + /collections/[slug] — 6K Admin CRUD + CollectionItems يدوي
  - P-32 (DECISION-014): Collections صارت Primary Taxonomy — 62→64 facts — PD-10 كان OPEN — HISTORY+EVIDENCE موسّع
  - CONFLICT: Collections role rail vs page vs album — VERSION DRIFT — Stage 5 pending

- **New:**

  **Collections (المجموعات) = التصنيف الأساسي للمحتوى بعد إزالة الفئات.**

  ```\n  1. من يُنشئ المجموعات؟\n  الأدمن فقط (Admin-Only Curated):\n  - المستخدم لا يستطيع إنشاء مجموعات\n  - المجموعات منتقاة يدويًا — كل مجموعة مدروسة\n  - الجودة أعلى — Curated = منسّق يدويًا\n  - Reason: جودة + بساطة — لا Boards معقدة — Flat Saves تبقى DECISION-003\n\n  2. كيف يدخل الرياكشن المجموعة؟\n  يدوي (Manual):\n  - الأدمن يضيف الرياكشن للمجموعة\n  - عند الرفع (Upload Form) — خيار إضافة لمجموعة\n  - عند المراجعة (Admin Review) — إضافة لمجموعة\n  - لا إضافة تلقائية — لا اقتراحات نظام — الأدمن يقرر\n  - Reason: تحكم تحريري — P-20 Rubric + P-05 human decision\n\n  3. كيف تظهر المجموعات في الواجهة؟\n  Rail في الرئيسية + صفحة مستقلة /collections:\n  - Rail في الرئيسية:\n    - صف أفقي تحت \"جديد المكتبة\" (أو حسب ترتيب Stage 4)\n    - يعرض 3-5 مجموعات (المختارة)\n    - عنوان + عدد + صورة غلاف\n    - عند الضغط → /collections/[slug]\n  - صفحة /collections:\n    - قائمة كل المجموعات النشطة\n    - عرض كبطاقات (عنوان + عدد + غلاف)\n    - عند الضغط → /collections/[slug]\n  - صفحة /collections/[slug]:\n    - عنوان المجموعة + وصف\n    - شبكة رياكشنات (Pinterest-like Masonry)\n    - زر \"متابعة المجموعة\" (للمستخدم المسجل) — Follow\n  - Reason: حضر متوازن — Rail للاكتشاف السريع + Page للتصفح الكامل\n\n  4. Multi-membership (العضوية المتعددة):\n  نعم — الرياكشن يمكن أن يكون في أكثر من مجموعة:\n  - مثال: \"رياكشن للجامعة\" → في \"طلاب\" + \"قروبات\" + \"بلا سياق\"\n  - Schema الحالي يدعم (Foreign Key مركّب CollectionItem collectionId+reactionId)\n  - لا حد أقصى لعدد المجموعات للرياكشن الواحد\n  - Reason: مرونة — رياكشن يخدم أكثر من سياق — لا تقييد\n\n  5. المستخدم يحفظ المجموعة؟\n  نعم — المتابعة (Follow):\n  - المستخدم المسجل يمكنه متابعة مجموعة\n  - المجموعة المتابعة تظهر في /saved (قسم منفصل)\n  - ليس Board (لوحة) — هي متابعة فقط — Flat Saves تبقى كما هي DECISION-003\n  - Follow منفصل عن Save — Save = حفظ رياكشن فردي — Follow = متابعة مجموعة كاملة\n  - Reason: تفاعل بدون تعقيد — المستخدم يتابع دون Boards معقدة — P-06 Save core CTA يبقى\n\n  6. كم مجموعة عند الإطلاق؟\n  3 الموجودة فقط:\n  - \"طلاب\" (students)\n  - \"قروبات\" (group-chat)\n  - \"بلا سياق\" (no-context)\n  - تُبقى كما هي — التوسع لاحقًا حسب النمو — لا إضافة جديدة قبل الإطلاق\n  - Reason: بساطة — لا تعقيد قبل الإطلاق — 3 كافية للاختبار\n\n  7. SEO:\n  نعم — قابلة للفهرسة:\n  - /collections — Meta title \"المجموعات | يمن رياكت\"\n  - /collections/[slug] — Title: \"[اسم المجموعة] | يمن رياكت\"\n  - Meta description لكل مجموعة\n  - OpenGraph image (صورة الغلاف)\n  - Canonical URL — الرابط الأصلي لتفادي التكرار\n  - Sitemap يتضمنها — خريطة الموقع\n  - Reason: اكتشاف — صفحات موضوعية تجلب زوار من Google — Acquisition DECISION-008 من بحث\n\n  تفاصيل مؤجلة — Stage 4/5/6/7:\n  1. ترتيب Rail في الرئيسية: قبل/بعد \"جديد المكتبة\"؟ كم مجموعة في Rail؟ 3؟ 5؟ 10؟ → Stage 4 Experience\n  2. تصميم بطاقة المجموعة: عنوان+عدد+غلاف — الغلاف صورة أول رياكشن؟ صورة مختارة؟ → Stage 4\n  3. Follow في /saved: قسم منفصل داخل الصفحة؟ تبويب \"رياكشنات\" + \"مجموعات\"؟ → Stage 5 IA + Stage 6 Flows\n  4. Collections في Bottom Nav: هل للمجموعات وجهة في Bottom Nav؟ كان مقترحًا سابقًا SUPERSEDED → Stage 5 IA\n  5. علاقة Collections بـSubmissions: هل الأدمن يضيف مجموعة عند قبول مساهمة؟ → Stage 6 Flows\n\n  Revisable — مرن:\n  - القرار مرن — يمكن تعديل أي بند لاحقًا\n  - Multi-membership قد يُقيَّد إذا احتجنا\n  - Follow قد يُوسَّع أو يُقيَّد\n  - SEO قد يُخفَّف لمجموعات معينة\n\n  Terminology — المصطلحات:\n  - Collections → المجموعات (تصنيف موضوعي: طلاب، قروبات، بلا سياق) — التصنيف الأساسي الجديد\n  - Curated → منسّق (يُختار يدويًا)\n  - Multi-membership → العضوية المتعددة\n  - Follow → المتابعة — زر \"متابعة المجموعة\"\n  - Rail → شريط أفقي (صف من البطاقات)\n  - Page → صفحة مستقلة /collections + /collections/[slug]\n  - SEO → تحسين محركات البحث — قابلية الفهرسة\n  - OpenGraph → وسوم المشاركة الاجتماعية — og:image غلاف\n  - Sitemap → خريطة الموقع — sitemap.xml يتضمن collections\n  - Canonical URL → الرابط الأصلي لتفادي التكرار\n  - Board → لوحة (مفهوم Pinterest — مرفوض per DECISION-003 Flat Saves)\n  ```\n

**Reason:**

1) DECISION-014 (Categories Removed): Collections تصبح التصنيف الأساسي (P-32) — 62→64 — P-31 + P-32 + P-33 + P-34 متكاملان — لا تعارض
2) السياق أقوى من العاطفة: "طلاب" أوضح من "سخرية" — P-32 Collections as Primary Taxonomy موضوعي طلاب قروبات بلا سياق أقوى للسياق من الفئات العاطفية ضحك صدمة غضب — DECISION-014 Reason 3 — P-15 Audience أي شخص في موقف — Collections تغطي السياق الاجتماعي
3) Curated = جودة: الأدمن وحده يضمن جودة المجموعات — P-20 Rubric 6 + P-05 human decision + P-18 Modified Arena-Agent يبني حمدان يرفع — تحكم تحريري
4) Multi-membership = مرونة: رياكشن يخدم أكثر من سياق — Schema الحالي يدعم CollectionItem مركّب — لا حد أقصى — مرونة بدون تعقيد
5) Follow = التفاعل: المستخدم يتابع دون Boards معقدة — P-06 Save is core CTA + P-07 Flat Saves + DECISION-003 — Follow منفصل عن Save — Save فردي + Follow مجموعة — ليس Board — Flat Saves تبقى
6) SEO = اكتشاف: صفحات موضوعية تجلب زوار من Google — DECISION-008 Acquisition من بحث — OpenGraph + Sitemap + Canonical — Discovery
7) 3 مجموعات = بسيط: لا تعقيد قبل الإطلاق — T-03 DB Collection=3 + CollectionItem=8 موجودة — تُبقى كما هي — التوسع لاحقًا حسب النمو — 300-500 Target P-13
8) Rail + Page = حضر متوازن: لا تكرار مفرط — Rail في الرئيسية للاكتشاف السريع + Page /collections للتصفح الكامل — P-09 Core Loop Discover limited + P-11 + IA-01 Home=Library

**Alternative rejected:**

- من ينشئ (ب) المستخدمون فقط: رُفض — جودة منخفضة — لا تحكم تحريري — Boards معقدة
- من ينشئ (ج) الاثنان (أدمن + مستخدمون): رُفض — تعقيد + Boards مؤجلة per DECISION-003 Flat Saves — لا Boards الآن
- من ينشئ (د) تلقائي: رُفض — لا يحترم السياق — يحتاج خوارزمية — OPEN-Q-08 Keyword Tool مؤجل — لا تلقائي الآن
- كيف يدخل (ب) تلقائي: رُفض — الأدمن يقرر — تحكم تحريري — P-05 human decision
- كيف يدخل (ج) تلقائي + موافقة: رُفض — تعقيد الآن — يدوي أبسط — Manual الآن
- أين تظهر (أ) Rail فقط: رُفض — تحتاج صفحة للاكتشاف — /collections صفحة مستقلة مهمة — Discovery + SEO
- أين تظهر (ب) Page فقط: رُفض — Rail في الرئيسية حيوي — اكتشاف سريع — Home=Library + Rail
- Multi-membership (ب) لا: رُفض — يقيد المرونة — رياكشن يخدم أكثر من سياق — مثال جامعة → طلاب+قروبات+بلا سياق
- حفظ (أ) لا: رُفض — Follow قيمة للمستخدم — تفاعل بدون Boards — متابعة مجموعة مفيدة
- حفظ (ج) Group + Flat مختلط: رُفض — Flat Saves تبقى DECISION-003 — Follow منفصل — لا خلط — Group+Flat مختلط يعقد
- كم (ب) 3+5-10 مجموعات جديدة قبل الإطلاق: رُفض — لا حاجة الآن — 3 الموجودة كافية — بساطة
- SEO (ب) لا: رُفض — نريد Discovery — صفحات موضوعية تجلب زوار — Acquisition من بحث — DECISION-008

**Impact:**

- PD-10 CLOSED — Stage 3 CLOSED — Stage 3 Content & Editorial System مكتمل الآن (PD-04 + PD-05 + PD-06 SKIPPED + PD-07 + PD-08 + PD-09 + PD-10) — 64 → 66 facts
- P-33 NEW: Collections Admin-Only Curated — من يُنشئ الأدمن فقط — لا يستطيع المستخدم إنشاء مجموعات — منتقاة يدويًا — جودة أعلى — Curated منسّق — لا Boards — Flat Saves تبقى DECISION-003 — يدوي Manual عند الرفع + عند المراجعة — لا تلقائي — لا اقتراحات — الأدمن يقرر — P-05 human decision
- P-34 NEW: Collections Multi-Membership + Follow + SEO — Multi-membership نعم — الرياكشن في أكثر من مجموعة — لا حد أقصى — Schema يدعم FK مركّب — Follow نعم — متابعة مجموعة — المستخدم المسجل يتابع — تظهر في /saved قسم منفصل — ليس Board — Flat Saves تبقى — SEO نعم — قابلة للفهرسة — /collections Meta title + /collections/[slug] Title + Meta description + OpenGraph image غلاف + Canonical URL + Sitemap — 3 مجموعات عند الإطلاق طلاب قروبات بلا سياق تُبقى كما هي — Rail في الرئيسية صف أفقي 3-5 مجموعات عنوان+عدد+غلاف → /collections/[slug] + Page /collections قائمة بطاقات + /collections/[slug] عنوان+وصف+Masonry + زر متابعة — Revisable مرن
- P-32 UPDATED: Collections as Primary Taxonomy — يُعزَّز بتفاصيل DECISION-015 — الآن Admin-Only Curated + Manual + Rail+Page + Multi-membership + Follow + SEO + 3 مجموعات — 64→66 — PD-10 موسّع CLOSED
- Canonical Facts: 64 → 66 (8 brand + 34 product + 6 IA + 10 technical + 8 security)
- PD-09 (DECISION-014) — Categories Removed: لا تعارض — Collections الآن Primary Taxonomy — P-31 + P-32 + P-33 + P-34 متكاملان — P-31 Categories Removed Staged A/B + P-32 Collections Primary + P-33 Admin-Only Curated + P-34 Multi+Follow+SEO — متوافق
- P-06 (Save is core CTA): Follow منفصل عن Save — Flat Saves تبقى DECISION-003 — Save = حفظ رياكشن فردي — Follow = متابعة مجموعة كاملة — ليس Board — هو زر "متابعة" — P-07 Flat Saves يبقى — متوافق
- P-20 (Rubric 6): "بياناته جاهزة" — هل تشمل "ينتمي لمجموعة"؟ — لا — Rubric يبقى كما هو (اسم لو معروف + اسم شخص + جملة/كلام مضمن + وصف مشهد + كلمات مفتاحية أساسية + استخراج تلقائي OPEN-Q-09) — لا يُضاف "ينتمي لمجموعة" — المجموعة تحريرية منفصلة — متوافق — لا تعديل Rubric
- 6K (Admin CRUD Collections): يبقى — لكن يُوسَّع في Stage 7 — إضافة Follow Schema إذا احتجنا جدول جديد — لكن Foreign Key موجود — CollectionItem يدعم Multi-membership — لا Migration الآن
- Schema: لا Migration — يبقى كما هو — Collection=3 + CollectionItem=8 + Reaction=12 — Multi-membership مدعوم — Follow قد يحتاج جدول جديد FollowedCollection userId+collectionId — مؤجل Stage 7
- T-02: /collections + /collections/[slug] موجودان — يُحسَّنان — Rail + Page + SEO Metadata
- Stage 4 (Experience): ترتيب Rail في الرئيسية + تصميم البطاقات + دراسة 9 ألوان الفئات من DECISION-014 + Safe Area Guides + Overlays جديدة + Qussasa مراجعة لـ 16:9
- Stage 5 (IA): Collections في Bottom Nav؟ — كان مقترحًا SUPERSEDED — يُحسم الآن — Follow في /saved — تبويب رياكشنات + مجموعات؟ — قسم منفصل؟
- Stage 6 (Flows): تدفق Follow + Saved + إضافة لمجموعة عند قبول مساهمة — Submissions → Collections
- Stage 7 (Technical): SEO Metadata + Sitemap + OpenGraph + Canonical + Follow Schema إذا احتجنا + تحسين /collections + /collections/[slug]
- YEMREACT-HISTORICAL-NOT-CURRENT.md: Collections role rail vs page vs album VERSION DRIFT → RESOLVED — Rail + Page — DECISION-015 — PD-10 CLOSED — Stage 3 CLOSED
- NEXT: Stage 4 — Experience & Identity — HISTORY + EVIDENCE فقط — بانتظار أمر حمدان

**Stage:** Stage 3 — PD-10 — CLOSED — DECISION-015 ACCEPTED 2026-09-14 — Stage 3 CLOSED — 64 → 66 facts — NEXT Stage 4 Experience & Identity

**Evidence:** S10 Brand v1.0, S03 Collections tool admin-only + Axis C Rail vs Page, T-03 DB Collection=3 students 3 group-chat 3 no-context 2 CollectionItem=8 + Reaction=12, T-02 Routes /collections + /collections/[slug] existing, IA-01 Home=Library + Collections كألبومات, P-31 Categories Removed Staged A/B + P-32 Collections as Primary Taxonomy, P-06 Save core CTA + P-07 Flat Saves DECISION-003, P-05 human decision + P-20 Rubric 6 بياناته جاهزة, P-13 Library Size 300-500, DECISION-014 Categories Full Removal, DECISION-008 Acquisition من بحث SEO, CONFLICT-009 CLOSED, Collections role VERSION DRIFT, 6K Admin CRUD Collections existing

---

## Topic 10 — PD-10 — CLOSED — DECISION-015 ACCEPTED — Stage 3 CLOSED

- Collections = التصنيف الأساسي بعد إزالة الفئات — P-32 UPDATED + P-33 + P-34 — 64→66 facts
- من يُنشئ: الأدمن فقط (Admin-Only Curated) — المستخدم لا ينشئ — منتقاة يدويًا — جودة أعلى — Curated منسّق — لا Boards — Flat Saves تبقى — يدوي Manual عند الرفع + عند المراجعة — لا تلقائي
- كيف يدخل: يدوي Manual — الأدمن يضيف — عند الرفع خيار إضافة لمجموعة + عند المراجعة إضافة لمجموعة — لا تلقائي — لا اقتراحات — تحكم تحريري
- أين تظهر: Rail في الرئيسية (صف أفقي 3-5 مجموعات عنوان+عدد+غلاف تحت جديد المكتبة أو حسب Stage4) → /collections/[slug] + Page /collections قائمة بطاقات + /collections/[slug] عنوان+وصف+Masonry + زر متابعة Follow
- Multi-membership: نعم — الرياكشن في أكثر من مجموعة — مثال جامعة → طلاب+قروبات+بلا سياق — Schema يدعم FK مركّب — لا حد أقصى
- حفظ المجموعة: نعم — Follow — متابعة مجموعة — المستخدم المسجل يتابع — تظهر في /saved قسم منفصل — ليس Board — Flat Saves تبقى — Save فردي + Follow مجموعة — P-06 + P-07 متوافق
- كم عند الإطلاق: 3 الموجودة فقط طلاب قروبات بلا سياق تُبقى كما هي — لا إضافة جديدة — التوسع لاحقًا حسب النمو — بساطة
- SEO: نعم — قابلة للفهرسة — /collections Meta title "المجموعات | يمن رياكت" + /collections/[slug] Title "[اسم] | يمن رياكت" + Meta description + OpenGraph image غلاف + Canonical URL + Sitemap يتضمنها — اكتشاف من بحث
- Reason: DECISION-014 Collections تصبح أساسية P-32 + السياق أقوى من العاطفة طلاب أوضح من سخرية + Curated جودة الأدمن وحده + Multi-membership مرونة + Follow تفاعل بدون Boards + SEO اكتشاف صفحات موضوعية + 3 مجموعات بسيط + Rail+Page حضر متوازن
- REJECTED: من ينشئ ب المستخدمون فقط جودة منخفضة + ج الاثنان تعقيد Boards مؤجلة + د تلقائي لا يحترم السياق + كيف يدخل ب تلقائي الأدمن يقرر + ج تلقائي+موافقة تعقيد + أين تظهر أ Rail فقط تحتاج صفحة + ب Page فقط Rail حيوي + Multi ب لا يقيد المرونة + حفظ أ لا Follow قيمة + ج Group+Flat مختلط Flat تبقى + كم ب 3+5-10 لا حاجة + SEO ب لا نريد Discovery
- Impact: P-33 Admin-Only Curated + P-34 Multi+Follow+SEO — 64→66 — P-32 UPDATED يُعزَّز — PD-09 Categories Removed لا تعارض متكامل P-31+P-32+P-33+P-34 — P-06 Save core CTA Follow منفصل Flat Saves تبقى ليس Board — P-20 Rubric لا يشمل ينتمي لمجموعة يبقى كما هو — 6K يبقى يُوسَّع Stage7 — Schema لا Migration Multi يدعم Follow قد يحتاج جدول جديد — T-02 /collections + /collections/[slug] يُحسَّنان — Stage4 ترتيب Rail+تصميم بطاقة+دراسة 9 ألوان+Safe Area+Overlays+Qussasa — Stage5 Collections في Bottom Nav؟ Follow في /saved — Stage6 تدفق Follow+Saved+إضافة عند قبول مساهمة — Stage7 SEO Metadata+Sitemap+OpenGraph+Canonical+Follow Schema
- تفاصيل مؤجلة: ترتيب Rail قبل/بعد جديد المكتبة؟ كم 3/5/10؟ → Stage4 + تصميم بطاقة عنوان+عدد+غلاف صورة أول رياكشن؟ → Stage4 + Follow في /saved قسم منفصل؟ تبويب؟ → Stage5+6 + Collections في Bottom Nav؟ → Stage5 + علاقة Collections بـSubmissions → Stage6
- Revisable مرن: يمكن تعديل أي بند لاحقًا — Multi قد يُقيَّد — Follow قد يُوسَّع/يُقيَّد — SEO قد يُخفَّف
- Stage 3 CLOSED — Content & Editorial System مكتمل الآن PD-04+PD-05+PD-06 SKIPPED+PD-07+PD-08+PD-09+PD-10 — NEXT Stage 4 Experience & Identity — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB — لا Migration — لا تنفيذ — لا تعديل Brand

## DECISION-I01 — Brand Direction — الختم (Al-Khatm) — ACCEPTED — Stage 4 — PD-I01

- **Status:** ACCEPTED — CLOSED — PD-I01 CLOSED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-21 — Stage 4 — Identity Re-Foundation — PD-I01 Brand Direction
- **Topic:** اتجاه الهوية العامة — Modern Product First, Yemeni Character Second — الختم
- **Chosen:** Direction C — الختم (Al-Khatm)

**Context — رحلة الاختيار:**

1. Claude 4.5 أنتج 4 اتجاهات أولى (الترانزستور، قمرية، السوق، المثل) → مرفوضة — كلها "متحف" (ثقافة تسيطر على الموقع)
2. DeepSeek أعاد صياغة الفلسفة: "Modern Product First, Yemeni Character Second" — ChatGPT راجع الاستراتيجية واعتمد الصياغة + أضاف طبقة Content Art Direction
3. Claude 4.5 أنتج 4 اتجاهات ثانية (الزاوية، الحرف، الختم، الإيقاع) → كلها حديثة + بصمة خفيفة
4. Claude 4.5 أنتج 4 Artifacts بصرية فعلية (HTML mockups) → حمدان رأى الأربعة بصريًا
5. حمدان اختار: Direction C — الختم

**Previous → New:**

- **Previous:**
  - Brand v1.0 LOCKED (YemReact-Brand-v1.0-LOCKED.html) — Qussasa Mark + Peel + Watermark 9-15% أعلى + ظل مزدوج + Safe Area 6% top 20% bottom 14% right 6% left + قلب الكتلة — كان LOCKED لكنه تاريخي بعد رحلة Brand Direction الجديدة
  - B-01 to B-08 — Brand Truth — LOCKED — Ink, Qishr Amber, Paper, Coral — Qussasa + Watermark concept — CONFIRMED but CONFLICTED spec 11% vs 14% — CONFLICT-019 OPEN
  - PD-14 Watermark Spec — OPEN — HISTORY+EVIDENCE done — 9-15% أعلى بظل مزدوج vs 14% أسفل-يمين بلا ظل — يحتاج قرار PD-I05
  - S10 Brand v1.0 LOCKED — Persona مثل شعبي رقمي — "خذها. حطها. يمنية." — B-02 + B-03
  - Stage 3 CLOSED — 66 facts — NEXT Stage 4 Experience & Identity — ترتيب Rail + تصميم بطاقة + دراسة 9 ألوان + Safe Area + Overlays + Qussasa + Watermark 11% vs 14% — كان NEXT

- **New:**

  **Direction C — الختم (Al-Khatm) — Brand Direction الجديد — ACCEPTED**

  ```\n  Persona: منهجي، واثق، الشخصيات هي البطل — Systematic, Confident, Characters are Hero\n  Mood: منتج له نظام هوية صغير يتكرر بثقة — يشبه بصمة استوديو لا زخرفة — Product has small identity system repeating confidently — like studio stamp not decoration\n\n  الفلسفة:\n  - البصمة تُبنى حول نظام العلامة + الحركة — Identity built around Mark System + Motion\n  - الشخصية اليمنية تتحول إلى بنية تصنيف (chips) بدل زخرفة سطحية — Yemeni character becomes taxonomy structure not surface decoration\n  - يستغل حقيقة بنيوية: المحتوى فيه شخصيات يمنية بالاسم (ميزة لا يملكها Giphy/Pinterest) — Leverages structural truth: content has Yemeni characters by name (advantage Giphy/Pinterest don't have)\n  - Modern Product First, Yemeni Character Second — منتج حديث أولًا، طابع يمني ثانيًا — DeepSeek philosophy — ChatGPT approved\n\n  الـ 3 Signature Anchors — المراسي الثلاثة المميزة:\n\n  1. Watermark موحد:\n  - شكل هندسي مجرد صغير جدًا (ليس رمزًا ثقافيًا) — Very small abstract geometric shape (not cultural symbol)\n  - زاوية ثابتة من كل وسائط — Fixed corner of all media\n  - يظهر في كل رياكشن (فيديو + صور) — Appears in all reactions\n  - مكان محدد: يُحدد في PD-I05 — Location TBD in PD-I05\n  - يخلف B-07 القديم (تقشّر ورقي بزاوية + Qussasa) — B-07 الآن HISTORICAL — الجديد هندسي مجرد\n  - CONFLICT-019 يحل جزئيًا: Watermark الجديد ليس 11% أعلى-يمين بظل مزدوج ولا 14% أسفل-يمين بلا ظل — هو شكل هندسي مجرد صغير جدًا — التفاصيل في PD-I05\n\n  2. Motion Signature:\n  - حركة \"ختم/قلب\" صغيرة (150-200ms) عند الحفظ/الإضافة لـCollection — Small stamp/flip motion 150-200ms on Save/Add to Collection\n  - توقيع حركي فريد لا يوجد في منافسين — Unique motion signature competitors don't have\n  - يظهر فقط عند الفعل الإيجابي (Save / Add to Collection) — Only on positive action\n  - يُحدد في PD-I09 — منحنى، توقيت، trigger — Details in PD-I09\n  - يتوافق مع P-06 Save is core CTA + P-07 Flat Saves + P-09 Core Loop Save/Share/Use + P-34 Follow\n\n  3. chips اسم الشخصية:\n  - تحت بعض البطاقات (اختياري) — Under some cards (optional)\n  - تحمل اسم الشخصية (مثال: مصطفى المومري، هديل مانع) — Character name chip (e.g. Mustafa Al-Momri)\n  - تصنيف موازٍ للـCollections — Parallel taxonomy to Collections\n  - لا يظهر في كل بطاقة — فقط في الشخصيات المعروفة — Only known characters\n  - يُحدد في PD-I06 (Reaction Card) + PD-I07 (Filters?) — Details in PD-I06 + PD-I07\n  - يستغل P-14 Search Nature + P-20 بياناته جاهزة اسم الشخص + OPEN-Q-07 اسم الشخص — Search by person name\n  - لا يظهر في كل بطاقة — optional — يحترم P-20 تنوع + P-15 Audience أي شخص في موقف\n\n  Modern UI Foundation — الأساس الحديث:\n  - Pinterest-like Masonry Grid — P-08 CONFIRMED — Presentation visual only\n  - Search فوري بلا احتكاك — P-01 Search equal to browsing + P-14 Search Nature + DECISION-007 Value قابل للبحث\n  - Spacing واسع (Linear-style) — Linear-style spacing — حديث\n  - كل الأزرار/التنقل/الحالات نظام واحد صارم — All buttons/navigation/states one strict system\n  - Account flows قياسية بالكامل — Standard account flows — لا تراث في الـUI\n  - لا \"تراث\" في الـUI — No heritage in UI — يرفض المتحف\n  - يتوافق مع P-08 Pinterest-like + IA-01 Home=Library + IA-04 Account Menu/Sheet + P-03 No social feed REJECTED\n\n  Content Art Direction — توجيه فن المحتوى:\n  - الـthumbnails تُقص لإطار موحد — Thumbnails cropped to unified frame — يتوافق مع DECISION-013 بدون فراغ أسود no black bars — يملأ الإطار\n  - الـCaptions قصيرة بلهجة يمنية — Short captions in Yemeni dialect — يتوافق مع B-02 مثل شعبي رقمي + P-15 لهجة يمنية + P-20 هوية يمنية\n  - التصنيف يعتمد على الشخصيات كطبقة اكتشاف — Taxonomy based on characters as discovery layer — chips + Collections + Search\n  - التركيز على \"مين قالها\" أكثر من \"شو قالها\" — Focus on who said it more than what was said — Character-driven discovery\n  - يتوافق مع P-12 Value منتقاة + بجودة عالية + هوية يمنية + P-13 Library Size 300-500 + P-20 بياناته جاهزة اسم الشخص\n\n  الاختبارات التي اجتازها:\n  1. اختبار الإخفاء/الإظهار: أخفِ chips + motion + watermark → Pinterest عادي — أضفها → YemReact واضح — Hide/Show test passed\n  2. اختبار المتحف: لا رموز ثقافية مباشرة (لا كاسيت، لا قمرية، لا خنجر) — لا تكثيف ثقافي — لا خط يد غير رسمي — Museum test passed — No direct cultural symbols\n  3. اختبار الحداثة: Pinterest + Linear + Superhuman — حديث 100% — Modernity test passed — Modern Product First\n\n  Revisable — مرن:\n  - القرار يحدد الشخصية العامة — لا التفاصيل — General personality not details\n  - التفاصيل في PD-I02 Logo/Mark + PD-I03 Colors + PD-I04 Typography + PD-I05 Watermark + PD-I06 Reaction Card + PD-I09 Motion\n  - يمكن تعديل أي Anchor لاحقًا — Watermark شكل/حجم/مكان PD-I05 — Motion منحنى/توقيت PD-I09 — chips متى/حجم/لون PD-I06+PD-I07\n\n  Terminology:\n  - Brand Direction → اتجاه الهوية — الشخصية العامة\n  - Al-Khatm → الختم — بصمة استوديو — Studio stamp\n  - Signature Anchors → المراسي المميزة — Watermark + Motion + chips\n  - Watermark → العلامة المائية — شكل هندسي مجرد صغير\n  - Motion Signature → التوقيع الحركي — حركة ختم/قلب 150-200ms\n  - chips → شرائح اسم الشخصية — تصنيف موازٍ\n  - Modern Product First, Yemeni Character Second → منتج حديث أولًا، طابع يمني ثانيًا\n  - Museum → متحف — ثقافة تسيطر على الموقع — مرفوض\n  ```\n

**Reason:**

1) يحل PD-I01 Brand Direction — Stage 4 Identity Re-Foundation — رحلة اختيار منهجية: Claude 4.5 4 اتجاهات أولى متحف مرفوضة → DeepSeek فلسفة Modern Product First, Yemeni Character Second → ChatGPT مراجعة + Content Art Direction → Claude 4.5 4 اتجاهات ثانية حديثة + بصمة خفيفة → 4 Artifacts بصرية HTML mockups → حمدان اختار Direction C الختم — قرار مؤسس
2) يتوافق مع DECISION-001 Product Definition Hybrid مكتبة مصنفة مسبقًا قابلة للبحث جاهزة للاستخدام الفوري — Modern UI Foundation Pinterest-like Masonry + Search فوري + Spacing واسع Linear-style — حديث 100% — لا متحف
3) يستغل حقيقة بنيوية لا يملكها المنافسون: المحتوى فيه شخصيات يمنية بالاسم (مصطفى المومري، هديل مانع) — ميزة Giphy/Pinterest لا يملكانها — chips اسم الشخصية تصنيف موازٍ للـCollections — P-32 Collections as Primary Taxonomy + P-33 Admin-Only Curated + P-34 Multi+Follow+SEO — الآن chips طبقة اكتشاف ثانية — P-14 Search Nature اسم الشخص + P-20 بياناته جاهزة اسم الشخص + OPEN-Q-07
4) يحل CONFLICT-019 جزئيًا: Watermark القديم 11% vs 14% — الآن Watermark الجديد شكل هندسي مجرد صغير جدًا ليس رمز ثقافي — مكان محدد يُحدد في PD-I05 — ليس 11% أعلى-يمين بظل مزدوج ولا 14% أسفل-يمين بلا ظل — تفاصيل PD-I05 — B-07 القديم يصبح HISTORICAL — الجديد هندسي مجرد
5) يتوافق مع P-06 Save is core CTA + P-07 Flat Saves + P-09 Core Loop Save/Share/Use + P-34 Follow — Motion Signature حركة ختم/قلب 150-200ms عند الحفظ/الإضافة لـCollection — توقيع حركي فريد — يظهر فقط عند الفعل الإيجابي — يعزز Save CTA
6) يرفض المتحف كفلسفة — لا رموز ثقافية مباشرة (لا كاسيت، لا قمرية، لا خنجر، لا خنجر يمني، لا زخارف) — لا تكثيف ثقافي — لا خط يد غير رسمي — اختبار المتحف — Modern Product First — يتوافق مع B-02 مثل شعبي رقمي + B-03 خذها حطها يمنية + P-15 Audience أي شخص في موقف + P-20 هوية يمنية لهجة/سياق/شخص معروف بدون رموز مباشرة
7) يتوافق مع DECISION-013 Aspect Ratio أي مقاس مسموح + لا فراغ أسود + Watermark+Qussasa ديناميكي — الآن Watermark موحد شكل هندسي مجرد صغير جدًا زاوية ثابتة — يعمل على أي مقاس — Thumbnails تُقص لإطار موحد — بدون فراغ أسود
8) يتوافق مع Stage 3 CLOSED — P-12 Value منتقاة + قابلة للبحث + جاهزة + P-13 300-500 + P-20 Rubric 6 + P-25 Pipeline لقطات قصيرة من مواقع التواصل + P-27 Duration 2-60s + P-29 Aspect أي مقاس — لا تعارض — Brand Direction يبني فوق Content & Editorial System — لا يلغيه
9) يفتح Stage 4 — PD-I02 Logo/Mark + PD-I03 Colors + PD-I04 Typography + PD-I05 Watermark + PD-I06 Reaction Card + PD-I09 Motion — تفاصيل لاحقة — هذا القرار يحدد الشخصية العامة لا التفاصيل

**Alternative rejected:**

- Direction A — الزاوية (آمنة جدًا، بصمة 2-3px ضئيلة) — REJECTED per DECISION-I01 — بصمة ضئيلة جدًا — لا تكفي كهوية — آمنة جدًا
- Direction B — الحرف (خط عربي فقط — لا يكفي كهوية) — REJECTED per DECISION-I01 — خط عربي فقط لا يكفي — يحتاج نظام علامة + حركة
- Direction D — الإيقاع (بصمة ضعيفة جدًا) — REJECTED per DECISION-I01 — بصمة ضعيفة — لا توقيع واضح
- الاتجاهات الأربعة الأولى (الترانزستور، قمرية، السوق، المثل) — REJECTED per DECISION-I01 — كلها متحف — ثقافة تسيطر على الموقع — مرفوضة — Modern Product First, Yemeni Character Second تفوق عليها
- كل الرموز اليمنية المباشرة (كاسيت، قمرية، خنجر، زخارف) — REJECTED per DECISION-I01 — متحف — لا رموز مباشرة — اختبار المتحف
- "المتحف" كفلسفة — REJECTED per DECISION-I01 — ثقافة تسيطر — نريد منتج حديث أولًا — DeepSeek philosophy

**Impact:**

- PD-I01 CLOSED — Stage 4 Identity Re-Foundation OPEN — PD-I01 Brand Direction — Direction C الختم — ACCEPTED 2026-09-21 — 66 → 68 facts
- P-35 NEW: Brand Direction — الختم (Al-Khatm) — Persona منهجي واثق الشخصيات هي البطل — Mood منتج له نظام هوية صغير يتكرر بثقة بصمة استوديو لا زخرفة — فلسفة Modern Product First, Yemeni Character Second — البصمة حول نظام العلامة+الحركة — الشخصية اليمنية بنية تصنيف chips بدل زخرفة — يستغل حقيقة بنيوية شخصيات يمنية بالاسم ميزة لا يملكها Giphy/Pinterest — 3 Signature Anchors Watermark موحد شكل هندسي مجرد صغير جدًا زاوية ثابتة كل رياكشن + Motion Signature حركة ختم/قلب 150-200ms عند الحفظ/الإضافة + chips اسم الشخصية تحت بعض البطاقات اختياري تصنيف موازٍ للـCollections — Modern UI Foundation Pinterest-like Masonry + Search فوري + Spacing واسع Linear-style + نظام واحد صارم + Account flows قياسية + لا تراث في UI — Content Art Direction thumbnails تُقص لإطار موحد + Captions قصيرة لهجة يمنية + تصنيف يعتمد على الشخصيات كطبقة اكتشاف + تركيز مين قالها أكثر من شو قالها — اختبارات اجتازها إخفاء/إظهار + متحف + حداثة — Revisable مرن — تفاصيل PD-I02+I03+I04+I05+I06+I09
- Canonical Facts: 66 → 67 (9 brand + 34 product? actually 9 brand + 35 product + 6 IA + 10 technical + 8 security = 68? but 66→67 per count — P-35)
- B-01 to B-08 — Brand v1.0 LOCKED — الآن HISTORICAL / SUPERSEDED partially — B-07 Watermark تقشّر ورقي + Qussasa يصبح HISTORICAL — الجديد Watermark هندسي مجرد — B-04 Qussasa Mark يصبح HISTORICAL — الجديد chips اسم الشخصية — B-06 9 category colors محفوظة للدراسة Stage4 → الآن قد تُدرس في PD-I03 Colors لكن Direction C لا رموز ثقافية مباشرة — لا تكثيف — B-01 Brand v1.0 LOCKED exists يبقى كمرجع تاريخي لكن Direction الجديد يتفوق — يحتاج مراجعة Stage 4
- CONFLICT-019 Watermark Spec 11% vs 14% — يحل جزئيًا — Watermark الجديد شكل هندسي مجرد صغير — ليس 11% ولا 14% — تفاصيل PD-I05 — CONFLICT-019 يبقى OPEN حتى PD-I05 يحدد مكان/حجم/شكل نهائي — لكن المبدأ تغير من تقشّر+Qussasa إلى هندسي مجرد
- P-06 Save core CTA + P-07 Flat Saves + P-09 Core Loop + P-34 Follow — متوافق — Motion Signature يعزز Save
- P-14 Search Nature + P-20 بياناته جاهزة اسم الشخص + OPEN-Q-07 — متوافق — chips اسم الشخصية تصنيف موازٍ يعزز Search by person
- P-32 Collections as Primary Taxonomy + P-33 Admin-Only Curated + P-34 Multi+Follow+SEO — متوافق — chips طبقة اكتشاف ثانية موازية للـCollections — لا تعارض
- P-29 Aspect Ratio أي مقاس مسموح + لا فراغ أسود — متوافق — Watermark موحد + thumbnails تُقص لإطار موحد — بدون فراغ أسود
- Stage 3 CLOSED — 66 facts — لا تعارض مع Stage 4 Brand Direction — Brand Direction يبني فوق Content & Editorial System — لا يلغيه — P-12 Value + P-13 300-500 + P-20 Rubric + P-25 Pipeline + P-27 Duration + P-29 Aspect كلها تبقى
- Stage 4 — Experience & Identity — الآن OPEN — PD-I01 CLOSED — يفتح PD-I02 Logo/Mark + PD-I03 Colors + PD-I04 Typography + PD-I05 Watermark + PD-I06 Reaction Card + PD-I09 Motion — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان
- YEMREACT-HISTORICAL-NOT-CURRENT.md: B-07 Watermark تقشّر+Qussasa → HISTORICAL SUPERSEDED by DECISION-I01 Watermark هندسي مجرد — B-04 Qussasa Mark → HISTORICAL — Brand v1.0 LOCKED → HISTORICAL reference — CONFLICT-019 partially resolved — PD-14 Watermark Spec OLD → SUPERSEDED by PD-I05 NEW
- YEMREACT-REFORMATION-MASTER-PLAN.md + PROJECT_CONTEXT_AND_DECISIONS.md + Roadmap — يحتاج تحديث — Brand Direction الختم — Stage 4 OPEN
- NEXT: Stage 4 — PD-I02 Logo/Mark — HISTORY+EVIDENCE فقط — ما هي العلامة الجديدة؟ هل Qussasa تبقى أم شكل هندسي مجرد؟ — بانتظار أمر حمدان

**Stage:** Stage 4 — PD-I01 — CLOSED — DECISION-I01 ACCEPTED 2026-09-21 — Brand Direction الختم — NEXT PD-I02 + PD-I05 + PD-I09 + PD-I06

**Evidence:** Claude 4.5 4 directions first (Transistor, Qamaria, Souq, Mathal) → Rejected Museum — DeepSeek philosophy Modern Product First, Yemeni Character Second — ChatGPT review + Content Art Direction — Claude 4.5 4 directions second (Angle, Letter, Khatm, Rhythm) — 4 Artifacts HTML mockups visual — Hamdan chose Direction C Al-Khatm — Persona منهجي واثق الشخصيات هي البطل — Mood بصمة استوديو — 3 Signature Anchors Watermark+Motion+chips — Modern UI Pinterest-like Masonry + Search instant + Spacing Linear + No heritage in UI — Content Art Direction thumbnails cropped unified + Captions Yemeni dialect + Character taxonomy — Tests Hide/Show + Museum + Modernity passed — S10 Brand v1.0 LOCKED historical — B-02 B-03 — P-01 to P-34 — DECISION-013 Aspect + CONFLICT-019 — Stage 3 CLOSED 66 facts

---

## Topic 11 — PD-I01 — CLOSED — DECISION-I01 ACCEPTED — Stage 4 — Brand Direction الختم

- Brand Direction: Direction C — الختم (Al-Khatm) — Persona منهجي واثق الشخصيات هي البطل — Mood بصمة استوديو لا زخرفة — Modern Product First, Yemeni Character Second — DeepSeek + ChatGPT
- رحلة: Claude 4.5 4 أولى متحف مرفوضة (ترانزستور، قمرية، السوق، المثل) → DeepSeek فلسفة حديث أولًا يمني ثانيًا → ChatGPT مراجعة + Content Art Direction → Claude 4.5 4 ثانية (الزاوية، الحرف، الختم، الإيقاع) حديثة بصمة خفيفة → 4 Artifacts HTML mockups → حمدان اختار C الختم
- 3 Signature Anchors: 1) Watermark موحد شكل هندسي مجرد صغير جدًا ليس رمز ثقافي زاوية ثابتة كل رياكشن مكان يُحدد PD-I05 — 2) Motion Signature حركة ختم/قلب 150-200ms عند الحفظ/الإضافة لـCollection توقيع فريد — 3) chips اسم الشخصية تحت بعض البطاقات اختياري مثال مصطفى المومري هديل مانع تصنيف موازٍ للـCollections لا يظهر في كل بطاقة فقط المعروفة
- Modern UI Foundation: Pinterest-like Masonry Grid + Search فوري بلا احتكاك + Spacing واسع Linear-style + نظام واحد صارم + Account flows قياسية + لا تراث في UI — P-08 + IA-01 + IA-04 + P-03 متوافق
- Content Art Direction: thumbnails تُقص لإطار موحد بدون فراغ أسود + Captions قصيرة لهجة يمنية + تصنيف يعتمد على الشخصيات كطبقة اكتشاف + تركيز مين قالها أكثر من شو قالها — P-12 + P-20 + P-15 متوافق
- اختبارات: إخفاء/إظهار Pinterest عادي → YemReact واضح + متحف لا رموز مباشرة + حداثة Pinterest+Linear+Superhuman حديث 100%
- REJECTED: Direction A الزاوية آمنة جدًا بصمة 2-3px + Direction B الحرف خط عربي فقط + Direction D الإيقاع بصمة ضعيفة + 4 الأولى متحف + كل الرموز اليمنية المباشرة + المتحف كفلسفة
- Impact: P-35 Brand Direction الختم — 66→68 facts — B-01 to B-08 Brand v1.0 LOCKED الآن HISTORICAL partially B-07 تقشّر+Qussasa → هندسي مجرد B-04 Qussasa → chips CONFLICT-019 partially resolved Watermark جديد هندسي مجرد ليس 11% ولا 14% تفاصيل PD-I05 — P-06 Save+Motion متوافق — P-14 Search+chips متوافق — P-32 Collections+chips طبقة ثانية موازية — P-29 Aspect+Watermark موحد+thumbnails مقصوصة — Stage3 CLOSED لا تعارض — Stage4 OPEN PD-I01 CLOSED يفتح PD-I02 Logo/Mark + PD-I03 Colors + PD-I04 Typography + PD-I05 Watermark + PD-I06 Reaction Card + PD-I09 Motion — لا كود/Git/DB توثيق فقط
- NEXT: Stage 4 — PD-I02 Logo/Mark + PD-I05 Watermark + PD-I09 Motion + PD-I06 Reaction Card — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — تفاصيل PD-I02+I03+I04+I05+I06+I09 تحدد التفاصيل — هذا القرار شخصية عامة لا تفاصيل


## DECISION-I02 — Qussasa Mark v1.0 Adopted As-Is — ACCEPTED — Stage 4 — PD-I02

- **Status:** ACCEPTED — CLOSED — PD-I02 CLOSED
- **Decided by:** حمدان (Founder)
- **Date:** 2026-09-23 — Stage 4 — Identity Re-Foundation — PD-I02 Logo/Mark
- **Topic:** اعتماد Qussasa Mark v1.0 كما هو — بدون تحسين

**Context — رحلة الاختيار:**

1. DECISION-I01 Brand Direction الختم Direction C ACCEPTED 2026-09-21 — Persona منهجي واثق الشخصيات هي البطل — 3 Anchors Watermark موحد هندسي مجرد + Motion ختم/قلب + chips اسم الشخصية
2. Claude 4.5 أنتج 4 اتجاهات جديدة للـLogo/Mark في H1-R2: Direction A الزاوية + Direction B الحرف + Direction C الختم الجديد + Direction D الإيقاع — كلها مع نسخ محسّنة مقترحة
3. Claude اقترح Qussasa Mark Improvement في H1-R3 — تحسين Qussasa الحالي
4. حمدان راجع: Qussasa Mark v1.0 اجتاز اختبار 8 سيناريوهات فعلية في Brand v1.0 LOCKED — يعمل 16-512px — متوافق مع Direction C الختم (التقشير = بصمة بصرية) — يوفر وقت Stage 4
5. القرار: اعتماد Qussasa Mark v1.0 كما هو — بدون تحسين — لا نسخ جديدة — لا Improvement

**Previous → New:**

- **Previous:**
  - B-04 Qussasa Mark: مربع بزاوية علوية يمنى مشطوفة/ممزقة بتسنين + ثقب تشغيل مثلث كفراغ سالب fill-rule evenodd — CONFIRMED in Brand v1.0 LOCKED — ثم في DECISION-I01 تم وضع B-04 كـ HISTORICAL جزئيًا مع B-07 Watermark peel+Qussasa → هندسي مجرد — الآن يُعاد اعتماده
  - B-01 Brand v1.0 LOCKED exists as YemReact-Brand-v1.0-LOCKED.html — CONFIRMED — S10 says built after test on 8 real scenarios — Qussasa اجتاز 8 سيناريوهات
  - B-07 Watermark: تقشّر ورقي بزاوية + شعار بداخله + نسخة مقواة بظل مزدوج — HISTORICAL SUPERSEDED by DECISION-I01 — الآن Watermark سيُبنى على Qussasa Mark per DECISION-I02 — يفتح PD-I05
  - DECISION-I01 Brand Direction الختم — Direction C — 3 Anchors — Watermark موحد شكل هندسي مجرد صغير جدًا ليس رمز ثقافي — الآن Qussasa Mark v1.0 هو الـMark نفسه — التقشير = بصمة بصرية — متوافق مع Direction C — الختم
  - PD-I02 Logo/Mark كان OPEN — HISTORY+EVIDENCE done — يحتاج قرار
  - CONFLICT-019 Watermark Spec 11% vs 14% — partially resolved by DECISION-I01 — الآن Watermark سيُبنى على Qussasa Mark — تفاصيل PD-I05

- **New:**

  **Qussasa Mark v1.0 Adopted As-Is — ACCEPTED**

  ```
  القرار: اعتماد Qussasa Mark v1.0 كما هو — بدون تحسين

  Qussasa Mark v1.0:
  - مربع بزاوية علوية يمنى مشطوفة/ممزقة بتسنين
  - ثقب تشغيل مثلث كفراغ سالب fill-rule evenodd
  - اجتاز اختبار 8 سيناريوهات فعلية في Brand v1.0 LOCKED
  - يعمل في كل الأحجام 16-512px
  - مفهوم: التقشير = بصمة بصرية = متوافق مع Direction C الختم

  السبب:
  1. Qussasa اجتاز اختبار 8 سيناريوهات فعلية — Brand v1.0 LOCKED — S10
  2. متوافق مع Direction C — الختم (التقشير = بصمة بصرية) — Direction C الختم بصمة استوديو — Qussasa تقشير = بصمة
  3. يعمل في كل الأحجام (16-512px) — لا حاجة لإعادة رسم — يوفر وقت
  4. يوفر وقت Stage 4 للمواضيع الأكثر تأثيرًا — PD-I03 Colors + PD-I05 Watermark أكثر تأثيرًا من إعادة رسم Mark اجتاز الاختبار

  ما تم رفضه:
  - Direction A (الزاوية) — Claude — REJECTED per DECISION-I02
  - Direction B (الحرف) — Claude — REJECTED per DECISION-I02
  - Direction C (الختم الجديد) — Claude — REJECTED per DECISION-I02 — Qussasa الحالي يكفي
  - Direction D (الإيقاع) — Claude — REJECTED per DECISION-I02
  - كل النسخ المحسّنة المقترحة من Claude في H1-R2 — REJECTED per DECISION-I02
  - Qussasa Mark Improvement (H1-R3) — لم يُنفذ — REJECTED per DECISION-I02 — لا تحسين الآن

  Impact:
  - P-36 NEW: Qussasa Mark v1.0 adopted as-is — بدون تحسين — اجتاز 8 سيناريوهات — يعمل 16-512px — متوافق Direction C الختم تقشير=بصمة — يوفر وقت Stage 4
  - B-04 UPDATED: Qussasa Mark — من HISTORICAL → ACCEPTED — DECISION-I02 — Qussasa Mark v1.0 adopted as-is — مربع بزاوية مشطوفة + مثلث سالب — 16-512px — اجتاز 8 سيناريوهات
  - PD-I02 CLOSED — Stage 4 — 2026-09-23
  - يفتح: PD-I03 Color System + PD-I05 Watermark — Watermark سيُبنى على Qussasa Mark — PD-I05 سيحدد كيف يُبنى Watermark على Qussasa
  - B-07 Watermark: الآن — Watermark سيُبنى على Qussasa Mark — ليس abstract geometric منفصل تمامًا — هو Qussasa-based — تفاصيل PD-I05 — CONFLICT-019 remains partially resolved حتى PD-I05
  - Revisable: إذا احتجنا تحسين Qussasa لاحقًا → PD جديد — لا يمنع التطوير المستقبلي — مرن
  - No conflict Stage 3 — P-12 to P-34 + P-35 Brand Direction الختم كلها تبقى — Qussasa Mark v1.0 يبني فوقها
  ```

**Reason:**

1) Qussasa اجتاز اختبار 8 سيناريوهات فعلية — Brand v1.0 LOCKED — S10 says built after test on 8 real scenarios — لا حاجة لإعادة اختراع Mark اجتاز اختبار فعلي — يوفر وقت
2) متوافق مع Direction C — الختم (التقشير = بصمة بصرية) — DECISION-I01 Direction C الختم — Persona منهجي واثق — Mood بصمة استوديو — Qussasa تقشير ورقي بزاوية = بصمة بصرية = يطابق الختم — ليس متحف — هو بصمة — اختبار المتحف + الحداثة
3) يعمل في كل الأحجام (16-512px) — S10 + Brand v1.0 LOCKED — لا تشويه — scalable — 16px favicon حتى 512px cover — لا حاجة لتحسين
4) يوفر وقت Stage 4 للمواضيع الأكثر تأثيرًا — PD-I03 Colors + PD-I05 Watermark + PD-I06 Card + PD-I09 Motion أكثر تأثيرًا على تجربة المستخدم من إعادة رسم Mark اجتاز 8 سيناريوهات — Stage 4 OPEN — تركيز على الأكثر تأثيرًا

**Alternative rejected:**

- Direction A — الزاوية (آمنة جدًا، بصمة 2-3px ضئيلة) — Claude — REJECTED per DECISION-I02 — آمنة جدًا — لا تكفي كهوية — Qussasa الحالي أوضح
- Direction B — الحرف (خط عربي فقط — لا يكفي كهوية) — Claude — REJECTED per DECISION-I02 — خط عربي فقط لا يكفي — Qussasa أقوى
- Direction C — الختم الجديد (نسخة جديدة من الختم) — Claude — REJECTED per DECISION-I02 — Qussasa الحالي هو الختم نفسه — التقشير = بصمة — لا حاجة لختم جديد
- Direction D — الإيقاع (بصمة ضعيفة جدًا) — Claude — REJECTED per DECISION-I02 — بصمة ضعيفة — Qussasa أوضح
- كل النسخ المحسّنة المقترحة من Claude في H1-R2 — REJECTED per DECISION-I02 — كلها محاولات تحسين لمطلوب اجتاز اختبار — لا حاجة
- Qussasa Mark Improvement (H1-R3) — لم يُنفذ — REJECTED per DECISION-I02 — اقتراح تحسين Qussasa — لم يُنفذ — Qussasa v1.0 adopted as-is — Improvement مؤجل لـ PD جديد إذا احتجنا

**Impact:**

- PD-I02 CLOSED — Stage 4 Identity Re-Foundation — PD-I02 Logo/Mark — ACCEPTED 2026-09-23 — 68 → 69 facts
- P-36 NEW: Qussasa Mark v1.0 adopted as-is — بدون تحسين — اجتاز 8 سيناريوهات — يعمل 16-512px — متوافق Direction C الختم تقشير=بصمة — يوفر وقت Stage 4 — يفتح PD-I03+PD-I05
- B-04 UPDATED: Qussasa Mark — من HISTORICAL SUPERSEDED by DECISION-I01 → ACCEPTED — DECISION-I02 — Qussasa Mark v1.0 adopted as-is — مربع بزاوية علوية يمنى مشطوفة/ممزقة بتسنين + ثقب تشغيل مثلث كفراغ سالب fill-rule evenodd — 16-512px — اجتاز 8 سيناريوهات — B-01 Brand v1.0 LOCKED reference — B-07 Watermark سيُبنى على Qussasa Mark
- B-07 Watermark: UPDATE — Watermark سيُبنى على Qussasa Mark — ليس abstract geometric منفصل تمامًا — هو Qussasa-based — تفاصيل PD-I05 — CONFLICT-019 partially resolved remains حتى PD-I05 — Old 11% vs 14% → New Qussasa-based
- Canonical Facts: 68 → 69 (10 brand? Actually 9 brand + 35 product + 6 IA +10 tech +8 sec =68 → 9 brand? Let's recalc: B-04 UPDATED not new count + P-36 NEW = 69) — B-04 UPDATED — P-36 NEW
- B-01 to B-09 — Brand v1.0 LOCKED — الآن B-04 ACCEPTED — B-07 Watermark Qussasa-based — B-09 Brand Direction الختم — كلها متوافقة — Direction C الختم + Qussasa Mark v1.0
- CONFLICT-019 Watermark Spec 11% vs 14% — partially resolved by DECISION-I01 abstract geometric — الآن update: Watermark سيُبنى على Qussasa Mark — تفاصيل PD-I05 — CONFLICT-019 remains partially resolved حتى PD-I05 يحدد مكان/حجم/شكل نهائي Qussasa-based
- P-35 Brand Direction الختم + P-36 Qussasa Mark v1.0 — متوافق — Brand Direction + Mark — Direction C الختم + Qussasa تقشير=بصمة
- P-06 Save core CTA + P-07 Flat Saves + P-34 Follow — متوافق — Qussasa Mark لا يؤثر على Save — Motion PD-I09 سيُبنى لاحقًا
- P-29 Aspect Ratio أي مقاس + لا فراغ أسود — متوافق — Qussasa Mark يعمل على أي مقاس — Watermark Qussasa-based ديناميكي
- Stage 3 CLOSED — 66 facts — لا تعارض مع Stage 4 PD-I02 — Qussasa Mark v1.0 يبني فوق Content & Editorial System — لا يلغيه
- Stage 4 — Experience & Identity — الآن OPEN — PD-I01 CLOSED Brand Direction الختم + PD-I02 CLOSED Qussasa Mark v1.0 adopted — يفتح PD-I03 Color System + PD-I05 Watermark (Qussasa-based) + PD-I04 Typography + PD-I06 Reaction Card + PD-I09 Motion
- YEMREACT-HISTORICAL-NOT-CURRENT.md: B-04 Qussasa Mark → من HISTORICAL → ACCEPTED — DECISION-I02 — B-07 Watermark → UPDATE Qussasa-based — CONFLICT-019 partially resolved → Qussasa-based — PD-I02 CLOSED
- YEMREACT-REFORMATION-MASTER-PLAN.md + PROJECT_CONTEXT_AND_DECISIONS.md + Roadmap — يحتاج تحديث — PD-I02 مغلق — Qussasa Mark v1.0 adopted — يفتح PD-I03+PD-I05
- NEXT: Stage 4 — PD-I03 Color System + PD-I05 Watermark Qussasa-based — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان

**Stage:** Stage 4 — PD-I02 — CLOSED — DECISION-I02 ACCEPTED 2026-09-23 — Qussasa Mark v1.0 Adopted As-Is — NEXT PD-I03 + PD-I05

**Evidence:** Brand v1.0 LOCKED YemReact-Brand-v1.0-LOCKED.html S10 says built after test on 8 real scenarios, B-04 Qussasa Mark مربع بزاوية مشطوفة + مثلث سالب fill-rule evenodd, S01 Asset Inventory overlay PNGs watermark/qs.png 200, DECISION-I01 Brand Direction الختم Direction C Persona منهجي واثق 3 Anchors Watermark+Motion+chips Modern UI Pinterest-like+Search فوري, Claude H1-R2 4 directions A B C D + H1-R3 Qussasa Improvement proposed, Hamdan chose Qussasa v1.0 as-is — اجتاز 8 سيناريوهات — متوافق Direction C تقشير=بصمة — يعمل 16-512px — يوفر وقت Stage 4, Stage 4 OPEN PD-I01 CLOSED 68 facts

---

## Topic 12 — PD-I02 — CLOSED — DECISION-I02 ACCEPTED — Stage 4 — Qussasa Mark v1.0 Adopted As-Is

- Qussasa Mark v1.0 adopted as-is — بدون تحسين — اجتاز 8 سيناريوهات فعلية — Brand v1.0 LOCKED — يعمل 16-512px — متوافق Direction C الختم تقشير=بصمة بصرية
- Reason: 1) اجتاز 8 سيناريوهات 2) متوافق Direction C الختم 3) يعمل 16-512px 4) يوفر وقت Stage 4 للمواضيع الأكثر تأثيرًا PD-I03+PD-I05
- Rejected: Direction A الزاوية + Direction B الحرف + Direction C الختم الجديد + Direction D الإيقاع + كل النسخ المحسّنة H1-R2 + Qussasa Improvement H1-R3 لم يُنفذ
- Impact: P-36 Qussasa Mark v1.0 adopted — B-04 UPDATED HISTORICAL→ACCEPTED — B-07 Watermark سيُبنى على Qussasa Mark — PD-I02 CLOSED — يفتح PD-I03 Color System + PD-I05 Watermark Qussasa-based — 68→69 facts — Revisable إذا احتجنا تحسين Qussasa → PD جديد — لا يمنع التطوير المستقبلي
- NEXT: PD-I03 Color System + PD-I05 Watermark Qussasa-based — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB


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

## DECISION-I05 — Watermark Deferred — DEFERRED — Stage 4 — PD-I05

**Date:** 2026-09-24
**Stage:** Stage 4 — Experience & Identity — Identity Re-Foundation
**Decided by:** حمدان (Founder)
**Status:** DEFERRED — مُجمّد مؤقتًا — ليس CLOSED — قابل لإعادة الفتح
**Topic:** PD-I05 — Watermark

── القرار ──

تجميد Watermark مؤقتًا — لا يُنفّذ الآن.

── السبب ──

1. يحتاج دراسة أعمق — تأثير على صناع المحتوى + التكاليف + الجانب القانوني
2. يمكن إضافته بعد الإطلاق — ليس حرجًا للنسخة الأولى
3. Direction C — الختم — يبقى صالحًا مع 2 Anchors فعّالين: Motion Signature + chips الشخصية
4. صفر مخاطرة تقنية — قرار قابل للتراجع

── ما تم تجميده ──

- Watermark على الفيديو
- Watermark على الصور
- Watermark على البطاقات
- Watermark في صفحة التفاصيل
- معالجة FFmpeg للـWatermark

── ما يبقى فعّالًا ──

- Qussasa Mark (PD-I02) — كـLogo في الهيدر فقط — ليس كعلامة مائية على المحتوى
- Motion Signature (PD-I09) — Anchor فعّال
- chips الشخصية (PD-I06 + PD-I07) — Anchor فعّال

── إعادة الفتح ──

- القرار قابل للمراجعة بعد الإطلاق
- يُفتح PD-I05-R2 عند الحاجة
- يستند إلى بيانات حقيقية — سلوك المستخدم

── الأثر ──

- P-38 NEW — Watermark Deferred — مُجمّد — لا Watermark في النسخة الأولى — يُفتح PD-I05-R2 بعد الإطلاق ببيانات حقيقية
- B-07 UPDATED: من ACCEPTED Qussasa-based → FROZEN/DEFERRED per DECISION-I05 — لا Watermark الآن — Qussasa Mark يبقى Logo في الهيدر فقط — B-04 Qussasa Mark v1.0 يبقى ACCEPTED unaffected
- B-09 UPDATED: Direction C الختم — Watermark Anchor مُجمّد — يبقى 2 Signature Anchors فعّالين فقط Motion Signature + chips الشخصية
- P-35 UPDATED: Brand Direction الختم — Watermark Anchor مُجمّد — 2 Anchors فعّالين
- 70→71 facts — PD-I05 DEFERRED وليس CLOSED — لا تعارض مع Stage 3
- NEXT: PD-I04 Typography + PD-I06 Reaction Card + PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد

**Stage:** Stage 4 — PD-I05 — DEFERRED — DECISION-I05 2026-09-24 — Watermark مُجمّد — NEXT PD-I04 + PD-I06 + PD-I07 + PD-I08 + PD-I09 + Settings Modal

---

## Topic 14 — PD-I05 — DEFERRED — DECISION-I05 — Stage 4 — Watermark

- Watermark — مُجمّد مؤقتًا — لا يُنفّذ الآن — ليس مرفوضًا — ليس مغلقًا
- المجمّد: Watermark على الفيديو + الصور + البطاقات + صفحة التفاصيل + معالجة FFmpeg
- الفعّال: Qussasa Mark كـLogo في الهيدر فقط + Motion Signature PD-I09 + chips الشخصية PD-I06+PD-I07
- Reason: 1) يحتاج دراسة أعمق صناع المحتوى+تكاليف+قانوني 2) يمكن إضافته بعد الإطلاق ليس حرجًا للنسخة الأولى 3) Direction C يبقى صالحًا مع 2 Anchors 4) صفر مخاطرة تقنية قابل للتراجع
- إعادة الفتح: قابل للمراجعة بعد الإطلاق — يُفتح PD-I05-R2 عند الحاجة — يستند إلى بيانات حقيقية سلوك المستخدم
- Impact: P-38 NEW — B-07 FROZEN — B-09 UPDATED 2 Anchors — P-35 UPDATED — 70→71 facts
- NEXT: PD-I04 + PD-I06 + PD-I07 + PD-I08 + PD-I09 + Settings Modal — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB

---

## DECISION-I06 — Reaction Card & Detail Page — ACCEPTED — Stage 4 — PD-I06

**Date:** 2026-09-24
**Stage:** Stage 4 — Experience & Identity — Identity Re-Foundation
**Decided by:** حمدان (Founder)
**Status:** ACCEPTED
**Topic:** PD-I06 — Reaction Card

── القرار: البطاقة (Card) — النسخة النهائية ──

- الوسائط: الفيديو/الصورة تملأ الإطار — بدون فراغ أسود — لا Watermark عليها per DECISION-I05
- **Duration badge** — ✅ **في البطاقة فقط** — أعلى يمين الوسائط — **فيديو فقط** — الصور بلا شارة
- **العنوان** — سطر أساسي تحت الوسائط
- **⋮ ثلاث نقاط** — على يسار العنوان (جهة اليمين في RTL)
- نقرة واحدة على البطاقة → /r/[code]

── القرار: صفحة التفاصيل /r/[code] — النسخة النهائية ──

1. [← رجوع]
2. [الفيديو/الصورة] — ❌ **بلا Duration** — CORRECTED 2026-09-25
3. العنوان (H1) + [حفظ] [تنزيل] [مشاركة] [...] — **نفس السطر** — الأزرار جهة **اليسار** في RTL — **ليست سطرًا منفصلًا** — CORRECTED 2026-09-25
4. ● اسم الشخصية — الوصف الأساسي — يُحذف إذا فارغ
5. [الوصف الثنائي المطوي ▼] — لا يظهر الزر إذا لا يوجد وصف ثنائي
6. المجموعات — لا قسم إذا لا مجموعات
7. رياكشنات ذات صلة
8. رياكشنات عشوائية

── الأزرار ──

- **رئيسية:** حفظ — تنزيل — مشاركة
- **⋮ ثلاث نقاط:** نسخ الرابط — إبلاغ
- ❌ CORRECTED 2026-09-24 — «تعديل (Admin فقط)» **محذوف** من ⋮ — قرار حمدان السابق: «مثل المستخدم تمامًا + الصلاحيات في صفحة الأدمن فقط» — لا أزرار Admin في المكتبة — الأدمن يعدّل من /admin فقط
- P-23 UPDATED — CORRECTED: القائمة النهائية نفس العناصر الخمسة — التوزيع: حفظ+تنزيل+مشاركة أزرار رئيسية ظاهرة — ⋮ = نسخ الرابط + إبلاغ فقط — عنصران لا ثلاثة

── ملاحظات ──

- P-11 UPDATED: قسم الاكتشاف قسمان — ذات صلة 10 أولًا + تحميل المزيد حتى 50 حسب الصلة + عشوائية محدودة 10-20 — بدون Infinite Feed
- P-40 NEW — CORRECTED 2026-09-24: رياكشنات عشوائية — قسم **محدود 10-20 رياكشن — تصحيح ثان 2026-09-25: كان 20-40 → أصبح 10-20** — ليس Infinite Scroll — لا Load More — يتوقف عند 10-20 — يتوافق P-03 No Infinite Feed + DECISION-006
- لا Watermark في البطاقة ولا في صفحة التفاصيل per DECISION-I05
- لا فئة ولا لون فئة per DECISION-014 — لا عدادات ولا تعليقات per P-03 — لا مصدر/حقوق per IA-05

── الأثر ──

- P-39 NEW — Reaction Card & Detail Page Spec — البطاقة + صفحة التفاصيل + الأزرار
- P-40 NEW — رياكشنات ذات صلة + رياكشنات عشوائية محدودة 10-20 — P-11 UPDATED
- P-23 UPDATED — CORRECTED — توزيع الأزرار: رئيسية 3 + ⋮ عنصران فقط نسخ الرابط + إبلاغ — لا تعديل Admin

── التصحيح 2026-09-24 — تصحيح حمدان على DECISION-I06 ──

**التصحيح 1 — رياكشنات عشوائية (P-40):** قسم محدود 10-20 رياكشن — تصحيح ثان 2026-09-25: كان 20-40 → أصبح 10-20 — ليس Infinite Scroll — لا Load More — يتوقف عند 10-20 — يتوافق مع P-03 No Infinite Feed + DECISION-006

**التصحيح 2 — تعديل Admin فقط (P-23):** تُرجع القائمة إلى عنصرين فقط — نسخ الرابط + إبلاغ — حذف «تعديل (Admin فقط)» — السبب قرار حمدان السابق «مثل المستخدم تمامًا + الصلاحيات في صفحة الأدمن فقط» — لا أزرار Admin في المكتبة — الأدمن يعدّل من /admin فقط

**الأثر:** P-40 CORRECTED — P-23 CORRECTED — P-39 CORRECTED — لا تغيير في عدد الحقائق 73 — PD-I06 يبقى CLOSED
── التصحيح 2026-09-25 — التصحيح الثالث: موضع الأزرار + إلغاء Empty States ──

**التصحيح 1 — موضع الأزرار في صفحة التفاصيل:** الأزرار (حفظ + تنزيل + مشاركة + [...]) تظهر **بجانب العنوان — في اليسار (في RTL: يسار العنوان) — نفس السطر — ليست سطرًا منفصلًا**

الشكل:

```
[← رجوع]

[الوسائط]

العنوان (H1)              [حفظ] [تنزيل] [مشاركة] [...]

● اسم الشخصية — الوصف

...
```

**التصحيح 2 — إلغاء Empty States:** لا تظهر أي رسائل فارغة للمستخدم — لا اسم شخصية → لا شيء — لا وصف → لا شيء — لا وصف ثنائي → لا زر ▼ — لا مجموعات → لا قسم — غير مضاف → لا شيء — **القاعدة: الصفحة نظيفة — الحقل يُحذف من DOM إذا كان فارغًا — لا placeholder — لا empty message**

**التوافق:** متوافق P-09 «وصف ثنائي مطوي **إن وجد**» + P-35 chips «اختياري تحت بعض البطاقات فقط» + P-34 المجموعات «إن وُجدت» + P-06 حفظ CTA أساسي يبقى ظاهرًا دائمًا — لا تعارض — لا حقائق جديدة — العدد ثابت 74

── التصحيح 2026-09-25 — الرابع: Duration Position — توضيح PD-I07 ──

**1. في البطاقة (Card):** ✅ Duration **أعلى يمين الوسائط** — كما في PD-I06 — فيديو فقط — الصور بلا شارة

**2. في صفحة التفاصيل:** ❌ **يُحذف — لا يظهر Duration**

**السبب:**
- مشغل الفيديو يعرض المدة — progress bar + time
- التكرار = ازدحام
- Pinterest-like لا يعرضها

**التوافق:** متوافق P-27 المدة 2s-60s تبقى حقيقة بيانات + P-39 البطاقة + لا تعارض مع Stage 3 — لا حقائق جديدة — العدد ثابت 74 — PD-I06 يبقى CLOSED

- 71→73 facts — PD-I06 CLOSED — يفتح PD-I04 Typography + PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد
- التفاصيل البصرية الدقيقة (الخطوط PD-I04 + الحركة PD-I09 + ألوان P-37) تُحسم في مواضيعها

**Stage:** Stage 4 — PD-I06 — CLOSED — DECISION-I06 ACCEPTED 2026-09-24 — Reaction Card & Detail Page — NEXT PD-I04 + PD-I07 + PD-I08 + PD-I09 + Settings Modal

---

## Topic 15 — PD-I06 — CLOSED — DECISION-I06 ACCEPTED — Stage 4 — Reaction Card

- البطاقة: وسائط + ✅ Duration أعلى يمين الوسائط فيديو فقط + العنوان + ⋮ — بدون Watermark
- صفحة التفاصيل: 8 كتل — رجوع / وسائط ❌ بلا Duration / **عنوان H1 + أزرار على نفس السطر جهة اليسار في RTL** / شخصية+وصف أساسي يُحذف إذا فارغ / وصف ثنائي مطوي لا زر ▼ إن لم يوجد / مجموعات لا قسم إن لم توجد / ذات صلة / عشوائية محدودة 10-20 — **لا Empty States** — الحقل يُحذف من DOM إذا فارغ — لا placeholder ولا empty message
- الأزرار الرئيسية: حفظ + تنزيل + مشاركة — ⋮: نسخ الرابط + إبلاغ فقط — CORRECTED 2026-09-24 حذف تعديل Admin
- عشوائية: قسم محدود 10-20 رياكشن — تصحيح ثان 2026-09-25: كان 20-40 → أصبح 10-20 — ليس Infinite Scroll — لا Load More — P-40 CORRECTED
- Reason: 1) يحسم PD-I06 2) متوافق P-06 حفظ CTA أساسي 3) متوافق P-23 نفس العناصر الخمسة 4) متوافق DECISION-I05 لا Watermark 5) متوافق P-11 لا Infinite Feed 6) يفتح PD-I04+I07+I08+I09+Settings Modal
- Impact: P-39 + P-40 NEW — P-23 UPDATED — P-11 UPDATED — 71→73 facts — PD-I06 CLOSED — CORRECTED 2026-09-24: P-40 محدود 10-20 + P-23 عنصران فقط بلا تعديل Admin
- NEXT: PD-I04 + PD-I07 + PD-I08 + PD-I09 + Settings Modal — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB

---

## DECISION-I04 — Typography System — ACCEPTED — Stage 4 — PD-I04

**Date:** 2026-09-25
**Stage:** Stage 4 — Experience & Identity — Identity Re-Foundation
**Decided by:** حمدان (Founder)
**Status:** ACCEPTED
**Topic:** PD-I04 — Typography System

── النظام المعتمد ──

**1. الخطوط:**

- **Display:** Lalezar — الـLogo فقط + عناوين التسويق
- **Primary Arabic:** IBM Plex Sans Arabic — 400 / 500 / 600 / 700
- **Latin:** Inter — 400 / 500 / 600 / 700
- **Mono:** IBM Plex Mono — 400 / 500

**2. Type Scale:**

- H1: 32px / 700 / 1.2
- H2: 24px / 600 / 1.3
- H3: 20px / 600 / 1.3
- Body L: 16px / 400 / 1.5
- Body: 14px / 400 / 1.5
- Body S: 13px / 400 / 1.5
- Caption: 12px / 400 / 1.4
- Micro: 11px / 500 / 1.4 — Mono

**3. RTL:** كامل — أرقام Western

**4. Letter Spacing:**

- عربي: 0
- لاتيني H1/H2: -0.01em
- Mono: 0

── ملاحظات مؤجلة ──

- Micro 11px: يُختبر في Stage 7 — قد يُرفع لـ 12px
- Settings Modal: Topic مستقبلي — لا يُعتبر قرار الآن

── ما تم رفضه ──

- خطوط عربية تقليدية — Amiri + Reem Kufi + Aref Ruqaa — REJECTED
- خط يد — REJECTED
- Lalezar في UI — REJECTED — فقط في الـLogo
- أكثر من 4 خطوط — REJECTED

── الأثر ──

- P-41 NEW: Typography System
- PD-I04 CLOSED
- يفتح: PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion
- 73→74 facts

**Stage:** Stage 4 — PD-I04 — CLOSED — DECISION-I04 ACCEPTED 2026-09-25 — Typography System — NEXT PD-I07 + PD-I08 + PD-I09

---

## Topic 16 — PD-I04 — CLOSED — DECISION-I04 ACCEPTED — Stage 4 — Typography System

- الخطوط 4: Display Lalezar Logo فقط + عناوين التسويق — Primary Arabic IBM Plex Sans Arabic 400/500/600/700 — Latin Inter 400/500/600/700 — Mono IBM Plex Mono 400/500
- Type Scale 8 مستويات: H1 32/700/1.2 — H2 24/600/1.3 — H3 20/600/1.3 — Body L 16/400/1.5 — Body 14/400/1.5 — Body S 13/400/1.5 — Caption 12/400/1.4 — Micro 11/500/1.4 Mono
- RTL كامل + أرقام Western — Letter Spacing عربي 0 + لاتيني H1/H2 -0.01em + Mono 0
- مؤجل: Micro 11px يُختبر Stage 7 قد يُرفع 12px — Settings Modal Topic مستقبلي ليس قرار الآن
- Rejected: خطوط عربية تقليدية Amiri+Reem Kufi+Aref Ruqaa + خط يد + Lalezar في UI + أكثر من 4 خطوط
- Impact: P-41 NEW — PD-I04 CLOSED — 73→74 facts — يفتح PD-I07 + PD-I08 + PD-I09
- NEXT: PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB

---

## DECISION-I07 — PD-I07 Closed — ACCEPTED — Stage 4 — PD-I07

**Date:** 2026-09-25
**Stage:** Stage 4 — Experience & Identity — Identity Re-Foundation
**Decided by:** حمدان (Founder)
**Status:** ACCEPTED — CLOSED — بدون تصميم جديد
**Topic:** PD-I07 — chips الشخصية

── القرار ──

1. **PD-I07 (chips) = مغلق** — المواصفة النهائية للـchip:
   - **Chip = وسم بصري فقط** — Visual tag — ليس زرًا ولا رابطًا
   - **Inline قبل الوصف** — داخل سطر الوصف في صفحة التفاصيل — ليس سطرًا منفصلًا
   - **غير قابل للنقر** — Not clickable — لا Navigation
   - **لا يظهر في البطاقة** — ❌ Chip في صفحة التفاصيل فقط — ⚠️ يُصحَّح ما كان مثبتًا في P-35/B-09 «chips تحت بعض البطاقات اختياري» → **CORRECTED: لا يظهر في البطاقة**
2. **Duration في صفحة التفاصيل = يُحذف** — مُثبَّت بالتصحيح الرابع على DECISION-I06 — **P-39** — **في البطاقة: ✅ أعلى يمين الوسائط** / **في التفاصيل: ❌ يُحذف** — السبب: المشغل يعرضها progress bar + time
3. **Related + More (تأكيد):**
   - **Related (ذات صلة) = 10 رياكشن**
   - **More (عشوائية) = 10-20 رياكشن**
   - **كلاهما = نفس بطاقة Reaction Card** — لا تصميم جديد — البطاقة المعتمدة في **P-39** تُستخدم كما هي — **لا تغيير في تصميم P-39**

── ملاحظات ──

- لا حقائق جديدة — العدد ثابت **74 facts**
- P-40 UPDATED: Related = 10 + More = 10-20 + كلاهما نفس بطاقة Reaction Card
- P-35 UPDATED + B-09 UPDATED: chip **لا يظهر في البطاقة** — CORRECTED — يظهر inline قبل الوصف في صفحة التفاصيل فقط — وسم بصري غير قابل للنقر
- P-39 UPDATED: الكتلة 4 chip inline قبل الوصف — غير قابل للنقر — وسم بصري فقط — و Duration ❌ في التفاصيل
- ⚠️ OPEN للاستيضاح: P-11/P-09 يثبتان «ذات صلة 10 أولًا + تحميل المزيد حتى 50 حسب الصلة» — إن كان المقصود **10 ثابتة بلا Load More** يُعدَّل P-11 بقرار لاحق

── الأثر ──

- لا P-XX جديد — 74 facts ثابتة
- PD-I07 CLOSED
- يفتح: PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق

**Stage:** Stage 4 — PD-I07 — CLOSED — DECISION-I07 ACCEPTED 2026-09-25 — بدون تصميم جديد — NEXT PD-I08 + PD-I09 + Settings Modal

---

## Topic 17 — PD-I07 — CLOSED — DECISION-I07 ACCEPTED — Stage 4 — chips الشخصية

- PD-I07 مغلق — لا تصميم جديد — chips تُبنى على P-35 + P-39
- Chip = وسم بصري فقط + inline قبل الوصف + غير قابل للنقر + ❌ لا يظهر في البطاقة — P-35/B-09 CORRECTED — P-39 UPDATED
- Duration في التفاصيل = يُحذف — ✅ البطاقة أعلى يمين / ❌ التفاصيل — P-39 UPDATED — المشغل يعرضها
- Related = 10 رياكشن + More (عشوائية) = 10-20 رياكشن — كلاهما نفس بطاقة Reaction Card — P-40 UPDATED
- الأثر: لا حقائق جديدة — 74 facts — PD-I07 CLOSED — يفتح PD-I08 + PD-I09 + Settings Modal
- NEXT: PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB

---

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

## STAGE 4 — CLOSED — Identity Re-Foundation — مكتمل 100%

**10 Topics:**

| # | Topic | الحالة | القرار |
|---|---|---|---|
| PD-I01 | Brand Direction | ✅ CLOSED | Direction C — الختم |
| PD-I02 | Qussasa Mark | ✅ CLOSED | Qussasa Mark v1.0 adopted as-is |
| PD-I03 | Multi-Accent | ✅ CLOSED | Base Ink/Paper/Grey + Amber/Purple/Teal + Day/Night/Auto |
| PD-I04 | Typography | ✅ CLOSED | Lalezar + IBM Plex Sans Arabic + Inter + Plex Mono |
| PD-I05 | Watermark | ❄️ **DEFERRED** | مُجمّد — PD-I05-R2 بعد الإطلاق |
| PD-I06 | Card + Detail | ✅ CLOSED | Duration top-right · أزرار نفس السطر · لا Empty States |
| PD-I07 | Chips | ✅ CLOSED | وسم بصري · inline · غير قابل للنقر · لا في البطاقة |
| PD-I08 | Light/Dark + Soft Depth | ✅ CLOSED | Dark دافئ Qishr · 4 مستويات ظل · Auto افتراضي |
| PD-I09 | Motion | ✅ CLOSED | Hybrid Subtle + Seal Anchor |
| PD-I10 | UI Language | ✅ CLOSED | Studio Seal |

**النتيجة:** 76 → **79 facts** — Stage 4 مكتمل — **الانتقال إلى Stage 5 — IA & Navigation**
**المؤجل خارج Stage 4:** PD-I05-R2 بعد الإطلاق · Search Route (Stage 5) · Scroll Restoration (مستقبلي) · 7 تصحيحات Stage 7 · 3 تصحيحات Stage 7 من DECISION-I08

---

## NEXT — Stage 3 CLOSED — Stage 4 CLOSED — Stage 5 OPEN — 79 facts

- Stage 3 — Content & Editorial System — **CLOSED** — 2026-09-14 — 66 facts
- Stage 4 — Experience & Identity — Identity Re-Foundation — **CLOSED 100%** — 2026-09-30 — 79 facts — PD-I01 CLOSED + PD-I02 CLOSED + PD-I03 CLOSED + PD-I04 CLOSED + **PD-I05 DEFERRED (PD-I05-R2 بعد الإطلاق)** + PD-I06 CLOSED + PD-I07 CLOSED + PD-I08 CLOSED + PD-I09 CLOSED + PD-I10 CLOSED per DECISION-I10 — Direction C الختم · Qussasa Mark v1.0 Logo هيدر · Multi-Accent · Typography · Reaction Card & Detail Page · Chips · Light/Dark + Soft Depth · Motion Hybrid + Seal Anchor · **UI Language Studio Seal**
- Stage 4 — المؤجل: PD-I05-R2 بعد الإطلاق · Search Route → Stage 5 · Scroll Restoration → مستقبلي · 7 تصحيحات Stage 7 من DECISION-I10 + 3 تصحيحات Stage 7 من DECISION-I08
- **Stage 5 — IA & Navigation — OPEN** — NEXT: Search Route (صفحة منفصلة vs ?q=) · Bottom Nav · Account UI · IA-01 إلى IA-06
- Rules: HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB — توثيق فقط — لا Migration — لا تنفيذ — وثّق فقط لا تنفذ
 — PD-I01 CLOSED — PD-I02 CLOSED — PD-I03 CLOSED — PD-I04 CLOSED — PD-I05 DEFERRED — PD-I06 CLOSED — PD-I07 CLOSED — PD-I08 CLOSED — PD-I09 CLOSED

- Stage 3 — Content & Editorial System — CLOSED — 2026-09-14 — 66 facts — PD-04+PD-05+PD-06 SKIPPED+PD-07+PD-08+PD-09+PD-10
- Stage 4 — Experience & Identity — OPEN — Identity Re-Foundation — 2026-09-21 PD-I01 CLOSED + 2026-09-23 PD-I02 CLOSED + 2026-09-23 PD-I03 CLOSED + 2026-09-24 PD-I05 DEFERRED + 2026-09-24 PD-I06 CLOSED + 2026-09-25 PD-I04 CLOSED + 2026-09-25 PD-I07 CLOSED + 2026-09-25 PD-I08 CLOSED + 2026-09-26 PD-I09 CLOSED per DECISION-I09 — 75→76 facts — Direction C الختم + Qussasa Mark Logo هيدر فقط + Multi-Accent + Typography + Reaction Card & Detail Page + chips + Light/Dark + Soft Depth + Motion Language Hybrid Subtle UI + Seal Motion Anchor 6 مراحل ~1.7s + Durations 120/180/240/320 + Easings Standard/Decelerate/Accelerate/Spring Seal فقط + لا Page Transitions + Scroll Header Mobile 250ms + Skeleton/Spinner/Fade + Reduced Motion
- Stage 4 NEXT: PD-I10 UI Language — آخر Topic — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB — توثيق فقط — لا Migration — لا تنفيذ — لا تعديل Brand القديم — وثّق فقط لا تنفذ
 — PD-I01 CLOSED — PD-I02 CLOSED — PD-I03 CLOSED — PD-I04 CLOSED — PD-I05 DEFERRED — PD-I06 CLOSED — PD-I07 CLOSED — PD-I08 CLOSED

- Stage 3 — Content & Editorial System — CLOSED — 2026-09-14 — 66 facts — PD-04+PD-05+PD-06 SKIPPED+PD-07+PD-08+PD-09+PD-10
- Stage 4 — Experience & Identity — OPEN — Identity Re-Foundation — 2026-09-21 Brand Direction الختم PD-I01 CLOSED + 2026-09-23 Qussasa Mark v1.0 PD-I02 CLOSED + 2026-09-23 Multi-Accent Color System PD-I03 CLOSED + 2026-09-24 Watermark DEFERRED per DECISION-I05 + 2026-09-24 Reaction Card & Detail Page PD-I06 CLOSED per DECISION-I06 + 2026-09-25 Typography System PD-I04 CLOSED per DECISION-I04 + 2026-09-25 chips الشخصية PD-I07 CLOSED per DECISION-I07 + 2026-09-25 Light/Dark + Soft Depth PD-I08 CLOSED per DECISION-I08 — 74→75 facts — Light #FAFAF8/#FFFFFF/#121214 + Dark دافئ #18140F/#221C16/#F3ECE2 + Soft Depth sm/md/lg/float + Dark .30-.50 + Auto افتراضي prefers-color-scheme + 200ms transitions + P-11 CONFIRMED 10 أولية + Load More حتى 50 + 3 تصحيحات مؤجلة Stage 7
- Stage 4 NEXT: PD-I09 Motion + Settings Modal Topic جديد + PD-I05-R2 بعد الإطلاق — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB — توثيق فقط — لا Migration — لا تنفيذ — لا تعديل Brand القديم — وثّق فقط لا تنفذ
 — PD-I01 CLOSED — PD-I02 CLOSED — PD-I03 CLOSED — PD-I04 CLOSED — PD-I05 DEFERRED — PD-I06 CLOSED — PD-I07 CLOSED

- Stage 3 — Content & Editorial System — CLOSED — 2026-09-14 — 66 facts — PD-04+PD-05+PD-06 SKIPPED+PD-07+PD-08+PD-09+PD-10
- Stage 4 — Experience & Identity — OPEN — Identity Re-Foundation — 2026-09-21 Brand Direction الختم PD-I01 CLOSED + 2026-09-23 Qussasa Mark v1.0 PD-I02 CLOSED + 2026-09-23 Multi-Accent Color System PD-I03 CLOSED + 2026-09-24 Watermark DEFERRED per DECISION-I05 + 2026-09-24 Reaction Card & Detail Page PD-I06 CLOSED per DECISION-I06 + 2026-09-25 Typography System PD-I04 CLOSED per DECISION-I04 + 2026-09-25 chips الشخصية PD-I07 CLOSED per DECISION-I07 — 74 facts ثابتة — Direction C Al-Khatm + Qussasa Mark v1.0 Logo هيدر فقط + Multi-Accent Base Ink/Paper/Grey + Accent Qussasa-derived Amber + Optional Amber/Purple/Teal + Theme Day/Night/Auto + Reduce Motion + Settings Modal على ذوقك + Reset + Watermark مُجمّد PD-I05-R2 بعد الإطلاق + البطاقة وسائط+Duration+عنوان+⋮ + التفاصيل 8 كتل + أزرار رئيسية حفظ+تنزيل+مشاركة + ⋮ نسخ رابط+إبلاغ فقط لا تعديل Admin + عشوائية محدودة 10-20 + أزرار التفاصيل على نفس سطر العنوان جهة اليسار في RTL + لا Empty States + Duration ✅ البطاقة فقط ❌ لا في التفاصيل + Related+More نفس بطاقة Reaction Card + Typography Lalezar Logo فقط + IBM Plex Sans Arabic + Inter + IBM Plex Mono + RTL كامل أرقام Western
- Stage 4 NEXT: PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB — توثيق فقط — لا Migration — لا تنفيذ — لا تعديل Brand القديم — وثّق فقط لا تنفذ
 — PD-I01 CLOSED — PD-I02 CLOSED — PD-I03 CLOSED — PD-I04 CLOSED — PD-I05 DEFERRED — PD-I06 CLOSED

- Stage 3 — Content & Editorial System — CLOSED — 2026-09-14 — 66 facts — PD-04+PD-05+PD-06 SKIPPED+PD-07+PD-08+PD-09+PD-10
- Stage 4 — Experience & Identity — OPEN — Identity Re-Foundation — 2026-09-21 Brand Direction الختم PD-I01 CLOSED + 2026-09-23 Qussasa Mark v1.0 PD-I02 CLOSED + 2026-09-23 Multi-Accent Color System PD-I03 CLOSED + 2026-09-24 Watermark DEFERRED per DECISION-I05 + 2026-09-24 Reaction Card & Detail Page PD-I06 CLOSED per DECISION-I06 + 2026-09-25 Typography System PD-I04 CLOSED per DECISION-I04 — 73→74 facts — Direction C Al-Khatm + Qussasa Mark v1.0 Logo هيدر فقط + Multi-Accent Base Ink/Paper/Grey + Accent Qussasa-derived Amber + Optional Amber/Purple/Teal + Theme Day/Night/Auto + Reduce Motion + Settings Modal على ذوقك + Reset + Watermark مُجمّد PD-I05-R2 بعد الإطلاق + البطاقة وسائط+Duration+عنوان+⋮ + التفاصيل 8 كتل + أزرار رئيسية حفظ+تنزيل+مشاركة + ⋮ نسخ رابط+إبلاغ فقط لا تعديل Admin + عشوائية محدودة 10-20 + أزرار التفاصيل على نفس سطر العنوان جهة اليسار في RTL + لا Empty States + Duration ✅ البطاقة فقط ❌ لا في التفاصيل + Typography Lalezar Logo فقط + IBM Plex Sans Arabic + Inter + IBM Plex Mono + RTL كامل أرقام Western
- Stage 4 NEXT: PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB — توثيق فقط — لا Migration — لا تنفيذ — لا تعديل Brand القديم — وثّق فقط لا تنفذ
