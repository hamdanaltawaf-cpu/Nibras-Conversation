# ARENA-TECHNICAL-HANDOFF.md
## YemReact — Phase 0 / Technical Knowledge Handoff
### التسليم الرسمي من Arena-Agent إلى مرحلة إعادة تأسيس YemReact (إلى: نِبراس)

| البند | القيمة |
|---|---|
| تاريخ التسليم | 2026-09-02 |
| المُسلِّم | Arena-Agent (وكيل Arena.ai Agent Mode) |
| المستلم | نِبراس |
| المستودع المعني | `/home/user/yemreact-next` — HEAD `331c1b3` (branch `master`) |
| طبيعة هذه الوثيقة | قراءة + تحليل + توثيق فقط. **لم يُعدَّل كود، ولا Git، ولا قاعدة بيانات، ولا Vercel/Neon.** |
| الملفات المرافقة (من نفس المُسلِّم) | `/home/user/audit-2026-09-02/YemReact-Technical-State-Audit.md` (Part 1)، `…-Part2-UI-Surfaces.md` (Part 2)، 47 لقطة شاشة في `audit-2026-09-02/shots*/`، `/home/user/team/Arena-Agent.md` |

### قاعدة الأدلة المستخدمة في هذه الوثيقة
- `CODE` — قرأته مباشرة من ملفات المستودع.
- `DATABASE` — استعلام **قراءة فقط** (SELECT/count) على قاعدة Neon الإنتاجية، 2026-09-02.
- `COMMAND OUTPUT` — أمر شغّلته فعليًا ورأيت مخرجاته (tsc/lint/vitest/build/curl/playwright/prisma).
- `DOC` — وثيقة في البيئة (README/ADR/prototype/uploads/MVP docs).
- `INFERENCE` — **استنتاج وليس حقيقة مثبتة** (مكتوب صراحة عند كل استخدام).
- **UNKNOWN — لا أملك دليلًا كافيًا** (القسم 15 يجمعها).

### حدود معرفتي (اقرأ هذا أولًا)
1. سياقي في هذا المشروع بدأ بملخّص محقون **مبتور** من "نموذج لغوي آخر". كل ما قبل تدقيقي (كتابة Phase 0→6L) أعرفه **من الملفات فقط**، لا من ذاكرة عمل.
2. لم أتحدث مع أي وكيل آخر. لا أعرف من هو "Manus" ولا "نِبراس" سوى من هذا الطلب.
3. لا وصول لي إلى لوحات Vercel / Neon / Google Cloud / GitHub. كل ما أعرفه عن النشر مستنتج من ملفات `.env*` و`.vercel/`.
4. لم أشغّل اختبارات التكامل (94) ولا 11 من ملفات E2E (≈30 اختبارًا) لأنها **تكتب في قاعدة الإنتاج** — القاعدة الوحيدة المتاحة.
5. لا ffmpeg في بيئتي؛ خط الوسائط لم أشغّله بنفسي — أدلتي عليه: الكود + 216 مخرجًا موسومًا في `.storage/` + اختبارات وحدة.

---

## القسم 1 — هوية المشروع كما تراها من الكود

### 1.1 ما هو موجود فعليًا (CODE + DATABASE + COMMAND OUTPUT)
تطبيق **Next.js 15 (App Router) + React 19 + Prisma 5 + PostgreSQL (Neon)** يقدّم:
- **مكتبة رياكشنات عامة**: صفحة رئيسية (hero + بحث + شريط تصنيفات + "جديد المكتبة" + "مختار الأسبوع" + مجموعات)، صفحة بحث/تصفح بلا نهاية، صفحة تفاصيل `/r/YR-0001`، فهرس مجموعات وصفحة مجموعة، صفحة محفوظات.
- **بحث عربي منسَّق** (`pg_trgm` similarity + ILIKE + keyset pagination) على `caption/situation/description/keywords`.
- **حسابات Google فقط** (Auth.js v5، JWT) مع دور من قاعدة البيانات؛ محفوظات محلية للزائر تُدمج مع السحابة عند تسجيل الدخول.
- **إرسال مساهمات** (فيديو + بيانات) من المستخدم المسجَّل → طابور مراجعة → اعتماد بشروط.
- **لوحة إدارة** لـ ADMIN: رياكشنات (CRUD + أرشفة + وسائط)، تصنيفات، مجموعات (+ترتيب)، إرسالات (اعتماد/رفض/إعادة معالجة).
- **خط معالجة وسائط** (ffprobe/ffmpeg: thumbnail + watermark + MP4) بحالات صريحة وسجل تدقيق.
- **تجريد تخزين** (local FS / S3-compatible عبر minio).
- **تحليلات**: أحداث view/save/download/share مع فلترة بوتات وتكرار.

نص التعريف في الكود نفسه متعارض: `package.json` → "Yemeni visual reaction **search engine**"؛ `layout.tsx` metadata → "محرك بحث عن رياكشنات يمنية"؛ eyebrow الـ hero و caption الـ header → "**مكتبة** رياكشنات يمنية". (CODE)

### 1.2 ما يبدو أنه كان مخططًا (DOC + CODE)
- ADR-0001: مصادقة **OTP + جلسات DB** — نُفِّذ بدلًا منها Google + JWT (models `Session`, `OneTimeCode` بقايا). (DOC vs CODE)
- ADR-0002: "aggregation job" للعدادات — غير موجود؛ العدادات تُزاد فورًا. (DOC vs CODE)
- `lib/media/types.ts`: "FFmpeg implementation lands in Phase 9" — نُفِّذ في "Phase 6H". (CODE comment قديم)
- `.env.example`: `MEDIA_DRIVER=service`, `SMTP_*`, `MEDIA_WATERMARK_PATH`, `ADMIN_EMAIL` — تُقرأ في `env.ts` ولا يستخدمها أي كود. (CODE)
- الأدوار `EDITOR`، `MediaRole.SUBTITLE`، `MediaKind.PROCESSED` كمخرج pipeline، `Submission.contact/sessionId`، model `Setting` — معرَّفة بلا منطق. (CODE)
- MVP القديم `arena.md` §17 يخطط: HLS، جودات متعددة، PWA، SEO لكل رياكشن، إشعارات بريد، rate limiting، صفحات قانونية، بحث دلالي عند 300+ — **لا شيء منها في الكود الحالي**. (DOC)

### 1.3 ما هو غير مكتمل (CODE + COMMAND OUTPUT)
- الوسائط في **الإنتاج**: 0 `MediaAsset` في Neon؛ لا ffmpeg على Vercel؛ storage افتراضي محلي. (DATABASE + INFERENCE عن Vercel)
- تتبّع الأحداث من الواجهة معطَّل فعليًا (BUG-1، القسم 11).
- Featured بلا أي واجهة إدارة؛ إدارة المستخدمين/الأدوار غير موجودة؛ قارئ AuditLog غير موجود.
- Settings غير موجودة (model فارغ).
- `?sent=1` بعد الإرسال و`?forbidden=1` بعد رفض الأدمن لا يعرضان شيئًا.
- `keywords`/`sourceUrl` في نموذج الإرسال تُتحقَّق ثم تُهمَل (لا أعمدة).
- `generateMetadata` لصفحات الرياكشنات غير موجود (لا OG لكل رياكشن).

### 1.4 ما هو مجرد تصور أو وثيقة قديمة (DOC)
- `README.md` للمستودع يصف "Phase 0 + Foundation" ويقول إن auth/admin/submissions/FFmpeg "غير منفَّذة بعد" — **كلها منفَّذة**.
- `docs/ARCHITECTURE.md` يذكر "Public routes are cacheable (`revalidate`)" — لا يوجد أي `revalidate`؛ كل شيء `force-dynamic`.
- `ui-prototype/` (v4 "Library-First"): يعلن نفسه "النسخة المرجعية النهائية قبل أي تنفيذ" ويتعارض جوهريًا مع التنفيذ (لا sidebar، modal للتفاصيل، بحث في المكان، settings، BottomNav فيه المجموعات).
- `uploads/YemReact — Hybrid Technical Specification.md`: مواصفة لمشروع **React 19 + Vite + Tailwind 4 + wouter + tRPC** بمسارات `client/src/*` — **ليس هذا المستودع**.
- `uploads/*.tsx.txt`, `*.css`: استخراج من ذلك المشروع الآخر بتاريخ 2026-08-31.
- `yemreact-app/` (MVP Termux) و`yemreact-web/` (prototype ثابت): نسخ سابقة.

**لا أوحّد هذه التناقضات** — القسم 13 يجدولها فقط.

---

## القسم 2 — الحالة الفعلية للمشروع

| البند | القيمة | المصدر |
|---|---|---|
| Framework | Next.js **15.5.23** (package.json `^15.1.0`)، App Router فقط، لا Pages Router، لا middleware، لا Server Actions | COMMAND OUTPUT (`node -e require(...)/package.json`) + CODE |
| Runtime | Node **v20.20.2** في بيئتي؛ `engines.node >=20.9.0`؛ `"type": "module"` | COMMAND OUTPUT + CODE |
| Frontend | React **19.2.8**، RSC افتراضيًا + 19 client island (`"use client"`)، CSS عادي (`tokens.css` + `globals.css` + `components.css` 2682 سطرًا)، `next/font/google` (Lalezar, Cairo, Archivo Black, Inter, IBM Plex Mono)، RTL `lang="ar" dir="rtl"` | CODE |
| Backend | Route Handlers في `src/app/api/**` (23 ملف) + `src/app/media/[...key]/route.ts`؛ zod للتحقق؛ `AppError` + `handleError` موحَّدان | CODE |
| Database | PostgreSQL على **Neon** (`neondb`, `us-east-1`, pooler) عبر `.env.local`؛ `.env` يشير إلى `localhost:5432` (لا Postgres محلي في بيئتي) | CODE (env) + COMMAND OUTPUT (TCP check) |
| ORM | Prisma **5.22.0** (client + CLI)، 15 model، 7 enum، 4 migrations | COMMAND OUTPUT + CODE |
| Authentication | Auth.js `next-auth@5.0.0-beta.32`، Google provider **شرطي** (يُحذف إن غابت `AUTH_GOOGLE_ID/SECRET`)، `session.strategy: "jwt"`، `pages.signIn: "/"` | CODE |
| Storage | `StorageDriver` interface؛ `LocalStorage` (`./.storage` → يُخدَم من `/media/<key>`) افتراضي؛ `S3Storage` عبر `minio@8.0.7` عند `STORAGE_DRIVER=s3` | CODE |
| Media processing | `LocalMediaService`: `spawn("ffprobe"/"ffmpeg")` من PATH، thumbnail JPEG + watermark PNG مولَّد برمجيًا + MP4 H.264/AAC؛ `processor.ts` in-process، fire-and-forget | CODE |
| Testing | Vitest **2.1.9** (unit 18 ملف / 171 اختبار؛ integration 10 ملفات / 94 اختبار)، Playwright **1.62.1** (18 spec / 124 اختبار، chromium + Pixel 7)، ESLint 9 (`next lint`)، Prettier 3 | COMMAND OUTPUT + CODE |
| Deployment | `.vercel/project.json` → `projectName: yemreact-next`؛ `.env.local`/`.env.vercel` "Created by Vercel CLI" مع متغيرات Neon. **لا `vercel.json`**. رابط الإنتاج العام: UNKNOWN | CODE (files) |
| Environment | `.env` (محلي، لا Google، لا admin email)؛ `.env.local` (Neon prod، لا Google، لا S3)؛ `.env.vercel` (DB + Turbo/Vercel vars فقط)؛ `.env.example` (قالب كامل) | CODE |
| Git | branch `master`، **commit واحد** `331c1b3` (2026-08-24)، لا remote، 28 معدَّل + 119 غير مُتتبَّع (+40 لقطة)، 0 stash | COMMAND OUTPUT |

