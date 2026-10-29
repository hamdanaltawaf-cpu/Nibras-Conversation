# DECISION-5B.29 — Empty and Error State Copy

**Status:** ACCEPTED — product/content policy only  
**Date:** 2026-10-29  
**Authority:** Delegated Stage 5 documentation work.  
**Scope:** Initial Arabic copy and display rules for empty states and recoverable read failures that were not already specified by an earlier canonical decision. This does not prove implementation or authorize code changes.

## 1. General rules

1. Loading, empty, error, permission-denied, and success states must remain distinct.
2. Show an empty state only after a successful load confirms there is nothing to display. A failed request must never appear as an empty list.
3. Use a retry action only where retrying is safe. Do not show success until the relevant operation is confirmed.
4. Do not show counts, social engagement numbers, or invented content to make an empty state look populated.
5. Existing copy in DECISION-5B.25 for Saved and My Contributions remains authoritative and is not replaced by this decision.
6. For optional sections, do not show a section-level empty message if the product can simply omit the section without losing essential information. A request failure is not a reason to silently omit content.

## 2. Approved initial copy

### Library

- **Empty after successful load:** «ما في رياكشنات متاحة حاليًا.»
- **Supporting text:** «جرّب البحث أو استكشف المجموعات.»
- **Actions:** «البحث في المكتبة» → `/?q=`; «استكشف المجموعات» → `/collections`.
- **Read failure:** «تعذّر تحميل المكتبة. حاول مرة ثانية.»
- **Retry action:** «إعادة المحاولة».

### Search

- **No useful results:** «ما لقينا رياكشن مطابق.»
- **Supporting text:** «جرّب كلمات مختلفة أو ارجع للمكتبة.»
- **Actions:** «مسح البحث» (clears the query) and «العودة للمكتبة» → `/`.
- **Search failure:** «تعذّر إكمال البحث. حاول مرة ثانية.»
- **Retry action:** «إعادة المحاولة».
- Do not describe weak results as confirmed matches. Follow OPEN-Q-08 for retrieval policy.

### Collections list

- **Empty after successful load:** «ما في مجموعات متاحة حاليًا.»
- **Supporting text:** «ارجع للمكتبة لاستكشاف الرياكشنات.»
- **Action:** «العودة للمكتبة» → `/`.
- **Read failure:** «تعذّر تحميل المجموعات. حاول مرة ثانية.»
- **Retry action:** «إعادة المحاولة».
- For a signed-in user, absence of followed collections does not make the whole page empty; show the full admin-ordered collection list.

### Collection detail

- **Empty after successful load:** «ما في رياكشنات في هذه المجموعة حاليًا.»
- **Action:** «استكشف المجموعات» → `/collections`.
- **Read failure:** «تعذّر تحميل المجموعة. حاول مرة ثانية.»
- **Retry action:** «إعادة المحاولة».
- Omit an absent optional description. Do not replace it with placeholder text.

### Optional related/discovery sections

- If a successful response contains no items, omit that optional section rather than displaying a standalone empty panel.
- If the request fails, do not treat the failure as a successful empty response; use the page's recoverable error behavior.
- Do not expose the number of related/random items as a visible count, per DECISION-5B.23.

### Shared read failure where no page-specific copy exists

- **Message:** «تعذّر تحميل المحتوى. حاول مرة ثانية.»
- **Action:** «إعادة المحاولة».
- Use this only for recoverable read failures. Permission-denied, authentication, media playback, save, upload, and report-submission failures require their own truthful state and must not be mislabeled as a generic empty state.

## 3. Existing decisions remain authoritative

- Saved and My Contributions empty-state copy: DECISION-5B.25.
- Help copy and report reliability: DECISION-5B.26 and DECISION-5B.27.
- Signup prompts, collection presentation, and initial Help copy: DECISION-5B.27.
- Policy routes and not-found/unavailable-reaction copy: DECISION-5B.28.
- Number/count display: DECISION-5B.23.
- Search quality and weak/no-result handling: OPEN-Q-08, closed for documentation only.

## 4. Deferred and unverified

- Exact messages for upload validation, authentication cancellation, media playback, save failure, and ambiguous network outcomes remain governed by their relevant flow decisions or require separate documentation; this decision does not invent them.
- This decision does not define HTTP status codes, server responses, retry mechanics, analytics, or UI implementation.
- Stage 5 remains OPEN until the complete documentation inventory and explicit documentation-closure record are complete.
- No Stage 5.3 is created and Stage 6 is not started.
- No app code, database changes, security review, tests, build, or runtime verification is authorized or implied.
