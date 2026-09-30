# YEMREACT-REFORMATION-MASTER-PLAN.md — Phase 2A — Product Re-Foundation Orientation

> Phase 2A only — No product decisions, no UX decisions, no technical decisions, no code/Git/DB modification.
> Inputs: YEMREACT-CANONICAL-BASELINE.md (37 facts), YEMREACT-OPEN-DECISIONS-FINAL.md (61 open: 20 Product + 15 UX/IA + 18 Technical + 8 Blocked), YEMREACT-HISTORICAL-NOT-CURRENT.md (43 items), YEMREACT-UNKNOWNS-FINAL.md (49 unknowns: Must Before 10 / During 21 / Deferred Technical 17 / Informational 1), YEMREACT-REFOUNDATION-ORDER.md (49 ordered), YEMREACT-PHASE-1C-REPORT.md (PARTIAL), plus 12 original sources when needed.
> Date: 2026-09-11

---

## 1. مبادئ إعادة التأسيس (10 قواعد)

1. **نبدأ من الصفر الفكري، لا من الصفر التقني.** الكود الحالي (Next.js working tree 331c1b3 + 119 untracked) هو حقيقة تقنية حالية، ليس حقيقة منتج. نحتفظ به كمرجع تقني فقط.
2. **التاريخ مرجع وليس سلطة.** ملفات Claude Foundation, Manus V1/V2, Arena Discussion/Technical, Prototypes, Existing Code — كلها مصادر يجب تدقيقها، ليست قرارات تلقائية.
3. **القرار الجديد يتفوق على القرار التاريخي فقط بعد اعتماده الصريح بكلمة "تم" من صاحب المشروع.** لا يعتبر الأحدث زمنيًا صحيحًا تلقائيًا.
4. **لا تنفيذ أثناء النقاش.** ممنوع code / Git / DB / Migration / تصميم بصري جديد / تنفيذ حتى إغلاق المراحل الثماني كـ ACCEPTED.
5. **لا قرار تقني يسبق القرار المنتج الذي يعتمد عليه.** مثال: لا نناقش worker vs S3 presigned (TD-01) قبل حسم PD-07 duration و PD-08 aspect و PD-01 product definition.
6. **نميز دائمًا بين:** Product Truth (ما يجب أن يكون المنتج)، UX/IA Decision (كيف يتنقل المستخدم)، Technical Reality (ما هو موجود فعلًا في الكود/DB)، Historical Artifact (نسخة قديمة/بروتوتايب/اقتراح superseded)، Unknown (لا دليل كافٍ).
7. **كل مرحلة لها مدخل ومخرج واضح.** لا ننتقل للمرحلة التالية قبل تحقيق Exit Criteria + تم من المالك.
8. **نِبراس هو المتحدث والمناقش الوحيد مع المالك في Product Re-Foundation.** Arena-Agent لا ينفذ، لا يصمم، فقط يقرأ ويعلق كملاحظات حتى Phase 3 Blueprint / Handoff.
9. **لا نعيد إدخال عناصر تاريخية تلقائيًا لمجرد ظهورها في مصدر.** Historical يبقى Historical حتى يعاد اختياره صراحة (Historical Contamination Guard).
10. **عندما لا تكفي الأدلة، نُبقي المسألة Open أو Unknown — لا نخترع تسوية.** نستخدم لغة CONFIRMED / ACCEPTED / PROPOSED / CONFLICTED / UNKNOWN فقط.

---

## 2. المراحل الثماني — الخريطة

Based on REFOUNDATION-ORDER.md Level 1-5 (49 ordered) and Phase 1C PARTIAL assessment, the 8 stages are kept as proposed, with slight Arabic clarification to match YemReact context:

- **Stage 1 — Product Definition** (تعريف المنتج)
- **Stage 2 — Audience & Value** (الجمهور والقيمة)
- **Stage 3 — Content & Editorial System** (المحتوى ونظام التحرير)
- **Stage 4 — Experience & Identity** (التجربة والهوية)
- **Stage 5 — Information Architecture & Navigation** (البنية والتنقل)
- **Stage 6 — Core User Flows** (التدفقات الأساسية)
- **Stage 7 — Technical Foundation** (الأساس التقني)
- **Stage 8 — Operations / Growth / Launch** (التشغيل والنمو والإطلاق)

> No stage discussion started here — only map.

---

## 3. لكل مرحلة — التفصيل

### Stage 1 — Product Definition

- **Objective:** حسم ما هو YemReact فعلًا — هل هو محرك بحث عن رياكشنات أم مكتبة اكتشاف أولًا؟ ما الحلقة الأساسية التي تحكم كل شيء تحته؟
- **Questions:**
  1. هل YemReact "محرك بحث عن رياكشنات يمنية" (package.json/layout.tsx) أم "مكتبة رياكشنات يمنية" (hero/header) — ما التعريف الذي يمثل الوعد "خذها. حطها. يمنية."؟
  2. ما Core Loop النهائي: Utility-first (أداة عند الحاجة، تذكر وقت الحاجة) vs Discovery-first (تصفح يومي) vs Hybrid vs Content-library-first — ما ترتيب الأولويات داخل الحلقة؟
  3. هل القيمة الأساسية (بحث موقفي + انتقاء + واترمارك جاهز) تصمد أمام "أسجل الشاشة من TikTok" — ما الدليل؟
  4. ما تعريف النجاح الرقمي: Search Success Rate؟ Save Rate؟ Share Rate؟ Submission Conversion؟ Retention mental availability vs engagement loop؟
  5. هل نبدأ من الصفر الفكري مع الحفاظ على Brand LOCKED و Video-only و No social feed كـ Canonical؟
- **Decisions Produced:** PD-01, PD-02, PD-03, PD-20
- **Dependencies:** None — root. Depends only on Canonical Baseline B-01 to B-07, P-01 to P-06, IA-01 to IA-06.
- **What must NOT be discussed yet:** BottomNav 4th, Search route /?q= vs /search vs /بحث, Collections/Categories role as navigation, Submit fields, Media infra worker vs S3, Git hygiene, Env separation, Bugs, Settings UI, Footer legal details.
- **Relevant historical sources:** S02 Vision, S08 Arena-Discussion (tensions library vs utility), S10 Claude Foundation (reaction = digital proverb, tool at need → hybrid), S09 Technical (package.json vs hero conflict), S01 Taxonomy note up to 60s
- **Open decisions from 61:** PD-01, PD-02, PD-03, PD-20
- **Unknowns affecting:** U-01, U-02, U-03, U-04? Actually U-04 good content but also product, U-10? No — U-01 to U-03, U-10? Actually Must Before 10 includes product definition, core loop, value, good content, pipeline timing, duration, aspect, search route, bottom nav, sidebar — but for Stage 1 only U-01, U-02, U-03
- **Exit criteria:** Owner written تم on PD-01 product definition + PD-02 core loop + PD-03 value validation + PD-20 metrics — with explicit Arabic + English short formulation + priority order inside loop + impact on next stages documented.

### Stage 2 — Audience & Value

- **Objective:** تحديد من نخدم أولًا وما القيمة التي نقدمها له وما الذي لا نقدمه.
- **Questions:**
  1. من الجمهور الأساسي: صناع ميمز 16-30، صناع محتوى يبحثون عن بديل محلي لـ Giphy/Tenor، مستخدم عادي يريد تعبير سريع، صفحات يمنية/عربية — ما الترتيب؟
  2. ما احتياجات كل شريحة وآلامها (بحث سريع، أصالة لهجة، جاهزية فورية بلا تعديل يدوي)؟
  3. هل نستهدف الشبكة/الجهاز اليمني 3G بطيء + هاتف منخفض كافتراض غير مقاس أم نحتاج أرقام حقيقية؟
  4. ما الذي لا نخدمه: متابعين/تعليقات/لايكات عامة/ترند/فيد لا نهائي — هل نبقيها REJECTED؟
  5. كيف نقيس القيمة: هل البحث الموقفي ("لما صاحبك يقول بكرة") أقوى من المشاعر المجردة ("صدمة") — ما الدليل؟
- **Decisions Produced:** PD-04? Actually audience & value includes target audience definition (not in open list but implied), PD-03 already, PD-20 metrics
- **Dependencies:** PD-01, PD-02 (product definition, core loop)
- **What must NOT be discussed yet:** Categories fixed vs open, Collections editorial vs rail, Video duration/aspect details, Search intent segmentation, Media infra, Settings, Legal pages details, Git/Env.
- **Relevant historical sources:** S02 Vision (target audience table, differentiation matrix), S08 open questions acquisition channel, S10 product principles انتقاء أهم من الكمية
- **Open decisions:** PD-03, PD-20, plus audience definition (not in 61 but from S02)
- **Unknowns:** U-03 value vs screen record, plus network/device not measured (S08 open)
- **Exit criteria:** Owner تم on primary persona + audience priority + value proposition that withstands screen record + what we explicitly do NOT serve (REJECTED list reaffirmed).

### Stage 3 — Content & Editorial System

- **Objective:** حسم ما هو "محتوى جيد" وكيف يُنتج ويُراجع وينظم.
- **Questions:**
  1. ما Rubric تشغيلي ثابت 6 نقاط: يُفهم فورًا بلا سياق، قصير (2-8s vs حتى 60s)، أصالة لهجة يمنية، تحديد موقفي كافٍ، نظافة تقنية، راحة مصدر — هل نعدله بسبب المدة الجديدة حتى دقيقة؟
  2. كيف نطبق Rubric على فيديو 45 ثانية لا يزال رياكشن — هل نفرق بين Clip سريع ≤8s و Clip سردي حتى 60s؟
  3. ما معنى التنوع كبيانات داخلية: عمر/جنس/لهجة/سياق — هل نتتبعه داخليًا فقط؟
  4. ما مصدر المحتوى: جمع يدوي 30-50 أولًا من المسؤول ثم فتح مساهمات عند دليل سلوكي — ما تعريف الدليل السلوكي (S5 لا اتفق)؟
  5. ما سياسة التكرار: ملف متطابق = رفض، نفس الموقف بأداء مختلف = قبول بشرط الأصالة — هل نكتب معايير مكتوبة بسيطة؟
  6. ما نظام التصنيف: 9 فئات ثابتة كبيانات داخلية + كلمات مفتاحية مفتوحة 3-5 كلمات بلغة موقف + أداة قابلة للتطوير لهيكلة خوارزمية مستقبلًا — كيف نهيكله؟
  7. ما دور المجموعات: أداة تنظيم للمسؤول فقط أم Rail داخلي أم صفحة ألبومات عنوان+عدد؟
