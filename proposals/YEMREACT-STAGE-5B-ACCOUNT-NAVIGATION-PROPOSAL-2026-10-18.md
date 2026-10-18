# YemReact Stage 5-B — Account, Header & Navigation Proposal

**Status:** Proposal for review only — not canonical, not merged  
**Date:** 2026-10-18  
**Authority:** Founder choices recorded in the 5-B discussion, including the uploaded handoff note “YEMREACT-STAGE5-5B-DISCUSSION-NOTE-2026-10-15.md”  
**Scope:** Documentation and decision reconciliation only. No code, build, database, runtime, or security audit.

## Purpose

Record the founder's explicit choices from 5-B.07 through 5-B.18 and the additional approved decisions captured in the handoff note, identify affected earlier decisions, and propose narrowly scoped updates. Preserve history; do not directly edit canonical files, the decisions log, README, or `main`. Nibras should update canonical documentation only after founder review and approval of this proposal.

## 1. Explicit founder choices from 5-B.07–5-B.18

| Discussion item | Founder choice | Proposed outcome |
|---|---|---|
| 5-B.07 Settings surface | C | Use a dedicated settings page from the outset. It should be extensible but show only real, approved functions; no empty sections. |
| 5-B.08 Settings sections | C | Organize the settings page around Appearance, Account, and Privacy. Display only sections/functions with approved content. |
| 5-B.09 Identity | C, with identity editing deferred | Private account identity may include an optional display name and optional avatar. No public user profiles. Do not add identity editing until the fields actually needed for contributions are defined. |
| 5-B.10 Guest account page | E | A concise guest account view may show locally saved reactions and a login invitation. Do not show account statistics or an empty contributions panel that implies an account exists. |
| 5-B.11 Account counts | C | For signed-in users, show a compact summary near the top of the account page, followed by the Saved / My Contributions switcher and its content. Contribution count means published contributions only. |
| 5-B.12 `/saved` | B | Redirect `/saved` to the account page with the Saved section selected. |
| 5-B.13 Desktop saved navigation | A | Saved reactions belong inside Account; do not keep Saved as a separate desktop header destination. |
| 5-B.14 Collections | A | Collections remain an independent destination on mobile and desktop. |
| 5-B.15 Mobile Send Reaction placement | A | Send Reaction is available from the Library and Account. It is not a fifth bottom-navigation item and does not appear in the general mobile header. |
| 5-B.16 Desktop account control | C | Clicking the account image opens the account page; clicking the adjacent arrow opens the dropdown. Provide clear keyboard access and focus behavior for both controls. |
| 5-B.17 Help | C | Direction is a full help center with FAQs, usage guidance, and issue reporting. Its route, exact scope, and content still require specification; do not assume `/help` is already approved. |
| 5-B.18 Documentation method | B | Create a separate proposal with a traceability table connecting new choices to prior decision IDs and the scope affected. |

## 2. Additional approved decisions from the 2026-10-15 handoff note

The user explicitly instructed that the decisions in the uploaded “YEMREACT-STAGE5-5B-DISCUSSION-NOTE-2026-10-15.md” be treated as approved and incorporated into this Stage 5-B proposal. The note itself said it was temporary and noncanonical; the current instruction establishes the founder's approval for its decisions. It does not establish technical implementation or runtime verification.

### 2.1 Library entry and optional login invitation

- An optional login gate/invitation may appear on the first visit to the Library. `/` and `/?q=` remain the Library surface under Stage 5.1.
- The Library gate must not block browsing: the visitor can choose “الاستمرار كزائر”.
- Direct reaction and collection links open the requested content directly; they must not be redirected to the login page.
- A non-blocking sign-up invitation appears near the top of a reaction or collection page. The invitation text is context-sensitive: general on a reaction page, and related to following the collection on a collection page.
- The invitation is shown once per browser. If the visitor continues or closes it, it should not appear again in that same browser, including after logout; it may appear on another browser or device.
- `/saved` remains accessible to guests; `/submit` opens the contribution preparation flow, and Google sign-in is required at submission as established in existing decisions.
- After sign-in, return the user to the intended internal destination, preserving the search query when present. Reject external return destinations.