---

## القسم 3 — ما الذي بُني فعليًا؟

### ✅ مكتمل ويعمل (مُثبَت بالتشغيل)
| العنصر | الدليل |
|---|---|
| typecheck / lint / prettier نظيفة | COMMAND OUTPUT: `tsc --noEmit --incremental false` = 0؛ `next lint` = 0؛ `prettier --check .` = clean |
| Unit tests | COMMAND OUTPUT: `vitest run` → 18 files, **171 passed** (مرتان في جلستين) |
| Production build | COMMAND OUTPUT: `next build` ✓، 45 routes، كلها ƒ Dynamic |
| التصفح العام (`/`, `/search`, `/search?q`, `/search?cat`, `/r/[code]`, `/collections`, `/collections/[slug]`, `/saved`, 404) | COMMAND OUTPUT: curl 200/404 + **94/94 E2E** (7 specs read-only × chromium + mobile-chrome) |
| البحث العربي + keyset cursor | COMMAND OUTPUT: `/api/reactions?q=خبر` → total=2 (YR-0012, YR-0001)؛ cursor مُنتَج |
| حماية المسارات | COMMAND OUTPUT: guest `/submit`,`/submissions`,`/admin` → 307؛ `/api/me|submissions|admin` → 401؛ USER → `/api/admin/*` 403 + صفحة 403 مرئية؛ ADMIN → 200 |
| Google OAuth على الإنتاج (حدث مرة على الأقل) | DATABASE: مستخدمان حقيقيان بأفاتار `googleusercontent`، 2026-08-29 |
| AccountMenu (popover/sheet) + Sidebar + BottomNav + Header 2-tier | COMMAND OUTPUT: 47 لقطة، 0 horizontal overflow على 320→1440 |
| `/media/<key>` يبث ملفًا محليًا | COMMAND OUTPUT: `/media/watermark/qs.png` → 200 |
| Admin pages تُعرض للـ ADMIN بالبيانات الحقيقية | COMMAND OUTPUT: لقطات `admin-desktop-admin*.png` (12 صف، 3 مشاهدات لـ YR-0011 = `events=3`) |

### 🟡 موجود لكنه جزئي
| العنصر | ما ينقص | الدليل |
|---|---|---|
| Saves | الحفظ يعمل؛ حدث `save` لا يُسجَّل (BUG-1)؛ `/saved` يسجّل view لكل بطاقة | CODE + COMMAND OUTPUT (POST بالـ UUID → 404) |
| Search page | SSR ثم إعادة جلب فورية (double fetch)؛ اختيار تصنيف يُسقط `q` والعكس | CODE `ReactionGrid` L38–41, `CategoryNav`, `SearchBar` |
| Collections cards | `collectionRepository` يحمّل `media.kind = PROCESSED` فقط (الـ pipeline ينتج WATERMARKED/THUMBNAIL) | CODE L7 |
| Categories counts | تشمل draft/archived | CODE `categoryRepository.findActive` |
| Featured | يُعرض؛ لا يمكن تغييره إلا بـ SQL/seed | CODE (0 مراجع في admin) |
| Submissions | الدورة كاملة؛ `keywords/sourceUrl` تُهمَل؛ لا تأكيد؛ لا إشعارات؛ لا تعديل قبل الاعتماد | CODE |
| Media pipeline | يعمل محليًا (216 خرج)؛ غير قابل للتشغيل في الإنتاج | CODE + `.storage` + INFERENCE عن Vercel |
| Admin | CRUD كامل؛ بلا KPIs/pagination/Featured/Users/Audit viewer؛ BottomNav يتداخل على الموبايل | CODE + لقطة `admin-mobile-admin.png` |
| Reaction detail | كل الإجراءات موجودة؛ Share بلا fallback على الديسكتوب؛ Download بلا `Content-Disposition`؛ `<video muted>` ثابت؛ Related مبسَّطة (اقتباس فقط) | CODE |
| S3 driver | كود كامل؛ مختبر بـ mocks فقط | CODE + `tests/unit/storage-s3.test.ts` |
| Env validation | في dev تحذّر وتكمل بـ defaults غير آمنة (`AUTH_SECRET`, `IP_SALT`) | CODE `env.ts` |

### 🔴 موجود لكنه مكسور
| العنصر | العطل | الدليل |
|---|---|---|
| تتبّع save/download/share من الواجهة | العميل يرسل `reaction.id` (UUID)؛ الـ route يحلّ `[id]` كـ code → 404 صامت دائمًا | CODE + COMMAND OUTPUT (`POST /api/reactions/<uuid>/event` → 404) + DATABASE (events=3 كلها view) |
| Schema ↔ DB | 3 indexes في DB غير معرَّفة في `schema.prisma` → `migrate dev` القادم يقترح `DROP INDEX` (منها GIN البحث) | COMMAND OUTPUT (`prisma migrate diff`) |
| `processingStatus = processing` عالق | لا timeout؛ retry يقبل `failed` فقط؛ processor يرفض `processing` | CODE |
| seed `duration` | مُعرَّف في `REACTIONS[]` ولا يُكتب في `durationMs` → `dur: null` للـ 12 | CODE + DATABASE (`durationMs` NULL) |
| Media في الإنتاج | Vercel بلا ffmpeg؛ `LocalStorage` على قرص مؤقت؛ حد body 4.5MB مقابل قراءة 80MB في الذاكرة | INFERENCE (قيود Vercel معروفة) + CODE + DATABASE (media=0) |

### ⚪ مخطط فقط ولم يُنفَّذ
Settings · إدارة المستخدمين/الأدوار · Featured admin · AuditLog viewer · Search suggestions/recent/sort · صفحة `/categories` · Notifications · Rate limiting (عدا pending≤5) · CSP · `middleware.ts` · `loading.tsx` · favicon/robots/sitemap/manifest/OG · PWA · Job queue/worker خارجي · Range/HLS/CDN/signed URLs · Aggregation job · CI · git remote · Embedding search · تنظيف `.storage` اليتيم. (CODE: غياب تام)

---

## القسم 4 — Routes وواجهات المستخدم

مصدر القائمة: مخرجات `next build` (45 route) + curl ضد الـ build + قراءة الملفات. "الحالة" = ما رأيته فعليًا. (COMMAND OUTPUT + CODE)

### 4.1 صفحات (RSC)
| المسار | الوظيفة الحالية | الحالة | مستخدم فعليًا؟ | أهم المكوّنات |
|---|---|---|---|---|
| `/` | hero + banner(`?signin=required`) + `CategoryNav` + 8 جديد + `FeaturedStrip` + ≤3 مجموعات | ✅ 200 (TTFB ~1.4s أول طلب) | نعم | `page.tsx`, `SearchBar`, `CategoryNav`, `ReactionCard`, `FeaturedStrip`, `CollectionCard`, `GoogleSignInButton` |
| `/search` (`?q`, `?cat`) | SSR 24 نتيجة + شبكة لا نهائية | ✅ 200 | نعم | `(site)/search/page.tsx`, `ReactionGrid`, `useReactions` |
| `/r/[slug]` | تفاصيل بالـ code؛ **لا يسجّل view** | ✅ 200 / 404 | نعم | `ReactionDetail` |
| `/collections` | فهرس المجموعات النشطة | ✅ 200 | نعم | `CollectionCard`, `EmptyState` |
| `/collections/[slug]` | مجموعة واحدة (published فقط) | ✅ 200 / 404 | نعم | `ReactionCard` |
| `/saved` | shell + client island يجلب كل code | ✅ 200 | نعم | `SavedReactionsClient`, `SavesProvider` |
| `/submit` | `requireUserOrRedirect` → فورم | ✅ 307 (guest) / 200 (user) | نعم | `SubmissionForm` |
| `/submissions` | إرسالات المستخدم | ✅ 307 / 200 | نعم | — |
| `/admin` | لوحة 4 بطاقات | ✅ 307 / 403-page / 200 | نعم | `admin/layout.tsx` |
| `/admin/reactions` | جدول ≤200 + بحث/فلتر | ✅ | نعم | `ReactionStatusButton`, `ArchiveReactionButton` |
| `/admin/reactions/new` | إنشاء | ✅ | نعم | `ReactionForm` |
| `/admin/reactions/[code]/edit` | تعديل + وسائط | ✅ | نعم | `ReactionForm`, `ReactionMedia` |
| `/admin/categories`, `/new`, `/[slug]/edit` | CRUD | ✅ | نعم | `CategoryForm`, `TaxonomyToggle` |
| `/admin/collections`, `/new`, `/[slug]/edit` | CRUD + عناصر | ✅ | نعم | `CollectionForm`, `CollectionItems` |
| `/admin/submissions` (`?status=`) | طابور | ✅ | نعم (فارغ في الإنتاج) | — |
| `/admin/submissions/[code]` | تفاصيل + إجراءات | ✅ (بالكود؛ لا بيانات لاختباره في الإنتاج) | نعم | `SubmissionActions` |
| `/_not-found` | 404 مخصص | ✅ | نعم | `not-found.tsx` |
| `error.tsx` | error boundary عام | لم أُثِر خطأً لاختباره | — | — |

### 4.2 Route Handlers
| المسار | Methods | Auth | الحالة (curl) | ملاحظة |
|---|---|---|---|---|
| `/api/health` | GET | — | 200 | لا يفحص DB |
| `/api/categories` | GET | — | 200 | — |
| `/api/reactions` | GET | — | 200 | zod: cat/q(≤200)/limit(≤100)/cursor |
| `/api/reactions/[id]` | GET | — | 200/404 | `[id]`=code؛ **يسجّل view** |
| `/api/reactions/[id]/event` | POST | — | 404 بالـ UUID (ما ترسله الواجهة) | `[id]`=code؛ لم أرسل بالـ code كي لا أكتب Event |
| `/api/collections`, `/[slug]` | GET | — | 200 | — |
| `/api/featured` | GET | — | 200 | لا مستهلك UI |
| `/api/auth/[...nextauth]` | GET/POST | — | `providers` → `{}` محليًا؛ `session` → `null` | Google غير مهيَّأ محليًا |
| `/api/me/saves`, `/[id]` | GET/POST · DELETE | user | 401 guest / 200 user | codes |
| `/api/submissions` | GET/POST | user | 401 guest | multipart، pending≤5 |
| `/api/admin/reactions`, `/[id]`, `/[id]/media`, `/[id]/media/[mediaId]` | GET/POST · PATCH/PUT/DELETE · GET/POST · DELETE/PATCH | admin | 401 guest / 403 user / 200 admin (GET فقط جُرِّب) | — |
| `/api/admin/submissions`, `/[code]` | GET · GET/PATCH/POST | admin | 401/403/200 (GET) | approve gate |
| `/api/admin/categories`, `/[slug]` | GET/POST · PATCH | admin | لم أختبرها بطلب | — |
| `/api/admin/collections`, `/[slug]`, `/[slug]/items`, `/[slug]/items/[reactionCode]` | GET/POST · GET/PATCH · POST/PUT · DELETE | admin | لم أختبرها بطلب | — |
| `/media/[...key]` | GET | — | 200 / 404 | لا Range؛ MIME من الامتداد؛ يبث أي مفتاح بما فيه `submissions/*` |

**تحذير من الأسماء:** `/api/reactions/[id]` و`/api/admin/reactions/[id]` تستقبل **code** لا id؛ `/api/me/saves/[id]` تستقبل **code** أيضًا. (CODE)

---

## القسم 5 — Architecture

### 5.1 المخطط المستهدف (كما في `docs/ARCHITECTURE.md` و ADR-0003) مقابل الفعلي

