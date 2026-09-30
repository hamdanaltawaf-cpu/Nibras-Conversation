# YEMREACT-UNKNOWN-REGISTER.md — Phase 1B — Unknown Register

> Phase 1B only — No decisions, no implementation. Only unknowns that cannot be proven from 12 sources.
> Format: UNKNOWN — لا يوجد دليل كافٍ.

## Product / Vision

- UNKNOWN — لا يوجد دليل كافٍ على تعريف المنتج النهائي هل هو محرك بحث أم مكتبة اكتشاف أولًا — المصادر تحمل الاثنين (CONFLICT-001)
- UNKNOWN — لا يوجد دليل كافٍ على القيمة الأساسية هل تصمد أمام "أسجل الشاشة من TikTok" — S08 open question
- UNKNOWN — لا يوجد دليل كافٍ على قناة الاكتساب الحقيقية (SEO؟ Facebook؟ متناقل؟) — S08 open
- UNKNOWN — لا يوجد دليل كافٍ على تعريف رقمي للنجاح (metrics 5) — S08 open
- UNKNOWN — لا يوجد دليل كافٍ على هل Core Loop عادة يومية أم تذكر وقت الحاجة — S08 tension

## UX / IA

- UNKNOWN — لا يوجد دليل كافٍ على تركيبة BottomNav النهائية (4th item) — 3 اقتراحات متنافسة (CONFLICT-007)
- UNKNOWN — لا يوجد دليل كافٍ على هل /search صفحة منفصلة أم /?q= — قرار ACCEPTED vs implementation (CONFLICT-005)
- UNKNOWN — لا يوجد دليل كافٍ على هل Sidebar دائم مطلوب على Desktop — قرار ACCEPTED no sidebar vs code has sidebar (CONFLICT-008)
- UNKNOWN — لا يوجد دليل كافٍ على أنواع نية البحث (حرفية/موقف/مزاج/شخص) هل حقل واحد يكفي — S03 open question 1
- UNKNOWN — لا يوجد دليل كافٍ على أولوية Featured/New/Collections rails — S03 open question 2
- UNKNOWN — لا يوجد دليل كافٍ على توقيت Settings (autoplay/صوت/توفير بيانات/حركة) — S03 open question 3
- UNKNOWN — لا يوجد دليل كافٍ على هل استئناف نموذج الإرسال بعد تسجيل الدخول يعمل — S03 open question
- UNKNOWN — لا يوجد دليل كافٍ على Accessibility / RTL edge cases تم التحقق — S03 open
- UNKNOWN — لا يوجد دليل كافٍ على محتوى Onboarding walkthrough — S03 open
- UNKNOWN — لا يوجد دليل كافٍ على تسمية نهائية للمكتبة/البحث/جديد المكتبة/عرض الكل — S08 terminology
- UNKNOWN — لا يوجد دليل كافٍ على هل Reaction Detail يحتاج Intercepting route — S08 deferred

## Technical / Architecture

- UNKNOWN — لا يوجد دليل كافٍ على رابط الإنتاج العام على Vercel وحالة النشر الحالية — S09 says UNKNOWN
- UNKNOWN — لا يوجد دليل كافٍ على متغيرات بيئة Vercel الفعلية (AUTH_SECRET, AUTH_GOOGLE_ID/SECRET, IP_SALT, STORAGE_DRIVER, S3_*) — S09 says UNKNOWN, .env.vercel لا يحويها
- UNKNOWN — لا يوجد دليل كافٍ على وجود bucket R2/S3/MinIO مهيأ — S09 UNKNOWN
- UNKNOWN — لا يوجد دليل كافٍ على هل S3Storage يعمل ضد خدمة حقيقية — S09 tested with mocks only
- UNKNOWN — لا يوجد دليل كافٍ على نتائج اختبارات التكامل 94 و11 spec E2E ≈30 اختبار — S09 لم يشغلها لأنها تكتب في الإنتاج
- UNKNOWN — لا يوجد دليل كافٍ على هل خط ffmpeg يعمل الآن في أي بيئة غير الجهاز الذي أنتج .storage 216 خرج — S09 says Sep 2 02:03 all mtimes unified (snapshot restore)
- UNKNOWN — لا يوجد دليل كافٍ على سلوك error.tsx عمليًا — S09 لم يثر خطأ خادم
- UNKNOWN — لا يوجد دليل كافٍ على الأداء تحت حمل وحدود Neon pooler مع 44 مسار dynamic — S09
- UNKNOWN — لا يوجد دليل كافٍ على هل Google OAuth app في وضع Testing أم Production في Google Console — S09
- UNKNOWN — لا يوجد دليل كافٍ على وجود نسخ/فروع من المستودع خارج الصندوق (جهاز المالك، Vercel Git integration — VERCEL_GIT_* فارغة) — S09 INFERENCE CLI deploy not Git
- UNKNOWN — لا يوجد دليل كافٍ على التاريخ الفعلي لأحداث الملفات — كل mtimes موحدة snapshot restore — S09
- UNKNOWN — لا يوجد دليل كافٍ على هل .storage 829 ملفًا اختباريًا يجب تنظيفه — S09
- UNKNOWN — لا يوجد دليل كافٍ على مواصفة العلامة المائية المعتمدة (14% bottom-right no shadow vs 11% top-right double shadow) — CONFLICT-019

