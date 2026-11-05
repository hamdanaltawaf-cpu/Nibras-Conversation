# DECISION-5B.27 — Remaining UX Details: Signup Prompts, Header, Collections, Help

**Status:** ACCEPTED — delegated resolution authorized by Hamdan on 2026-10-28 (message received during the ongoing roadmap workflow).  
**Recorded:** 2026-10-29  
**Scope:** Remaining Stage 5-B product/UI questions only. This document records product policy; it does not prove implementation, tests, build, or runtime behavior.

## Authority and boundaries

Hamdan explicitly directed the assistant to resolve the remaining open decisions and maintain the reviewed roadmap and its change log after each work item. This decision resolves only the four open UX details below. It does not reopen accepted decisions, alter canonical product fundamentals, or authorize app-code/database changes.

## 1. Signup invitations

### Decision
1. Signup invitations must never block browsing, searching, opening a reaction, or using guest-local saves.
2. The first library invitation is optional and non-blocking. Use a compact inline/banner-style invitation, not a blocking modal or timed interruption.
3. Contextual invitations appear only when a guest reaches an action that genuinely requires an account (for example, following a collection), or in the already approved contextual location. Saving a reaction alone is not a reason to block or interrupt the guest.
4. Once dismissed or continued past, a given invitation is not shown again in the same browser session/profile context. Do not repeatedly prompt on every page or every action.
5. The invitation provides an explicit close/dismiss action and a clear continue-as-guest path. Google is the active sign-in provider; do not imply Apple/Microsoft sign-in is available.
6. Use the following approved Arabic copy as the default:
   - **Library invitation heading:** «خلّ رياكشناتك المحفوظة معك»
   - **Body:** «سجّل دخولك عشان تزامن محفوظاتك وتوصل لها من حسابك. وتقدر تواصل التصفح كزائر.»
   - **Primary action:** «تسجيل الدخول بـ Google»
   - **Secondary action:** «الاستمرار كزائر»
   - **Dismiss label/accessibility name:** «إغلاق»
7. For a guest attempting an account-only collection-follow action:
   - **Heading:** «تابع المجموعة من حسابك»
   - **Body:** «سجّل دخولك عشان تحفظ المجموعات التي تتابعها.»
   - **Primary action:** «تسجيل الدخول بـ Google»
   - **Secondary action:** «ليس الآن»
8. Do not claim that guest saves are synchronized until server confirmation. Follow DECISION-5B.24 for additive merge, retry, deduplication, and account isolation.

### Rationale / rejected alternatives
- Rejected: blocking signup modal, forced login before browsing/saving, repeated prompts, and implying that local guest saves are already synchronized.
- Reason: preserve low-friction library access, guest utility, and honest account boundaries.

## 2. Header visual reference

### Decision
1. The visual authority is the locked YemReact Brand v1.0 and Qussasa Mark, combined with the already accepted Stage 5-B responsive navigation and clean product-first visual language.
2. Pinterest is **not** the header reference. Pinterest-like masonry remains a presentation pattern for the library only; it does not authorize copying Pinterest navigation, controls, branding, or social features.
3. Preserve the accepted interaction structure:
   - Mobile: Library, Collections, Account in the bottom navigation; submission is not a bottom-nav item.
   - Desktop: Library and Collections as primary destinations; search and Submit in the header; no standalone Saved destination in the desktop header.
   - Account avatar opens Account; its adjacent chevron opens the account menu.
4. The header must remain visually quiet, RTL-correct, responsive, and consistent with the approved typography/color/mark system. Do not add social metrics, profile feeds, decorative Pinterest-like controls, or a new navigation destination.
5. No new reference screenshot is required to establish the product rule. A later visual comparison may evaluate execution quality but may not silently change the approved structure or brand.

### Rationale / rejected alternatives
- Rejected: treating a historical Pinterest-like prototype as a binding header design, or using the header redesign to reopen accepted navigation.
- Reason: distinguish visual inspiration for the content grid from the product's own brand and navigation system.

## 3. Collections display and ordering

### Decision
1. Collections remain admin-curated editorial groupings, not user-created Boards or a social graph.
2. On the Library page, show a compact, horizontally scrollable collection strip after the primary page introduction/search area and before the reaction grid. On narrow screens, the strip must not displace the core search/library experience or force horizontal page overflow.
3. The `/collections` page lists active, published collections in an explicit admin-controlled order. Do not sort by follower count, engagement, popularity, or an invented score.
4. Collection cards use an admin-selected cover when one is supplied; otherwise use a deterministic, available reaction thumbnail from that collection. Show title and a short description when present. The actual clip count may be shown with a clear label in accordance with DECISION-5B.23. Do not show follower counts or engagement counters.
5. The `/collections/[slug]` page shows the collection title, description when present, reaction grid, and follow/unfollow action for signed-in users. Empty/error/loading states must remain distinct; an absent optional description is omitted rather than replaced with a placeholder.
6. Guests can view collections and their reactions. If a guest attempts to follow a collection, show the non-blocking contextual invitation from section 1; do not require login merely to view.
7. For signed-in users, followed collections appear in a clearly labelled «المجموعات التي تتابعها» section at the top of `/collections`, followed by the full admin-ordered collection list. This section is personal and private; it is not a public profile or social feed. Do not create a separate route or add a new Account tab for it in this decision.
8. If a collection is unfollowed, removed, unpublished, or unavailable, reflect the actual state without making stale entries appear available. Never invent counts, covers, or collection content.

