# DECISION-5B.24 — Guest Saves Reconciliation at Sign-in

**Status:** ACCEPTED  
**Date:** 2026-10-28  
**Authority:** Founder delegated full decision authority after review of conflicts and likely effects.  
**Scope:** Stage 5-B product behavior; not implementation evidence.

## Decision

1. **Additive merge:** after successful sign-in, merge guest-local saved reaction codes into the signed-in account's existing saved reactions. Neither set overwrites the other.
2. **Deduplication:** deduplicate by unique reaction code. The same reaction saved locally and in the account appears only once.
3. **Safe persistence:** do not clear or discard guest-local saves until the server confirms successful persistence of guest-only additions. If synchronization fails or the network is unavailable, preserve local data and allow retry. Retrying must be idempotent and must not create duplicates.
4. **Account isolation:** keep guest-local saves distinct from account-associated saves. Never copy a signed-in account's saves into the shared guest-local set on sign-out. A different account signing in on the same device must not inherit the previous account's saves.
5. **Unavailable content:** a saved code does not make deleted, unpublished, or otherwise unavailable content available. Handle unavailable entries under the content-availability rules without discarding other valid saves.
6. **Guest access and routing:** preserve guest access to local saves and the intended /saved behavior (Account with Saved selected).

## Conflict review and technical implications

The canonical technical record T-07 currently states that the implementation uses localStorage key yr:saved, merges it with /api/me/saves, and does not clear local storage on logout. A shared local key can conflict with account isolation if account data is written into it or treated as guest data. The implementation must distinguish the guest-local set from account-scoped saves and must only merge the independent guest set into the account that signs in.

The merge should be safe under repeated login callbacks, retries, and partial network failures. Server confirmation is required before guest data is considered synchronized and eligible for cleanup. If the existing design cannot distinguish guest-local from account-associated saves, it must be corrected before claiming this decision is implemented.

## Acceptance criteria

- Existing account saves remain intact.
- Guest-only saves are added to the signed-in account.
- Duplicate reaction codes are stored/displayed once.
- A failed sync does not lose guest-local saves.
- Retrying sync is idempotent.
- Signing out does not place account saves in the shared guest store.
- A different account on the same device cannot see the previous account's private saves.
- Unavailable reactions are not falsely presented as available, and their state does not delete unrelated valid saves.
- Guest saves remain accessible without login.

## Governance and verification boundary

This is product policy only. It does not establish that code, tests, builds, redirects, database behavior, or runtime have been changed or verified. Stage 5 remains OPEN. Do not create Stage 5.3 or start Stage 6. OPEN-Q-08 and OPEN-Q-09 remain separate and open. SEC-06, server-side upload enforcement, routes, tests, builds, and runtime remain unverified.
