# Nibras-Conversation

**الغرض:** حفظ سياق مشروع **YemReact** — ملفات التوثيق والقرارات عبر كل المراحل.
**التاريخ:** 2026-10-01
**المالك:** حمدان (@hamdanaltawaf-cpu)
**مُعد الحزمة:** أرينا (Arena Agent)

---

## حالة المشروع

| البند | الحالة |
|---|---|
| **المرحلة الحالية** | **Stage 5 — IA & Navigation** |
| **الموضوع الحالي** | 5.1 — Search Route (نقاش مفتوح) |
| **عدد الحقائق Canonical** | **79** (9 brand + 46 product + 6 IA + 10 technical + 8 security) |
| **المراحل المكتملة** | **Stage 1** — Source Reconciliation · **Stage 2** — Reformation · **Stage 4** — Identity Re-Foundation |
| **Stage 3** | Content & Editorial System — مكتمل (مُرقّم ضمن التسلسل) |
| **مرحلة غير مُنشأة** | **Stage 3** كما هو مُشار إليه في خطة المالك — «(3 لم يُنشأ)» |
| **المراحل القادمة** | **Stage 6** — Core User Flows · **Stage 7** — Technical · **Stage 8** — Launch |

---

## Stage 4 — Identity Re-Foundation — مكتمل 100% (2026-09-30)

| # | Topic | الحالة | القرار |
|---|---|---|---|
| PD-I01 | Brand Direction | ✅ CLOSED | Direction C — الختم |
| PD-I02 | Qussasa Mark | ✅ CLOSED | Qussasa Mark v1.0 adopted as-is |
| PD-I03 | Multi-Accent | ✅ CLOSED | Base Ink/Paper/Grey + Amber/Purple/Teal + Day/Night/Auto |
| PD-I04 | Typography | ✅ CLOSED | Lalezar + IBM Plex Sans Arabic + Inter + IBM Plex Mono |
| PD-I05 | Watermark | ❄️ DEFERRED | مُجمّد — PD-I05-R2 بعد الإطلاق |
| PD-I06 | Card + Detail | ✅ CLOSED | Duration top-right · أزرار نفس السطر · لا Empty States |
| PD-I07 | Chips | ✅ CLOSED | وسم بصري · inline · غير قابل للنقر |
| PD-I08 | Light/Dark + Soft Depth | ✅ CLOSED | Dark دافئ Qishr · 4 مستويات ظل · Auto افتراضي |
| PD-I09 | Motion | ✅ CLOSED | Hybrid Subtle + Seal Anchor |
| PD-I10 | UI Language | ✅ CLOSED | Studio Seal |

**الهوية المعتمدة:** Direction C — الختم · **Studio Seal** — نظام هادئ كـLinear + دفء Qishr + نظام ختم صارم + الشخصية اليمنية في **المحتوى** لا في الواجهة.

---

## بنية المجلدات

```
nibras-export/
├── README.md
├── .gitignore
├── canonical/                          ← المرجع الحي
│   ├── YEMREACT-CANONICAL-BASELINE.md  ← 79 حقيقة
│   └── YEMREACT-DECISIONS-LOG.md       ← DECISION-001…015 + I01…I10
├── stage-1-source-reconciliation/      ← 12 ملفًا (مطابقة المصادر)
├── stage-2-reformation/                ← خطة إعادة التأسيس
├── stage-4-identity/
│   ├── decisions/                      ← DECISION-I01 … DECISION-I10 (مستخرجة حرفيًا)
│   ├── YEMREACT-STAGE4-PD14-HISTORY-EVIDENCE.md
│   └── YEMREACT-PD-I10-UI-LANGUAGE-OPENING.md
├── stage-5-ia-navigation/
│   └── YEMREACT-STAGE5-5.1-SEARCH-ROUTE-DISCUSSION.md
└── reference/
    ├── نبراس.md
    ├── YemReact_Claude_Foundation_Package.md
    ├── YemReact_Prompt_For_Claude.md
    └── uploads/
```

---

## قواعد هذا المستودع

- ❌ **لا تعديل على أي قرار أو حقيقة** — الملفات نسخ حرفية من مساحة العمل
- ❌ **لا حذف** للملفات الأصلية
- ❌ **لا `--force`** في أي عملية Git
- ✅ أرشيف للقراءة والمرجعية — القرار بيد حمدان فقط

> الملفات داخل `stage-4-identity/decisions/` **مستخرجة حرفيًا** من `YEMREACT-DECISIONS-LOG.md` — للسهولة فقط. **المرجع الملزم هو السجل الأصلي** في `canonical/`.

---

## ⚠️ ملفات غير موجودة في هذه الحزمة

هذه الملفات **لم تصل إلى مساحة عمل أرينا** — هي في بيئة Claude 4.5:

- `YEMREACT-PD-I10-R2` (Mockups)
- `YEMREACT-PD-I10-R3` (النقاش)
- `YEMREACT-PD-I10-R4` (Mockup نهائي)

لإضافتها: أرسلها في المحادثة أو ارفعها مباشرة إلى هذا المستودع.

---

## الخطوة التالية

**Stage 5 — موضوع 5.1 — Search Route** — نقاش مفتوح:
- الخيارات: (أ) `/search` منفصلة · (ب) `?q=` في المكتبة · (ج) Hybrid · (د) `/search/[term]`
- **توصية أرينا:** **(ب)** `?q=` على نفس سطح المكتبة + `/search` يوجّه إليها + `noindex` عند وجود `q`
- **الدليل الحاسم:** جوجل حذف 210,843 صفحة `/search/` من Giphy دفعة واحدة — صفحات نتائج البحث الداخلي لا تُفهرس
- **بانتظار:** قرار حمدان → ثم 5.2 — Bottom Nav التبويبات النهائية