- **Decisions Produced:** PD-04, PD-06, PD-07, PD-08, PD-09, PD-10, PD-15, PD-16, PD-17, PD-18
- **Dependencies:** PD-01, PD-02, PD-03 (product definition, core loop, value)
- **What must NOT be discussed yet:** Search route details, BottomNav final, Sidebar final, Header/Footer composition, Media infra worker vs S3, Git/Env, BUG fixes, Settings UI timing, Legal pages exact scope.
- **Relevant historical sources:** S06 Content Assets + Production Guide (pipeline 8 steps, quality rubric, checklist), S10 Claude Foundation (content system caption formats, 9 categories, collections admin-edit, review flow), S02 Vision (150-300 threshold), recent Axis B notes (6 criteria + diversity + tool algorithmic)
- **Open decisions:** PD-04, PD-06, PD-07, PD-08, PD-09, PD-10, PD-15, PD-16, PD-17, PD-18, plus S1-S5 from Axis B (keyword system, duplication criteria, diversity ratios, daily need, behavioral evidence)
- **Unknowns:** U-04 good content, U-05 pipeline timing, U-06 duration, U-07 aspect, plus content unknowns (real content existence, seed vs mock, tags model)
- **Exit criteria:** Owner تم on Rubric 6 points + diversity internal tracking + content types priority (عند الحاجة أولًا ثم مكتبة الأسبوع ثم اليومي مؤجل) + taxonomy 9 categories data-only + open keywords tool + collections as admin tool + duplication policy + pipeline manual 30-50 first then submissions condition (with alternative definition for behavioral evidence after S5 لا اتفق).

### Stage 4 — Experience & Identity

- **Objective:** تثبيت كيف نحافظ على الهوية المقفلة ونطبقها على أي مقاس/مدة بدون تغييرها، وما التجربة الشعورية.
- **Questions:**
  1. كيف نطبق Qussasa / Peel / Duration Tag / Category Dot على أي مقاس (16:9 أفقي، 9:16 عمودي، 1:1 مربع، 4:5، 3:4) — Safe Area نسبي كيف يُحسب؟
  2. هل Overlays الحالية (06-... Default/Mirrored) تبقى كمرجع فقط أم نحتاج نظام توليد ديناميكي؟
  3. ما مواصفة الواترمارك المعتمدة: 11% أعلى-يمين بظل مزدوج (arena.md) vs 14% أسفل-يمين بلا ظل (ffmpeg.ts) — ما الحجم/الزاوية/الظل النهائي؟
  4. هل مدة 60 ثانية لا تزال "رياكشن" أم تصبح "مقطع" — كيف نفرق في UI بين سريع ≤8s وطويل حتى 60s — هل نضيف فلتر مدة؟
  5. ما صيغ الكابشن: اقتباس مباشر، "لمّا..." موقفي، بلا نص — لا نص يشرح النكتة — حد 3 إيموجي — لا مقدمات فيديو؟
- **Decisions Produced:** PD-14 watermark spec, PD-07 duration, PD-08 aspect, plus brand application rules (not in open list but from S10)
- **Dependencies:** PD-01, PD-02, PD-04, PD-07, PD-08 (product definition, core loop, good content, duration, aspect)
- **What must NOT be discussed yet:** IA sitemap exact, BottomNav final, Search route exact, Collections page vs rail, Submit button tension exact timing, Media infra choice, Git/Env, Bugs, Legal pages, Growth viral loop.
- **Relevant historical sources:** S10 Claude Foundation (Brand LOCKED details, Qussasa geometry, watermark double-shadow + flip rule, clip system 9:16+1:1 2-8s), S05 UI Design System (color tokens, typography, spacing, breakpoints), S01 Taxonomy (overlays, safe-area guides), S09 Technical (tokens.css matches LOCKED, watermark/qs.png 200, .storage 216 pairs)
- **Open decisions:** PD-14, PD-07, PD-08, plus brand application (safe area relative)
- **Unknowns:** U-06 duration, U-07 aspect, U-26 watermark spec, plus brand unknowns (exact hex BD-01)
- **Exit criteria:** Owner تم on how to apply identity to any size + duration distinction (fast ≤8s vs narrative up to 60s) + watermark spec authoritative + caption formats 3 + no intro rule + safe area relative calculation — without changing Brand v1.0 LOCKED.

### Stage 5 — Information Architecture & Navigation

- **Objective:** حسم خريطة الموقع والتنقل — ما الصفحات، كيف نتنقل، ما موطن كل وظيفة.
- **Questions:**
  1. ما خريطة الموقع النهائية: الرئيسية = المكتبة، صفحة تفاصيل /ر/[رمز] برابط حقيقي، صفحة بحث منفصلة /بحث أم /?q= فقط، صفحة مجموعات /مجموعات كألبومات، قائمة حساب منبثقة، لوحة إدارة 4 أقسام، تذييل مبسط؟
  2. ما تركيبة الشريط العلوي الثابت: شعار + بحث (عدسة) + زر مساهمة (+) للمستخدم — هل زر المسؤول في الإدارة فقط؟
  3. ما تركيبة الشريط السفلي: الرئيسية، [زر مؤقت مكان البحث سيتغير]، المجموعات، الحساب — هل البحث يعتمد في العلوي فقط؟
  4. هل الفئات تظهر كفلتر بارز أم بيانات داخلية فقط — هل نحتاج 3 طبقات (فئة + مجموعة + كلمات مفتاحية)؟
  5. هل المجموعات تظهر في السفلي أم Rail داخلي أم صفحة ألبومات — ما عتبة 150-300؟
  6. ما تذييل نهائي: معلومات الموقع + خريطة + حسابات + مطور بدون قانونية — هل القانونية مؤجلة لمرحلة فتح المساهمات؟
- **Decisions Produced:** UX-01 search route, UX-02 bottom nav 4th, UX-03 sidebar, UX-04 home composition, UX-05 header, PD-09 categories role, PD-10 collections role, PD-13 footer, PD-11 legal, PD-12 terminology, UX-11 account consolidation
- **Dependencies:** PD-01, PD-02, PD-04, PD-06, PD-07, PD-08 (product definition, core loop, good content, library size, duration, aspect)
- **What must NOT be discussed yet:** Core user flows exact sequence (video→title→window→category→collections→save→share→related), Submit form exact fields, Save sync details, Admin bulk approve, Media infra worker vs S3, Git/Env, BUG fixes, Settings UI, Growth viral loop, Monetization.
- **Relevant historical sources:** S03 IA & Sitemap (Home=library ACCEPTED, no sidebar ACCEPTED, detail page ACCEPTED, bottom nav 4 items, sitemap /?q=, /r/[code], /saved, /account sheet, /settings, /terms, /privacy, /admin), S05 UI (breakpoints mobile <700 tablet 700-1023 desktop ≥1024, header 2-tier, footer), S08 Discussion (13 axes, bottom nav chain, sidebar debate, terminology فئات vs تصنيفات), S09 Technical (45 routes, sidebar 286px exists, /search 200, /collections 200, /saved 200, BottomNav has Submit), recent Axis C notes (top search only + bottom placeholder, collections as albums title+count, category removal final, admin 4 sections + 3 permissions, footer info+map+accounts+developer)
- **Open decisions:** UX-01, UX-02, UX-03, UX-04, UX-05, PD-09, PD-10, PD-11, PD-12, PD-13, UX-11, plus CONFLICT-004, 005, 007, 008, 009, 010, 034, 035
- **Unknowns:** U-08 search route, U-09 bottom nav, U-10 sidebar, plus IA unknowns (search intent segmentation, rails priority, onboarding, accessibility)
- **Exit criteria:** Owner تم on sitemap final (Main=library, Detail page /r/[code] real link, Search separate /بحث with writing bar → results vs /?q=, Collections /مجموعات as albums, Account menu popup with saved count, Admin 4 sections, Footer info+map+accounts+developer) + top bar (logo + search + submit + for user) + bottom bar (home, [temp], collections, account) — all as NOTES ONLY first, then ACCEPTED.

### Stage 6 — Core User Flows

- **Objective:** تصميم تفصيلي لتسلسل كل تدفق أساسي بدون بناء.
- **Questions:**
  1. ما تسلسل صفحة تفاصيل الرياكشن: فيديو → عنوان + ثلاث نقاط يسار محاذاة العنوان (حفظ أولًا ثم تنزيل ثم نسخ رابط ثم مشاركة) → وصف أساسي → زر مطوي للوصف الثنائي يظهر فقط إذا وجد → مجموعات مرتبطة إن وجدت → فيديوهات قريبة — بدون فئة نهائيًا — هل هذا الترتيب منطقي؟
  2. ما تدفق البحث: ضغط عدسة → شريط كتابة يظهر → يكتب → اقتراحات تصحيح/مشابه عند الكتابة فقط مثل بنترست → ضغط بحث → صفحة نتائج منفردة → شبكة نتائج + حالة فارغة مشجعة — بدون فلاتر الآن؟
  3. ما تدفق الحفظ: ضغط حفظ (يتطلب حساب جوجل فقط) → إذا غير مسجل يفتح تسجيل جوجل ثم يعود ويحفظ تلقائيًا → يظهر في المحفوظات مع عدد ظاهر بجانب الكلمة؟
  4. ما تدفق المساهمة: زر (+) مساهمة للمستخدم يظهر الآن للجميع → إذا لم يكن مسجلاً يطلب جوجل فقط → نموذج مساهمة (فيديو + ملاحظة اختيارية) → يذهب لقسم المساهمات في الإدارة → حالة في حسابه (قيد الانتظار/مقبولة/مرفوضة) → رسالة "ستبدأ المراجعة بعد اكتمال الأساسي 30-50" إذا اخترنا Option C؟
  5. ما تدفق الإدارة: قائمة انتظار → مراجعة واحدة مع 6 معايير + نقطة تنوع + كلمات مفتاحية قابلة للتطوير + إضافة لمجموعة اختيارية → قبول/رفض جماعي → اختصارات لوحة مفاتيح → 40 في الساعة؟
  6. ما حالات كل صفحة: عادية، تحميل (هيكل رمادي)، فارغة، لا نتائج، جديد، عائد، خطأ؟