```
المستهدف:  UI → Components → Routes/API → Services/Controllers → Repositories → Prisma → PostgreSQL

الفعلي — مسار القراءة العام:
  RSC pages / client islands → (fetch) /api/{reactions,categories,collections,featured}
     → catalogService → {reaction,category,collection,event}Repository → prisma → Neon   ✅ طبقات واضحة

الفعلي — كل ما عدا ذلك (saves, submissions, admin/*, صفحات admin و submit/submissions):
  RSC page أو route handler → requireUser/requireAdmin → prisma مباشرةً (+ lib/admin/* للتحقق فقط) → Neon
     ⟹ لا service ولا repository. منطق الأعمال داخل الـ handler.
```

### 5.2 أين الطبقات واضحة (CODE)
- `src/lib/services/catalogService.ts` + `src/lib/repositories/*` + `toReactionDTO` — عقد DTO واحد للواجهة العامة.
- `src/lib/http.ts` + `src/lib/errors/AppError.ts` — أخطاء موحَّدة في 23 handler.
- `src/lib/auth/{config,index,guards,users}.ts` — مصادقة/تفويض معزولان.
- `src/lib/storage/*` و`src/lib/media/*` — تجريدات حقيقية بواجهات.
- `src/lib/saves/{localStore,union,cloud}.ts` — منطق نقي مختبَر.

### 5.3 أين توجد استدعاءات Prisma مباشرة (CODE، عدّ بالملفات: 46 ملفًا تستورد `@/lib/db`)
- **صفحات RSC:** `submit/page.tsx`, `submissions/page.tsx`, كل `admin/**/page.tsx` (9 صفحات).
- **Route handlers:** كل `api/admin/**` (12 ملفًا)، `api/me/saves/*` (2)، `api/submissions` (1).
- **الـ processor** `lib/media/processor.ts` و`lib/admin/{reactions,submissions}.ts` (`nextCode`).
- **`catalogService.getFeaturedAndNew`** يستخدم `prisma.featured` مباشرة (خرق داخل الـ service نفسه).

### 5.4 مسؤوليات متكررة (CODE)
| المسؤولية | التكرار |
|---|---|
| حلّ اسم التصنيف للإرسال (لا relation) | `admin/submissions/page.tsx`, `admin/submissions/[code]/page.tsx`, `api/admin/submissions/route.ts`, `api/admin/submissions/[code]/route.ts` |
| `firstChar()` fallback للأفاتار | `AccountEntry`, `AccountMenu`, `SiteSidebar`, (+ inline في `admin/page.tsx`) |
| أيقونات SVG inline | Home ×3, Search ×2, Bookmark ×3, History ×2, Send ×3, Logout ×2, User ×2, Admin (شكلان مختلفان) |
| بلوك الهوية | `SiteSidebar` (`sidebar-user`), `AccountMenu` (`account-menu__identity`), `admin/page.tsx` (`admin-identity`) |
| زر Google | `AccountMenu`, `SiteSidebar` (نسختان: كاملة + أيقونة للوضع المضغوط), `page.tsx` banner, `SavedReactionsClient` |
| `safeExt`/`MIME_EXT` | `lib/admin/media.ts` و `lib/admin/submissions.ts` |
| `streamToBuffer` | `storage/local.ts`, `storage/s3.ts` |
| `nextReactionCode`/`nextSubmissionCode` (قراءة كل الصفوف ثم max) | `lib/admin/reactions.ts`, `lib/admin/submissions.ts` |
| `getCurrentUser()` لكل طلب صفحة | `layout.tsx` + `SiteHeader.tsx` + `page.tsx` = 3 استعلامات `User` متطابقة (لا `React.cache`) |

### 5.5 Technical debt (CODE)
- `components.css` ملف واحد 2682 سطرًا، يحمل تعليقات مراحل 6B→6L متراكبة.
- 44 ملفًا `force-dynamic`؛ لا caching من أي نوع.
- Worker in-process (`enqueueProcessing` = `void promise`) — لا queue، لا retry تلقائي، لا lease.
- الرفع يقرأ الملف كاملًا في الذاكرة (`file.arrayBuffer()` حتى 80MB).
- `ensureWatermarkFile()` يكتب إلى `./.storage/watermark/qs.png` **بغض النظر عن `STORAGE_DRIVER`**.
- `admin/layout.tsx` يخفي الـ sidebar بـ `<style>` inline و`!important`.
- `SubmissionForm` يقرأ الملف عبر `document.getElementById` بدل ref.
- بقايا schema (القسم 6).

### 5.6 الأجزاء التي أعتبرها سليمة (CODE + COMMAND OUTPUT) — تقييم تقني، ليس قرارًا
`auth/guards.ts` + `getCurrentUser` (الدور من DB دائمًا) · `reactionRepository.search/browse` (keyset مركَّب صحيح) · `SavesProvider` + `lib/saves/*` · `media/processor.ts` + `ffmpeg.ts` (argv، حالات صريحة، transaction، audit) · `media/watermark.ts` (بلا تبعيات) · `storage/*` interface · `AppError/http` · `AccountMenu` (a11y + portal) · صرامة TS (`strict` + `noUncheckedIndexedAccess`) · تغطية unit للطبقات النقية.

---

## القسم 6 — Database (قراءة فقط — لم يُعدَّل شيء)

### 6.1 Models (15) و Enums (7) — `prisma/schema.prisma` (CODE)
`User`, `Session`, `OneTimeCode`, `Category`, `ReactionKeyword`, `Reaction`, `MediaAsset`, `Collection`, `CollectionItem`, `Featured`, `Submission`, `SavedReaction`, `Event`, `AuditLog`, `Setting`.
Enums: `UserRole(USER, EDITOR, ADMIN)`, `ReactionStatus(draft, published, archived)`, `MediaKind(ORIGINAL, PROCESSED, THUMBNAIL, WATERMARKED)`, `MediaProcessingStatus(idle, processing, done, failed)`, `MediaRole(VIDEO, IMAGE, SUBTITLE)`, `SubmissionStatus(pending, approved, rejected)`, `EventType(view, save, download, share)`.

### 6.2 أهم العلاقات (CODE)
- `Reaction` 1→N `ReactionKeyword` (Cascade), `MediaAsset` (SetNull), `CollectionItem` (Cascade), `SavedReaction` (Cascade), `Event` (Cascade); 1→0..1 `Featured` (SetNull); N→1 `Category`.
- `User` 1→N `SavedReaction`, `Submission` (SetNull), `AuditLog` (SetNull), `Session` (Cascade).
- `MediaAsset` N→0..1 `Reaction` **و** N→0..1 `Submission` (كلاهما nullable — الأصل يُنقل من Submission إلى Reaction عند الاعتماد بتحديث `reactionId` وتصفير `submissionId`).
- `Collection` 1→N `CollectionItem` (PK مركَّب `[collectionId, reactionId]`, `position`).
- **بلا relation** (نصوص عادية): `Submission.categoryId`, `Submission.reactionId`, `Submission.reviewedById`, `AuditLog.targetId`.

### 6.3 البيانات الموجودة حاليًا (DATABASE — Neon, 2026-09-02, قبل وبعد التدقيق متطابقة)
```
User=2 (ADMIN: hamdanaltawaf@gmail.com · USER: qnasly189@gmail.com) — كلاهما Google، 2026-08-29
Category=9 (كلها active)          Reaction=12 (كلها published، كلها من seed، durationMs=NULL)
ReactionKeyword=62                 MediaAsset=0
Collection=3 (students 3, group-chat 3, no-context 2) · CollectionItem=8
Featured{id:1} → YR-0001           Submission=0
SavedReaction=2 (كلاهما YR-0011: واحد لكل مستخدم)
Event=3 (كلها view، 2026-08-29..31)  AuditLog=0   Session=0   OneTimeCode=0   Setting=0
```
⟹ الإنتاج = محتوى seed فقط؛ لا فيديو؛ لم تُنفَّذ أي عملية إدارة عليه. (DATABASE)

### 6.4 Migrations (CODE + COMMAND OUTPUT)
| المجلد | المحتوى | مُتتبَّع في git؟ |
|---|---|---|
| `0001_init` | كل الجداول (348 سطر) | نعم |
| `0002_search_text` | `CREATE EXTENSION pg_trgm, unaccent`؛ دالة `yemreact_normalize()`؛ عمود `Reaction.searchText` + backfill؛ **3 indexes يدوية** | نعم |
| `0003_auth_google` | `User.name/image/emailVerified` (nullable) | **لا (untracked)** |
| `0004_media_processing` | enum `MediaProcessingStatus` + `MediaAsset.processingStatus` default idle | **لا (untracked)** |
| `migration_lock.toml` | **غير موجود** | — |
`prisma migrate status` ضد Neon: **"Database schema is up to date"** (4 migrations). (COMMAND OUTPUT)

### 6.5 Schema drift (COMMAND OUTPUT: `prisma migrate diff --from-url <neon> --to-schema-datamodel`)
```sql
DROP INDEX "Reaction_category_published_idx";
DROP INDEX "Reaction_published_status_idx";
DROP INDEX "Reaction_searchText_gin";
```
أي أن `schema.prisma` **لا يعرف** هذه الـ indexes الثلاثة؛ أي `prisma migrate dev` قادم سيقترح حذفها. الدالة `yemreact_normalize` والـ extensions أيضًا خارج الـ schema (طبيعي لـ Prisma 5). `prisma format --check` → غير منسَّق.

### 6.6 Indexes المعرَّفة في schema (CODE)
`User(email)`, `Session(userId)`, `OneTimeCode(userId), (email)`, `Category(active, sortOrder)`, `ReactionKeyword @@unique(reactionId, term), (term)`, `Reaction(status, publishedAt), (categoryId, status), (code)`, `MediaAsset(reactionId), (submissionId), (hash)`, `CollectionItem(collectionId, position)`, `Submission(status, createdAt), (userId)`, `SavedReaction(userId, createdAt)`, `Event(reactionId, type, createdAt), (createdAt)`, `AuditLog(action, createdAt), (targetType, targetId)`. + الثلاثة اليدوية أعلاه في DB فقط.

### 6.7 غير المستخدم (CODE: 0 مراجع في `src/`)
`Session`, `OneTimeCode`, `Setting` (models)؛ `UserRole.EDITOR` (بلا منطق)؛ `MediaRole.SUBTITLE`؛ `MediaKind.PROCESSED` كمخرج (يُقبل فقط برفع أدمن يدوي)؛ `Submission.contact`, `Submission.sessionId` (لا تُملأ)؛ `Reaction.savesCount/downloadsCount/sharesCount` (تُزاد عبر مسار معطَّل — BUG-1).

### 6.8 يبدو legacy (INFERENCE — استنتاج وليس حقيقة مثبتة)
`Session` + `OneTimeCode` + `ADMIN_EMAIL`/`SMTP_*` في env → بقايا تصميم OTP الوارد في ADR-0001 والـ MVP القديم (`arena.md` §9.2)، استُبدل بـ Google في "Phase 6A".

### 6.9 يحتاج قرارًا لاحقًا (لا أقرره)
- إبقاء/حذف models الميتة وenum values غير المستخدمة.
- إضافة relations لـ `Submission` (category/reaction/reviewer) أم لا.
- إعلان الـ indexes اليدوية في schema أم migration وهمية.
- هل يبقى `Featured` صفًّا واحدًا (`id=1`) أم يتعدد.
- سياسة `hash` للتكرار (العمود موجود، لا منطق يستخدمه).

---

## القسم 7 — Authentication / Authorization