## Content

- UNKNOWN — لا يوجد دليل كافٍ على وجود محتوى حقيقي منشور في بيئة إنتاج — S09 media=0, Event=3 view only, S11/S12 mock API
- UNKNOWN — لا يوجد دليل كافٍ على نموذج قاعدة البيانات الكامل وrelations — S11/S12 no full schema proof
- UNKNOWN — لا يوجد دليل كافٍ على سياسة المحتوى والاعتدال والحقوق (takedown, مصدر الفيديو, source/sourceUrl إلزامية) — S08 open
- UNKNOWN — لا يوجد دليل كافٍ على هل التصنيفات مقفلة على 9 أم مفتوحة — S09/CONFLICT-012
- UNKNOWN — لا يوجد دليل كافٍ على هل Featured يدوي عبر admin أم يُلغى — S08/S09
- UNKNOWN — لا يوجد دليل كافٍ على هل Submission keywords/sourceUrl/description مسموحة للمرسل — CONFLICT-012
- UNKNOWN — لا يوجد دليل كافٍ على مصدر البيانات الحقيقي للكتالوج — S11/S12 seed vs mock
- UNKNOWN — لا يوجد دليل كافٍ على وجود صور أو فيديوهات أصلية للرياكشنات — S11/S12 UNKNOWN

## Infrastructure / Deployment

- UNKNOWN — لا يوجد دليل كافٍ على وجود CI / isolated test DB — S09 G9
- UNKNOWN — لا يوجد دليل كافٍ على وجود vercel.json — S09 says no vercel.json
- UNKNOWN — لا يوجد دليل كافٍ على وجود Range/HLS/CDN/signed URLs — S09 says no Range
- UNKNOWN — لا يوجد دليل كافٍ على وجود Job queue/worker خارجي — S09 says void promise in-process
- UNKNOWN — لا يوجد دليل كافٍ على وجود favicon/robots/sitemap/manifest/OG — S09 says none

## Historical / Team / Ownership

- UNKNOWN — لا يوجد دليل كافٍ على من كتب Phase 0→6L (أي وكيل/نموذج) — S09 says summary injected from another language model
- UNKNOWN — لا يوجد دليل كافٍ على ما هو Manus (وكيل؟ مصمم؟ مشروع؟) وعلاقة uploads/client/src/* بهذا المستودع رسميًا — S09
- UNKNOWN — لا يوجد دليل كافٍ على من هو نِبراس ودوره — S09 knows name from this request only
- UNKNOWN — لا يوجد دليل كافٍ على دور حساب qnasly189@gmail.com (مختبر؟ متعاون؟) — S09
- UNKNOWN — لا يوجد دليل كافٍ على ما إذا كانت كل الملفات المذكورة في S01 قد بقيت في المستودع بعد تغييرات لاحقة — S11 possible drift
- UNKNOWN — لا يوجد دليل كافٍ على أي نسخة هي الرسمية فعليًا (Astro vs Next.js) — S08/S11
- UNKNOWN — لا يوجد دليل كافٍ على عدد المستخدمين أو المساهمات الحقيقيين أو مؤشرات استخدام — S11/S12

## Summary Counts

- Product unknowns: 5
- UX/IA unknowns: 11
- Technical unknowns: 13
- Content unknowns: 8
- Infrastructure unknowns: 5
- Historical/Team unknowns: 7
- Total unknowns: 49
