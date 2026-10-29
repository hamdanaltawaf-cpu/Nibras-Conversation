# DECISION-5B.28 — Route and Not-Found Boundaries

**Status:** ACCEPTED — product/IA documentation only  
**Date:** 2026-10-29  
**Authority:** Hamdan delegated resolution of the remaining Stage 5 documentation questions and requested that the roadmap and its change log be updated after each work item.  
**Scope:** Standalone policy routes, invalid public URLs/reactions, and the product-level boundary for admin subroutes. This decision does not specify implementation, framework behavior, API endpoints, or database changes.

## 1. Standalone policy, privacy, and rights pages

1. Stage 5 does **not** introduce standalone `/privacy`, `/terms`, or `/rights` routes.
2. The product must not display a privacy/rights link unless it leads to a real, approved policy destination.
3. The product may explain the difference between guest-local saves and account-associated data in relevant help/settings copy, but must not imply a full privacy policy exists if it does not.
4. Defining legal/policy content and whether a dedicated destination is needed is **DEFERRED** to a separately scoped policy-content decision. No placeholder or invented policy page is approved by this decision.

## 2. Unknown URL and unavailable reaction

1. A public URL that does not resolve to an approved page, or a reaction code that is unknown, unpublished, or unavailable to the public, uses a consistent not-found experience.
2. Do not disclose whether a reaction exists privately, is awaiting review, was unpublished, or was removed. The public message remains generic.
3. Initial Arabic copy:
   - Unknown page: **«الصفحة غير موجودة»**
   - Unavailable reaction: **«الرياكشن غير متاح»**
   - Supporting text: **«يمكنك العودة للمكتبة أو البحث عن رياكشن آخر.»**
   - Primary action: **«العودة للمكتبة»** → `/`
   - Secondary action: **«البحث في المكتبة»** → `/?q=` with an empty query or the approved library search entry point; do not invent a new search route.
4. Do not silently redirect an invalid public URL to an unrelated reaction. A direct user action may navigate back to the library.
5. This is a UX/content decision only; HTTP status codes, routing implementation, metadata, and tests remain unverified and are not prescribed here.

## 3. Admin surface and subroutes

1. `/admin` remains the only admin entry route established at this level.
2. The product inventory must cover these functional areas where applicable: reaction/content management, submission review, collections management, issue reports, speech extraction, and access/permission handling.
3. Listing a functional area does not mean it must have its own URL. No admin subroute names are accepted in Stage 5 by this decision.
4. Admin information architecture and detailed operator flows remain documented as functional sections until a dedicated admin-flow decision explicitly establishes any separate routes. Historical technical patterns such as `/admin/*` are not accepted product routes.

## 4. Alternatives rejected

- Inventing `/privacy`, `/terms`, or `/rights` without approved policy content and a real destination.
- Treating historical 404 responses as a complete user-facing design.
- Revealing private moderation/publication state through an error message.
- Redirecting an invalid URL to unrelated content without user intent.
- Treating every admin function as a separate route merely because an old technical inventory lists wildcards.

## 5. Impact and boundaries

- Resolves the Stage 5 documentation questions about policy-route status, invalid public URL/reaction messaging, and the scope of admin subroutes.
- It does **not** close Stage 5 by itself.
- Stage 5 remains OPEN pending the complete documentation inventory and a separate explicit documentation-closure record.
- No Stage 5.3 is created and Stage 6 is not started.
- No application code, database, API, routing implementation, security review, tests, build, or runtime verification is authorized or implied.
- OPEN-Q-08 and OPEN-Q-09 remain separate and closed for documentation only.
