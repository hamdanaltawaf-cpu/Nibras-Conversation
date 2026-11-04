# النصوص الأصلية للقرارات الملغاة أو المستبدلة — نقل 2026-11-04

**الحالة:** أرشيف تاريخي فقط. لا يُعاد اعتماد أي نص أدناه كقرار نافذ.
**قاعدة النقل:** النصوص أدناه نُقلت من مواضعها في السجلات الحالية، وحلّت إحالات قصيرة محلها. Git يحتفظ بالنسخ السابقة للملفات.

## DECISION-014

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

---

## P-02

- **Previous:** P-02 (Video only — static images rejected) — CONFIRMED في Canonical Baseline القديم:
  - S02, S06, S10 explicitly reject Pinterest static
  - S04 MVP excludes static
  - 12 مصدر تاريخي تعتبر الصور مرفوضة كمنتج

---

## P-18

    - P-18 القديم: "Arena-Agent يرفع 300-500"

---

## P-18-repeat

P-18 القديم "Arena-Agent يرفع 300-500" → P-18 المُعدّل "Arena-Agent يبني ويجهّز وينشر. حمدان يرفع 300-500."

---

## old placeholder log

النص السابق لحقل البحث: «ابحث عن رياكشن أو موقف...»

---

## 5.2.57

- **5.2.57:** الخيار B السابق (إبقاء الرياكشن المحذوف/غير المنشور في النتائج حتى نهاية الجلسة) SUPERSEDED بالنطاق المحدد في 5.2.66؛ يبقى محفوظًا كسجل تاريخي ولا يُنفّذ.

---

## old placeholder baseline

النص السابق لحقل البحث: «ابحث عن رياكشن أو موقف...»

---

## old nav and modal

The earlier five-item mobile navigation in DECISION-I10 is historical for the affected navigation scope only; its Library, Collections, Account concepts and unrelated decisions are not erased. The earlier Settings Modal presentation in DECISION-I03/P-37 is superseded only as the presentation pattern by the founder-approved dedicated page; existing settings values are not automatically superseded.

---

## old Day default

- Theme default conflict: P-37 says Day by default; DECISION-I08 says Auto by default. Do not choose silently.

---

## old reconciliation

**Reconciliation:** This decision supersedes the “Day default” wording in the historical P-37 entry only for the default-theme choice. DECISION-I08’s “Auto = default” behavior is reaffirmed. The prior Stage 5-B choice of a dedicated Settings page supersedes the old modal-only presentation direction; it does not silently change the approved appearance controls or tokens.

---

## project superseded register

### SUPERSEDED (مستبدلة مع تاريخ)

- BottomNav: Submit → Collections → Saved (كما موضح أعلاه).
- انبهار كفئة عاشرة بلون مستقل → أُلحقت بعائلة استغراب (نفس التركواز) لتفادي تضخم التصنيف.

---

## old BottomNav

- **BottomNav الخانة الرابعة = Saved:** تاريخ القرار: أولًا Submit (SUPERSEDED لأنه يضع إنشاء محتوى بنفس مستوى الاكتشاف)، ثم Collections (SUPERSEDED لأن 3 مجموعات لا تبرر مقعد تنقل دائم)، حاليًا Saved لأنه أقرب فعل شخصي متكرر لـ"خذها. حطها.".

---

## old BottomNav timeline

- BottomNav الرابعة: Submit (SUPERSEDED) → Collections (SUPERSEDED) → Saved (PROPOSED حاليًا).

---

## old nav settings

- **Historical scope:** DECISION-I10's former five-item mobile navigation and DECISION-I03/P-37's modal-only Settings presentation are superseded only in the affected scope. Historical records remain intact.

---

## stale C01

- **Next topic:** **C-01 — تعريف المحتوى اليمني (Content Axis)**. The deferred P-20 criterion #6 (“يكتمل معناه بلا شرح”) remains assigned to C-01.
