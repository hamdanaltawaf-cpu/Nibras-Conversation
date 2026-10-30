# DECISION-5B.29 — Empty and Error State Copy

**Status:** ACCEPTED — product/content policy only  
**Date:** 2026-10-30  
**Authority:** Selective adoption from PR #18 under Hamdan's explicit authorization to process its documentation content.  
**Scope:** Initial Arabic copy and display rules for empty states and recoverable read failures not already specified by an earlier canonical decision. This does not prove implementation or authorize code changes.

## 1. General rules

1. Loading, empty, error, permission-denied, and success states remain distinct.
2. Show an empty state only after a successful load confirms there is nothing to display. A failed request must never appear as an empty list.
3. Show retry only where retrying is safe; never show success before confirmation.
4. Do not show counts, social engagement numbers, or invented content to make an empty state look populated.
5. DECISION-5B.25 remains authoritative for Saved and My Contributions; this decision does not replace its copy.
6. For optional sections, omit a section-level empty panel when omission loses no essential information. A request failure must not be silently treated as empty content.

## 2. Approved initial copy

### Library
- Empty after successful load: «ما في رياكشنات متاحة حاليًا.»
- Supporting text: «جرّب البحث أو استكشف المجموعات.»
- Actions: «البحث في المكتبة» → `/?q=`; «استكشف المجموعات» → `/collections`.
- Read failure: «تعذّر تحميل المكتبة. حاول مرة ثانية.»
- Retry: «إعادة المحاولة».

### Search
- No useful results: «ما لقينا رياكشن مطابق.»
- Supporting text: «جرّب كلمات مختلفة أو ارجع للمكتبة.»
- Actions: «مسح البحث» (clears the query) and «العودة للمكتبة» → `/`.
- Search failure: «تعذّر إكمال البحث. حاول مرة ثانية.»
- Retry: «إعادة المحاولة».
- Do not describe weak results as confirmed matches; follow OPEN-Q-08 retrieval policy.

### Collections list
- Empty after successful load: «ما في مجموعات متاحة حاليًا.»
- Supporting text: «ارجع للمكتبة لاستكشاف الرياكشنات.»
- Action: «العودة للمكتبة» → `/`.
- Read failure: «تعذّر تحميل المجموعات. حاول مرة ثانية.»
- Retry: «إعادة المحاولة».
- For signed-in users, absence of followed collections does not make the whole page empty; show the full admin-ordered collection list.

### Collection detail
- Empty after successful load: «ما في رياكشنات في هذه المجموعة حاليًا.»
- Action: «استكشف المجموعات» → `/collections`.
- Read failure: «تعذّر تحميل المجموعة. حاول مرة ثانية.»
- Retry: «إعادة المحاولة».
- Omit an absent optional description; do not replace it with placeholder text.

### Optional related/discovery sections
- If a successful response contains no items, omit the optional section rather than displaying a standalone empty panel.
- If the request fails, do not treat it as a successful empty response; use the page's recoverable error behavior.
- Do not expose counts of related/random items, per DECISION-5B.23.

### Shared recoverable read failure
- Message: «تعذّر تحميل المحتوى. حاول مرة ثانية.»
- Action: «إعادة المحاولة».
- Use only for recoverable read failures. Permission, authentication, media playback, save, upload, and report-submission failures require truthful flow-specific states and must not be mislabeled as generic empty states.

## 3. Existing decisions remain authoritative

- Saved and My Contributions: DECISION-5B.25.
- Help copy and report reliability: DECISION-5B.26 and DECISION-5B.27.
- Signup prompts, collection presentation, and initial Help copy: DECISION-5B.27.
- Route boundaries and unavailable/not-found states: DECISION-5B.28.
- Number/count display: DECISION-5B.23.
- Search quality and weak/no-result handling: OPEN-Q-08, CLOSED FOR DOCUMENTATION ONLY.

## 4. Deferred and unverified

- Exact messages for upload validation, authentication cancellation, media playback, save failure, and ambiguous network outcomes remain governed by their relevant flow decisions or require separate documentation; this decision does not invent them.
- This decision does not define HTTP status codes, server responses, retry mechanics, analytics, or UI implementation.
- Stage 5 remains CLOSED FOR DOCUMENTATION ONLY under the existing closeout record; this decision is an additive documentation clarification, not a reopening.
- No Stage 5.3 is created and Stage 6/9 are not started.
- No app code, database changes, security review, tests, build, or runtime verification is authorized or implied.