- **Decisions Produced:** PD-15 submission fields, PD-16 privacy, UX-08 detail modal vs page, UX-12 save UI, UX-13 search bar, UX-14 error/empty Arabic, plus flow sequences (not in 61 list but derived)
- **Dependencies:** PD-01, PD-02, PD-04, PD-05, PD-07, PD-08, UX-01, UX-02, UX-03, UX-04, PD-09, PD-10 (product + IA)
- **What must NOT be discussed yet:** Media infra worker vs S3, storage driver, ffmpeg details, upload memory vs streaming, delivery Range/auth, worker queue, schema drift, BUG fixes, Git hygiene, Env separation, Testing isolation, CI, SEO metadata, Monetization, Growth viral loop.
- **Relevant historical sources:** S03 IA (core flows Search→Preview→Take, Save, Submission, Onboarding open), S04 Features (core loop, searchable catalogue, detail page, save local↔cloud, submission workflow, admin CRUD, watermark-gate, empty/error states, analytics internal), S05 UI (ReactionCard, ReactionDetail, SearchBar, CategoryNav, BottomNav, AccountMenu, SavedReactionsClient, SubmissionForm, AdminLayout), S06 Content (pipeline 8 steps, copy deck, quality rubric, checklist), S09 Technical (ReactionDetail all actions exist, Share no fallback, Download no Content-Disposition, muted fixed, Related simplified, /saved logs view per card N requests, double fetch /search, getCurrentUser 3x), recent Axis C (detail three dots left aligned title, collapsible binary description only if exists, collections if exists, nearby videos, no category final)
- **Open decisions:** PD-15, PD-16, UX-08, UX-12, UX-13, UX-14, plus flow details
- **Unknowns:** Search intent, onboarding, save UI, search bar debounce, etc. (UX unknowns)
- **Exit criteria:** Owner تم on detailed sequence for Detail Page + Search separate page + Save with Google only + Submit now with queue message Option C (or A/B) + Admin 4 sections + all states (normal, loading, empty, no results, new, returning, error) — as NOTES ONLY.

### Stage 7 — Technical Foundation