| البند | الواقع (CODE ما لم يُذكر غيره) |
|---|---|
| Google OAuth | `next-auth/providers/google` يُضاف **فقط إذا** `AUTH_GOOGLE_ID && AUTH_GOOGLE_SECRET`. محليًا غائبان → `/api/auth/providers` = `{}` (COMMAND OUTPUT). على الإنتاج عمل (DATABASE: مستخدمان). |
| Login flow | `signIn("google")` من العميل → Auth.js → Google → `jwt` callback (`trigger === signIn/signUp`) → `findOrCreateGoogleUser` → `token.userId` → `session.user.id`. لا صفحة login؛ `pages.signIn: "/"`. |
| Session strategy | **JWT** (`session.strategy: "jwt"`) موقَّع بـ `AUTH_SECRET`. كوكي `authjs.session-token`. لا استخدام لـ model `Session`. |
| Roles | `User.role` ∈ USER/EDITOR/ADMIN. يُعيَّن **مرة واحدة** عند إنشاء الحساب: ADMIN إذا `email === HAMADAN_ADMIN_EMAIL` (default مضمَّن في `env.ts`: `hamdanaltawaf@gmail.com`)، وإلا USER. لا API/UI لتغييره. `EDITOR` = USER عمليًا. |
| Current user | `getCurrentUser()` = `auth()` + `prisma.user.findUnique` → الدور من DB **كل طلب** (لا يُثق بالـ JWT للتفويض). بلا `React.cache` → 3 مرات/طلب صفحة. |
| Admin protection | `admin/layout.tsx` RSC: `requireAdmin()` → 401 → `redirect("/?signin=required")`؛ 403 → مكوّن `AdminForbidden` (**HTTP 200**). كل `api/admin/**` handler يستدعي `requireAdmin()` بنفسه. **لا middleware.** (COMMAND OUTPUT: USER → 403 JSON على API، صفحة 403 على الويب) |
| User protection | `requireUserOrRedirect()` في `/submit`, `/submissions`؛ `requireUser()` في `/api/me/*`, `/api/submissions`. |
| Guest behavior | كل القراءة عامة. `/saved` يعمل محليًا. المسارات المحمية → 307 إلى `/?signin=required` → banner + زر Google في الرئيسية (فقط إن كان زائرًا). |
| Saves | Guest: `localStorage['yr:saved']` (codes). Authed: `GET /api/me/saves` → union → `POST` diff → optimistic toggles مع rollback؛ `DELETE /api/me/saves/[code]` مقيَّد بـ `userId`. localStorage لا يُمسح أبدًا (حتى عند logout). |
| Submission permissions | POST: user + pending<5؛ GET: صفوف المستخدم فقط؛ approve/reject/retry: admin. |
| Logout | `signOut()` بلا `callbackUrl` (يبقى في الصفحة). |

**تناقضات ومخاطر:**
1. `AUTH_SECRET` default `dev-only-insecure-secret-change-me` و`IP_SALT` default يمرّان في `NODE_ENV != production`؛ حالة Vercel **UNKNOWN**.
2. `?forbidden=1` يُضبط في `requireAdminOrRedirect` — الدالة غير مستخدمة والـ param لا يُعرض.
3. صفحة 403 بـ HTTP 200 (دلاليًا خاطئ؛ وظيفيًا يعمل).
4. `HAMADAN_ADMIN_EMAIL` بريد شخصي كـ default داخل الكود المصدري (`env.ts` L37).
5. E2E helper `tests/e2e/helpers/session.ts` يقرأ `AUTH_SECRET` من `.env` ويصنع كوكي JWT صالحًا — أي من يملك `.env` يصنع جلسة لأي مستخدم (طبيعي لـ JWT، لكنه يؤكد حساسية `AUTH_SECRET`).
6. ADR-0001 يقول "signed, DB-backed sessions; OTP codes; no passwords" — الكود Google + JWT (CONFLICT، القسم 13).
7. `session.user.id` هو الشيء الوحيد في الـ JWT؛ لا `role` فيه (مقصود وموثَّق).

---

## القسم 8 — Media System

### 8.1 الخط الكامل كما هو مكتوب (CODE)
```
UPLOAD
  admin: POST /api/admin/reactions/[code]/media (multipart: file [,kind,role])
  user : POST /api/submissions (multipart: file + caption + situation + categoryId [+source,sourceUrl,keywords])
  ├─ buffer = Buffer.from(await file.arrayBuffer())          ⚠️ الملف كله في الذاكرة
VALIDATION  LocalMediaService.validate()
  ├─ MIME ∈ {video/mp4, video/quicktime, video/webm}
  ├─ 2 KB < size ≤ MEDIA_MAX_BYTES (default 80 MB)
  └─ magic bytes: "ftyp" | "webm" | "matroska" | "moov" في البايتات 4..12
STORE ORIGINAL
  ├─ key = reactions/<reactionId>/<uuid>.<ext> | submissions/<submissionId>/<uuid>.<ext>
  ├─ storage.put()  → LocalStorage (./.storage) أو S3Storage
  ├─ MediaAsset{kind ORIGINAL, role VIDEO, processingStatus idle, hash sha256}
  └─ AuditLog media.attach | submission.create
ENQUEUE  enqueueProcessing(assetId)  →  void processMediaAsset().catch(()=>{})   ⚠️ in-process, fire-and-forget
PROCESSING  processMediaAsset()
  ├─ guard: kind ORIGINAL && role VIDEO && status ∉ {processing, done}
  ├─ status → processing
  ├─ withTempDir → storage.getStream → temp file
  ├─ ffprobe -print_format json → width/height/durationMs/codec  (fail if no width/height)
  ├─ THUMBNAIL: ffmpeg -ss min(0.5, dur/2) -frames:v 1 -vf scale=480:-2 → <base>.thumb.jpg → storage.put
  ├─ WATERMARK: ensureWatermarkFile() → ./.storage/watermark/qs.png (يُولَّد برمجيًا من هندسة QussasaMark)
  │             ffmpeg -filter_complex "[1][0]scale2ref=w=iw*0.14:h=ow/mdar[wm][vid];[vid][wm]overlay=(W-w-16|16):H-h-16"
  │             -c:v libx264 -preset veryfast -crf 23 -pix_fmt yuv420p -c:a aac -b:a 96k -movflags +faststart -shortest
  │             → <base>.wm.mp4 → storage.put
  ├─ $transaction: createMany[THUMBNAIL(IMAGE, done), WATERMARKED(VIDEO, done, watermarked=true)]
  │                + ORIGINAL → done + metadata ; + Reaction.durationMs (إن كان مرتبطًا برياكشن)
  ├─ thumbnail sizeBytes backfill ; AuditLog media.process.done
  └─ catch → ORIGINAL → failed ; AuditLog media.process.failed   (الأصل لا يُمس)
PUBLIC DTO  toReactionDTO()
  ├─ video = pickPublicVideo: WATERMARKED > PROCESSED > ORIGINAL   ⚠️ يسقط إلى الأصل الخام
  ├─ thumb = pickPublicThumb: THUMBNAIL(IMAGE) > any IMAGE
  └─ url  = storage.getUrl(key) = NEXT_PUBLIC_SITE_URL + /media/<key> (local) | S3_PUBLIC_URL أو /media/ (s3)
DELIVERY  GET /media/[...key]
  ├─ getStorage().getStream(key) → Response(ReadableStream)
  ├─ Content-Type من الامتداد (mp4/m4v/mov/webm/jpg/jpeg/png/webp، وإلا octet-stream)
  ├─ Cache-Control: public, max-age=31536000, immutable
  └─ ❌ لا Range / 206 ; ❌ لا Content-Disposition ; ❌ لا تفويض (submissions/* قابلة للبث)
PLAYBACK  <video src poster muted playsInline controls>  ; DOWNLOAD <a href download target=_blank>
```

### 8.2 ما يعمل محليًا (CODE + `.storage` + unit tests)
- كل ما سبق نُفِّذ محليًا مرارًا: `.storage/` يحتوي **829 ملفًا / 11 MB**: 282 تحت `reactions/`، 546 تحت `submissions/`، **216 زوج `.wm.mp4` + `.thumb.jpg`**، و`watermark/qs.png`. (COMMAND OUTPUT: find/count)
- unit: `media-validation` (9), `media-processing` (10, processor بحالاته عبر mocks), `media-storage-agnostic` (2), `storage-s3` (11) — كلها ✅.
- integration `media-process.test.ts` (2) و e2e `admin-media*.spec.ts` (9) موجودة — **لم أشغّلها** (لا ffmpeg + تكتب في DB).

### 8.3 ما لا يعمل على Vercel (INFERENCE — استنتاج وليس حقيقة مثبتة، مبني على قيود Vercel المعروفة + CODE)
- `spawn("ffmpeg")` → ENOENT (لا ffmpeg في runtime الـ functions) → كل أصل يصبح `failed`.
- `LocalStorage` يكتب إلى `./.storage` على نظام ملفات مؤقت/للقراءة فقط؛ `/media/<key>` لن يجد الملفات بعد cold start.
- `ensureWatermarkFile` يكتب إلى `./.storage` حتى مع `STORAGE_DRIVER=s3`.
- حد جسم الطلب لـ Serverless Functions (≈4.5 MB) مقابل قراءة حتى 80 MB في الذاكرة.
- المعالجة بعد إرسال الرد (`void promise`) قد تُقتل عند انتهاء الـ invocation.
- **الدليل القاطع الوحيد الذي أملكه:** `MediaAsset = 0` في الإنتاج (DATABASE).

### 8.4 ما هو تجريد فقط
- `S3Storage` (كود كامل، مختبر بـ mocks فقط، لم يُشغَّل ضد MinIO/R2 حقيقي — UNKNOWN).
- `MediaService` interface + `MEDIA_DRIVER=service` (لا تنفيذ لـ "service").
- `MediaKind.PROCESSED` (لا مسار ينتجه).

