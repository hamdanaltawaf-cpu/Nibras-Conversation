# DECISION-5B.25 — Saved and My Contributions Empty States

Status: Accepted product policy.

## Rules
- Show an empty state only after a successful load confirms there are no displayable items. Loading, network/server errors, and permission failures are distinct states; offer retry where supported.
- Guest Saved: heading “ما حفظت أي رياكشن لحد الآن”; body “تصفّح المكتبة واحفظ الرياكشنات التي تعجبك، وبتحصل عليها هنا.”; action “استكشف المكتبة” → `/`.
- Signed-in Saved: heading “محفوظاتك بتظهر هنا”; body “احفظ الرياكشنات التي تريد الرجوع إليها، وستجدها في مكان واحد.”; action “استكشف المكتبة” → `/`.
- Signed-in My Contributions: heading “ما عندك مساهمات حتى الآن”; body “أرسل رياكشن يمنيًا ليستفيد منه الآخرون بعد مراجعته واعتماده.”; action “أرسل رياكشن” → `/submit`.
- Guest Account must not show account statistics or an empty My Contributions panel. Preserve guest local saves and the established sign-in invitation.
- Any submission with a status (pending, needs changes, declined/rejected, published) is an item, not an empty state. Show contributor-facing status and reasons/change requests only; never expose internal moderation notes.
- Unavailable saved codes do not make content available and must not cause valid saves to be discarded.
- Do not imply automatic publication; human review remains required.
- Scope is Saved and My Contributions only. The existing rule about optional reaction-detail fields remains scoped to reaction details.
- DECISION-5B-CANONICAL and decisions 5B.22, 5B.23, and 5B.24 remain in force.

## Verification boundary
This is product policy, not evidence of implementation or tests. Stage 5 remains OPEN. Do not create Stage 5.3 or start Stage 6. OPEN-Q-08 and OPEN-Q-09 remain separate/open. SEC-06, server-side upload allowlist enforcement, routes, tests, builds, and runtime remain unverified.
