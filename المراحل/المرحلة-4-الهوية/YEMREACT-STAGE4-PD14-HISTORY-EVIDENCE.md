# PD-14 — Watermark Spec — HISTORY + EVIDENCE — Stage 4 — Experience & Identity

> STATUS: OPEN — HISTORY + EVIDENCE فقط — لا DISCUSSION — لا OPTIONS — لا قرار
> Date: 2026-09-14 — Stage 4 — PD-14 Watermark Spec
> Founder: حمدان — بانتظار DISCUSSION ثم DECISION
> Sources checked: YemReact-Brand-v1.0-LOCKED.html + YemReact-identity-system.html + YemReact_Claude_Foundation_Package.md + ARENA-TECHNICAL-HANDOFF.md + YEMREACT-CONFLICT-REGISTER-V2.md + YEMREACT-CONFLICT-REGISTER.md + YEMREACT-CANONICAL-BASELINE.md + YEMREACT-DECISIONS-LOG.md (DECISION-013) + S09 T-04 technical

---

## 1. YemReact-Brand-v1.0-LOCKED.html — Spec الرسمي

**File:** `/home/user/uploads/YemReact-Brand-v1.0-LOCKED.html` — 343 lines — LOCKED v1.0 — READY FOR HANDOFF — Validated on 8 real use cases

### Watermark — ما يقوله LOCKED HTML صراحة:

**من قسم Tier 3 — وجب تغييره قبل الاعتماد — ونُفّذ في هذه النسخة:**

> **تقوية الـWatermark:** النسخة الأصلية (تعتيم فقط، بلا حافة) تختفي فعليًا فوق خلفية فاتحة — وهذا فشل وظيفي مباشر بما أن المصدر لقطات خام غير مُصوَّرة خصيصًا لنا. الإصلاح: ظلّ مزدوج داكن خلف شكل التقشّر `(drop-shadow 0 1px 2px + 0 0 2px, opacity .6/.4)` يمنحه حافة داكنة كافية على أي خلفية. هذا هو المعيار المعتمد من الآن فصاعدًا، ويُلغي النسخة السابقة بلا ظل.

**من قسم Final Locked Spec — 04 / النسخة المثبّتة — Lock Grid:**

> **Watermark — ✓ LOCKED — نسخة مُقوّاة**
> تقشّر ٩–١٥٪ من العرض، أعلى الزاوية الافتراضية، مع ظل مزدوج للتباين على أي خلفية. قاعدة القلب عند الحاجة.

**تحليل دقيق للنص LOCKED:**

