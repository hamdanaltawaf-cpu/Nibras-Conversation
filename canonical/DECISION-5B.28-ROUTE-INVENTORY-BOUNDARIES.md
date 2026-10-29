# DECISION-5B.28 — Route Inventory Boundaries and Unavailable States

**Status:** ACCEPTED — product/documentation scope only  
**Recorded:** 2026-10-29  
**Authority:** Hamdan directed the assistant to continue resolving remaining documentation questions before considering Stage 5 closure, while explicitly deferring implementation work until documentation is complete.  
**Scope:** Classify the remaining route-inventory gaps without inventing product routes. This decision does not select implementation architecture, prove any route exists in the application, or authorize code/database changes.

## 1. Admin area and subroutes

1. `/admin` is the only admin route currently established at the product-inventory level.
2. No additional public or product-level route names are approved for admin subsections by this decision.
3. Content management, submission review, collection management, report review, and permissions belong to the admin area according to authorized roles; their exact internal screen/URL structure is not a Stage 5 product-route decision.
4. Do not invent or publish an assumed list of admin URLs in the product route inventory. Their actual route tree must be documented during a separately authorized application/technical review.
5. This does not weaken the requirement that sensitive admin actions be restricted to authorized staff; enforcement remains unverified.

## 2. Privacy, rights, and legal pages

1. Stage 5 does not approve new standalone routes such as `/privacy`, `/terms`, `/rights`, or `/report` based solely on gaps in the inventory.
2. The accepted product surfaces remain `/settings` for the approved account/privacy settings area and `/help` for help content and reporting guidance. Reporting begins through the already specified Help/reaction-menu workflow; DECISION-5B.26 does not approve a separate public report route.
3. Substantive legal requirements, terms, rights/takedown policy, and any required legal disclosures remain a separate legal-scope obligation (historically assigned to the later Legal scope). This decision neither waives those obligations nor decides whether a future legal page will be required.
4. Until that legal scope is explicitly reviewed, the Stage 5 inventory records no approved standalone privacy/rights/legal route. Do not create or name one by inference.

## 3. Invalid or unavailable reaction links

1. An invalid reaction code or a reaction that is not available for public viewing is handled as an unavailable/not-found state of the existing `/r/[code]` route, not as a new product route.
2. Do not render a misleading empty reaction detail, fabricate reaction data, or reveal internal moderation details.
3. The user-facing state should communicate that the reaction is unavailable and provide a clear return path to the library. The default copy may be concise, for example: «هذا الرياكشن غير متاح».
4. Unknown application paths likewise use the app's general not-found state; no additional named route is approved by this decision.
5. Exact HTTP status codes, indexing/crawl behavior, redirects, telemetry, and visual implementation remain technical specification/verification matters and are not claimed as implemented here.

## 4. Inventory classification

| Inventory topic | Product/documentation outcome | Remaining technical status |
|---|---|---|
| Admin subroutes | No additional product-level routes approved in Stage 5; `/admin` is the documented umbrella. | Actual application route tree and authorization checks unverified. |
| Privacy/rights/legal routes | No standalone route approved by Stage 5. Legal content/obligations remain outside this decision and require separate legal-scope review. | Whether future legal requirements require a page remains for that scope; no implementation verified. |
| Report route | No standalone public `/report` route; follow DECISION-5B.26. | End-to-end report workflow remains unverified and cannot be presented as operational before its gate passes. |
| Invalid reaction code | Unavailable/not-found state within `/r/[code]`; no new product route. | Status code, SEO/crawl treatment, and actual state rendering unverified. |
| Unknown app path | General not-found state; no named route added to product scope. | Actual fallback, status code, and navigation behavior unverified. |

## 5. Stage boundary and governance

- This resolves the remaining Stage 5 **product-route inventory classification** gaps; it does not claim every legal obligation, internal admin URL, or technical state has been implemented or fully specified.
- The route inventory may now label the above product-scope questions as resolved, while retaining technical details as UNVERIFIED and future legal requirements as a separate scope.
- Stage 5 remains OPEN pending a separate documentation closeout review and Hamdan's explicit closure decision.
- No Stage 5.3 is created and Stage 6 is not started.
- OPEN-Q-08 and OPEN-Q-09 remain separate and CLOSED FOR DOCUMENTATION only.
- No app code, database, security settings, tests, build, runtime, or release configuration is changed or verified by this decision.