- **Objective:** حسم الأساس التقني كفكرة فقط (لا تنفيذ) بعد اعتماد Product و IA و Flows.
- **Questions:**
  1. ما خيار البنية التحتية للوسائط: worker خارجي (VPS/Fly/Railway) + R2/S3 + presigned upload vs خدمة معالجة مُدارة (Cloudflare Stream) vs ترك Vercel — ما التكلفة؟
  2. ما تجريد التخزين: Local FS ./storage vs S3/R2, ensureWatermarkFile writes to ./storage even with S3, S3_PUBLIC_URL override, /media vs direct URL + signed — ما النهائي؟
  3. ما تفاصيل FFmpeg: ffprobe json, thumbnail JPEG 480 vs scale ≤1080 WebP, watermark PNG Qussasa 14% bottom-right no shadow vs 11% top-right double shadow — ما المواصفة المعتمدة؟
  4. ما سياسة الرفع: file.arrayBuffer() حتى 80MB في الذاكرة vs streaming مباشر للتخزين, حد body 4.5MB Vercel vs 80MB env — كيف نصلح؟
  5. ما سياسة التسليم: /media/[...key] no Range/206, no Content-Disposition, no auth for submissions/* — هل نضيف Range, guard, direct S3 URL + signed?
  6. ما Worker: void promise fire-and-forget vs real queue + retry + lease + ?retry endpoint — كيف نمنع processing عالق؟
  7. ما Schema drift: 3 raw indexes (Reaction_searchText_gin, Reaction_category_published_idx, Reaction_published_status_idx) not in schema.prisma — هل نضيف @@index أم migration وهمية؟
  8. ما إصلاح BUG-1/2/3/5: code vs UUID 404, PROCESSED vs WATERMARKED placeholder, durationMs NULL, double fetch, /saved N requests, getCurrentUser 3x no cache, category counts include draft, etc.?
  9. ما Git hygiene: 1 commit 331c1b3 2026-08-24, 28 modified, 119 untracked, no remote, working tree is reference — كيف نحفظ الحالة قبل أي checkout?
  10. ما Env separation: .env.local production Neon creds, AUTH_SECRET defaults insecure, E2E helper forges JWT, Vercel env vars UNKNOWN — كيف نفصل dev Neon branch؟
- **Decisions Produced:** TD-01 to TD-18 (18 technical decisions)
- **Dependencies:** All product decisions PD-01 to PD-20 + IA UX-01 to UX-05 + Flows (Stage 6) — especially PD-07 duration, PD-08 aspect, PD-14 watermark spec, PD-16 privacy, PD-09 categories locked vs open
- **What must NOT be discussed yet:** Growth viral loop, Monetization, Launch constraints, Marketing channels, Success metrics final, Operations runbooks — these are Stage 8. Also no implementation, no Git commit, no DB migration, no Vercel deploy in this stage — only idea.
- **Relevant historical sources:** S09 ARENA-TECHNICAL-HANDOFF (best technical truth — stack, routes, DB counts, media pipeline 829 files local 0 prod, testing 171 unit 94 E2E, Git dirty, env prod leak, bugs P0-P3, doc vs code conflicts, UNKNOWN 20), S07 GAPS (G1-G12, C1-C4, risk matrix R1-R7, roadmap P0-P8, final verdict 60%), S04 FEATURES (technical spec Next.js 15, routing, UI components, auth, DB, media pipeline, storage driver, watermark, API routes 23, AuditLog 0 rows, Saves, Search, Rate limiting pending≤5, Error handling), S05 UI (breakpoints, component catalog), S03 IA (schema cleanup ACCEPTED direction, media processing managed service ACCEPTED direction)
- **Open decisions:** TD-01 to TD-18 (18) + BD-01 to BD-08 blocked by unresolved evidence
- **Unknowns:** U-32 to U-48 deferred technical (production URL, Vercel env vars, bucket existence, S3 real test, integration tests 94+30, ffmpeg now, media infra, storage, upload, delivery, worker, schema drift, bugs, git hygiene, env separation, testing isolation)
- **Exit criteria:** Owner + Arena-Agent agree on technical foundation as idea only (no code) — media infra choice (worker + S3/R2 + presigned), storage driver, FFmpeg spec, upload streaming, delivery Range + auth guard for submissions/*, worker queue with lease, schema drift fix approach, BUG-1/2/3/5 fix approach, Git hygiene commit+remote, Env separation dev Neon branch, Testing isolation — all documented as PROPOSED, not implemented, with cost estimate and owner تم on infra cost (TD-01).

### Stage 8 — Operations / Growth / Launch

- **Objective:** حسم التشغيل والنمو والإطلاق — كيف نطلق Facebook أولًا ثم الموقع، ما القيود، ما القنوات.
- **Questions:**
  1. ما خطة إطلاق Facebook: 30-50 فيديو حقيقي متنوع كحد أدنى اختبار + بحث جانبي + حفظ بجوجل فقط + تفاصيل برابط — هل 150-300 عتبة فائدة حقيقية؟
  2. ما قناة الاكتساب الحقيقية: SEO + روابط قابلة للمشاركة + Facebook + كلام متناقل + Google — ما القناة الأساسية غير المعروفة؟
  3. هل يوجد Viral Loop حقيقي أم تفكير مسقط من منتجات اجتماعية — هل Watermark كقناة توزيع فعال؟
  4. ما Settings أولوية: autoplay/صوت/توفير بيانات/حركة — هل نأجلها post-MVP بسبب واقع الشبكة اليمنية أم نجعلها front-and-center؟
  5. ما Onboarding walkthrough minimal لشرح "بحث موقفي + أخذ" — هل نحتاجه؟
  6. ما Metrics الخمسة النهائية: Search Success Rate? Save Rate? Share Rate? Submission Conversion? Retention mental availability vs engagement loop?
  7. ما Observability: لو تعطّل الموقع غدًا كيف نعرف — لا سجلات مركزية حاليًا — ما الحل؟
  8. ما Performance Budget بأرقام حقيقية لشبكة/جهاز يمني فعلي (3G بطيء افتراض غير مقاس)؟
  9. ما Accessibility / RTL edge cases — هل نتحقق؟
  10. ما Git: 147 ملف بلا Remote — Critical، فروع، CI، حماية إنتاج — كيف نمنع تكرار؟
  11. ما Monetization DEFERRED — لا قرار الآن لكن هل أي قرار تقني يمنعها مستقبلًا؟
- **Decisions Produced:** PD-11 legal pages, PD-19 monetization deferred check, PD-20 metrics, plus growth, operations, launch constraints (not in 61 list but from S02 pending decisions + S08 open questions + S07 roadmap P0-P8)
- **Dependencies:** All previous stages 1-7 — especially PD-01 product definition, PD-02 core loop, PD-05 pipeline timing, UX-01 search route, UX-02 bottom nav, TD-01 media infra, TD-12 git hygiene, TD-13 env separation
- **What must NOT be discussed yet:** No new product definition, no new IA, no new UX flows — only operations, growth, launch. No implementation yet — only constraints.
- **Relevant historical sources:** S02 Vision (differentiation matrix WhatsApp vs TikTok vs Giphy vs Telegram, immediate next steps 3 pending decisions video-review order, legal pages, original retention), S07 Gaps/Roadmap (P0 Git hygiene, P1 Env separation, P2 Media infra, P3 BUG-1, P4 BUG-2/3/5, P5 Security hardening, P6 Env & CI, P7 Terminology cleanup, P8 Post-MVP polish, final verdict 60% → 90% after P0/P1), S08 Discussion (open questions acquisition channel unknown, chicken-egg submissions, no numeric success, Yemeni network not measured, submission as growth engine), S09 Technical (AuditLog 0 rows, no Featured/Users/Audit UI, Settings not built, no CI, no isolated test DB, no favicon/robots/sitemap/manifest/OG, no PWA, no Range/HLS/CDN/signed URLs)
- **Open decisions:** PD-11, PD-19, PD-20, plus growth/ops questions (acquisition channel, viral loop, settings priority, onboarding, observability, performance budget, accessibility, git critical)
- **Unknowns:** U-49 informational (Manus relation, who wrote phases, qnasly189 role, mtimes unified, error.tsx behavior, performance under load, a11y, Google OAuth mode, other branches) + content unknowns (real content existence) + infra unknowns (CI, vercel.json, Range/HLS/CDN)
- **Exit criteria:** Owner تم on Facebook launch checklist (Profile 720x720, Cover 1640x720 2x, Overlays 9:16+1:1 Default+Mirrored, Safe Area Guides x4, Post Template 1080x1350, Category Collection, Announcements Intro/ComingSoon/Milestone, Story RequestReaction — all READY per S06) + first 10 posts per Content System + launch constraints (P0 Git hygiene commit+remote, P1 Env separation, P2 Media infra) + metrics 5 final + observability plan + performance budget numbers + accessibility check — as PROPOSED, not implemented.

---

## 4. Decision Dependency Map

```
Level 0 — Canonical Baseline (37 facts)
    |
    v
Stage 1 — Product Definition
    PD-01 Product Definition (search engine vs library)
        ↓
    PD-02 Core Loop (utility vs hybrid)
        ↓
    PD-03 Value vs screen record
        ↓
    PD-20 Success metrics (depends on PD-01, PD-02)
        |
        v
Stage 2 — Audience & Value
    Audience priority + Value proposition + Network/device assumption
        |
        v
Stage 3 — Content & Editorial System
    PD-04 Good content rubric (depends on PD-02)
        ↓
    PD-07 Video Duration (depends on PD-04 concept short = genre)
        ↓
    PD-08 Video Aspect (depends on PD-07)
        ↓
    PD-06 Library size thresholds (depends on PD-04)
        ↓
    PD-09 Categories role (depends on PD-01, PD-02)
        ↓
    PD-10 Collections role (depends on PD-06, PD-09)
        ↓
    PD-15 Submission fields (depends on PD-04, PD-05)
        ↓
    PD-16 Privacy of submissions (depends on PD-05)
        ↓
    PD-18 Featured selection
        |
        v
Stage 4 — Experience & Identity
    PD-14 Watermark spec (depends on PD-07, PD-08, Brand LOCKED)
    Brand application to any size (safe area relative)
    Caption formats 3 + no intro rule
        |
        v
Stage 5 — Information Architecture & Navigation
    UX-01 Search route /?q= vs /search vs /بحث (depends on PD-01, PD-02)
        ↓
    UX-04 Home composition (depends on PD-01, PD-02, UX-01)
        ↓
    UX-02 BottomNav 4th (depends on PD-02, PD-05)
        ↓
    UX-03 Sidebar final (depends on PD-01)
        ↓
    UX-05 Header composition (depends on UX-01, UX-02)
        ↓
    PD-09/PD-10 Categories/Collections role as navigation (depends on PD-06)
        ↓
    PD-13 Footer + PD-11 Legal + PD-12 Terminology
        |
        v
Stage 6 — Core User Flows
    Detail Page sequence (depends on UX-01 to UX-05, PD-09, PD-10, PD-07)
        ↓
    Search flow writing bar → results separate page (depends on UX-01, UX-13)
        ↓
    Save flow Google only + count visible (depends on UX-02)
        ↓
    Submit flow + tracking + queue message Option C (depends on PD-05, PD-15, PD-16)
        ↓
    Admin flow 40/hour + 6 criteria + diversity + keywords tool + bulk (depends on PD-04)
        ↓
    All states normal/loading/empty/no results/error
        |
        v
Stage 7 — Technical Foundation (idea only, no implementation)
    TD-01 Media infra worker vs S3 presigned vs managed (depends on PD-07, PD-08, PD-10, PD-14, PD-16)
        ↓
    TD-02 Storage driver Local vs S3 (depends on TD-01)
        ↓
    TD-03 FFmpeg + thumbnail + watermark generation (depends on TD-01, PD-14)
        ↓
    TD-04 Upload memory vs streaming (depends on TD-01)
        ↓
    TD-05 Delivery Range/auth guard (depends on PD-16, TD-01)
        ↓
    TD-06 Worker queue vs void promise (depends on TD-01)
        ↓
    TD-12 Git hygiene + TD-13 Env separation (independent P0, should be first technical)
        ↓
    TD-07 Schema drift + TD-08 BUG-1 + TD-09 BUG-2 + TD-10 BUG-3 + TD-11 other bugs
        ↓
    TD-14 Testing isolation + TD-15 Auth defaults + TD-16 Prisma tooling + TD-17 CSS + TD-18 SEO
        |
        v
Stage 8 — Operations / Growth / Launch
    PD-11 Legal pages + PD-19 Monetization deferred + PD-20 Metrics final
        ↓
    Acquisition channel unknown + Viral Loop + Watermark as distribution
        ↓
    Settings priority + Onboarding minimal + Observability + Performance Budget + Accessibility + Git critical
        ↓
    Facebook launch assets READY + first 10 posts + launch constraints P0-P2 → 90% ready
```

> This order is not assumed — it is derived from YEMREACT-REFOUNDATION-ORDER.md Level 1-5 (49 ordered) which itself was derived from evidence of dependencies (e.g., media infra depends on duration/aspect).

---

## 5. Decision Ownership

| Decision Type | Owner | Authority | Can Nibras approve instead of owner? | Examples |
|---|---|---|---|---|
| **Product Decisions** (PD-01 to PD-20) — definition, core loop, value, rubric, pipeline timing, duration, aspect, categories, collections, legal, terminology, watermark spec, submission fields, privacy, retention, featured, monetization, metrics | **Founder (صاحب المشروع)** | EXPLICIT — final authority, written تم required per MVP-Directive §6 | **NO** — Nibras cannot approve product decisions instead of owner. Nibras can propose, discuss, document as NOTES ONLY, but only owner تم makes it ACCEPTED. | PD-01 product definition, PD-02 core loop, PD-05 pipeline timing A/B/C, PD-07 duration, PD-08 aspect |
| **UX/IA Decisions** (UX-01 to UX-15) — search route, bottom nav, sidebar, home composition, header, footer, search intent, rails priority, detail modal vs page, settings timing, account consolidation, save UI, search bar, error states, modal قريباً | **Product Discussion (Nibras + Owner)** — Nibras leads discussion, Owner decides | ASSUMED for Nibras as facilitator, EXPLICIT for Owner as decider | **NO for final** — Nibras can propose UX blueprint as NOTES ONLY, but Owner تم required to close stage. | UX-01 search route /?q= vs /search vs /بحث, UX-02 bottom nav 4th, UX-03 sidebar, UX-04 home composition |
| **Technical Decisions** (TD-01 to TD-18) — media infra, storage driver, ffmpeg, upload, delivery, worker queue, schema drift, bugs, git hygiene, env separation, testing isolation, auth defaults, tooling, CSS, SEO | **Technical (Arena-Agent)** — leads technical foundation as idea only | ASSUMED for Arena-Agent as technical lead, but product-dependent technical (TD-01) needs Product Decision first | **NO** — Nibras cannot approve technical infra cost decision alone. Arena-Agent proposes as NOTES ONLY, Owner تم on cost (TD-01). | TD-01 media infra worker vs S3, TD-12 git hygiene, TD-13 env separation, TD-08 BUG-1 |
| **Blocked by Unresolved Evidence** (BD-01 to BD-08) — brand colors exact hex, watermark spec, production URL, Vercel env vars, bucket, integration tests, ffmpeg now, Manus relation, Google OAuth mode, real content | **Needs direct evidence** — file read of LOCKED HTML, Vercel dashboard, isolated test DB, build logs, Git history + owner | UNKNOWN — cannot be decided without evidence | **NO** — must not guess. Mark as UNKNOWN until evidence available. | BD-01 brand colors, BD-03 production URL, BD-06 Manus relation |

**Rule:** Nibras authority = Documentation authority (EXPLICIT) + Product Discussion facilitator (ASSUMED) — not Product authority, not Implementation authority, not Technical authority. Product authority = Founder EXPLICIT. Technical authority = Arena-Agent ASSUMED after product decisions.

---

## 6. Historical Contamination Guard

List of what must NOT be reintroduced automatically just because it appeared in a source. Historical stays Historical until explicitly re-chosen with تم.

| # | Historical Item | Appeared In | Why must not auto-reintroduce | Current Status |
|---|---|---|---|---|
| HC-01 | "محرك بحث عن رياكشنات" as sole product definition (package.json) | S09 Technical (package.json description) + S04 | Conflicts with "مكتبة رياكشنات يمنية" hero — need product decision PD-01 | CONFLICTED — do not auto |
| HC-02 | Brand colors #006633 deep green primary #B8860B mustard | S05 UI Design System | Conflicts with LOCKED HTML Ink #121214 Qishr Amber #C1592E per S10 + S09 tokens.css matches LOCKED | VERSION DRIFT — do not auto, need LOCKED HTML read |
| HC-03 | Typography Roboto only | S05 | S10 has Lalezar + Cairo + Archivo Black + Inter + IBM Plex Mono with usage rule ≤5 words, S09 supports S10 | VERSION DRIFT — do not auto |
| HC-04 | Home = hero + search + CategoryNav + 8 new + FeaturedStrip + ≤3 collections (dashboard) | S09 implementation / + S05 | Conflicts with ACCEPTED Home=library only (no rails) per S03/S08 | PROTOTYPE VS IMPLEMENTATION — do not auto, need PD-01/UX-04 decision |
| HC-05 | Search = /?q= only ACCEPTED as only truth | S03, S07 C1 | Implementation has /search 200 + recent Axis C separate /بحث page — evolution | VERSION DRIFT — do not auto, need UX-01 decision |
| HC-06 | Reaction Detail = Modal | Prototypes v1/v2, ui-prototype v4 | ACCEPTED is Page /r/[code] per S03/S08/S10 | HISTORICAL — Modal is superseded |
| HC-07 | BottomNav = Home/Search/Collections/Account (Collections in bottom) | S05 UI (old), S11 Manus V1, ui-prototype v4 | SUPERSEDED chain Submit→Collections→Saved, recent Groups in bottom | SUPERSEDED — do not auto |
| HC-08 | BottomNav = Home/Search/Submit/Account (Submit in bottom) | S05, S07, S09 docblock | Recent Axis C says top search only + bottom placeholder will change later, Groups in bottom per recent | VERSION DRIFT — do not auto, need UX-02 decision |
| HC-09 | Sidebar persistent 286px | S05, S09 code | ACCEPTED no permanent sidebar per S03/S08 | CONFLICT — decision vs implementation, do not auto as product truth |
| HC-10 | Categories = filter bar as main nav destination | S03 early, S10 early | Later data-only + color internal per S10 recent, S03 fixed buckets as filter — role questioned | VERSION DRIFT — do not auto |
| HC-11 | Collections = Rail internal only, not page | S02, S07 C2 | Recent Axis C albums title+count page, S09 Collection=3 page exists | VERSION DRIFT — do not auto |
| HC-12 | Submit form many fields (category/situation/tags/source/rights) | S10 early, S04 ignored fields | Minimal video+note only per S06/S10 recent, source/rights REMOVED ACCEPTED | SUPERSEDED — do not auto |
| HC-13 | Auth OTP + Session/OneTimeCode + ADMIN_EMAIL/SMTP_* | S09 models Session/OneTimeCode 0 rows, ADR-0001, .env.example | Replaced by Google + JWT Phase 6A, Google conditional per S09 | HISTORICAL — do not auto |
| HC-14 | Media pipeline local FS ./storage as production default | S04, S09 default | Blocked in prod, needs worker + S3/R2 per S07 G1 P0 blocker, S09 media=0 prod | HISTORICAL approach — do not auto as prod truth |
| HC-15 | Watermark 11% top-right double shadow as only spec | S10 arena.md §8.2 | Code has 14% bottom-right no shadow per S09 ffmpeg.ts, concept strengthened double shadow per S10 | CONFLICTED — do not auto, need PD-14 decision + LOCKED HTML read |
| HC-16 | Video duration 2-8s strict as only rule | S06, S10 | Note up to 60s flexible per S01, code no limit per S09 | VERSION DRIFT — do not auto, need PD-07 decision |
| HC-17 | Video aspect 9:16 primary + 1:1 secondary fixed only | S10 | Note any size per S01 | VERSION DRIFT — do not auto, need PD-08 decision |
| HC-18 | Search suggestions none | S03 | Manus V1 recent 4 + Yemeni suggestions + debounce 300ms + random reaction per S11 | VERSION DRIFT — do not auto, need UX-13 decision |
| HC-19 | Legal pages required at launch as only truth | S03, S07 | Deferred per S10, then info+map+accounts+developer no legal per recent Axis C | VERSION DRIFT — do not auto, need PD-11 decision |
| HC-20 | Featured manual via SQL/seed only as only way | S09 Featured id1→YR-0001 no admin UI | No way to change except SQL — needs product decision if manual UI needed | HISTORICAL limitation — do not auto as final |
| HC-21 | Manus V1/V2 WebDev stack React/Vite/Express/tRPC/Drizzle as current production | S11, S12 | Separate stack from Next.js yemreact-next HEAD 331c1b3, no Git remote to link, no production URL proof | HISTORICAL / separate project — do not auto merge into Next.js |
| HC-22 | Mock API for prerender as real data | S11, S12 | Build tool to bypass DB missing, not production content | PROTOTYPE-ONLY — do not auto as real content |
| HC-23 | Public preview Manus domain https://3000-... as production | S11, S12 | Temporary preview, not permanent hosting | PROTOTYPE-ONLY — do not auto |

**Guard Rule:** If an item is in this list, it must be explicitly re-chosen with Owner تم + evidence check before being presented as Current Truth in Phase 2. Otherwise it stays Historical.

---

## 7. Phase Entry / Exit Rules

### Entry Rules — When to start a stage

| Rule | Condition |
|---|---|
| E-01 | Previous stage Exit Criteria met + Owner تم written |
| E-02 | Canonical Baseline reviewed (37 facts) |
| E-03 | Open decisions for this stage identified from 61 list (PD/UX/TD/BD) |
| E-04 | Unknowns affecting this stage identified from 49 list (Must Before / During) |
| E-05 | Historical contamination guard checked — no auto-reintroduction of 23 historical items |
| E-06 | No code/Git/DB modification during discussion — only notes |

### Exit Rules — When to stop a stage

| Rule | Condition |
|---|---|
| X-01 | All Questions for this stage discussed (as NOTES ONLY) |
| X-02 | Decisions Produced for this stage documented as PROPOSED with evidence, not yet ACCEPTED |
| X-03 | Owner explicitly asked for تم on decisions of this stage |
| X-04 | What must NOT be discussed yet respected — no jumping to next stage topics |
| X-05 | No new product decisions made by Nibras alone — only Owner تم makes ACCEPTED |
| X-06 | Files updated: YEMREACT-CANONICAL-BASELINE remains unchanged (only new decisions add to OPEN), YEMREACT-OPEN-DECISIONS-FINAL updated with status, YEMREACT-REFORMATION-MASTER-PLAN entry/exit logged |

### When to pause and request clarification

| Condition | Action |
|---|---|
| Product vs Technical dependency unclear (e.g., TD-01 depends on PD-07) | Pause, ask Owner to confirm product first, do not discuss technical |
| Evidence insufficient (BD-01 to BD-08) | Pause, mark as UNKNOWN, request direct file read or dashboard, do not guess |
| Terminology conflict (فئات vs تصنيفات) | Pause, ask Owner to confirm dictionary, do not mass replace |
| Historical contamination suspected (item from HC-01 to HC-23 reappears) | Pause, check guard list, ask if explicitly re-chosen |
| Owner says "لا تنتقل لأرينا" or "توقف" or "لم أفهم" | Pause, clarify with user first, do not go to Arena |
| Same stage rebuilt 3 times (like Axis C) | Pause, summarize what is تم vs مؤجل, ask for explicit تم before proceeding |

### When to close a decision

| Condition | Action |
|---|---|
| Owner says "تم" explicitly on that decision | Move from PROPOSED/OPEN to ACCEPTED in CANONICAL BASELINE with source + confidence + تم date |
| Owner says "لا اتفق دعنا نناقشه" | Keep as OPEN, add to next stage or same stage re-discussion, document as مؤجل |
| Evidence resolves (e.g., CODE proves /r/[code] 200) | Mark as CURRENT technical reality, but still needs Product Decision if conflicts with Product Truth — do not auto-accept as Product Truth |

### When to transition to next stage

| Condition | Action |
|---|---|
| Exit Criteria met + Owner تم on all Decisions Produced of current stage | Transition to next stage in order (1→8) |
| If Level 1 not yet تم (PD-01, PD-02), cannot transition to Level 2+ | Stay in Level 1, do not jump to IA/UX/Technical |
| If P0 blockers (Git hygiene, Env separation, Media blocked) not fixed, can still transition to Stage 2-6 as product discussion, but cannot transition to Stage 7 implementation until P0 fixed | Product discussion can continue, technical implementation cannot |

---

## 8. Final Re-foundation Output — What we should have after 8 stages (as Outputs, not decisions yet)

After completing Stage 1-8, we should have:

1. **Product Definition** — Final definition: search engine vs library, core loop with priority order, value vs screen record validation, success metrics 5 — ACCEPTED with Arabic + English short formulation
2. **Product Principles** — 5-10 principles governing discussion (from Section 1) — ACCEPTED
3. **Audience & Value** — Primary persona, audience priority, network/device assumption, what we explicitly do NOT serve (REJECTED list reaffirmed)
4. **Content System** — Rubric 6 points + diversity internal tracking + content types priority (عند الحاجة أولًا ثم مكتبة الأسبوع ثم اليومي مؤجل) + taxonomy 9 categories data-only + open keywords tool algorithmic-capable + collections as admin tool (albums title+count) + duplication policy + pipeline manual 30-50 first then submissions condition with behavioral evidence alternative definition
5. **Experience & Identity** — How to apply identity to any size/aspect, safe area relative calculation, watermark spec authoritative (size/angle/shadow), caption formats 3 (اقتباس مباشر / لمّا... / بلا نص), no intro rule, duration distinction fast ≤8s vs narrative up to 60s
6. **Information Architecture & Sitemap** — Final sitemap: Main=library, Detail /ر/[رمز] real link, Search separate /بحث with writing bar → results vs /?q=, Collections /مجموعات as albums, Account menu popup with saved count, Admin 4 sections + 3 permissions, Footer info+map+accounts+developer no legal (or with legal if PD-11 decides required), terminology dictionary الفئات
7. **Navigation** — Top bar (logo + search + submit + for user) + Bottom bar (home, [temp that will change later], collections, account) — with search top only per recent decision, bottom placeholder future
8. **Core User Flows** — Detailed sequences: Detail Page (video → title + three dots left aligned title حفظ/تنزيل/نسخ/مشاركة → basic description → collapsible binary description only if exists → collections if exists → nearby videos, no category final), Search (lens → writing bar appears → type → suggestions correction/similar only when typing like Pinterest → search → separate results page grid + empty encouraging), Save (requires Google only → if not logged requests Google → opens and saves automatically → appears in saved with visible count), Submit ( + button appears now for all → if not logged requests Google only → form video+optional note → goes to submissions queue → status in account pending/approved/rejected → message "review after 30-50" if Option C), Admin (queue → single review with 6 criteria + diversity + keywords tool + optional add to collection → bulk approve/reject → keyboard shortcuts → 40/hour)
9. **Feature Scope** — MVP mandatory 10 features reaffirmed or revised (core loop, searchable catalogue home, detail page, save local↔cloud, submission workflow, admin CRUD, Google-only auth, watermark-gate, empty/error states, internal analytics) + explicitly excluded (infinite scroll, trending, leaderboards, comments, followers, PWA etc.) + deferred (semantic search embeddings post 300+, monetization)
10. **Technical Blueprint (idea only, no implementation)** — Media infra choice worker + S3/R2 + presigned upload vs managed service Cloudflare Stream with cost, storage driver Local vs S3, FFmpeg thumbnail + watermark spec, upload streaming vs arrayBuffer, delivery Range/206 + Content-Disposition + auth guard for submissions/*, worker queue with lease + retry, schema drift fix add @@index, BUG-1/2/3/5 fix approach, Git hygiene commit+remote, Env separation dev Neon branch, Testing isolation CI, Auth defaults tightening, Prisma tooling, CSS split, SEO metadata per reaction
11. **Operations / Growth / Launch Constraints** — Facebook launch assets READY (Profile 720x720, Cover 1640x720 2x, Overlays 9:16+1:1 Default+Mirrored, Safe Area Guides x4, Post Template 1080x1350, Category Collection, Announcements Intro/ComingSoon/Milestone, Story RequestReaction), first 10 posts per Content System, acquisition channel unknown need decision, viral loop watermark as distribution, settings priority, onboarding minimal, observability plan, performance budget numbers, accessibility check, Git critical branches/CI/protection, launch constraints P0 Git hygiene + P1 Env separation + P2 Media infra → 90% ready after P0/P1 + owner تم
12. **Decision Log Final** — All 61 open decisions resolved to ACCEPTED/REJECTED/HISTORICAL/DEFERRED with source + confidence + تم date, plus 49 unknowns resolved to known or explicitly kept as informational

> These Outputs are not decisions yet — only what we should have after 8 stages. Do not write them as decisions now.

---

## 9. What is forbidden in Phase 2A

- Do not resolve Product Definition, Core Loop, BottomNav, Search, Collections, Categories, Submit, any UX, any Technical — all will be discussed later in Stage 1-8
- Do not modify code, Git, DB, run migrations, deploy, design new visual
- Do not transition to Stage 1 itself — only build map
- Do not consider latest timestamp automatically correct
- Do not consider current implementation as Product Truth automatically
- Do not delete history — only classify as Historical/Superseded when sources support

---

## 10. Result of Phase 2A

Create only:

`YEMREACT-REFORMATION-MASTER-PLAN.md` — this file

Then provide:

1. Lines count
2. 8 stage names
3. Top 10 Dependencies
4. Top 10 questions for Stage 1
5. Confirmation no code/Git/DB modification

Then stop.

---

## 11. Phase 2A Summary Counts

- Principles: 10 rules
- Stages: 8
- Decisions ordered: 49 (Level 1 5 → Level 2 8 → Level 3 10 → Level 4 8 → Level 5 18)
- Open decisions mapped: 61 (20 Product + 15 UX/IA + 18 Technical + 8 Blocked)
- Unknowns mapped: 49 (Must Before 10 / During 21 / Deferred Technical 17 / Informational 1 group)
- Historical contamination guard: 23 items
- Entry rules: 6, Exit rules: 6, Pause rules: 6, Close rules: 3, Transition rules: 3
- Final outputs expected: 12 outputs (Product Definition to Decision Log Final)

---

*End of Phase 2A Orientation — Map built, no decisions made, ready for Stage 1 Product Definition when owner says تم.*


---

## UPDATE 2026-09-21 — Stage 4 — Identity Re-Foundation — PD-I01 Brand Direction — DECISION-I01 ACCEPTED

- **DECISION-I01:** Brand Direction — Direction C — الختم (Al-Khatm) — ACCEPTED 2026-09-21 — Stage 4 — PD-I01 CLOSED
- **Persona:** منهجي، واثق، الشخصيات هي البطل
- **Mood:** بصمة استوديو لا زخرفة — نظام هوية صغير يتكرر بثقة
- **Philosophy:** Modern Product First, Yemeni Character Second — DeepSeek + ChatGPT approved — Content Art Direction added
- **3 Signature Anchors:**
  1. Watermark موحد — شكل هندسي مجرد صغير جدًا ليس رمز ثقافي — زاوية ثابتة كل رياكشن — مكان يُحدد PD-I05
  2. Motion Signature — حركة ختم/قلب 150-200ms عند الحفظ/الإضافة لـCollection — توقيع فريد
  3. chips اسم الشخصية — تحت بعض البطاقات اختياري — مثال مصطفى المومري، هديل مانع — تصنيف موازٍ للـCollections
- **Modern UI Foundation:** Pinterest-like Masonry + Search فوري بلا احتكاك + Spacing واسع Linear-style + نظام واحد صارم + Account flows قياسية + لا تراث في UI — يتوافق مع P-08 + IA-01 + IA-04 + P-03
- **Content Art Direction:** thumbnails تُقص لإطار موحد بدون فراغ أسود + Captions قصيرة لهجة يمنية + تصنيف يعتمد على الشخصيات كطبقة اكتشاف + تركيز مين قالها أكثر من شو قالها
- **Tests passed:** Hide/Show (Pinterest عادي → YemReact واضح) + Museum (لا رموز مباشرة) + Modernity (Pinterest+Linear+Superhuman حديث 100%)
- **Rejected:** Direction A الزاوية بصمة 2-3px + Direction B الحرف خط عربي فقط + Direction D الإيقاع بصمة ضعيفة + 4 الأولى (ترانزستور، قمرية، السوق، المثل) متحف + كل الرموز اليمنية المباشرة + المتحف كفلسفة
- **Impact:** P-35 Brand Direction الختم — 66→67 facts — B-07 Watermark peel+Qussasa → HISTORICAL SUPERSEDED by abstract geometric — B-04 Qussasa Mark → HISTORICAL — B-06 9 colors محفوظة للدراسة → قد تُدرس في PD-I03 but Direction C لا رموز ثقافية — CONFLICT-019 partially resolved — Old 11% vs 14% → New abstract geometric small fixed corner — Details PD-I05
- **No conflict with Stage 3:** P-12 Value + P-13 300-500 + P-20 Rubric + P-25 Pipeline + P-27 Duration 2-60s + P-29 Aspect أي مقاس + P-31 Categories Removed + P-32 Collections Primary + P-33 Admin-Only Curated + P-34 Multi+Follow+SEO — All remain — Brand Direction builds on top of Content & Editorial System — لا يلغيه
- **NEXT:** Stage 4 — PD-I02 Logo/Mark + PD-I03 Colors + PD-I04 Typography + PD-I05 Watermark + PD-I06 Reaction Card + PD-I09 Motion — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB — توثيق فقط
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — No Brand edit old — Document only — Stop after documentation — Stage 4 OPEN



---

## UPDATE 2026-09-23 — Stage 4 — PD-I02 Logo/Mark — DECISION-I02 ACCEPTED — Qussasa Mark v1.0 Adopted As-Is

- **DECISION-I02:** Qussasa Mark v1.0 Adopted As-Is — ACCEPTED 2026-09-23 — Stage 4 — PD-I02 CLOSED
- **Decision:** اعتماد Qussasa Mark v1.0 كما هو — بدون تحسين — مربع بزاوية علوية يمنى مشطوفة/ممزقة بتسنين + ثقب تشغيل مثلث كفراغ سالب fill-rule evenodd
- **Reason:**
  1. Qussasa اجتاز اختبار 8 سيناريوهات فعلية — Brand v1.0 LOCKED — S10
  2. متوافق مع Direction C — الختم (التقشير = بصمة بصرية) — Direction C الختم بصمة استوديو — Qussasa تقشير = بصمة
  3. يعمل في كل الأحجام (16-512px) — scalable — 16px favicon حتى 512px cover
  4. يوفر وقت Stage 4 للمواضيع الأكثر تأثيرًا — PD-I03 Colors + PD-I05 Watermark Qussasa-based أكثر تأثيرًا من إعادة رسم Mark اجتاز اختبار
- **Rejected:**
  - Direction A (الزاوية) — Claude — REJECTED per DECISION-I02 — آمنة جدًا — Qussasa أوضح
  - Direction B (الحرف) — Claude — REJECTED per DECISION-I02 — خط عربي فقط لا يكفي
  - Direction C (الختم الجديد) — Claude — REJECTED per DECISION-I02 — Qussasa الحالي هو الختم نفسه — لا حاجة لختم جديد
  - Direction D (الإيقاع) — Claude — REJECTED per DECISION-I02 — بصمة ضعيفة
  - كل النسخ المحسّنة المقترحة من Claude في H1-R2 — REJECTED — تحسين لمطلوب اجتاز 8 سيناريوهات
  - Qussasa Mark Improvement (H1-R3) — لم يُنفذ — REJECTED — Qussasa v1.0 adopted as-is — Improvement مؤجل PD جديد
- **Impact:**
  - P-36 NEW: Qussasa Mark v1.0 adopted as-is — 68→69 facts — PD-I02 CLOSED
  - B-04 UPDATED: Qussasa Mark — من HISTORICAL→ACCEPTED — DECISION-I02 — 16-512px — اجتاز 8 سيناريوهات
  - B-07 UPDATE: Watermark سيُبنى على Qussasa Mark — Qussasa-based — ليس abstract geometric منفصل تمامًا — تفاصيل PD-I05 — CONFLICT-019 partially resolved Qussasa-based
  - PD-I02 CLOSED — يفتح PD-I03 Color System + PD-I05 Watermark Qussasa-based
  - Revisable: إذا احتجنا تحسين Qussasa لاحقًا → PD جديد — لا يمنع التطوير المستقبلي — مرن
  - No conflict Stage 3 — P-12 to P-36 كلها تبقى — Qussasa Mark v1.0 يبني فوق Content & Editorial System
- **Evidence:** Brand v1.0 LOCKED S10 built after test on 8 real scenarios, B-04 Qussasa Mark مربع بزاوية مشطوفة + مثلث سالب fill-rule evenodd, S01 overlay PNGs, DECISION-I01 Brand Direction الختم Direction C, Claude H1-R2 4 directions A/B/C/D + H1-R3 Improvement proposed, Hamdan chose Qussasa v1.0 as-is
- **NEXT:** Stage 4 — PD-I03 Color System + PD-I05 Watermark Qussasa-based — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB — توثيق فقط
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — No Brand edit old — Document only — Stop after documentation — Stage 4 OPEN PD-I01 CLOSED PD-I02 CLOSED



---

## UPDATE 2026-09-23 — Stage 4 — PD-I03 — Color System — DECISION-I03 ACCEPTED — Multi-Accent Color System

- **DECISION-I03:** Multi-Accent Color System — ACCEPTED 2026-09-23 — Stage 4 — PD-I03 CLOSED
- **Palette الأساسي:**
  - Base: Ink / Paper / Grey (Monochrome)
  - Accent الافتراضي: قهري/كهرماني (Qussasa-derived) — Qishr Amber — Brand v1.0 LOCKED
  - Success / Warning / Error (قياسية) — وظيفية
- **Accents اختيارية (من الإعدادات — Settings Modal "على ذوقك"):**
  - كهرماني (Amber) — افتراضي — دافئ — Qishr — يمني بدون علم
  - بنفسجي (Purple) — حديث — مميز — إبداع
  - تيل (Teal) — بارد — هادئ — توازن
- **Theme:**
  - نهاري (Day) — افتراضي — Paper فاتح Ink داكن
  - ليلي (Night) — Ink داكن خلفية
  - تلقائي (Auto — يتبع النظام) — prefers-color-scheme
- **Reduce Motion:** خيار On/Off — يحترم prefers-reduced-motion — تفاصيل PD-I09
- **Settings Modal:** موجود — UI "على ذوقك" — عنوان أنيق بلهجة يمنية — 3 Accents + Theme + Motion + زر استعادة الإعدادات Reset — Topic جديد يُفتح لاحقًا Stage 4/5
- **المرجع البصري — Prototype موقع تجريبي:** Home Pinterest-like Masonry + Settings Modal + Qussasa Mark في Header + Captions بلهجة يمنية + Flat Saves Bookmark + Duration badge — موقع تجريبي ليس نهائي — "الاستوديو" اسم مؤقت أدمن — البحث لاحقًا — تفاصيل نهائية مع بناء فعلي
- **ما تم رفضه:**
  - النظام 1 (الكهرماني فقط) — محدود — REJECTED — لا خيارات
  - النظام 2 (النيلي) — يفقد الدفء — REJECTED — Qishr دافئ يمني
  - النظام 4 (رمادي فقط) — بلا شخصية — REJECTED — ممل
  - 3 Accents ثابتة — نستخدم متعدد — REJECTED — لا اختيار
- **Impact:**
  - P-37 NEW: Multi-Accent Color System — 69→70 facts — PD-I03 CLOSED
  - B-05 UPDATED: Brand colors foundation → Multi-Accent — Base Ink/Paper/Grey + Accent Qussasa-derived + Optional Amber/Purple/Teal + Theme Day/Night/Auto + Reduce Motion + Settings Modal
  - B-06 9 category colors محفوظ للدراسة — لا يُستخدم كفلتر — Categories Removed — للدراسة Visual Accents/Mood Tags
  - PD-I03 CLOSED — يفتح PD-I04 Typography + PD-I05 Watermark Qussasa-based + PD-I06 Reaction Card + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد
  - Prototype مرجع بصري — ليس نهائي — ملاحظة موقع تجريبي + الاستوديو اسم مؤقت + البحث لاحقًا
  - No conflict Stage 3 — P-12 to P-37 كلها تبقى — Color System يبني فوق Content & Editorial System
- **Evidence:** B-05 Ink/Qishr Amber/Paper/Coral/Warm Grey Qishr from Yemeni coffee, B-06 9 colors #F4C430 #7C5CFF #C81E3A #2CB6C4 #F17FB2 #4CAF6D #6E8296 #D98E04 #E8712E, B-01 Brand v1.0 LOCKED, B-04 Qussasa Mark v1.0, B-09 Brand Direction الختم, P-08 Masonry, P-07 Flat Saves, P-27 Duration badge, Claude 4 color systems 1 Amber only + 2 Indigo + 3 Multi-Accent + 4 Grey only + 3 Accents fixed, Prototype Home Masonry + Settings Modal + Qussasa Header + Captions + Flat Saves + Duration badge, Hamdan chose Multi-Accent
- **NEXT:** Stage 4 — PD-I04 Typography + PD-I05 Watermark Qussasa-based + PD-I06 Reaction Card + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal — HISTORY+EVIDENCE فقط — بانتظار أمر حمدان — لا كود/Git/DB
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — No Brand edit old — Document only — Stop after documentation — Stage 4 OPEN PD-I01 CLOSED PD-I02 CLOSED PD-I03 CLOSED


---

## UPDATE 2026-09-24 — DECISION-I05 — Watermark Deferred — Stage 4 — PD-I05 — DEFERRED

- **Status:** DEFERRED — مُجمّد مؤقتًا — ليس CLOSED
- **Decided by:** حمدان (Founder) — 2026-09-24 — Stage 4 — PD-I05
- **القرار:** تجميد Watermark مؤقتًا — لا يُنفّذ الآن
- **السبب:**
  1. يحتاج دراسة أعمق — تأثير على صناع المحتوى + التكاليف + الجانب القانوني
  2. يمكن إضافته بعد الإطلاق — ليس حرجًا للنسخة الأولى
  3. Direction C — الختم — يبقى صالحًا مع 2 Anchors فعّالين: Motion Signature + chips الشخصية
  4. صفر مخاطرة تقنية — قرار قابل للتراجع
- **ما تم تجميده:** Watermark على الفيديو + Watermark على الصور + Watermark على البطاقات + Watermark في صفحة التفاصيل + معالجة FFmpeg للـWatermark
- **ما يبقى فعّالًا:** Qussasa Mark PD-I02 كـLogo في الهيدر فقط + Motion Signature PD-I09 + chips الشخصية PD-I06 + PD-I07
- **إعادة الفتح:** قابل للمراجعة بعد الإطلاق — يُفتح PD-I05-R2 عند الحاجة — يستند إلى بيانات حقيقية سلوك المستخدم
- **Impact:**
  - P-38 NEW: Watermark Deferred — 70→71 facts — PD-I05 DEFERRED
  - B-07 FROZEN: Watermark Qussasa-based → مُجمّد — لا Watermark الآن — Qussasa Mark Logo هيدر فقط
  - B-09 UPDATED: Direction C — Watermark Anchor مُجمّد — 2 Signature Anchors فعّالين
  - P-35 UPDATED: Brand Direction الختم — Watermark Anchor مُجمّد — 2 Anchors فعّالين
  - B-04 Qussasa Mark v1.0 يبقى ACCEPTED unaffected — DECISION-I02 Qussasa-based مرجع عند إعادة الفتح
- **NEXT:** Stage 4 — PD-I04 Typography + PD-I06 Reaction Card + PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation — Stage 4 OPEN PD-I01 CLOSED PD-I02 CLOSED PD-I03 CLOSED PD-I05 DEFERRED

---

## UPDATE 2026-09-24 — DECISION-I06 — Reaction Card & Detail Page — Stage 4 — PD-I06 — CLOSED

- **Status:** ACCEPTED — CLOSED
- **Decided by:** حمدان (Founder) — 2026-09-24 — Stage 4 — PD-I06
- **البطاقة (Card) — النسخة النهائية:** الوسائط تملأ الإطار بدون فراغ أسود + **Duration badge أعلى يمين — فيديو فقط** + **العنوان** + **⋮ ثلاث نقاط** + نقرة واحدة → /r/[code] — بدون Watermark per DECISION-I05
- **صفحة التفاصيل /r/[code] — النسخة النهائية — 8 كتل:**
  1. [← رجوع]
  2. [الفيديو/الصورة] + Duration أعلى يمين
  3. العنوان بخط كبير + [حفظ] [تنزيل] [مشاركة] [...]
  4. ● اسم الشخصية — الوصف الأساسي
  5. [الوصف الثنائي المطوي ▼]
  6. المجموعات — إن وُجدت
  7. رياكشنات ذات صلة
  8. رياكشنات عشوائية — محدودة 10-20 رياكشن
- **الأزرار:** رئيسية: حفظ + تنزيل + مشاركة — ⋮ ثلاث نقاط: نسخ الرابط + إبلاغ فقط
- **التصحيح 2026-09-24 — تصحيح حمدان على DECISION-I06:**
  1. **رياكشنات عشوائية (P-40):** قسم **محدود 10-20 رياكشن — تصحيح ثان 2026-09-25: كان 20-40 → أصبح 10-20** — ليس Infinite Scroll — لا Load More — يتوقف عند 10-20 — يتوافق P-03 No Infinite Feed + DECISION-006
  2. **تعديل Admin فقط (P-23):** تُرجع القائمة إلى **عنصرين فقط** — نسخ الرابط + إبلاغ — ❌ حذف «تعديل (Admin فقط)» — السبب قرار حمدان السابق «مثل المستخدم تمامًا + الصلاحيات في صفحة الأدمن فقط» — لا أزرار Admin في المكتبة — الأدمن يعدّل من /admin فقط
- **Impact:**
  - P-39 NEW: Reaction Card & Detail Page Spec — 71→73 facts — PD-I06 CLOSED
  - P-40 NEW — CORRECTED: رياكشنات ذات صلة + رياكشنات عشوائية **محدودة 10-20** — ليس Infinite Scroll — لا Load More
  - P-11 UPDATED: Discover similar — ذات صلة 10 أولًا + تحميل المزيد حتى 50 حسب الصلة + عشوائية — بدون Infinite Feed
  - P-23 UPDATED — CORRECTED: نفس العناصر الخمسة — رئيسية حفظ+تنزيل+مشاركة + ⋮ **نسخ الرابط + إبلاغ فقط** — ❌ لا تعديل Admin — لا أزرار Admin في المكتبة — الأدمن يعدّل من /admin فقط
  - متوافق DECISION-I05 لا Watermark + DECISION-014 لا فئة + P-03 لا عدادات/تعليقات + IA-05 لا مصدر/حقوق + IA-02 صفحة لا Modal
  - PD-I06 CLOSED — يفتح PD-I04 Typography + PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد
- **NEXT:** Stage 4 — PD-I04 Typography + PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic جديد + PD-I05-R2 بعد الإطلاق
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation — Stage 4 OPEN PD-I01 CLOSED PD-I02 CLOSED PD-I03 CLOSED PD-I05 DEFERRED PD-I06 CLOSED


---

## UPDATE 2026-09-25 — DECISION-I04 — Typography System — Stage 4 — PD-I04 — CLOSED

- **Status:** ACCEPTED — CLOSED
- **Decided by:** حمدان (Founder) — 2026-09-25 — Stage 4 — PD-I04
- **الخطوط (4):**
  - Display: **Lalezar** — الـLogo فقط + عناوين التسويق
  - Primary Arabic: **IBM Plex Sans Arabic** — 400/500/600/700
  - Latin: **Inter** — 400/500/600/700
  - Mono: **IBM Plex Mono** — 400/500
- **Type Scale (8 مستويات):** H1 32px/700/1.2 — H2 24px/600/1.3 — H3 20px/600/1.3 — Body L 16px/400/1.5 — Body 14px/400/1.5 — Body S 13px/400/1.5 — Caption 12px/400/1.4 — Micro 11px/500/1.4 Mono
- **RTL:** كامل — أرقام Western
- **Letter Spacing:** عربي 0 — لاتيني H1/H2 -0.01em — Mono 0
- **مؤجل:** Micro 11px يُختبر Stage 7 قد يُرفع لـ12px — Settings Modal Topic مستقبلي ليس قرار الآن
- **ما تم رفضه:** خطوط عربية تقليدية Amiri + Reem Kufi + Aref Ruqaa + خط يد + Lalezar في UI (فقط في الـLogo) + أكثر من 4 خطوط
- **Impact:**
  - P-41 NEW: Typography System — 73→74 facts — PD-I04 CLOSED
  - متوافق B-09 Direction C الختم — Modern Product First, Yemeni Character Second — لا تراث في UI
  - متوافق B-04 Qussasa Mark Logo + P-37 Multi-Accent + P-39 Reaction Card
  - PD-I04 CLOSED — يفتح PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion
- **NEXT:** Stage 4 — PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation — Stage 4 OPEN PD-I01 CLOSED PD-I02 CLOSED PD-I03 CLOSED PD-I04 CLOSED PD-I05 DEFERRED PD-I06 CLOSED


---

## UPDATE 2026-09-25 — تصحيح PD-I06 (Detail Page Layout) — التصحيح الثالث

- **المصدر:** تصحيح حمدان 2026-09-25 على DECISION-I06 — PD-I06 يبقى CLOSED
- **التصحيح 1 — موضع الأزرار في صفحة التفاصيل:** الأزرار (حفظ + تنزيل + مشاركة + [...]) تظهر **بجانب العنوان — في اليسار (في RTL: يسار العنوان) — نفس السطر — ليست سطرًا منفصلًا**

```
[← رجوع]

[الوسائط]

العنوان (H1)              [حفظ] [تنزيل] [مشاركة] [...]

● اسم الشخصية — الوصف
```
- **التصحيح 2 — إلغاء Empty States:** لا تظهر أي رسائل فارغة للمستخدم — لا اسم شخصية → لا شيء — لا وصف → لا شيء — لا وصف ثنائي → لا زر ▼ — لا مجموعات → لا قسم — غير مضاف → لا شيء — **القاعدة: الصفحة نظيفة — الحقل يُحذف من DOM إذا كان فارغًا — لا placeholder — لا empty message**
- **التوافق:** متوافق P-09 «وصف ثنائي مطوي **إن وجد**» + P-35 chips «اختياري تحت بعض البطاقات فقط» + P-34 المجموعات «إن وُجدت» + P-06 حفظ CTA أساسي يبقى ظاهرًا دائمًا — لا تعارض مع Stage 3
- **Impact:** P-39 CORRECTED — لا حقائق جديدة — العدد ثابت 74 facts — PD-I06 يبقى CLOSED
- **NEXT:** PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation


---

## UPDATE 2026-09-25 — تصحيح PD-I07 (Duration Position) — التصحيح الرابع

- **المصدر:** تصحيح حمدان 2026-09-25 — توضيح Duration Position — PD-I06 يبقى CLOSED
- **في البطاقة (Card):** ✅ Duration **أعلى يمين الوسائط** — كما في PD-I06 — فيديو فقط — الصور بلا شارة
- **في صفحة التفاصيل:** ❌ **يُحذف — لا يظهر Duration**
- **السبب:** مشغل الفيديو يعرض المدة progress bar + time — التكرار = ازدحام — Pinterest-like لا يعرضها
- **التوافق:** متوافق P-27 المدة 2s-60s تبقى حقيقة بيانات + P-39 البطاقة — لا تعارض Stage 3
- **Impact:** P-39 CORRECTED — لا حقائق جديدة — العدد ثابت 74 facts — PD-I06 يبقى CLOSED
- **NEXT:** PD-I07 chips الشخصية + PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation


---

## UPDATE 2026-09-25 — DECISION-I07 — PD-I07 Closed — chips الشخصية — Stage 4 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-25 — **بدون تصميم جديد**
- **1. PD-I07 (chips) = مغلق** — تُبنى على P-35 + P-39 — chips اختياري تحت بعض البطاقات فقط
- **2. Duration في صفحة التفاصيل = يُحذف** — ✅ البطاقة أعلى يمين الوسائط / ❌ التفاصيل بلا Duration
- **3. Related + More = نفس بطاقة Reaction Card** — لا تصميم جديد — P-40 — لا تغيير في P-39
- **Impact:** لا حقائق جديدة — 74 facts ثابتة — PD-I07 CLOSED — P-40 UPDATED + P-35 UPDATED
- **NEXT:** Stage 4 — PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation — Stage 4 OPEN PD-I01 CLOSED PD-I02 CLOSED PD-I03 CLOSED PD-I04 CLOSED PD-I05 DEFERRED PD-I06 CLOSED PD-I07 CLOSED


---

## UPDATE 2026-09-25 — DECISION-I07 — تفاصيل نهائية (Chip + Duration + Related/More) — PD-I07 CLOSED

- **1. Chip (PD-I07 مغلق):** **وسم بصري فقط** · **Inline قبل الوصف** · **غير قابل للنقر** · **❌ لا يظهر في البطاقة** — ⚠️ CORRECTED على P-35 + B-09
- **2. Duration:** البطاقة ✅ أعلى يمين الوسائط · التفاصيل ❌ يُحذف — المشغل يعرضها
- **3. Related + More (تأكيد):** ذات صلة = 10 رياكشن · عشوائية = 10-20 رياكشن · كلاهما نفس بطاقة Reaction Card — لا تصميم جديد
- **Impact:** P-39 UPDATED + P-40 UPDATED + P-35 CORRECTED + B-09 CORRECTED — 74 facts ثابتة — PD-I07 CLOSED
- **OPEN للاستيضاح:** Related 10 ثابتة بلا Load More؟ — يُعدَّل P-11 بقرار لاحق إن لزم
- **NEXT:** PD-I08 Light/Dark + PD-I09 Motion + Settings Modal Topic مستقبلي + PD-I05-R2 بعد الإطلاق
- **Rules:** No code/Git/DB — documentation only — Document only — Stop after documentation — Stage 4 OPEN PD-I01/I02/I03/I04/I06/I07 CLOSED + PD-I05 DEFERRED


---

## UPDATE 2026-09-25 — DECISION-I08 — Light/Dark + Soft Depth — Stage 4 — PD-I08 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-25 — Stage 4 — PD-I08
- **Color Tokens:** Light bg `#FAFAF8` / surface `#FFFFFF` / ink `#121214` — Dark bg `#18140F` / surface `#221C16` / ink `#F3ECE2` — **Dark دافئ يحفظ شخصية Qishr**
- **Soft Depth (R2):** shadow-sm `0 1px 3px rgba(0,0,0,.04)` · shadow-md `0 2px 8px rgba(0,0,0,.06)` · shadow-lg `0 4px 16px rgba(0,0,0,.08)` · shadow-float `0 8px 24px rgba(0,0,0,.12)` · **Dark .30-.50 معايرة ضرورية** · Border `rgba(0,0,0,.04)` / `rgba(255,255,255,.06)` · **Active** ring + 4% surface + shadow-lg · **Icon Containers** دائرة 36px `rgba(0,0,0,.03)` · **Nested Depth** كل طبقة بظلها
- **السلوك:** Auto = افتراضي `prefers-color-scheme` · 200ms transitions
- **3 تصحيحات مؤجلة — Stage 7:** 1) Duration البطاقة left → right (الصحيح أعلى يمين الوسائط) 2) Duration التفاصيل يُحذف 3) Settings Modal حذف «الإشعارات» خارج النطاق
- **Related Count:** P-11 CONFIRMED — 10 أولية + Load More حتى 50 max — ليس Infinite Feed — «10 رياكشن» = 10 أولية لا ثابتة — لا تعديل على P-11
- **Impact:** P-42 NEW — P-11 CONFIRMED — 74→75 facts — PD-I08 CLOSED — يفتح PD-I09 Motion + Settings Modal Topic جديد
- **NEXT:** Stage 4 — PD-I09 Motion + Settings Modal Topic جديد + PD-I05-R2 بعد الإطلاق + 3 تصحيحات Stage 7
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation — Stage 4 OPEN PD-I01/I02/I03/I04/I06/I07/I08 CLOSED + PD-I05 DEFERRED


---

## UPDATE 2026-09-26 — DECISION-I09 — Motion Language — Stage 4 — PD-I09 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-26 — Stage 4 — PD-I09
- **الفلسفة:** **Hybrid** — Subtle في UI (هادئ Linear/Vercel-style) + Anchor مميز (Seal Motion)
- **Durations:** Micro 120ms · Small 180ms · Medium 240ms · Large 320ms (Seal فقط)
- **Easings:** Standard `cubic-bezier(.4,0,.2,1)` · Decelerate `cubic-bezier(0,0,.2,1)` · Accelerate `cubic-bezier(.4,0,1,1)` · Spring `cubic-bezier(.34,1.56,.64,1)` — **Seal فقط**
- **Seal Motion:** 6 مراحل ~1.7s — `♡ → Mark → spin(Spring) → ✓ → ♡` — Spring محجوز له
- **Page Transitions:** ❌ None — Pinterest-style — أداء أولًا
- **Scroll:** Header Desktop ثابت · Header Mobile يختفي down/يظهر up 250ms · Bottom Nav ثابت دائمًا · لا Infinite Scroll (P-03)
- **Loading:** Skeleton shimmer للبطاقات · Spinner 16px للأزرار · Fade In 150ms للصور/الفيديو · لا Progress Bar
- **Reduced Motion:** يُلغي Rotation/translateY/Page transitions/shimmer · يُبقي التحول اللوني · prefers-reduced-motion + خيار Settings
- **Rejected:** حركة >320ms · Spring elsewhere · Page transitions · Progress bar · Parallax · Bounce/Shake/Wobble
- **Impact:** P-43 NEW — 75→76 facts — PD-I09 CLOSED — يفتح PD-I10 (UI Language) — آخر Topic
- **NEXT:** Stage 4 — PD-I10 UI Language + Settings Modal Topic جديد + PD-I05-R2 بعد الإطلاق + 3 تصحيحات Stage 7
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation — Stage 4 OPEN PD-I01/I02/I03/I04/I06/I07/I08/I09 CLOSED + PD-I05 DEFERRED


---

## UPDATE 2026-09-30 — DECISION-I10 — UI Visual Language (Studio Seal) — Stage 4 — PD-I10 — CLOSED

- **Status:** ACCEPTED — CLOSED — حمدان 2026-09-30 — **LAST TOPIC**
- **الاتجاه:** **Direction D — Hybrid «Studio Seal»** — نظام هادئ كـLinear + دفء Qishr + نظام ختم صارم + الشخصية في المحتوى لا الواجهة
- **Foundation:** Spacing `4/8/12/16/24/32/48/64` · Breakpoints `640/1024/1440` · Container `1120px` · Masonry `2/3/4/5`
- **Buttons:** 5 أنواع × 3 أحجام `40/44/48` × Radius `10px` × 5 حالات
- **Inputs:** `44px` · Radius `10px` · Border `1px` + shadow-sm · Focus ring `2px Accent`
- **Cards:** Reaction `14px` · Collection Rail/Square · Mini `70×70` · **Modals:** Desktop Center / Mobile Bottom Sheet `22px`
- **States:** Empty للصفحات فقط (Lucide + عنوان + إجراء) · Loading Skeleton + Spinner 16px · Error فصحى هادئة · **Toast Success + Error**
- **Icons:** Lucide `1.5px` `16/20/24` · Bottom Nav `layout-grid · layers · plus · bookmark · circle-user`
- **Navigation:** Header Desktop كامل · Header Mobile بلا Avatar + يختفي↓/يظهر↑ · **Bottom Nav 5 tabs**
- **Account Menu (P-45):** زائر / مستخدم / أدمن (+الاستوديو) — Popover ديسكتوب · Sheet جوال
- **زر (+):** محايد+🔒 قبل الإطلاق + Sheet «قريبًا» + Accent بعد الإطلاق
- **Search Bar:** 44px · 420-480px ديسكتوب · Placeholder «ابحث عن رياكشن أو موقف...» · بلا فلاتر v1
- **Guest Save (P-46):** localStorage + دمج عند الدخول + Seal Motion فورًا · **Mobile:** لا معاينة تلقائية · **Report Flow:** Sheet radio 5 أسباب
- **7 تصحيحات مؤجلة Stage 7:** Duration left→right · Duration تفاصيل يُحذف · Bottom Nav Lucide · Inter في HTML · aspect-ratio · حذف tabs الميت · Qussasa قابل للنقر
- **قراران مؤجلان:** Search Route → Stage 5 · Scroll Restoration → مستقبلي
- **Rejected:** Avatar جوال · المحفوظات/مساهماتي في Account · Toast للقريبًا · Emojis في UI · Infinite Scroll · Qussasa في Empty States · Linear نبرة Empty
- **Impact:** P-44 + P-45 + P-46 NEW — 76→79 facts — PD-I10 CLOSED — **Stage 4 CLOSED 100%**
- **NEXT:** **Stage 5 — IA & Navigation** — HISTORY+EVIDENCE فقط
- **Rules:** No code/Git/DB — documentation only — No Migration — No implementation — Document only — Stop after documentation

---

## STAGE 4 — CLOSED — Identity Re-Foundation — مكتمل 100% — 2026-09-30

| # | Topic | الحالة | القرار |
|---|---|---|---|
| PD-I01 | Brand Direction | ✅ CLOSED | Direction C — الختم |
| PD-I02 | Qussasa Mark | ✅ CLOSED | Qussasa Mark v1.0 adopted as-is |
| PD-I03 | Multi-Accent | ✅ CLOSED | Base Ink/Paper/Grey + Amber/Purple/Teal + Day/Night/Auto |
| PD-I04 | Typography | ✅ CLOSED | Lalezar + Plex Arabic + Inter + Plex Mono |
| PD-I05 | Watermark | ❄️ DEFERRED | مُجمّد — PD-I05-R2 بعد الإطلاق |
| PD-I06 | Card + Detail | ✅ CLOSED | Duration top-right · أزرار نفس السطر · لا Empty States |
| PD-I07 | Chips | ✅ CLOSED | وسم بصري · inline · غير قابل للنقر |
| PD-I08 | Light/Dark + Soft Depth | ✅ CLOSED | Dark دافئ Qishr · 4 ظلال · Auto افتراضي |
| PD-I09 | Motion | ✅ CLOSED | Hybrid Subtle + Seal Anchor |
| PD-I10 | UI Language | ✅ CLOSED | Studio Seal |

**76 → 79 facts** — **الانتقال إلى Stage 5 — IA & Navigation**