### 2.2 Account entry and sign-in flow

- The guest account-menu entry is labelled **“تسجيل الدخول”** and opens a full sign-in page.
- Do not show “الاستمرار كزائر” inside a sign-in flow opened from the account menu; that option remains in the first-visit Library gate.
- The sign-in page displays Google as an active option and Apple and Microsoft as “قيد التجهيز” cards. This is a product/UI choice and does not mean those providers are technically enabled.
- After sign-in initiated from the account menu, return to the previous page, preserving the search query when present; reject external return destinations.
- The signed-in account menu remains available according to the approved menu pattern. The later 5-B choice that the desktop account image opens the Account page and the adjacent arrow opens the dropdown remains in force; these behaviors are complementary, not contradictory.
- Do not add “مساهماتي” as an item in the account dropdown. The note cites 5.2.5 for this; the later Account-page design puts “مساهماتي” inside the Account page itself, not in the dropdown.

### 2.3 Settings and visual design review

- The selected direction is a dedicated settings page with sections added progressively; the later 5-B choice specifies the intended categories as Appearance, Account, and Privacy, but only real approved functions should be shown.
- This changes the presentation direction from the earlier modal in P-37 / DECISION-I03 only after the founder's explicit choices are documented and canonicalized. It does not silently change the settings' existing values.
- Compare header designs visually before approving the complete visual composition. The already specified desktop account interaction (image opens Account, arrow opens dropdown) is retained, but the overall header visual layout is not considered visually approved solely from this proposal.
- The ordering of the mobile bottom navigation described in the prototype/audit report is not treated as a conflict to reopen in this round. The current approved structure remains Library, Collections, Account.
- Do not assume an inspiration direction based on Pinterest until the founder identifies the specific element or supplies a reference.

## 3. Consolidated target experience

### Mobile navigation

Three primary destinations:
1. Library
2. Collections
3. Account

Saved reactions and the user's published contributions are sections within Account, not separate bottom-navigation destinations. Send Reaction remains an action available from Library and Account, not a bottom-navigation destination. The general mobile header does not show Settings or Send Reaction; those controls appear on the Account page as discussed, while the Send Reaction action is also available from the Library.

### Desktop navigation and account control

- Keep Library and Collections as top-level destinations.
- Do not keep Saved as a separate header destination.
- Keep Search and a distinct Send Reaction action in the header.
- The account image and adjacent arrow are separate controls: image opens Account; arrow opens the account dropdown.
- The dropdown's guest/signed-in/admin content continues to follow existing account-menu decisions unless a separately approved decision changes it.
- The guest account-menu item is “تسجيل الدخول” and opens the full sign-in page. Do not add “الاستمرار كزائر” there.
- Do not add “مساهماتي” to the account dropdown.
- Saved is reached inside Account. `/saved` should redirect to Account with Saved selected while preserving guest access to saved content according to the guest-save decisions.

### Account page

**Signed-in user:**
- Private identity area.
- Compact summary of saved-reaction count and published-contribution count.
- A switcher: **Saved | My Contributions**.
- The selected section's list appears below.
- If there are no contributions, show an appropriate empty state.
- Settings and Send Reaction actions appear on the Account page.
- “My Contributions” is a section of the Account page, not an item in the account dropdown.

**Guest:**
- A concise account view with a sign-in invitation.
- Local saves remain accessible.
- No account statistics and no empty My Contributions panel implying that an account exists.
- Identity editing and account-only controls are not shown as available before sign-in.

### Identity and privacy

- YemReact remains a curated reaction library, not a social network.
- Do not add public user profiles, follower counts, public activity pages, or other social-network affordances through this change.
- Optional display name/avatar are a possible private account identity, not a public profile.
- Identity editing is explicitly deferred until the fields needed for contributions are defined. This is a scope constraint, not an implementation claim.

### Settings page