### Rationale / rejected alternatives
- Rejected: user-created boards, engagement-ranked ordering, public follower counts, a separate new route/tab, or hiding the full collection catalogue behind the followed list.
- Reason: preserve curated discovery while keeping follows useful, private, and distinct from reaction saves.

## 4. Help center Arabic copy

### Decision
1. `/help` is a concise, scannable Arabic help center. Search within Help is optional; do not display a non-functional search control.
2. Use these initial sections and approved baseline copy. Copy must be revised before publication if it conflicts with verified shipped behavior:
   - **عن يمن رياكت:** «يمن رياكت مكتبة منظّمة لرياكشنات يمنية تقدر تتصفحها وتبحث عنها وتفتح صفحة الرياكشن لمشاركته أو حفظه.»
   - **كيف ألقى رياكشن؟** «تقدر تتصفح المكتبة أو تستكشف المجموعات أو تستخدم البحث. افتح الرياكشن لمشاهدة تفاصيله والخيارات المتاحة له.»
   - **كيف أحفظ رياكشن؟** «تقدر تحفظ الرياكشن كزائر على هذا الجهاز. إذا سجّلت دخولك، قد تُدمج محفوظات الزائر مع محفوظات حسابك بعد تأكيد نجاح المزامنة. إذا تعذرت المزامنة، احتفظ بالمحفوظات المحلية وأعد المحاولة.»
   - **هل الحفظ يحتاج حسابًا؟** «لا، تقدر تحفظ محليًا كزائر. بعض الوظائف المرتبطة بالحساب، مثل متابعة المجموعات، تتطلب تسجيل الدخول.»
   - **كيف أرسل رياكشن؟** «اختر إرسال رياكشن وأكمل النموذج. يلزم تسجيل الدخول عبر Google لإكمال الإرسال، وكل مساهمة تمر بمراجعة بشرية؛ الإرسال لا يضمن النشر.»
   - **متى يظهر الرياكشن الذي أرسلته؟** «لن يظهر في المكتبة العامة إلا بعد المراجعة والموافقة والنشر. يمكنك متابعة الحالة المعروضة في حسابك إذا كانت متاحة.»
   - **كيف أبلغ عن مشكلة؟** «إذا ظهر خيار إبلاغ في صفحة الرياكشن، استخدمه لبدء البلاغ. يمكنك أيضًا مراجعة مركز المساعدة لمعرفة قناة الإبلاغ المتاحة.» Do not claim an operational report form until it passes DECISION-5B.26's end-to-end launch gate.
   - **كيف أغيّر المظهر؟** «من الإعدادات، اختر تلقائي أو نهاري أو ليلي إذا كانت الخيارات متاحة في النسخة التي تستخدمها. الوضع التلقائي يتبع إعداد جهازك.»
3. Do not claim Apple/Microsoft sign-in, public contributor profiles, automatic publishing, guaranteed support replies, working report submission, or any unverified feature.
4. Help copy is content, not evidence of functionality. Where a described control or flow is not verified in the shipped product, either omit the answer until verified or clearly label it as guidance for the intended behavior.

### Rationale / rejected alternatives
- Rejected: help copy that promises unverified features, claims reports are sent without server confirmation, or promises support response times.
- Reason: accuracy and user trust.

## Acceptance checklist

- Signup prompts are optional, non-blocking, dismissible, not repetitive, and have clear guest continuation.
- Header reference and accepted navigation are unambiguous; Pinterest is limited to masonry presentation inspiration.
- Collections have a deterministic admin-controlled order, explicit card rules, private followed-collection placement, and no social counters.
- Help copy matches accepted policies and is withheld/qualified where implementation is unverified.
- No route, account tab, or public social feature is added beyond the decisions above.
- No code, database, security verification, tests, build, runtime, or release readiness is implied.

## Impact and governance

- Resolves the remaining Stage 5-B product questions for signup prompts, header visual reference, collection presentation, and Arabic Help copy.
- DECISION-5B.19 through DECISION-5B.26 remain in force; DECISION-5B.23 controls numeric UI, DECISION-5B.24 controls guest-save reconciliation, and DECISION-5B.26 controls the report launch gate.
- Stage 5 remains OPEN. This does not create Stage 5.3 or start Stage 6.
- OPEN-Q-08 and OPEN-Q-09 remain separate and closed for documentation only; their technical implementation is unverified.
- SEC-06, upload enforcement, route behavior, permissions, report workflow, tests, build, and runtime remain unverified.

## Current status reconciliation — 2026-10-30
The statement above that Stage 5 remains open describes the status at the time this decision was recorded. Current status: Stage 5 is **CLOSED FOR DOCUMENTATION ONLY** under the dated closeout record; the product questions resolved here remain accepted. OPEN-Q-08 and OPEN-Q-09 are each **CLOSED FOR DOCUMENTATION ONLY** in their separate documents. UX implementation, accessibility, route behavior, and runtime remain unverified/deferred. This addendum does not authorize implementation.
