# YemReact Stage 5-B — Account, Header & Navigation Proposal

**Status:** Proposal for review only — not canonical, not merged  
**Date:** 2026-10-18  
**Authority:** Founder choices recorded in the 5-B discussion  
**Scope:** Documentation and decision reconciliation only. No code, build, database, runtime, or security audit.

## Purpose

Record the founder's explicit choices from 5-B.07 through 5-B.18, identify affected earlier decisions, and propose narrowly scoped updates. Preserve history; do not directly edit canonical files, the decisions log, README, or `main`. Nibras should update canonical documentation only after founder review and approval of this proposal.

## 1. Explicit founder choices

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

## 2. Consolidated target experience

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
- Saved is reached inside Account.

### Account page

**Signed-in user:**
- Private identity area.
- Compact summary of saved-reaction count and published-contribution count.
- A switcher: **Saved | My Contributions**.
- The selected section's list appears below.
- If there are no contributions, show an appropriate empty state.
- Settings and Send Reaction actions appear on the Account page.

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

### Help

- Product direction: a help center with FAQs, usage guidance, and issue reporting.
- The exact route, initial content, reporting workflow, and launch scope remain to be specified. This proposal must not silently approve a route or operational process.

## 3. Traceability and affected prior decisions

| New 5-B choice | Earlier decision/reference | Required reconciliation |
|---|---|---|
| Dedicated settings page | DECISION-I03; P-37 | Replace only the settings presentation pattern (modal → page). Preserve approved appearance controls and the multi-accent/theme/motion decisions. |
| Settings categories | DECISION-I03; DECISION-I08; DECISION-I09; P-37 | Specify actual available functions under Appearance, Account, Privacy; no empty sections. Preserve the Day-vs-Auto default conflict as unresolved. |
| Private identity, no public profiles | DECISION-I10 and existing rejected-social scope P-03 | Clarify private account identity only. Do not introduce public profiles, followers, public activity, or social features. |
| Guest account view with local saves | DECISION-I10; DECISION-I10 guest menu; DECISION-I10/P-44 and guest-save context | Reconcile the Account page with local guest saves and login flow; do not imply technical local-storage behavior has been audited. |
| Summary counts and Saved/My Contributions | Account-page choices in this 5-B discussion; contribution moderation policy P-05 | Count saved items according to the displayed Saved section; count published contributions only. The exact definition of a saved-count total should match the implemented product behavior when verified. |
| `/saved` redirect | Existing accepted `/saved` route; DECISION-I10 account navigation | Redirect to Account with Saved selected. Preserve existing links where possible; implementation and route behavior are not checked by this proposal. |
| Remove Saved from desktop header | Existing desktop navigation in DECISION-I10 | Remove only Saved as a top-level destination; Saved remains accessible in Account. |
| Collections remain top-level | P-32–P-34 | Preserve collections as a primary destination; do not fold them into Account. |
| Send Reaction in Library and Account; not global mobile header | DECISION-I10 and 5.2.76 | Reconcile old header/plus-button wording narrowly. Preserve `/submit` availability and the existing sign-in-on-submit flow. Do not interpret this as withdrawing Send Reaction from Library. |
| Split desktop account image and arrow | DECISION-I10 account menu | Image opens Account page; arrow opens dropdown. Add keyboard/focus behavior without changing the agreed pointer behavior. |
| Help center direction | DECISION-I10 Help menu item; prior route status OPEN/unspecified | Keep destination route and detailed workflow OPEN until specified. Do not invent `/help`. |
| E architecture | Prior mobile bottom navigation and desktop header decisions | Reconcile only the changed navigation structure. Preserve historical decisions as historical records; do not erase them. |

## 4. Prior decisions requiring narrow review

1. **DECISION-I03 / P-37:** the settings modal presentation is superseded only if the founder approves this proposal; the settings values themselves are not automatically superseded.
2. **DECISION-I10:** update mobile account destination and desktop image/arrow behavior; retain menu contents according to guest/signed-in/admin state unless separately changed.
3. **P-45 / DECISION-I10 mobile bottom sheet:** the Account bottom-navigation item now opens the Account page. Review the prior bottom-sheet account-menu pattern only within this scope; do not reopen unrelated 5.2 decisions.
4. **Existing `/saved` route:** change it to redirect to Account with Saved selected, subject to canonical approval. This is a product-route proposal, not proof of implementation.
5. **DECISION-I10 / 5.2.76 Send Reaction entry points:** ensure Send Reaction remains available from Library and Account while removing it from the global mobile header and mobile bottom navigation.
6. **P-32–P-34:** reaffirm Collections as an independent destination; do not change collection behavior as a side effect of moving Saved into Account.
7. **P-03 social exclusions:** preserve rejection of public profiles, followers, likes/comments, social feeds, and similar network features.
8. **Theme default conflict:** P-37 Day default versus DECISION-I08 Auto default remains unresolved; this proposal does not choose one.

## 5. Open specifications (not blockers to recording the direction)

- Exact route name for the dedicated settings page.
- Which concrete, already-approved controls belong in each Settings section.
- Whether the existing settings-reset action resets appearance only or a broader set of settings; do not broaden its scope silently.
- Exact fields required for contribution attribution before identity editing can be designed.
- Exact definition and display formatting of saved count, including consistency with guest-local saves after sign-in.
- Exact empty states for Saved and My Contributions.
- Help center route, content, reporting workflow, and launch scope.
- Implementation details and runtime behavior for redirects, focus management, keyboard operation, guest-save merging, and session behavior remain unverified.

## 6. Governance and exclusions

- This document is a proposal only.
- Do not edit canonical files, the decisions log, README, or `main` directly.
- Do not merge this proposal PR without the founder's explicit approval.
- Preserve decision history. Mark only the exact affected scope as SUPERSEDED after approval; do not delete historical entries.
- Stage 5.1 and Stage 5.2 remain closed. Do not reopen C-01 or P-20 #6, assign a successor to P-20 #6, or create Stage 5.3.
- No code, build, database changes, runtime verification, or security audit is included. SEC-06 remains unaudited.