- A dedicated settings page is the selected product direction, rather than the former modal-only presentation.
- Organize it around Appearance, Account, and Privacy, but show only approved, functional options; do not render empty sections.
- Preserve the existing approved appearance options unless separately changed.
- Do not silently resolve the existing default-theme conflict: P-37 describes Day as default, while DECISION-I08 describes Auto as default. This remains an explicit documentation conflict requiring a separate founder decision or authoritative source reconciliation.
- The route name for the settings page must be confirmed before canonicalization if not already explicitly settled in the decision record.
- “Privacy” must not be assumed to mean legal-policy pages or unapproved data controls. Stage 8 and P-24 context remain relevant; define actual functions before adding them.

### Help

- Product direction: a help center with FAQs, usage guidance, and issue reporting.
- The exact route, initial content, reporting workflow, and launch scope remain to be specified. This proposal must not silently approve a route or operational process.

### Sign-in and return destination

- Google is the active sign-in option; Apple and Microsoft appear as “قيد التجهيز” cards, without any claim that those providers are enabled.
- A successful sign-in returns the user to the intended internal destination and preserves the search query when present.
- A sign-in flow initiated from the account menu returns to the previous page, preserving the query when present.
- External return destinations must be rejected.
- Technical validation of `returnTo`, crawler exceptions, preview cards, keyboard states, tests, and builds remains unverified and is not established by this product decision record.

### Non-blocking sign-up invitation

- Use context-sensitive wording on reaction and collection pages.
- The invitation must not block content.
- Show it once per browser; after close or continue, do not repeat it in that browser, including after logout. A different browser/device may show it.
- Exact final Arabic wording and close-button design remain open.

## 4. Traceability and affected prior decisions

| New Stage 5-B choice | Earlier decision/reference | Required reconciliation |
|---|---|---|
| Dedicated settings page | DECISION-I03; P-37 | Replace only the settings presentation pattern (modal → page) after canonical approval. Preserve approved appearance controls and the multi-accent/theme/motion decisions. |
| Settings categories | DECISION-I03; DECISION-I08; DECISION-I09; P-37; P-24 / Stage 8 | Specify actual available functions under Appearance, Account, Privacy; no empty sections. Privacy must not create unapproved legal pages or data controls. Preserve the Day-vs-Auto default conflict as unresolved. |
| Private identity, no public profiles | DECISION-I10 and existing rejected-social scope P-03 | Clarify private account identity only. Do not introduce public profiles, followers, public activity, or social features. |
| Guest account view with local saves | DECISION-I10; P-45; P-46; P-44 guest-save context | Reconcile the Account page with local guest saves and login flow; do not imply technical local-storage behavior has been audited. |
| Summary counts and Saved/My Contributions | Account-page choices in this 5-B discussion; P-05; 5.2.5 | Count published contributions only. My Contributions is an Account-page section, not an account-dropdown item. |
| `/saved` redirect with guest access | Existing accepted `/saved` route; P-46; guest-save context | Redirect `/saved` to Account with Saved selected while preserving guest access to local saves. Product route proposed; implementation not checked. |
| Remove Saved from desktop header | Existing desktop navigation in DECISION-I10 | Remove only Saved as a top-level destination; Saved remains accessible in Account. |
| Collections remain top-level | P-32–P-34 | Preserve collections as a primary destination; do not fold them into Account. Direct collection URLs must open content without login redirect. |
| Send Reaction in Library and Account; not global mobile header | DECISION-I10 and 5.2.76 | Reconcile old header/plus-button wording narrowly. Preserve `/submit` availability and the existing Google sign-in-on-submit flow. Do not interpret this as withdrawing Send Reaction from Library. |
| Split desktop account image and arrow | DECISION-I10 / P-45 account menu | Image opens Account page; arrow opens dropdown. Add keyboard/focus behavior without changing the agreed pointer behavior. |
| Guest account menu and sign-in flow | DECISION-I10; P-45; 5.2.5 | Guest menu item “تسجيل الدخول” opens full sign-in page; no “continue as guest” inside this flow; do not add My Contributions to dropdown. |
| Library first-visit gate | 5.1 Library surface; 5.2.2; P-46 | Optional gate/invitation must not block browsing; allow “الاستمرار كزائر”; direct reaction/collection links remain direct. |
| Contextual sign-up invitation | P-32–P-34; 5.2 account/login context | Non-blocking, context-specific, once per browser. Final copy and close affordance remain open. |
| Safe sign-in return | 5.1 and 5.2 search/return decisions | Preserve internal destination and query; reject external destinations. Product intent is recorded; technical security is not audited. |
| Help center direction | DECISION-I10 Help menu item; prior route status OPEN/unspecified | Keep destination route and detailed workflow OPEN until specified. Do not invent `/help`. |
| Visual review of header | Earlier header proposals and prototype/audit report | Require visual comparison before final visual approval. Do not infer Pinterest inspiration without a specified reference. |
| Mobile navigation structure | Prior mobile bottom navigation; P-32–P-34 | Keep Library, Collections, Account. Do not reopen ordering solely based on the prototype/audit report. |
| E architecture | Prior mobile bottom navigation and desktop header decisions | Reconcile only the changed navigation structure. Preserve historical decisions as historical records; do not erase them. |

