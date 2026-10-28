# DECISION-5B.26 — Help Center and Issue Reporting

**Status:** ACCEPTED — founder authorized proceeding on 2026-10-28  
**Scope:** Product policy and launch requirements for `/help` and issue reporting. This decision does not imply that any UI, reporting endpoint, moderation queue, or operational workflow has been implemented or tested.

## 1. Help center purpose and structure

The approved `/help` direction is a concise, searchable-or-scannable help center (search within Help is optional and must not be added as a fake control). Organize its initial content around:

1. **Getting started:** what YemReact is and how to browse the curated Yemeni reaction library.
2. **Finding reactions:** search, category filtering, and opening a reaction's shareable detail page.
3. **Saving reactions:** explain guest-local saves versus account-associated saves, including the approved additive guest-save reconciliation after successful sign-in. Do not imply that guest saves are synchronized to an account before confirmation.
4. **Collections and sharing:** explain only the real, released behavior; do not promise features that are merely planned.
5. **Submitting a reaction:** explain the submission path, Google sign-in requirement at submission, and human review. Never imply that submission guarantees acceptance or immediate publication.
6. **Account and settings:** explain approved sign-in, Saved, My Contributions, and settings behavior, while clearly marking providers or controls that are still being prepared.
7. **Reporting a problem:** explain how to report a technical issue or a problem with a reaction.

FAQ copy must reflect accepted product decisions and verified current behavior. If implementation status is unknown, phrase the answer as guidance about the intended product only when clearly labeled, or leave that answer out until verified. Do not claim a feature exists solely because a decision document specifies it.

## 2. Issue-reporting entry points and scope

- The Help center is the central explanatory entry point for reporting a problem.
- Where the existing reaction overflow menu provides **إبلاغ**, it should open the same reporting workflow with the relevant reaction code/URL prefilled. Do not create a second, inconsistent reporting process.
- Do not invent a separate public route for reports as part of this decision; route names beyond the already approved routes remain outside scope.
- Reports are operational messages for review, not public posts, comments, ratings, or social interactions.

## 3. Report categories and minimum data

Provide a required report category, with these initial options:
- مشكلة تقنية في الموقع
- مشكلة في الرياكشن (مثل رابط معطّل أو محتوى لا يعمل)
- ملاحظة تتعلق بالحقوق أو الإذن باستخدام المحتوى
- محتوى مخالف أو يحتاج إلى مراجعة
- أخرى

Required data:
- Category.
- A concise description of the issue.
- The affected reaction code or internal page URL when relevant; prefill it when the report starts from a reaction page.

Optional data:
- Contact method/address, only if the reporter wants a reply.
- Do not require account sign-in solely to report an issue.
- Do not request passwords, authentication codes, sensitive personal information, or unrelated personal details.
- Do not support file attachments in the first release unless a separate security and privacy review explicitly approves them.

## 4. Submission feedback and reliability

- Show a success confirmation only after the server confirms the report was accepted and persisted.
- If submission fails, clearly say the report was not sent and offer a safe retry where possible; do not silently discard the report or falsely show success.
- Prevent accidental duplicate submissions where practical, and apply basic server-side abuse controls such as rate limiting and input validation.
- Do not promise a response, resolution, or response time unless an operational support process has actually been established.
- Do not expose internal moderation notes, triage details, or other reporters' information to the reporter or the public.

## 5. Administration, privacy, and handling

- Reports are visible only to authorized personnel who need them to review and resolve the issue.
- Separate the reporter-facing confirmation/communication from internal notes.
- Collect only the data necessary to understand and handle the report. Optional contact data is used only for the stated follow-up purpose.
- Establish appropriate retention and deletion handling before production use; this decision does not invent a retention duration or substitute for a real privacy policy.
- Rights-related reports must be routed for human review. Do not automatically remove or publish content solely because a report was submitted.

## 6. First-release gate

The initial Help center may publish its static, accurate FAQ content independently. However:
- A report form or **إبلاغ** action must not be presented as operational unless the end-to-end submission path, persistence, authorized review access, failure handling, and basic abuse controls work.
- If reporting is not ready, do not ship a fake form, a dead button, or a success message that is not backed by server confirmation. Keep the explanatory content honest about the available reporting channel; provide an alternative contact link only if a real, approved destination exists.
- Before marking reporting launch-ready, verify it technically and review the privacy/security implications. Documentation alone is not verification.

## 7. Boundaries and reconciliation

- This decision defines the Help content direction and issue-reporting product requirements; exact FAQ wording may be refined without changing the policy.
- The previously accepted `/help` route and help-center direction in DECISION-5B.19 remain in force.
- Existing reaction overflow-menu direction that includes **نسخ الرابط** and **إبلاغ** is retained; this decision defines the intended reporting destination/workflow, not proof that it currently works.
- DECISION-5B.22 remains in force for contributor data visibility and internal moderation notes. This decision does not make reports public or expand contributor visibility.
- Stage 5 remains OPEN. Do not create Stage 5.3 or start Stage 6. OPEN-Q-08 and OPEN-Q-09 remain separate and OPEN. SEC-06, server-side upload enforcement, route behavior, tests, builds, runtime, and end-to-end reporting remain unverified unless separately tested.