- **الحجم:** ٩–١٥٪ من العرض — Range وليس رقم ثابت — `٩–١٥٪` — يسمح بالمرونة 9% إلى 15%
- **المكان:** "أعلى الزاوية الافتراضية" — أعلى (top) — الزاوية الافتراضية (default corner) — في الصور البصرية في LOCKED HTML: الزاوية الافتراضية هي أعلى-يمين (tr) — الدليل: كل النماذج الـ6 الافتراضية تستخدم `class=\"peel tr\"` — top-right — والنموذجان الاستثنائيان يستخدمان `peel tl` — top-left — عند قلب الكتلة
- **الظل:** "مع ظل مزدوج للتباين على أي خلفية" — double shadow — `drop-shadow 0 1px 2px + 0 0 2px, opacity .6/.4` — مُقوى — النسخة السابقة بلا ظل أُلغيت صراحة: "ويُلغي النسخة السابقة بلا ظل"
- **التقشّر (Peel):** شكل تقشّر ورقي بزاوية — `clip-path: polygon(100% 0,0 0,100% 100%)` للـ tr و `polygon(0 0,100% 0,0 100%)` للـ tl — خلفية `var(--paper) #f3eae0` — بداخله Qussasa Mark — `fill-rule: evenodd` — مثلث تشغيل كفراغ سالب
- **CSS في LOCKED HTML:** `.peel{ width:15%; height:15%; filter:drop-shadow(0 1px 2px rgba(0,0,0,.6)) drop-shadow(0 0 2px rgba(0,0,0,.4)); }` — 15% حجم بصري في النموذج — لكن النص يقول 9–15% range
- **العلاقة بـ Qussasa Mark:** Qussasa داخل التقشّر — `svg width:52% height:52% top:14%` — `opacity:.6` — لون `var(--ink) #121214` في LOCKED HTML (لكن في كود آخر #f3eae0) — Qussasa = مربع بزاوية علوية يمنى مشطوفة/ممزقة بتسنين + ثقب تشغيل مثلث
- **العلاقة بـ Safe Area:** Safe area: أعلى ٦٪، أسفل ٢٠٪، يمين ١٤٪، يسار ٦٪ (9:16) — القص الحقيقي مسموح فقط في البطاقات التي نتحكم بها، لا في الفيديو المُصدَّر — Safe Area مذكور في Lock Grid: `Clip Template — Safe area: أعلى ٦٪، أسفل ٢٠٪، يمين ١٤٪، يسار ٦٪ (9:16)`
- **قاعدة قلب الكتلة (Default/Mirrored):** 
  - النص: "قاعدة قلب الكتلة: إذا شغلت يد أو حركة الزاوية الافتراضية في أي لحظة من اللقطة، تُقلَب الكتلة (تقشّر + مدة + تصنيف) كوحدة واحدة للجهة المقابلة. ممنوع نقل عنصر واحد بمفرده — إما الكل بمكانه أو الكل مقلوب."
  - في الاختبار البصري: 6 نماذج وضع افتراضي بلا تعديل (peel tr + dur left + dot left) — نموذج حماس: يد مرفوعة تشغل الزاوية اليمنى — الكتلة كاملة انقلبت لليسار (peel tl + dur right + dot right) — نموذج رفض: قلب جزئي — يد ترفض تشغل الزاوية السفلية اليسرى — نقطة التصنيف فقط انتقلت لليمين، التقشّر بقي مكانه لأنه غير متأثر
  - في QA: "هل تعمل القُصاصة مع كل أنواع اللقطات؟ — في اللقطات القريبة جدًا أو التي فيها حركة يد نحو الكاميرا (حماس، رفض)، الزاوية الافتراضية قد تُشغَل. الحل: قاعدة قلب الكتلة الموثقة أدناه — لا تصميم جديد."

### YemReact-identity-system.html — مصدر إضافي:

- File: `/home/user/uploads/YemReact-identity-system.html`
- Safe Area: هامش 6% أعلى، 20% أسفل (تعليقات/يوزرنيم المنصة)، 14% يمين (أيقونات المنصة)، 6% يسار — مطابق لـ LOCKED HTML

---

## 2. المصادر الأخرى — S10 + S06 + S09 + CONFLICT-019 + DECISION-013

### S10 — Claude Foundation Package — YemReact_Claude_Foundation_Package.md

- **ما يقوله عن Watermark (حسب CONFLICT-REGISTER-V2 + CANONICAL):**
  - Spec A: 11% من العرض — أعلى-يمين (top-right) — بظل مزدوج (double shadow)
  - مصدر: `arena.md §8.2` — "مواصفات Brand v1.0"
  - B-07 في CANONICAL: Watermark: تقشّر ورقي بزاوية + شعار بداخله, نسخة مقواة بظل مزدوج بعد فشل أولى على خلفيات فاتحة, قاعدة قلب الكتلة Default/Mirrored — CONFIRMED as locked concept — CONFLICTED for exact spec 11% vs 14%
  - Evidence: S10 says strengthened after failure — S09 shows watermark/qs.png 200 — B-04 Qussasa Mark + B-07 Watermark LOCKED concept
  - **الخلاصة:** S10 يتوافق مع LOCKED HTML في المبدأ: نسخة مقواة + ظل مزدوج + أعلى + قاعدة قلب — لكن الرقم 11% مذكور في arena.md §8.2 كرقم محدد — بينما LOCKED HTML يقول 9–15% range

### S06 — Content Pipeline — Overlays + Safe Area Guides

- **ما يقوله (حسب DECISION-013 Evidence):**
  - Overlays 9:16 + 1:1 + Safe Area Guides x4 Default/Mirrored ×2
  - S10 Brand v1.0 LOCKED 9:16 Safe Area 6% top 20% bottom 14% right 6% left + Qussasa 6-15% + Watermark 9-15% double shadow
  - Evidence في DECISION-013: `S10 Brand v1.0 LOCKED 9:16 Safe Area 6% top 20% bottom 14% right 6% left + Qussasa 6-15% + Watermark 9-15% double shadow`
  - **الخلاصة:** S06 يؤكد Safe Area Guides + Overlays + Qussasa 6-15% + Watermark 9-15% double shadow — يطابق LOCKED HTML range 9-15% — ليس 11% ثابت ولا 14% ثابت

### S09 — Technical T-04 — ffmpeg watermark 14% bottom-right no shadow

- **ما يقوله CANONICAL T-04:**
  - Media pipeline local: LocalMediaService.validate MIME/size/magic bytes, storage.put LocalStorage ./storage default (829 files / 11MB, 282 reactions/, 546 submissions/, 216 pairs .wm.mp4 + .thumb.jpg, watermark/qs.png), S3Storage via minio optional, processor ffprobe/ffmpeg thumbnail + watermark 14% bottom-right no shadow, states idle→processing→done|failed, public DTO WATERMARKED > PROCESSED > ORIGINAL fallback — CURRENT local — S09 CODE + .storage count + unit tests 9+10+2+11
- **ما يقوله ARENA-TECHNICAL-HANDOFF.md (S09 تفصيلي):**
  - Line 404: `watermark | Qussasa بلون --paper (#f3eae0)، 14% من العرض، أسفل-يمين (أو أسفل-يسار لـ corner=tl)، إزاحة 16px؛ لا ظل (الـ MVP القديم كان بظل مزدوج و11% أعلى-يمين — CONFLICT مع "مواصفات Brand v1.0" حسب arena.md §8.2)`
  - Line 564: `uploads/YemReact-Brand-v1.0-LOCKED.html (حسب arena.md §8.2) watermark 11% أعلى-يمين بظل مزدوج | — | 14% أسفل-يمين بلا ظل (ffmpeg.ts) | CONFLICT — UNKNOWN أيهما المعتمد`
  - **ffmpeg command (من HANDOFF):**
    ```
    ffmpeg -filter_complex "[1][0]scale2ref=w=iw*0.14:h=ow/mdar[wm][vid];[vid][wm]overlay=(W-w-16|16):H-h-16"
    -c:v libx264 -preset veryfast -crf 23 -pix_fmt yuv420p -c:a aac -b:a 96k -movflags +faststart -shortest
    → <base>.wm.mp4
    ```
    - `w=iw*0.14` = 14% من عرض الفيديو
    - `overlay=(W-w-16|16):H-h-16` = أسفل-يمين مع إزاحة 16px — أو أسفل-يسار إذا corner=tl
    - `ensureWatermarkFile()` → `./.storage/watermark/qs.png` — يُولّد برمجيًا من هندسة QussasaMark — لون --paper #f3eae0
    - لا ظل في ffmpeg filter — no shadow
- **الخلاصة:** الكود الحالي يستخدم 14% أسفل-يمين بلا ظل — يخالف LOCKED HTML (9-15% أعلى بظل مزدوج) و S10 (11% أعلى بظل مزدوج) — CONFLICT-019

### CONFLICT-019 — Watermark Spec — تفاصيل التعارض

- **من YEMREACT-CONFLICT-REGISTER-V2.md:**
  - A (S10): 11% top-right double shadow
  - B (S09): 14% bottom-right no shadow #f3eae0 Qussasa
  - Type: VERSION DRIFT + REAL CONFLICT
  - Chronology: Yes — v1 failed on light backgrounds, v2 double shadow, then code 14% bottom-right
  - Implementation: Partial — need LOCKED HTML to confirm which spec is authoritative
  - Impact: Medium — brand locked
  - Status: CONFLICTED — NEEDS PRODUCT DECISION
- **من YEMREACT-CONFLICT-REGISTER.md:**
  - CONFLICT-019 | Watermark Spec | CLAUDE-FOUNDATION (11% top-right double shadow) | ARENA-TECHNICAL (14% bottom-right no shadow, #f3eae0) | 05_UI (implicit brand locked) | Watermark size/position/shadow | Watermark spec | Medium — brand locked | Yes — check ffmpeg.ts vs LOCKED HTML | YES | YES | CONFLICTED
- **من YEMREACT-CANONICAL-BASELINE.md:**
  - B-07: Watermark: تقشّر ورقي بزاوية + شعار بداخله, نسخة مقواة بظل مزدوج بعد فشل أولى على خلفيات فاتحة, قاعدة قلب الكتلة Default/Mirrored — CONFIRMED as locked concept — High for concept, CONFLICTED for exact spec 11% vs 14% (see OPEN)
  - P-29: Watermark+Qussasa تطبيق ديناميكي على أي مقاس — Watermark نسبة من عرض الفيديو 14% تقنيًا — Qussasa في الزاوية دائمًا قاعدة قلب الكتلة — يعملان على 9:16,1:1,16:9,4:5
  - P-30: CONFLICT-019 Watermark 11% vs 14% لم يُحل بعد Stage4/7 — CONFLICT-021 CLOSED
  - WHAT IS NOT: Watermark exact spec 11% vs 14% — CONFLICTED — Stage 4 + OPEN-Q-03

### DECISION-013 — Aspect Ratio — تطبيق ديناميكي

- **ما يقوله عن Watermark:**
  - "Watermark + Qussasa: تطبيق ديناميكي على أي مقاس — Watermark نسبة من عرض الفيديو 14% تقنيًا حاليًا — CONFLICT-019 يُحل في Stage 4/7 — 11% vs 14% — Qussasa في الزاوية دائمًا — قاعدة قلب الكتلة Default/Mirrored — يعملان على 9:16, 1:1, 16:9, 4:5 — بغض النظر عن المقاس — scale2ref يحافظ على النسبة"
  - "CONFLICT-019 Watermark 11% vs 14% — لم يُحل بعد — يبقى لـ Stage 4/7 — PD-08 لم يحسمه — VD-09 يبقى OPEN"
  - "Overlays 9:16 + 1:1 تبقى كمرجع بصري — ليست حد — Stage 4 يقرر هل نحتاج Overlays جديدة لـ 16:9/4:5/3:4 — VD-08 HISTORICAL"
  - "Stage 7 (Technical): MediaService.validate — لا يضيف فحص مقاس (لا حد صارم) — T-04 يبقى لا يفرض مقاس — ffmpeg watermark يحتاج مراجعة لـ بدون فراغ أسود (aspect fill vs fit)"
- **الخلاصة:** DECISION-013 أكد أن Watermark+Qussasa ديناميكيان يعملان على أي مقاس — لكنه لم يحسم CONFLICT-019 — أحاله لـ Stage 4/7 — P-29 ذكر 14% تقنيًا حاليًا مع الإشارة للتعارض

---

## 3. الأدلة التقنية — هل الكود الحالي يستخدم 14% bottom-right؟

**المصدر:** ARENA-TECHNICAL-HANDOFF.md + YEMREACT-CANONICAL-BASELINE.md T-04 + DECISION-013 Evidence

- **الحجم:** نعم — `w=iw*0.14` — 14% من عرض الفيديو — `scale2ref=w=iw*0.14:h=ow/mdar[wm][vid]` — يحافظ على aspect ratio
- **المكان:** أسفل-يمين — `overlay=(W-w-16|16):H-h-16` — bottom-right مع إزاحة 16px — أو أسفل-يسار `corner=tl` مع `overlay=16:H-h-16` — يخالف LOCKED HTML الذي يقول أعلى الزاوية الافتراضية (top)
- **الظل:** لا ظل — no shadow — ffmpeg filter لا يحتوي drop-shadow — بينما LOCKED HTML يفرض ظل مزدوج `drop-shadow 0 1px 2px + 0 0 2px opacity .6/.4` — النسخة القديمة بلا ظل أُلغيت صراحة في LOCKED HTML
- **قاعدة قلب الكتلة (Mirrored):** نعم موجودة في الكود — `corner=tl` vs `tr` — `overlay=(W-w-16|16):H-h-16` vs `16:H-h-16` — لكن في LOCKED HTML القلب يشمل الكتلة كاملة (تقشّر + مدة + تصنيف) كوحدة واحدة — بينما في الكود الحالي القلب فقط للـ Watermark (أسفل-يمين ↔ أسفل-يسار) — ليس أعلى
- **هل ينطبق على كل المقاسات؟** نعم — `scale2ref` يعمل على أي مقاس — 9:16, 1:1, 16:9, 4:5 — DECISION-013 أكد ديناميكية — لكن المكان أسفل-يمين ثابت لا يتكيف مع "بدون فراغ أسود" — قد يحتاج مراجعة Stage 7 aspect fill vs fit
- **لون Qussasa:** في الكود `--paper #f3eae0` — في LOCKED HTML `var(--ink) #121214` مع `opacity:.6` — تعارض لون — لكن LOCKED HTML CSS يستخدم `fill=var(--ink)` داخل SVG التقشّر — بينما HANDOFF يقول Qussasa بلون --paper
- **ملف Watermark:** `ensureWatermarkFile() → ./.storage/watermark/qs.png` — يُولّد برمجيًا من هندسة QussasaMark — يكتب إلى `./.storage/watermark/qs.png` بغض النظر عن STORAGE_DRIVER — S09 CODE
- **Thumbnail:** `ffmpeg -ss min(0.5, dur/2) -frames:v 1 -vf scale=480:-2 → <base>.thumb.jpg` — يحافظ على النسبة — لا علاقة مباشرة بـ Watermark لكنه جزء من pipeline

---

## 4. التعارضات — CONFLICT-019 لا يزال قائمًا؟ + تعارضات جديدة بعد DECISION-013؟

### CONFLICT-019 — هل لا يزال قائمًا؟

**نعم — لا يزال قائمًا — OPEN — Stage 4**

- **الدليل من LOCKED HTML (قراءة مباشرة):**
  - LOCKED HTML يقول: 9–15% من العرض، أعلى الزاوية الافتراضية، مع ظل مزدوج، قاعدة القلب عند الحاجة — نسخة مقواة ✓ LOCKED — تلغي النسخة السابقة بلا ظل
  - هذا يتوافق مع S10 Spec A: 11% top-right double shadow (11% ضمن range 9-15% — أعلى-يمين — ظل مزدوج)
  - يخالف S09 Spec B: 14% bottom-right no shadow (14% ضمن range 9-15% لكن المكان أسفل والظل مفقود)
  - **النتيجة:** LOCKED HTML يؤكد أن Spec A (أعلى + ظل مزدوج) هو المعتمد — Spec B (أسفل + بلا ظل) هو المخالف — لكن الحجم 14% نفسه ضمن range 9-15% لذا الحجم ليس تعارضًا حادًا — التعارض الحقيقي هو المكان (أعلى vs أسفل) والظل (مزدوج vs بلا)

- **من CANONICAL + CONFLICT-REGISTER-V2:**
  - B-07: CONFIRMED as locked concept — High for concept, CONFLICTED for exact spec 11% vs 14% (see OPEN)
  - CONFLICT-019: CONFLICTED — NEEDS PRODUCT DECISION — Status لم يُحل بعد DECISION-013
  - DECISION-013: CONFLICT-019 Watermark 11% vs 14% لم يُحل بعد — يبقى لـ Stage 4/7 — PD-08 لم يحسمه

- **الخلاصة:** CONFLICT-019 لا يزال OPEN — يحتاج قرار Stage 4 — LOCKED HTML الآن مقروء ويؤكد 9-15% أعلى + ظل مزدوج + قلب الكتلة

### تعارضات جديدة بعد DECISION-013 (Aspect Ratio — أي مقاس مسموح + لا فراغ أسود)؟

- **تعارض جديد محتمل 1 — بدون فراغ أسود vs Watermark أسفل-يمين:**
  - DECISION-013: أي مقاس مسموح — بدون فراغ أسود — الفيديو يملأ الإطار — لا letterboxing/pillarboxing — إذا كان 16:9 في بطاقة 9:16 يجب أن يملأها crop أو scale — توجيه فقط Rubric 6
  - Watermark الحالي أسفل-يمين — إذا تم crop لملء البطاقة — قد يُقص جزء من Watermark إذا كان قريبًا من الحافة — Safe Area 6% أعلى 20% أسفل 14% يمين 6% يسار لـ 9:16 — لكن لا Safe Area لـ 16:9/1:1/4:5 — UNKNOWN
  - يحتاج Stage 4 Safe Area Guides لكل مقاس + Stage 7 ffmpeg watermark fill vs fit

- **تعارض جديد محتمل 2 — Qussasa في الزاوية vs أي مقاس:**
  - DECISION-013: Qussasa في الزاوية دائمًا — قاعدة قلب الكتلة — يعملان على 9:16,1:1,16:9,4:5
  - LOCKED HTML: Qussasa داخل التقشّر — التقشّر 9-15% أعلى — قاعدة قلب الكتلة تشمل التقشّر+مدة+تصنيف كوحدة واحدة
  - الكود الحالي: Qussasa بلون --paper أسفل-يمين — ليس أعلى — القلب فقط Watermark — ليس الكتلة كاملة
  - يحتاج مراجعة Stage 4 — Qussasa في الزاوية مراجعة لـ 16:9

- **تعارض جديد محتمل 3 — Overlays 9:16+1:1 فقط vs أي مقاس:**
  - S06: Overlays 9:16+1:1 + Safe Area Guides x4 Default/Mirrored ×2 — موجودة
  - DECISION-013: Overlays الحالية 9:16+1:1 تبقى كمرجع بصري ليست حد — Stage 4 يقرر هل نحتاج Overlays جديدة لـ 16:9/4:5/3:4
  - Watermark 9-15% range قد يحتاج Overlays جديدة لكل مقاس — UNKNOWN

- **لا تعارض جديد مع Categories/Collections:**
  - P-31 Categories Removed + P-32 Collections Primary — لا علاقة بـ Watermark — متوافق

---

## 5. Unknowns — ما الذي لا نعرفه؟

### UNKNOWN-1 — الحجم الدقيق المعتمد:

- LOCKED HTML يقول 9–15% range — ليس رقم ثابت — هل 11% هو الرقم الدقيق داخل الـ range؟ — arena.md §8.2 يقول 11% — S06 يقول 9-15% double shadow — S09 يقول 14% — أي رقم داخل 9-15% يحقق LOCKED؟ — أم 11% هو المعتمد و 14% مخالف؟
- **UNKNOWN:** هل 11% هو الرقم الرسمي؟ أم 9-15% range هو الرسمي والـ 11% مثال؟ — LOCKED HTML لا يذكر 11% صراحة — يذكر 9-15% — لكن arena.md §8.2 يذكر 11% كـ Spec — يحتاج تأكيد

### UNKNOWN-2 — المكان الدقيق:

- LOCKED HTML: "أعلى الزاوية الافتراضية" — أعلى (top) — الزاوية الافتراضية top-right (tr) حسب الصور — مع قلب للـ tl عند الحاجة
- الكود الحالي: أسفل-يمين bottom-right — أو أسفل-يسار tl — أسفل وليس أعلى
- **UNKNOWN:** هل الكود الحالي نقل Watermark من أعلى إلى أسفل عمدًا؟ أم خطأ؟ — HANDOFF يقول: "الـ MVP القديم كان بظل مزدوج و11% أعلى-يمين — CONFLICT مع مواصفات Brand v1.0 حسب arena.md §8.2" — ثم يقول الكود الحالي 14% أسفل-يمين بلا ظل — هل النقل لأسفل قرار تقني لتفادي تداخل مع مدة الفيديو أو تصنيف؟ — لا دليل

### UNKNOWN-3 — الظل:

- LOCKED HTML: ظل مزدوج `drop-shadow 0 1px 2px + 0 0 2px opacity .6/.4` — "هذا هو المعيار المعتمد من الآن فصاعدًا، ويُلغي النسخة السابقة بلا ظل"
- الكود الحالي: بلا ظل — no shadow
- **UNKNOWN:** هل إزالة الظل في الكود قرار أداء (performance)؟ أم نسيان؟ — ffmpeg لا يدعم drop-shadow مباشرة — يحتاج filter إضافي — هل تم حذفه لتسهيل ffmpeg؟ — لا دليل — لكن LOCKED HTML يؤكد أن بلا ظل يفشل على خلفية فاتحة — وهذا فشل وظيفي مباشر

### UNKNOWN-4 — لون Qussasa:

- LOCKED HTML CSS: `.peel svg path fill=var(--ink) #121214` — Qussasa بلون Ink داكن داخل تقشّر Paper فاتح #f3eae0 — مع opacity .6
- HANDOFF: Qussasa بلون --paper #f3eae0 — 14% من العرض — أسفل-يمين — لا ظل — لون فاتح
- **UNKNOWN:** أي لون معتمد؟ — Ink داخل Paper (LOCKED) أم Paper (HANDOFF)؟ — هل Qussasa في Watermark نفس Qussasa Mark في البطاقات؟ — B-04 Qussasa Mark مربع بزاوية علوية يمنى مشطوفة/ممزقة + ثقب تشغيل مثلث fill-rule evenodd — B-07 Watermark تقشّر ورقي بزاوية + شعار بداخله — هل الشعار هو Qussasa؟ — نعم حسب LOCKED HTML — لكن اللون مختلف

### UNKNOWN-5 — العلاقة بـ Safe Area:

- LOCKED HTML Safe Area: أعلى 6%، أسفل 20%، يمين 14%، يسار 6% (9:16) — القص الحقيقي مسموح فقط في البطاقات التي نتحكم بها، لا في الفيديو المُصدَّر
- Watermark في LOCKED HTML: 9-15% أعلى الزاوية — هل داخل Safe Area أم خارج؟ — 15% width + top:0 right:0 — قد يتداخل مع Safe Area — لكن النص يقول Safe Area للـ Clip Template — Watermark جزء من Clip Template؟
- الكود الحالي: إزاحة 16px من الحافة — `overlay=(W-w-16):H-h-16` — 16px ثابتة — لا نسبة Safe Area — هل 16px كافية لـ Safe Area 6%/14%؟
- **UNKNOWN:** هل Watermark يجب أن يحترم Safe Area؟ أم Safe Area للـ UI فقط (مدة+تصنيف) وليس Watermark؟ — LOCKED HTML لا يوضح — يحتاج Stage 4

### UNKNOWN-6 — قاعدة قلب الكتلة — هل تشمل Watermark فقط أم الكتلة كاملة؟

- LOCKED HTML: قلب الكتلة (تقشّر + مدة + تصنيف) كوحدة واحدة — ممنوع نقل عنصر واحد بمفرده — إما الكل بمكانه أو الكل مقلوب — مثال حماس: الكتلة كاملة انقلبت لليسار (peel tl + dur right + dot right) — مثال رفض: قلب جزئي — يد ترفض تشغل الزاوية السفلية اليسرى — نقطة التصنيف فقط انتقلت لليمين، التقشّر بقي مكانه لأنه غير متأثر
- الكود الحالي: قلب Watermark فقط — أسفل-يمين ↔ أسفل-يسار — لا يشمل مدة أو تصنيف — ولا يشمل تقشّر+مدة+تصنيف كوحدة
- **UNKNOWN:** هل قاعدة قلب الكتلة في الكود الحالي مطبقة كاملة؟ أم فقط Watermark؟ — HANDOFF لا يذكر مدة+تصنيف — يذكر فقط watermark Qussasa 14% أسفل-يمين أو أسفل-يسار لـ corner=tl — يحتاج مراجعة كود ReactionCard + Clip Template

### UNKNOWN-7 — هل هناك تصميم جديد مطلوب؟

- LOCKED HTML: Overlays 9:16+1:1 موجودة كـ PNGs — S01 Asset Inventory lists overlay PNGs — S06 Overlays + Safe Area Guides x4 Default/Mirrored ×2
- DECISION-013: أي مقاس مسموح — Watermark+Qussasa ديناميكي — Overlays الحالية 9:16+1:1 تبقى مرجع بصري ليست حد — Stage 4 يقرر هل نحتاج Overlays جديدة لـ 16:9/4:5/3:4 — Safe Area Guides لكل مقاس — Qussasa مراجعة لـ 16:9 — كيفية تطبيق بدون فراغ أسود Crop vs Scale+Pad vs Masonry يتكيف
- **UNKNOWN:** هل نحتاج Overlays جديدة لـ 16:9/4:5/3:4؟ — هل نحتاج Safe Area Guides جديدة لكل مقاس؟ — هل نحتاج Watermark جديد لكل مقاس؟ — LOCKED HTML يذكر Safe Area لـ 9:16 فقط — لا يذكر 1:1/16:9/4:5 — يحتاج Stage 4 Experience

### UNKNOWN-8 — مراجعة الكود — هل نحتاج مراجعة ffmpeg.ts كامل؟

- لم يُعثر على ملف ffmpeg.ts في هذا الـ workspace — البحث `find -name ffmpeg.ts` فشل — الدليل من HANDOFF فقط — لا يمكن تأكيد الكود الحالي بدون قراءة الملف — يحتاج Stage 7 Technical — T-04 CURRENT local — لكن الملف غير موجود هنا — UNKNOWN
- **UNKNOWN:** هل الكود الحالي في هذا الـ workspace يطابق HANDOFF؟ — لا يمكن التأكد بدون ملف — يحتاج Stage 7

### UNKNOWN-9 — هل Watermark للصور نفس Watermark للفيديو؟

- DECISION-002 Video+Image equal — كلاهما منتج أساسي
- DECISION-013: الصور أكثر مرونة أي مقاس — لا قيد فراغ أسود على الصور — Rubric 6 صورة نقية — أكثر مرونة
- OPEN-Q-03: Watermark exact spec 11% vs 14% — Stage 4 + OPEN-Q-03 — Watermark واترمارك الفيديو معتمد 11% vs 14%، لكن واترمارك الصور غير محدد
- **UNKNOWN:** هل Watermark للصور نفس 9-15% أعلى + ظل مزدوج؟ أم مختلف؟ — LOCKED HTML لا يذكر صور — يذكر Watermark للفيديو فقط — يحتاج Stage 4

---

## 6. ملخص HISTORY + EVIDENCE — بدون قرار

### ما يقوله LOCKED HTML — المعتمد:

- **الحجم:** 9–15% من العرض — Range — ليس رقم ثابت — 15% في CSS النموذج — 9-15% في النص
- **المكان:** أعلى الزاوية الافتراضية — top — default top-right (tr) — مع قلب لـ top-left (tl) عند الحاجة — قاعدة قلب الكتلة
- **الظل:** ظل مزدوج — `drop-shadow 0 1px 2px + 0 0 2px opacity .6/.4` — معتمد — يلغي النسخة السابقة بلا ظل — فشل وظيفي على خلفية فاتحة بدون ظل
- **الشكل:** تقشّر ورقي بزاوية — clip-path polygon — خلفية Paper #f3eae0 — بداخله Qussasa Mark — fill-rule evenodd مثلث تشغيل — opacity .6 — Ink #121214
- **Safe Area:** أعلى 6%، أسفل 20%، يمين 14%، يسار 6% (9:16) — القص مسموح في البطاقات فقط لا في الفيديو المُصدَّر
- **قلب الكتلة:** إذا شغلت يد/حركة الزاوية الافتراضية — تُقلب الكتلة (تقشّر+مدة+تصنيف) كوحدة واحدة للجهة المقابلة — ممنوع نقل عنصر واحد — إما الكل أو الكل مقلوب — 6 نماذج افتراضي + 2 قلب كامل + 1 قلب جزئي

### ما يقوله الكود الحالي (S09 + HANDOFF):

- **الحجم:** 14% — `w=iw*0.14` — ضمن range 9-15% — يحقق LOCKED range
- **المكان:** أسفل-يمين bottom-right مع إزاحة 16px — أو أسفل-يسار bottom-left لـ corner=tl — يخالف LOCKED أعلى
- **الظل:** بلا ظل — no shadow — يخالف LOCKED ظل مزدوج — النسخة بلا ظل أُلغيت في LOCKED
- **الشكل:** Qussasa بلون --paper #f3eae0 — 14% — أسفل — لا ظل — يُولّد برمجيًا — `./.storage/watermark/qs.png`
- **قلب الكتلة:** موجود جزئيًا — corner=tl vs tr — لكن فقط Watermark — ليس الكتلة كاملة — يخالف LOCKED قلب كامل
- **ديناميكي:** يعمل على أي مقاس 9:16,1:1,16:9,4:5 — scale2ref يحافظ على النسبة — متوافق مع DECISION-013

### التعارض:

- **CONFLICT-019 لا يزال قائمًا — OPEN — Stage 4:**
  - Spec A (LOCKED HTML + S10 + arena.md §8.2): 9-15% (11% مثال) — أعلى-يمين — ظل مزدوج — معتمد — يلغي بلا ظل
  - Spec B (الكود الحالي ffmpeg.ts): 14% — أسفل-يمين — بلا ظل — مخالف للمكان والظل — لكن الحجم ضمن range
  - **التعارض الحقيقي:** المكان (أعلى vs أسفل) + الظل (مزدوج vs بلا) — الحجم ليس تعارض حاد (11% و 14% كلاهما ضمن 9-15%)
  - **الدليل:** LOCKED HTML قراءة مباشرة تؤكد أعلى + ظل مزدوج + 9-15% + قلب الكتلة — HANDOFF يؤكد 14% أسفل-يمين بلا ظل + CONFLICT مع Brand v1.0 حسب arena.md §8.2
  - **يحتاج:** قرار Stage 4 Experience — أي Spec معتمد؟ أم كلاهما استخدامات مختلفة؟ — هل نعيد Watermark لأعلى + ظل مزدوج؟ أم نبقي أسفل-يمين مع إضافة ظل؟

- **تعارضات جديدة بعد DECISION-013:**
  - بدون فراغ أسود vs Watermark أسفل-يمين — قد يُقص عند crop لملء البطاقة — Safe Area لـ 9:16 فقط — لا Safe Area لـ 16:9/1:1/4:5 — UNKNOWN
  - Qussasa في الزاوية vs أي مقاس — LOCKED أعلى + قلب كامل vs كود أسفل + قلب جزئي — يحتاج مراجعة Stage 4
  - Overlays 9:16+1:1 فقط vs أي مقاس — يحتاج Stage 4 هل نحتاج Overlays جديدة لـ 16:9/4:5/3:4 + Safe Area Guides لكل مقاس

### ما لا نعرفه — UNKNOWNs:

- UNKNOWN-1 الحجم الدقيق: 11% أم 9-15% range؟ — LOCKED يقول range — arena.md يقول 11%
- UNKNOWN-2 المكان: لماذا نُقل من أعلى إلى أسفل في الكود؟ — عمدًا أم خطأ؟
- UNKNOWN-3 الظل: لماذا أُزيل الظل في الكود؟ — أداء ffmpeg أم نسيان؟ — LOCKED يؤكد فشل بلا ظل على خلفية فاتحة
- UNKNOWN-4 لون Qussasa: Ink #121214 داخل Paper #f3eae0 (LOCKED) أم Paper #f3eae0 (HANDOFF)؟
- UNKNOWN-5 Safe Area: هل Watermark يحترم Safe Area؟ أم Safe Area للـ UI فقط؟
- UNKNOWN-6 قلب الكتلة: هل تشمل Watermark فقط أم الكتلة كاملة (تقشّر+مدة+تصنيف)؟
- UNKNOWN-7 تصميم جديد: هل نحتاج Overlays جديدة + Safe Area Guides لكل مقاس 16:9/4:5/3:4؟
- UNKNOWN-8 مراجعة الكود: ملف ffmpeg.ts غير موجود في هذا workspace — لا يمكن تأكيد بدون قراءة — يحتاج Stage 7
- UNKNOWN-9 Watermark للصور: هل نفس Watermark للفيديو؟ أم مختلف؟ — OPEN-Q-03

---

## 7. Evidence List — المصادر

- **YemReact-Brand-v1.0-LOCKED.html** — 343 lines — LOCKED v1.0 — Tier 3 تقوية Watermark ظل مزدوج `drop-shadow 0 1px 2px + 0 0 2px opacity .6/.4` يلغي بلا ظل — Final Locked Spec Watermark 9-15% أعلى الزاوية الافتراضية مع ظل مزدوج قاعدة القلب عند الحاجة — Safe Area 6% top 20% bottom 14% right 6% left (9:16) — Qussasa Mark fill-rule evenodd — قلب الكتلة (تقشّر+مدة+تصنيف) كوحدة واحدة
- **YemReact-identity-system.html** — Safe Area 6% top 20% bottom 14% right 6% left — مطابق
- **YemReact_Claude_Foundation_Package.md** — Brand v1.0 LOCKED Qussasa + Watermark مقوى + قاعدة قلب الكتلة — لا إعادة تصميم
- **ARENA-TECHNICAL-HANDOFF.md** — Line 404 watermark 14% bottom-right 16px offset no shadow — MVP old 11% top-right double shadow CONFLICT per arena.md §8.2 — Line 564 CONFLICT table 11% top-right double shadow vs 14% bottom-right no shadow — ffmpeg filter `scale2ref=w=iw*0.14:h=ow/mdar[wm][vid];[vid][wm]overlay=(W-w-16|16):H-h-16` — ensureWatermarkFile `./.storage/watermark/qs.png` Qussasa geometry
- **YEMREACT-CONFLICT-REGISTER-V2.md** — CONFLICT-019 Watermark Spec 11% top-right double shadow vs 14% bottom-right no shadow #f3eae0 Qussasa — VERSION DRIFT + REAL CONFLICT — NEEDS PRODUCT DECISION
- **YEMREACT-CONFLICT-REGISTER.md** — CONFLICT-019 CLAUDE-FOUNDATION 11% top-right double shadow vs ARENA-TECHNICAL 14% bottom-right no shadow — CONFLICTED
- **YEMREACT-CANONICAL-BASELINE.md** — B-07 Watermark تقشّر ورقي بزاوية + شعار بداخله نسخة مقواة بظل مزدوج بعد فشل أولى — CONFIRMED as locked concept — CONFLICTED for exact spec 11% vs 14% — T-04 Media pipeline 14% bottom-right no shadow CURRENT local — P-29 Watermark 14% تقنيًا حاليًا CONFLICT-019 — P-30 CONFLICT-019 لم يُحل بعد Stage4/7 — WHAT IS NOT Watermark exact spec 11% vs 14% CONFLICTED Stage 4
- **YEMREACT-DECISIONS-LOG.md** — DECISION-013 Aspect Ratio Watermark 14% تقنيًا حاليًا CONFLICT-019 يُحل Stage 4/7 — 11% vs 14% — Qussasa في الزاوية دائمًا قاعدة قلب الكتلة — ديناميكي على أي مقاس — CONFLICT-019 لم يُحل بعد — VD-09 OPEN — Evidence S10 Brand v1.0 LOCKED 9:16 Safe Area 6% top 20% bottom 14% right 6% left + Qussasa 6-15% + Watermark 9-15% double shadow

---

## 8. Conclusion — HISTORY + EVIDENCE فقط — لا قرار

- **قراءة LOCKED HTML تمت:** نعم — Spec الرسمي: 9–15% من العرض، أعلى الزاوية الافتراضية (default top-right)، مع ظل مزدوج `drop-shadow 0 1px 2px + 0 0 2px opacity .6/.4`، تقشّر Paper #f3eae0 بداخله Qussasa Ink #121214، Safe Area 6% top 20% bottom 14% right 6% left (9:16)، قاعدة قلب الكتلة (تقشّر+مدة+تصنيف) كوحدة واحدة للجهة المقابلة عند الحاجة، النسخة بلا ظل أُلغيت — هذا هو المعتمد من الآن فصاعدًا
- **Spec A (11% top-right double shadow) يتوافق مع LOCKED HTML:** 11% ضمن 9-15% + أعلى-يمين + ظل مزدوج — يطابق LOCKED — arena.md §8.2 يذكر 11% كمثال داخل range
- **Spec B (14% bottom-right no shadow) يخالف LOCKED HTML في المكان والظل:** 14% ضمن range لكن أسفل-يمين بدل أعلى + بلا ظل بدل مزدوج — مخالف — CONFLICT-019 قائم
- **الكود الحالي يستخدم Spec B:** 14% bottom-right no shadow — `w=iw*0.14` + `overlay=(W-w-16):H-h-16` — لا ظل — Qussasa بلون --paper — قلب جزئي فقط — ديناميكي على أي مقاس scale2ref — متوافق مع DECISION-013 ديناميكية لكن مخالف LOCKED مكان+ظل
- **CONFLICT-019 لا يزال OPEN:** يحتاج قرار Stage 4 — أيهما المعتمد؟ أم كلاهما استخدامات مختلفة؟ — LOCKED HTML يؤكد أعلى + ظل مزدوج معتمد
- **تعارضات جديدة بعد DECISION-013:** بدون فراغ أسود قد يقص Watermark عند crop — Safe Area لـ 9:16 فقط لا لـ 16:9/1:1/4:5 — Qussasa في الزاوية مراجعة لـ 16:9 — Overlays 9:16+1:1 فقط مرجع بصري ليست حد — تحتاج Stage 4 Safe Area Guides لكل مقاس + Overlays جديدة + Stage 7 ffmpeg fill vs fit
- **UNKNOWNs 9:** حجم دقيق 11% أم range؟ — مكان لماذا أسفل؟ — ظل لماذا بلا؟ — لون Qussasa Ink أم Paper؟ — Safe Area هل Watermark يحترم؟ — قلب الكتلة كاملة أم Watermark فقط؟ — تصميم جديد Overlays+Safe Area لكل مقاس؟ — مراجعة ffmpeg.ts ملف غير موجود — Watermark للصور نفس الفيديو؟

**END OF HISTORY + EVIDENCE — بانتظار أمر حمدان للانتقال إلى DISCUSSION**