## 5. Prior decisions requiring narrow review

1. **DECISION-I03 / P-37:** the settings modal presentation is superseded only if the founder approves and canonicalizes the dedicated-page choice; settings values are not automatically superseded.
2. **DECISION-I10 / P-45:** update mobile account destination and desktop image/arrow behavior; preserve guest/signed-in/admin menu content except the explicitly changed guest sign-in label/flow and the rule that My Contributions is not in the dropdown.
3. **P-45 / DECISION-I10 mobile bottom sheet:** the Account bottom-navigation item opens the Account page. Review the prior bottom-sheet account-menu pattern only within this scope; do not reopen unrelated 5.2 decisions.
4. **Existing `/saved` route:** redirect to Account with Saved selected, preserving guest access to saved content, subject to canonical approval. This is not proof of implementation.
5. **DECISION-I10 / 5.2.76 Send Reaction entry points:** ensure Send Reaction remains available from Library and Account while removing it from the global mobile header and mobile bottom navigation; preserve `/submit` and the Google sign-in requirement at submission.
6. **P-32–P-34:** reaffirm Collections as an independent destination and direct links as direct content entry; do not change collection behavior as a side effect of moving Saved into Account.
7. **P-03 social exclusions:** preserve rejection of public profiles, followers, likes/comments, social feeds, and similar network features.
8. **Theme default conflict:** P-37 Day default versus DECISION-I08 Auto default remains unresolved; this proposal does not choose one.
9. **Sign-in return flow:** record product behavior only; `returnTo` safety and crawler/preview behavior need a separate technical review.
10. **Header visual design:** interaction behavior is recorded, but final overall header visual layout remains OPEN pending visual comparison.

## 6. Open specifications

- Exact route names for sign-in, account, settings, and help; do not assume `/login`, `/account`, `/settings`, or `/help` without explicit approval.
- Which concrete, already-approved controls belong in each Settings section.
- Whether the existing settings-reset action resets appearance only or a broader set of settings; do not broaden its scope silently.
- Exact fields required for contribution attribution before identity editing can be designed.
- Exact definition and display formatting of saved count, including consistency with guest-local saves after sign-in.
- Exact empty states for Saved and My Contributions.
- Help center route, content, reporting workflow, and launch scope.
- Final Arabic copy and close-button design for the contextual sign-up invitation.
- Visual header alternatives and any inspiration reference the founder wants to use.
- Implementation details and runtime behavior for redirects, focus management, keyboard operation, guest-save merging, session behavior, crawler exceptions, preview cards, and return-destination validation remain unverified.

## 7. Governance and exclusions

- This document is a proposal only.
- Do not edit canonical files, the decisions log, README, or `main` directly.
- Do not merge this proposal PR without the founder's explicit approval.
- Preserve decision history. Mark only the exact affected scope as SUPERSEDED after approval; do not delete historical entries.
- Stage 5.1 and Stage 5.2 remain closed. Do not reopen C-01 or P-20 #6, assign a successor to P-20 #6, or create Stage 5.3.
- No code, build, database changes, runtime verification, or security audit is included. SEC-06 remains unaudited.