### 8.5 نقاط محددة
| النقطة | الواقع |
|---|---|
| مشكلة ffmpeg | مطلوب في PATH؛ غائب في Vercel وفي بيئتي؛ الـ MVP القديم استخدم `ffmpeg-static` ثم أسقطه لأجل Termux (`arena.md` §8) |
| مشكلة storage | الافتراضي local؛ لا bucket مهيَّأ في أي env أراه؛ `S3_PUBLIC_URL` إن ضُبط يتجاوز `/media` |
| حجم الملفات | ≤80 MB (env)؛ ≥2 KB؛ لا حد للمدة/الأبعاد (الـ MVP كان يقيّد 1–12 ثانية) |
| streaming | `/media` يبث stream كامل؛ لا chunking بالطلب |
| Range requests | **غير مدعومة** → seek/scrub لن يعمل على iOS Safari وبعض المتصفحات؛ `preload="none"` على البطاقات يخفف الحمل فقط |
| watermark | Qussasa بلون `--paper` (#f3eae0)، 14% من العرض، أسفل-يمين (أو أسفل-يسار لـ `corner=tl`)، إزاحة 16px؛ **لا ظل** (الـ MVP القديم كان بظل مزدوج و11% أعلى-يمين — CONFLICT مع "مواصفات Brand v1.0" حسب `arena.md` §8.2) |
| processing states | `idle → processing → done | failed`؛ `failed → idle` عبر retry؛ **`processing` عالق بلا مخرج** |
| خطر نشر أصل غير معالَج | **حقيقي**: `pickPublicVideo` يسقط إلى `ORIGINAL`؛ رفع الأدمن المباشر **غير محمي** ببوابة watermark (البوابة على مسار submissions فقط). رياكشن منشور + معالجة فاشلة = بث الفيديو الخام بلا علامة. إضافة: `/media/submissions/<id>/<uuid>.mp4` يُبث لأي من يعرف المفتاح (الـ API يعيد `mediaUrl` للمرسِل). |

---

## القسم 9 — Admin

| المجال | ما يستطيعه اليوم عبر UI | Backend فقط (بلا UI) | غير موجود |
|---|---|---|---|
| **Reactions** | قائمة ≤200 + بحث (caption/situation/code) + فلتر تصنيف؛ إنشاء؛ تعديل كامل (+keywords, corner, durationMs, status)؛ toggle نشر/إخفاء؛ أرشفة بتأكيد (زر "حذف") | `GET /api/admin/reactions` JSON | حذف نهائي؛ استرجاع من الأرشيف بزر؛ pagination؛ bulk |
| **Categories** | إنشاء (slug/name/sortOrder)؛ تعديل (name/sortOrder/active)؛ تفعيل/تعطيل | `GET /api/admin/categories` | حذف؛ لون (مقفل على 9 slugs في CSS)؛ ترتيب بالسحب |
| **Collections** | إنشاء؛ تعديل؛ تفعيل/تعطيل؛ إضافة رياكشن **بالرمز**؛ إزالة؛ ↑/↓ | `PUT …/items` reorder بقائمة كاملة | بحث/اختيار رياكشن؛ غلاف؛ حذف |
| **Submissions** | tabs بالحالة؛ تفاصيل + وسائط + مشغّل WATERMARKED؛ اعتماد (gate)؛ رفض بسبب؛ إعادة اعتماد؛ إعادة معالجة failed | `GET /api/admin/submissions` | تعديل قبل الاعتماد؛ حذف؛ تعيين مراجع؛ فلتر بالمرسِل؛ عدّاد pending |
| **Media** | (داخل تعديل الرياكشن) رفع؛ قائمة بالحالة/الأبعاد/المدة؛ عرض (رابط)؛ حذف بتأكيد؛ إعادة معالجة؛ polling 2.5s | `POST …/media` يقبل `kind/role` (PROCESSED/THUMBNAIL/WATERMARKED/IMAGE/SUBTITLE) — الواجهة ترسل الافتراضي فقط | مكتبة وسائط مستقلة؛ معاينة مضمَّنة؛ اختيار thumbnail؛ تعيين "الأساسي" |
| **Users** | — | — | **كل شيء** (قائمة، أدوار، حظر) |
| **Featured** | — | **لا API أيضًا** (يُقرأ فقط في `catalogService`) | تعيين/إلغاء |
| **Audit** | — | يُكتب في 17 action (`reaction.*`, `media.*`, `submission.*`, `category.*`, `collection.*`) | قارئ/فلتر/تصدير |
| **Overview** | هوية المدير + 4 بطاقات روابط | — | KPIs، آخر نشاط، صحة الطابور |
| **Settings** | — | — | — |

(CODE؛ اللقطات `admin-desktop-*.png` تؤكد ما يُعرض.) في الإنتاج: `AuditLog = 0` → لم يُستخدم أي من هذا على الإنتاج (DATABASE).

---

## القسم 10 — Testing

### 10.1 ما شغّلته أنا (COMMAND OUTPUT، 2026-09-02)
| النوع | الأمر | النتيجة |
|---|---|---|
| Typecheck | `npx tsc --noEmit --incremental false` | ✅ 0 errors (151 ملف) — مرتان |
| Lint | `npx next lint` | ✅ 0 — مرتان (تحذير: الأمر deprecated في Next 16) |
| Prettier | `npx prettier --check .` | ✅ clean |
| Prisma | `prisma validate` ✅ · `prisma format --check` ⚠️ unformatted · `migrate status` ✅ up to date · `migrate diff` ⚠️ 3 DROP INDEX |
| Unit | `npx vitest run` | ✅ 18 files / 171 tests — مرتان (7.3s, 9.5s) |
| Build | `npx next build` | ✅ 45 routes — مرتان (`-NNUVUfT79dELqNDeosJV`, `LQDyL5606cnpY1T3jvFCd`) |
| E2E | `E2E_BASE_URL=… npx playwright test` على 7 specs: `account-entry, chrome-and-loading, collections, core-flow, discoverability, header, hero` | ✅ **94/94** (chromium + mobile-chrome). المحاولة الأولى فشلت 94/94 بـ `libnspr4.so` مفقودة → حُلّت بـ `playwright install-deps` (بيئة، لا تطبيق) |
| Visual | 47 لقطة (زائر/مستخدم/مدير × 390/768/1024/1280/1440) + قياس `scrollWidth > clientWidth` | ✅ 0 overflow في كل الحالات |
| HTTP | curl على 29 مسارًا (guest) + 10 (user/admin بجلسات JWT محلية لمستخدمين موجودين) | مطابق للمتوقع (القسم 4) |

### 10.2 ما هو موجود ولم أشغّله
- **Integration (94):** `admin-api(8), admin-crud(12), admin-media(12), admin-taxonomy(15), auth-google(3), media-process(2), pagination(4), reactions.api(18), saves-api(11), submissions(9)` — تعمل على `DATABASE_URL` مباشرة وتُنشئ/تحذف صفوفًا. القاعدة الوحيدة المتاحة = الإنتاج → **لم أشغّلها**.
- **E2E المتبقية (11 spec ≈ 30 اختبار):** `account-menu, admin-crud, admin-media-process, admin-media, admin-taxonomy, admin, redesign, saved-sync, saves, sidebar, submissions` — تستخدم `helpers/session.ts` (يُنشئ users في DB) و/أو تنقر حفظ (يكتب Event) و/أو تحتاج ffmpeg.
- `test-results/.last-run.json` = `passed` — لكن **لا يسجّل أي subset نُفِّذ**؛ لا تعتبره دليلًا على اجتياز الـ 124.

### 10.3 اختبارات مضللة / متناقضة / خطرة ⚠️
1. **تناقض BUG-1:** `tests/unit/event-route.test.ts` يثبت أن `POST /api/reactions/:id/event` يحلّ `:id` كـ **code** ويرفض غيره بـ 404؛ `tests/unit/reaction-save.test.ts` يثبت أن `ReactionCard` يرسل **`REACTION.id` (UUID)**. كلاهما يمرّ، ومعًا يثبتان أن الميزة معطَّلة في الواقع. لا يوجد اختبار يغطي المسار من الطرف إلى الطرف.
2. **كل integration + 11 e2e تكتب في `DATABASE_URL`** — و`.env.local` يحمل Neon الإنتاج ويُحمَّل تلقائيًا بـ `next start/dev` و`prisma`. تشغيل `npm run test:integration` كما هو = كتابة في الإنتاج.
3. `playwright.config.ts` يرمي خطأ إن غاب `DATABASE_URL`/`E2E_BASE_URL` — لكنه لا يمنع كونه الإنتاج.
4. `tests/e2e/helpers/session.ts` يقرأ `AUTH_SECRET` من `.env` ويُنشئ مستخدمين بأدوار عبر Prisma مباشرة (`upsertTestUser`) — قد يترك صفوفًا إن فشل التنظيف.
5. `SavedReactionsClient` في E2E يسجّل views حقيقية (لم تظهر في قياساتي لأن `headlesschrome` مُفلتر كبوت في `eventService`، لكن متصفحًا حقيقيًا سيسجّل).
6. `api/health` يعيد 200 بلا فحص DB — لا يكشف انقطاع القاعدة.
7. `env.ts` في وضع test/dev يبتلع غياب `DATABASE_URL` بتحذير — الاختبارات تطبع `[env] Missing…` وتستمر.

---

## القسم 11 — الأخطاء والمخاطر

الحقول: **ID · المشكلة · مكانها · سببها · الأثر · هل ثبتت؟ · نوع القرار**

### P0 — يمنع الاستمرار
| ID | المشكلة | مكانها | سببها | الأثر | ثبتت؟ | قرار |
|---|---|---|---|---|---|---|
| P0-1 | كل عمل Phase 6 غير ملتزَم؛ commit واحد؛ لا remote | Git | لم يُلتزَم منذ 2026-08-24 | خطر فقدان 147 ملفًا؛ لا نقطة رجوع؛ لا تاريخ | ✅ COMMAND OUTPUT | هندسي (تنفيذ) — لكن **من ينفّذ** قرار مالك |
| P0-2 | لا مسار إنتاجي للوسائط (ffmpeg/storage/حد body/worker) | `lib/media/*`, `lib/storage/index.ts`, Vercel | بنية Serverless لا تناسب التصميم الحالي | المنتج لا يستطيع نشر فيديو | ✅ DATABASE (media=0) + INFERENCE (قيود Vercel) | **منتج + هندسي** (خيار البنية التحتية يكلّف) |
| P0-3 | بيئة التطوير/الاختبار = قاعدة الإنتاج | `.env.local` | `vercel env pull` | أي integration test أو تجربة محلية تكتب في الإنتاج | ✅ CODE + COMMAND OUTPUT | هندسي |

### P1 — خطر كبير
| ID | المشكلة | مكانها | سببها | الأثر | ثبتت؟ | قرار |
|---|---|---|---|---|---|---|
| P1-1 | أحداث save/download/share لا تُسجَّل | `ReactionCard.tsx` L27, `ReactionDetail.tsx` L40/51 ↔ `api/reactions/[id]/event/route.ts` L23–27 | العميل يرسل UUID، الـ route يحلّ code | عدادات savesCount/downloadsCount/sharesCount = 0 للأبد | ✅ COMMAND OUTPUT (404) + DATABASE | هندسي |
| P1-2 | بث ORIGINAL بلا علامة عند فشل معالجة رياكشن أدمن منشور | `lib/media/public.ts` L15–20؛ `api/admin/reactions/[id]/media/route.ts` | fallback صريح + لا gate على مسار الأدمن | تسريب محتوى خام يخالف "لا ملف بدون هوية" | ✅ CODE (المسار كامن؛ لم يحدث لعدم وجود وسائط) | **منتج** (سياسة) + هندسي |
| P1-3 | Schema drift: 3 indexes خارج `schema.prisma` | `prisma/schema.prisma` ↔ `0002_search_text` | indexes يدوية في SQL | `migrate dev` القادم يقترح حذف GIN البحث | ✅ COMMAND OUTPUT | هندسي |
| P1-4 | `processing` عالق بلا مخرج | `processor.ts` L40, `…/media/[mediaId]/route.ts` L84 | worker in-process بلا timeout؛ retry لـ failed فقط | أصل لا يُعالَج إلا بـ SQL | ✅ CODE | هندسي |
| P1-5 | `/media/submissions/*` قابل للبث بلا تفويض | `app/media/[...key]/route.ts` | لا فحص للمسار | تسريب محتوى قيد المراجعة لمن يعرف المفتاح | ✅ CODE | **منتج** (سياسة خصوصية) + هندسي |
| P1-6 | `AUTH_SECRET`/`IP_SALT` defaults غير آمنة | `lib/env.ts` L30, L44 | zod default | إن لم تُضبط في Vercel → جلسات قابلة للتزوير | ⚠️ الكود ثابت؛ حالة Vercel **UNKNOWN** | هندسي + تحقق من المالك |
| P1-7 | لا بيئة اختبار معزولة ولا CI | — | — | 124 اختبارًا غير قابلة للتشغيل بأمان؛ تناقضات لا تُكتشف | ✅ INFERENCE من P0-3 + غياب `.github/` | هندسي |
| P1-8 | الرفع يقرأ الملف كاملًا في ذاكرة function | `api/submissions/route.ts` L72, `…/media/route.ts` L100 | `file.arrayBuffer()` | فشل الرفع على Vercel قبل الوصول للكود (حد body) | ✅ CODE + INFERENCE | هندسي |

### P2 — مهم
| ID | المشكلة | مكانها | سببها | الأثر | ثبتت؟ | قرار |
|---|---|---|---|---|---|---|
| P2-1 | Collections تحمّل `PROCESSED` فقط | `collectionRepository.ts` L7 | include قديم | بطاقات المجموعات بلا فيديو/صورة | ✅ CODE | هندسي |
| P2-2 | seed بلا `durationMs` | `prisma/seed.ts` L169–190 | حقل لم يُمرَّر | شارة المدة غائبة للـ 12 | ✅ CODE + DATABASE | هندسي |
| P2-3 | `keywords`/`sourceUrl` تُهمَل في الإرسال | `api/submissions/route.ts` L82–93؛ schema | لا أعمدة على Submission | الرياكشن المعتمد بلا كلمات بحث | ✅ CODE | **منتج** (هل يُسمح للمرسِل بها؟) + هندسي |
| P2-4 | 3× `getCurrentUser()` لكل طلب | `layout.tsx`, `SiteHeader.tsx`, `page.tsx` | لا `cache()` | 3 استعلامات متطابقة | ✅ CODE | هندسي |
| P2-5 | double fetch على `/search` | `ReactionGrid.tsx` L38–41 | effect عند mount | طلب زائد + وميض | ✅ CODE | هندسي |
| P2-6 | `/saved` يسجّل view لكل بطاقة + N طلبات | `SavedReactionsClient.tsx` L28 | يستدعي endpoint التفاصيل | تضخيم viewsCount | ✅ CODE | هندسي |
| P2-7 | لا `generateMetadata` لـ `/r/[slug]` | `(site)/r/[slug]/page.tsx` | لم يُنفَّذ | كل الرياكشنات بنفس العنوان؛ لا OG | ✅ CODE | هندسي (المحتوى: منتج) |
| P2-8 | اختيار تصنيف يُسقط `q` والعكس | `CategoryNav.tsx` L31, `SearchBar.tsx` L29 | روابط تحمل param واحدًا | تجربة بحث مجزأة | ✅ CODE | **منتج** (سلوك) |
| P2-9 | Share بلا fallback؛ Download بلا `Content-Disposition`؛ `muted` ثابت | `ReactionDetail.tsx`, `media/[...key]/route.ts` | — | إجراءات لا تعمل على الديسكتوب/تفتح تبويبًا | ✅ CODE | منتج + هندسي |
| P2-10 | BottomNav يبقى فوق صفحات الأدمن (موبايل) | `admin/layout.tsx` (يخفي sidebar فقط) | — | يغطي المحتوى | ✅ لقطة | منتج (هل الأدمن على الموبايل مدعوم؟) |
| P2-11 | لا Range في `/media` | `media/[...key]/route.ts` | — | seek لا يعمل على iOS | ✅ CODE | هندسي |
| P2-12 | تصنيف جديد بلا لون | `tokens.css` (9 متغيرات ثابتة) | ألوان بالـ slug | chips/بطاقات بلا لون | ✅ CODE | **منتج** (هل التصنيفات مفتوحة أم مقفلة على 9؟) |
| P2-13 | `?sent=1`, `?forbidden=1` بلا UI | `submissions/page.tsx`, `guards.ts` | لم يُنفَّذ | لا تأكيد/لا رسالة | ✅ CODE | منتج (النص) + هندسي |
| P2-14 | 4 أسماء لوجهة `/search`؛ 4 مداخل لـ `/collections`؛ أيقونتان للإدارة | `SiteSidebar`, `BottomNav`, `page.tsx`, `AccountMenu` | قرارات IA متفرقة | ارتباك تنقّل | ✅ CODE + لقطات | **منتج (IA)** |

### P3 — تحسين لاحق
| ID | المشكلة | مكانها | ثبتت؟ | قرار |
|---|---|---|---|---|
| P3-1 | orphans: `lib/constants/reactions.ts`, `requireAdminOrRedirect`, `api.featured/collections/categories`, `rankMatch` (tests only)، env vars ميتة | src | ✅ CODE | هندسي |
| P3-2 | `agent/`, `.agents/`, `skills-lock.json` داخل المستودع | جذر | ✅ | هندسي |
| P3-3 | `components.css` أحادي؛ ~40 SVG مكرَّرة؛ `firstChar` ×3 | styles/components | ✅ | هندسي |
| P3-4 | `nextCode()` O(n)؛ admin `take: 200` | lib/admin | ✅ | هندسي |
| P3-5 | README/ADR/docblocks قديمة (القسم 13) | docs | ✅ | هندسي (توثيق) |
| P3-6 | `prisma format`؛ `migration_lock.toml`؛ `next lint` deprecated؛ Prisma 5→6 | tooling | ✅ | هندسي |
| P3-7 | لا favicon/robots/sitemap/manifest/OG | app | ✅ | منتج (الأصول) + هندسي |
| P3-8 | Featured/Users/Audit بلا UI | admin | ✅ | **منتج (أولوية)** |
| P3-9 | `.storage` 829 ملفًا اختباريًا بلا تنظيف | `.storage` (gitignored) | ✅ | هندسي |
| P3-10 | Related كنسخة مبسَّطة؛ Hero copy "temporary" | components | ✅ | منتج |

---

## القسم 12 — Git وبيئة المشروع (COMMAND OUTPUT، لا mutation)

| البند | القيمة |
|---|---|
| branch | `master` (الوحيد؛ لا فروع أخرى محلية ولا remote) |
| commits | **1** — `331c1b327e87c34a2354afd396e1ba1cc1e5ef1a` "feat: complete phase 5 core library polish" — 2026-08-24 03:42:07 +0000 — 80 ملفًا / +12873 |
| remote | **لا يوجد** (`git remote -v` فارغ) |
| working tree | **dirty** |
| modified (28) | `.env.example`, `.gitignore`, `.prettierignore`, `package-lock.json`, `package.json`, `playwright.config.ts`, `prisma/schema.prisma`, `src/app/(site)/search/page.tsx`, `src/app/globals.css`, `src/app/layout.tsx`, `src/app/page.tsx`, `src/components/layout/{CategoryNav,SearchBar,SiteFooter,SiteHeader}.tsx`, `src/components/reactions/{FeaturedStrip,ReactionCard,ReactionDetail}.tsx`, `src/lib/env.ts`, `src/lib/media/local.ts`, `src/lib/repositories/reactionRepository.ts`, `src/lib/storage/{index,local,types}.ts`, `src/styles/components.css`, `tests/e2e/{chrome-and-loading,core-flow}.spec.ts`, `vitest.config.ts` — إجمالي +4183/−572 |
| untracked (119 كود + 40 لقطة) | `prisma/migrations/0003_*`, `0004_*`; `src/app/(site)/{collections/page,saved/page}.tsx`; `src/app/{admin,submit,submissions,media}/**`; `src/app/api/{admin,auth,me,submissions}/**`; `src/components/{account,admin,providers,saves,submissions}/**`; `src/components/layout/{BottomNav,HeaderShell,SiteSidebar}.tsx`; `src/lib/{admin,auth,saves}/**`; `src/lib/media/{ffmpeg,processor,public,watermark}.ts`; `src/lib/storage/s3.ts`; `src/types/next-auth.d.ts`; 16 e2e specs + helper; 8 integration; 11 unit; `docs/phase-6{b..l}-shots/`; `agent/`, `.agents/`, `skills-lock.json` |
| ignored لكنه موجود | `.env`, `.env.local`, `.env.vercel`, `.vercel/`, `.storage/` (829 ملفًا), `test-results/`, `tsconfig.tsbuildinfo`, `next-env.d.ts` |
| stash | 0 |
| فروع مهمة | لا توجد |
| **النسخة المرجعية الحالية** | **working tree الحالي كما هو** (وليس `331c1b3`): هو الوحيد الذي يحتوي auth/admin/media/submissions وهو ما بُني ونُشر (INFERENCE: الإنتاج يحتوي مستخدمي Google ↔ الكود عند `331c1b3` لا يحتوي auth). لا يمكن استرجاع أي "Phase 6X" بعينها — كلها متراكبة. |

**تحذير:** `.gitignore` المعدَّل يحتوي `.env*` — أي `git add -A` مستقبلي سيتجاهل `.env.example` الجديدة إن أُعيد إنشاؤها (الحالية مُتتبَّعة فلا تتأثر).

---

## القسم 13 — تعارضات الوثائق مع الكود

| المصدر | يقول ماذا؟ | الكود يقول ماذا؟ | الحالة |
|---|---|---|---|
| `README.md` (repo) | "Phase 0 + Foundation… Not implemented yet: auth, admin, submissions, FFmpeg, R2" | كلها منفَّذة (Google auth, admin CRUD, submissions, ffmpeg pipeline, S3 adapter) | **OUTDATED** |
| `README.md` "Getting started: `prisma migrate dev --name init`" | migration اسمها init تُنشأ | يوجد `0001_init`…`0004` جاهزة | OUTDATED |
| `docs/ADR-0001` "Auth: signed, DB-backed sessions; OTP codes; no passwords" | OTP + DB sessions | Google OAuth + JWT؛ `Session`/`OneTimeCode` بلا استخدام | **CONFLICT** |
| `docs/ADR-0001` "Heavy work queued/backgrounded from Phase 9" | worker/queue | `void promise` in-process في "6H" | CONFLICT (جزئي) |
| `docs/ADR-0002` "counters updated by event service (or an aggregation job)" | aggregation | زيادة فورية فقط | OUTDATED (النصف الثاني) |
| `docs/ADR-0003` "Guest save and OTP-account flow (later phases)" | OTP | Google | CONFLICT |
| `docs/ARCHITECTURE.md` "Public routes are cacheable (`revalidate`)" | ISR/caching | 0 `revalidate`؛ 44 `force-dynamic` | **CONFLICT** |
| `docs/ARCHITECTURE.md` طبقات controller→service→repository | لكل شيء | مطبَّق للقراءة العامة فقط | CONFLICT (جزئي) |
| `src/lib/media/types.ts` docblock "FFmpeg implementation lands in Phase 9" | مستقبلي | منفَّذ (`local.ts`, `ffmpeg.ts`) | OUTDATED |
| `src/lib/media/index.ts` "A real FFmpeg/worker-based service replaces this in Phase 9" | مستقبلي | `LocalMediaService` هو التنفيذ الحقيقي | OUTDATED |
| `src/lib/session.ts` "Auth/sessions for users land in Phase 6" | مستقبلي | منفَّذ | OUTDATED |
| `src/app/page.tsx` docblock "submit CTA for signed-in users only" | زر إرسال في الهيرو | غير موجود | **CONFLICT** |
| `src/app/page.tsx` + `components.css` "title copy is temporary" | نص مؤقت | في الإنتاج | CURRENT (كما هو موثَّق) — يحتاج قرارًا |
| `src/components/layout/BottomNav.tsx` docblock "الرئيسية / البحث / إرسال رياكشن / الحساب" | 4 عناصر | مطابق | CURRENT |
| `src/components/layout/SiteHeader.tsx` docblock "Mobile: BottomNav (الرئيسية/البحث/المحفوظات/الحساب)" | المحفوظات في BottomNav | BottomNav فيه "إرسال رياكشن" لا "المحفوظات" | CONFLICT (تعليق قديم داخل نفس الدفعة) |
| `src/components/layout/SiteSidebar.tsx` "inspired by the Manus design" | مرجع خارجي | `uploads/SiteSidebar.tsx.txt` (مشروع wouter/tRPC) يحمل نفس التسميات ("استكشف"، "أحدث الرياكشنات"، `yemreact:sidebar-compact`) | CURRENT كمصدر إلهام؛ **UNKNOWN** من هو Manus |
| `.env.example` `MEDIA_WATERMARK_PATH=./src/assets/watermark.png` | ملف watermark | المجلد غير موجود؛ العلامة تُولَّد برمجيًا | OUTDATED |
| `.env.example` `MEDIA_DRIVER=local|service`, `SMTP_*`, `ADMIN_EMAIL` | خيارات | تُقرأ ولا تُستخدم | OUTDATED |
| `package.json` description "search engine" / `layout.tsx` "محرك بحث" | محرك بحث | hero/header/footer: "مكتبة رياكشنات يمنية" | **CONFLICT** (تعريف المنتج) |
| `ui-prototype/README.md` "النسخة المرجعية النهائية قبل أي تنفيذ على YemReact الحقيقي" | لا sidebar؛ تفاصيل modal؛ بحث في المكان + اقتراحات + ترتيب؛ BottomNav: الرئيسية/البحث/المجموعات/الحساب؛ `[+ إرسال]` في الهيدر؛ Settings 4 مفاتيح؛ Saved كـ sheet | sidebar 286px؛ صفحة `/r/`؛ بحث صفحة بلا اقتراحات؛ BottomNav: …/إرسال رياكشن/…؛ لا +؛ لا Settings؛ `/saved` صفحة | **CONFLICT** (شامل) |
| `ui-prototype/README.md` "الفئات = أداة فلترة؛ لا صفحة" | filter | مطابق (chips → `?cat=`) | CURRENT |
| `uploads/YemReact — Hybrid Technical Specification.md` | مشروع React 19 + Vite + Tailwind 4؛ `client/src/pages/Home.tsx`؛ `sort`, `lockedSection`, `ComingSoonOverlay`, suggestions | مستودع Next.js؛ لا Tailwind؛ لا sort؛ لا overlay؛ لا suggestions | **CONFLICT** (مشروع مختلف) |
| `uploads/*.tsx.txt`, `*.css`, `sha256sums.txt` | استخراج من `client/src/*` (wouter, tRPC, lucide, shadcn Sheet/Tooltip) | لا شيء منها في `yemreact-next` | مرجع لمشروع آخر — **UNKNOWN** علاقته الرسمية |
| `uploads/YemReact-Brand-v1.0-LOCKED.html` | tokens (ink #121214, paper #f3eae0, amber #c1592e…) | `src/styles/tokens.css` يطابق | **CURRENT** |
| `uploads/YemReact-Brand-v1.0-LOCKED.html` (حسب `arena.md` §8.2) watermark 11% أعلى-يمين بظل مزدوج | — | 14% أسفل-يمين بلا ظل (`ffmpeg.ts`) | **CONFLICT** — UNKNOWN أيهما المعتمد |
| `uploads/12-Final-Asset-Inventory.md` "Website / Product UI مؤجلان بقرار صريح" | UI مؤجل | UI موجود | OUTDATED (سياقه إطلاق Facebook) |
| `yemreact-app/arena.md` §16 "المنتج محرك بحث… ليس شبكة اجتماعية" + "المعرّفات YR-0001 للعرض فقط" + "Repository/Service/Controller" + "لا أسرار افتراضية" | مبادئ إلزامية | `code` للعرض ✅؛ الطبقات جزئية؛ defaults غير آمنة موجودة | جزئي: CURRENT/CONFLICT |
| `yemreact-app/arena.md` §8.2 حد المدة 1–12 ثانية؛ scale ≤1080؛ WebP thumb | قيود المعالجة | لا حد مدة؛ لا scale؛ JPEG 480 | CONFLICT (تصميم مختلف) |
| `yemreact-app/PHASE5.md` `POST /api/admin/featured` | API للمختار | لا يوجد | OUTDATED (MVP) |
| `yemreact-app/CONVERSATION.md` "لا Next.js ثقيل على 3G" | قرار معماري MVP | Next.js هو الأساس | CONFLICT (قرار عُكس لاحقًا — ADR-0001) |
| `screenshots-phase4/` (login-request, verify) | تدفق OTP | Google | OUTDATED |

**لا أحلّ أيًّا منها.**

---

## القسم 14 — تعارضات المشروع مع المشاريع/النسخ الأخرى

| المسار | ما هو | الحالة | التعامل المقترح (تقني) |
|---|---|---|---|
| `/home/user/yemreact-next` | Next.js 15 + Prisma + Neon — **المشروع الحالي** والمنشور على Vercel (INFERENCE من `.vercel/` + مستخدمي Google) | CURRENT | **المرجع الوحيد للكود** |
| `/home/user/yemreact-app` | MVP سابق: Node خالص، JSON DB (`data/mock-db.json`)، OTP، admin بكلمة سر، بلا ffmpeg (نسخة Termux)؛ وثائق غنية: `arena.md` (855 سطرًا: مراجعة شاملة + دروس + مبادئ)، `CONVERSATION.md`, `PHASE2–5.md`, `ARCHITECTURE.md` (يذكر SQLite — تناقض داخلي مع README الذي يقول JSON) | OLD — **مرجع قرارات/دروس فقط** | لا يُلمس؛ `arena.md` §8/§14/§16 قيّمة كمرجع |
| `/home/user/yemreact-web` | prototype ثابت (HTML/CSS/JS + data.js، 12 رياكشن mock، خطوط محلية) | OLD prototype | أرشيف |
| `/home/user/ui-prototype` | **Prototype v4 "Library-First"** — ملف واحد 78KB، 4 views + modal + sheets + settings + role switcher؛ يعلن نفسه المرجع النهائي | REFERENCE (تصميم/IA) — **يتعارض مع التنفيذ** | مرجع لقرار المالك؛ ليس كودًا يُنقل |
| `/home/user/uploads` | 33 ملفًا: Brand v1.0 LOCKED (HTML) + دليل الهوية + Social Design System + Content/Launch Kit (Facebook) + **Hybrid Technical Spec + استخراج UI من مشروع React/Vite/tRPC آخر** (`client/src/*`, 2026-08-31) + prompt العصف الذهني | REFERENCE مختلط: البراند = **CURRENT** (tokens تطابق)؛ الاستخراج = **مشروع مختلف** | البراند ملزم؛ الباقي مرجع؛ لا يُستورد منه كود |
| `/home/user/screenshots*` | لقطات MVP (Phase 0–5) | OLD | أرشيف |
| `/home/user/fonts` | Cairo/Lalezar ttf+woff2 | — | التطبيق يستخدم `next/font/google` — غير مستخدمة |
| `/home/user/audit-2026-09-02`, `/home/user/team` | مخرجاتي (تقارير، لقطات، تعريف) | CURRENT (مرجع تدقيق) | — |

**ما لا ينبغي لمهندس لاحق أن يلمسه:** `yemreact-app/` (لا تعديل — مرجع)، `uploads/` (أصول براند مقفلة + استخراج مرجعي)، `ui-prototype/` (بانتظار قرار)، `yemreact-next/.storage/` (بيانات اختبار محلية — لا تُرفع)، `yemreact-next/.env.local` (**إنتاج** — لا يُستخدم للتطوير)، أي شيء في قاعدة Neon بدون قرار.

---

## القسم 15 — UNKNOWN

كل بند أدناه: **UNKNOWN — لا أملك دليلًا كافيًا**

1. **من كتب Phase 0→6L** (أي وكيل/نموذج)، وهل سيستمر. الملخّص المحقون يقول "another language model".
2. **ما هو "Manus"** (وكيل؟ مصمم؟ مشروع؟) وعلاقة `uploads/client/src/*` بهذا المستودع رسميًا.
3. **من هو نِبراس** ودوره — أعرف الاسم من هذا الطلب فقط.
4. **رابط الإنتاج العام** على Vercel، وحالة النشر الحالية (هل آخر deploy من working tree الحالي؟ من أي commit؟ — لا remote يربط).
5. **متغيرات بيئة Vercel الفعلية**: `AUTH_SECRET`, `AUTH_GOOGLE_ID/SECRET`, `IP_SALT`, `STORAGE_DRIVER`, `S3_*`, `NEXT_PUBLIC_SITE_URL`, `HAMADAN_ADMIN_EMAIL` — `.env.vercel` المسحوب لا يحويها.
6. **هل يوجد bucket** (R2/S3/MinIO) مهيَّأ في أي مكان.
7. **ما إذا كان `S3Storage` يعمل ضد خدمة حقيقية** (لم يُختبر إلا بـ mocks).
8. **نتائج اختبارات التكامل (94) و11 spec E2E** — لم أشغّلها.
9. **هل يعمل خط ffmpeg الآن** في أي بيئة غير الجهاز الذي أنتج `.storage/` (216 خرجًا) — تاريخ تلك الملفات في صندوقي كلها `Sep 2 02:03` (وقت استعادة الصندوق) فلا أعرف متى أُنتجت فعلًا.
10. **الـ "independent experiment"** المذكور في الملخّص المبتور — لا أثر له في الملفات.
11. **دور حساب `qnasly189@gmail.com`** (مختبر؟ متعاون؟) وهل يُسمح باستخدام الإنتاج للتجارب.
12. **مواصفة العلامة المائية المعتمدة** (14% أسفل-يمين بلا ظل كما في الكود، أم 11% أعلى-يمين بظل كما في `arena.md`).
13. **هل التصنيفات مقفلة على 9** (كما توحي tokens والـ MVP) أم مفتوحة (كما يوحي admin CRUD).
14. **هل `yemreact-app/ARCHITECTURE.md` (SQLite/FTS5) يصف نسخة وسيطة لم تعد موجودة** — README المجاور يقول JSON.
15. **سلوك `error.tsx`** عمليًا (لم أُثِر خطأ خادم).
16. **الأداء تحت حمل** وحدود Neon pooler مع 44 مسارًا dynamic.
17. **إمكانية الوصول (a11y)** بمقياس آلي (لا axe) وقراءة الشاشة.
18. **هل الـ Google OAuth app في وضع Testing أم Production** في Google Console (يؤثر على من يستطيع تسجيل الدخول).
19. **هل توجد نسخ/فروع من المستودع خارج هذا الصندوق** (جهاز المالك، Vercel Git integration — `VERCEL_GIT_*` في `.env.vercel` كلها فارغة → INFERENCE: النشر عبر CLI لا عبر Git).
20. **التاريخ الفعلي لأحداث الملفات** — كل mtimes في الصندوق موحَّدة (استعادة snapshot).

---

## القسم 16 — NEEDS PRODUCT DECISION

لا تستطيع الهندسة حسم ما يلي:

1. **تعريف المنتج:** "محرك بحث عن رياكشنات" أم "مكتبة اكتشاف أولًا"؟ (الكود يحمل الاثنين؛ v4 يقول الثاني؛ `arena.md` يقول الأول).
2. **المرجع التصميمي الملزم:** التنفيذ الحالي (6L: sidebar + صفحات) أم `ui-prototype` v4 (لا sidebar + modal + بحث في المكان + settings) أم Hybrid Spec (مشروع آخر) — أم Blueprint جديد.
3. **بنية المعلومات (IA):** هل `/search` = "المكتبة"؟ اسم واحد لهذه الوجهة. مكان "الفئات" في التنقّل (filter فقط أم وجهة). عدد مداخل المجموعات. ماذا يحمل BottomNav (إرسال أم المجموعات).
4. **المصطلحات:** اعتماد «الفئات» بدل «التصنيفات» (20 موضعًا) — قرارك السابق يحتاج تثبيتًا في قاموس؛ «المكتبة/البحث/جديد المكتبة/عرض الكل/كل الرياكشنات».
5. **تفاصيل الرياكشن:** صفحة (SEO-friendly، رابط قابل للمشاركة) أم modal يحفظ المكان — أم الاثنان.
6. **Settings:** هل تُبنى، وما المفاتيح (v4: autoplay/صوت/توفير بيانات/حركة).
7. **سياسة الوسائط:** هل يُسمح أبدًا ببث `ORIGINAL`؟ هل رفع الأدمن يخضع لنفس watermark gate؟ حد المدة/الأبعاد؟ مواصفة العلامة (حجم/زاوية/ظل).
8. **خصوصية الإرسالات:** هل ملف المرسِل الخام يُخفى حتى الاعتماد؟ هل يرى المرسِل معاينة؟
9. **حقول الإرسال:** هل يقدّم المرسِل keywords/sourceUrl/description؟ هل يعدّلها الأدمن قبل النشر؟
10. **البنية التحتية للوسائط (تكلفة):** worker خارجي + R2/S3 + presigned upload، أم خدمة معالجة مُدارة، أم ترك Vercel.
11. **التصنيفات:** مقفلة على 9 بألوانها أم مفتوحة (وحينها نظام ألوان).
12. **الأدوار:** هل يُستخدم `EDITOR`؟ من يستطيع ترقية الأدمن؟ هل البريد المضمَّن في الكود مقبول.
13. **الإشعارات:** هل يُخطَر المرسِل بالنتيجة، وبأي قناة.
14. **Featured:** يدوي عبر admin (يحتاج UI) أم يُلغى.
15. **الأولويات:** ترتيب P0–P3 من منظور المنتج (خصوصًا: إصلاح الأخطاء الحالية أولًا أم Blueprint أولًا).
16. **نصوص الواجهة:** عنوان الهيرو "المؤقت"، رسائل التأكيد/الأخطاء، placeholder "الفيديو يُرفع في مرحلة لاحقة".
17. **سياسة المحتوى والاعتدال والحقوق** (takedown، مصدر الفيديو، `source/sourceUrl` إلزامية؟).
18. **مصير المشاريع الأخرى:** أرشفة `yemreact-app`/`yemreact-web` رسميًا؟ حالة `uploads/client-src` (مشروع Manus) — هل يُدمج أو يُهمل.
19. **Git:** من يملك المستودع البعيد وأين (GitHub؟)، وسياسة الفروع.

---

## القسم 17 — ما الذي يمكن الاحتفاظ به؟ (تقييم تقني محايد — ليس قرارًا)

### KEEP (يستحق البناء عليه)
- `src/lib/auth/{config,index,guards,users}.ts` + `src/types/next-auth.d.ts` — نموذج تفويض صحيح ومختبر.
- `src/lib/repositories/reactionRepository.ts` (browse/search/keyset) + `src/lib/search/normalize.ts` + migration `0002` (trgm + `yemreact_normalize`).
- `src/lib/saves/*` + `src/components/providers/SavesProvider.tsx` + `api/me/saves/*`.
- `src/lib/media/{processor,ffmpeg,watermark,public}.ts` — المنطق (يحتاج بيئة تنفيذ مختلفة، لا إعادة كتابة).
- `src/lib/storage/*` (interface + local + s3).
- `src/lib/errors/AppError.ts`, `src/lib/http.ts`, `src/lib/env.ts` (بعد تشديد defaults).
- `prisma/schema.prisma` كأساس (بعد تنظيف) + migrations 0001–0004.
- `src/components/account/AccountMenu.tsx` (a11y/portal/keyboard) و`QussasaMark.tsx` و`tokens.css` (Brand).
- الاختبارات: `tests/unit/*` (171) كلها؛ integration/e2e كأصول قيّمة **بعد** توفير بيئة معزولة.
- منطق admin API (`api/admin/**`) — صحيح وظيفيًا حتى لو احتاج طبقة service.

### REWORK (يستحق إعادة هيكلة)
- **تنفيذ** خط الوسائط: من in-process إلى worker/queue + presigned upload + storage عام؛ `ensureWatermarkFile` → temp dir؛ `/media` → Range أو URL مباشر + تفويض `submissions/*`.
- `components.css` → تقسيم/scoping؛ أيقونات → مكتبة واحدة؛ بلوك الهوية → مكوّن واحد.
- Shell التنقّل (`SiteSidebar`/`SiteHeader`/`BottomNav`) — سليم تقنيًا لكنه **رهن قرار IA**؛ يُعاد بناؤه على الـ Blueprint لا يُرمّم.
- طبقة admin/submissions: استخراج services من الـ handlers، relations لـ `Submission`، `nextCode` عبر sequence.
- `SavedReactionsClient` (batch endpoint)، `ReactionGrid` (double fetch)، `getCurrentUser` (`cache`).
- Event tracking (BUG-1) — إصلاح صغير لكنه يمس العقد بين العميل والـ API.
- الوثائق: README/ARCHITECTURE/ADR-0001 تُعاد كتابتها لتطابق الواقع (أو ADR جديد يوثّق الانحراف).

### REPLACE (قد يكون الأفضل استبداله)
- `enqueueProcessing()` (`void promise`) بآلية طابور حقيقية.
- `LocalStorage` كافتراضي للإنتاج → S3/R2 (يبقى للتطوير).
- قراءة الملف في الذاكرة (`arrayBuffer`) → رفع مباشر للتخزين.
- `next lint` → ESLint CLI (فرض Next 16)؛ Prisma 5 → 6 (تحديث مدروس، ليس عاجلًا).
- بقايا schema (`Session`, `OneTimeCode`, `Setting`, `EDITOR`, `SUBTITLE`) — حذف أو تفعيل بقرار.

### ARCHIVE (مرجع فقط)
- `yemreact-app/` (خصوصًا `arena.md` كسجل قرارات/دروس)، `yemreact-web/`, `screenshots*/`, `fonts/`.
- `ui-prototype/` (حتى صدور Blueprint)، `uploads/` (البراند ملزم كمرجع؛ الاستخراج مرجع لمشروع آخر).
- `docs/phase-6*-shots/` و`audit-2026-09-02/shots*` — توثيق بصري تاريخي.
- `.storage/` المحلي (بيانات اختبار؛ لا يُرفع).
- `agent/`, `.agents/`, `skills-lock.json` — ليست جزءًا من المنتج.

---

## القسم 18 — أهم ما يحتاجه المهندس القادم (أول 10 أشياء)

1. **الكود الحقيقي هو working tree، لا الـ commit.** `git log` يُظهر Phase 5 فقط؛ كل auth/admin/media/submissions **غير ملتزَمة**. لا تعمل `git checkout`/`stash`/`clean` قبل حفظ الحالة.
2. **`.env.local` = قاعدة الإنتاج.** `next dev`, `next start`, `prisma`, و`test:integration` كلها ستضربها. لا تشغّل اختبارات تكتب قبل توفير DB منفصلة.
3. **`[id]` في `/api/reactions/[id]`, `/api/admin/reactions/[id]`, `/api/me/saves/[id]` يعني code (`YR-0001`) لا UUID.** هذا سبب BUG-1 — والاختباران المتناقضان ينجحان معًا.
4. **الوسائط تعمل محليًا فقط.** ffmpeg مطلوب في PATH؛ `.storage/` محلي؛ الإنتاج بلا فيديو واحد. لا تفترض أن "الـ pipeline جاهز" يعني "الميزة تعمل".
5. **لا تشغّل `prisma migrate dev` قبل معالجة الـ drift** — سيقترح حذف GIN index البحث و2 indexes أخرى.
6. **ثلاثة مراجع تصميم متعارضة** (التنفيذ 6L / `ui-prototype` v4 / `uploads` Hybrid Spec لمشروع آخر). لا تنفّذ من أيٍّ منها قبل Blueprint معتمد من المالك. قرارات IA لا تُتخذ داخل docblocks.
7. **`README.md` و`docs/ADR-0001` و`ARCHITECTURE.md` قديمة.** الكود هو مصدر الحقيقة؛ ابدأ من تقريري التدقيق ثم الكود، لا من README.
8. **`ORIGINAL` يُبث للعامة إذا لم توجد نسخة موسومة** (`pickPublicVideo`)، وبوابة العلامة المائية تحمي مسار الإرسالات فقط لا رفع الأدمن. لا تنشر رياكشنًا بفيديو قبل التأكد من `WATERMARKED done`.
9. **الطبقات (service/repository) موجودة للقراءة العامة فقط.** كل admin/saves/submissions تستدعي Prisma مباشرة داخل الـ handlers — لا تبحث عن service غير موجود، ولا تضف واحدًا بلا خطة.
10. **الأدوار من قاعدة البيانات، وأول ADMIN يُعيَّن بمطابقة بريد مضمَّن في `env.ts`.** لا UI لتغيير الأدوار؛ `AUTH_SECRET` له default غير آمن — تحقق من Vercel قبل أي شيء يخص الحسابات.

---

## القسم 19 — علاقة التقرير بإعادة التأسيس

### ما يجب ألا نفترض أنه نهائي
- بنية الـ shell (sidebar/header/bottom nav) ومحتوى كل منها.
- تعريف المنتج ("محرك بحث" مقابل "مكتبة") ونص الهيرو ("مؤقت" بنص الكود).
- المصطلحات (التصنيفات/الفئات، المكتبة/البحث).
- كون التفاصيل صفحة، والمحفوظات صفحة، وعدم وجود Settings.
- ألوان التصنيفات المقفلة على 9 والعدد نفسه.
- مواصفة العلامة المائية (حجم/زاوية/ظل) وحدود الرفع.
- الاستمرار على Vercel + Neon بالشكل الحالي للوسائط.
- بقايا الـ schema (models/enums غير المستخدمة) وغياب relations على Submission.
- أي "قرار" مكتوب كتعليق داخل الكود ("أزلنا الزر لأنه ضجيج"، "نقلنا المحفوظات من BottomNav").
- ترقيم المراحل (0–5 MVP، 0–5 Foundation، 6A–6L، "Phase 9").

### ما يمكن أن نعتبره حقيقة تقنية حالية (مُثبَتة)
- Next 15.5.23 / React 19.2.8 / Prisma 5.22 / next-auth 5 beta.32 / Node 20؛ typecheck+lint+prettier نظيفة؛ 171 unit ✅؛ build ✅ 45 routes؛ 94 E2E عامة ✅. (COMMAND OUTPUT)
- Neon الإنتاج: 2 users (1 ADMIN)، 12 reactions seed بلا وسائط، 9 categories، 3 collections، 0 submissions، 0 audit، 3 view events. Migrations 4/4 مطبَّقة. Drift = 3 indexes. (DATABASE + COMMAND OUTPUT)
- Google OAuth عمل على الإنتاج مرة على الأقل؛ التفويض (401/403/307) يعمل كما هو موصوف. (DATABASE + COMMAND OUTPUT)
- خط الوسائط منطقيًا كامل ومختبر بالوحدات وأنتج 216 خرجًا محليًا؛ غير قابل للتشغيل في الإنتاج بالإعداد الحالي. (CODE + `.storage` + DATABASE)
- BUG-1 حقيقي (404 مُثبَت). Drift حقيقي. `.env.local` = إنتاج حقيقي. commit واحد بلا remote حقيقي. (COMMAND OUTPUT)
- Brand tokens في `tokens.css` تطابق `YemReact-Brand-v1.0-LOCKED.html`. (CODE + DOC)
- لا Settings، لا إدارة مستخدمين، لا Featured admin، لا suggestions، لا Range، لا middleware، لا CI. (CODE: غياب)

### ما يجب أن ينتظر قرارات إعادة التأسيس
- أي تعديل على الواجهة (IA، تسميات، shell، تفاصيل/modal، settings) — بانتظار الـ Blueprint.
- خيار البنية التحتية للوسائط (worker/queue/storage/CDN) — قرار تكلفة ومالك.
- سياسات: بث الأصل، خصوصية الإرسالات، حقول المرسِل، حد المدة، مواصفة العلامة، التصنيفات مفتوحة/مقفلة، الأدوار.
- تنظيف الـ schema والـ relations — بعد حسم السياسات أعلاه.
- مصير `ui-prototype` و`uploads/client-src` (Manus) و`yemreact-app` — تصنيف رسمي.
- إصلاح BUG-1 وأخواتها: تقنيًا واضح، لكن **ترتيبه** (قبل/بعد Blueprint) قرار أولوية.
- **ما لا يحتاج انتظارًا (تقنيًا بحت، لكنه ليس ضمن هذه المهمة):** حفظ الحالة في Git + remote، وفصل قاعدة التطوير عن الإنتاج — بدونهما كل ما بعدهما هش.

---

*نهاية التسليم. لم يُعدَّل أي ملف داخل `/home/user/yemreact-next`؛ HEAD `331c1b3`؛ 28 معدَّل / 119 غير مُتتبَّع كما كانت؛ لا commit؛ لا migration؛ لا كتابة في Neon؛ لا تغيير في Vercel. خادم المعاينة السابق (منفذ 3000) لم يعد يعمل (الصندوق أُعيد تشغيله).*
