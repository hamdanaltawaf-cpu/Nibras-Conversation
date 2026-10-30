# DECISION — OPEN-Q-08: Search and Indexing for YemReact

**Status:** ACCEPTED — resolved by delegated review authority on 2026-10-28  
**Scope:** Search retrieval, indexing inputs, derived-data governance, normalization, ranking, no-result handling, and quality evaluation. Product/search policy only; not implementation evidence.  
**Authority:** Founder explicitly delegated review authority and authorized recording the decision, updating canonical files, and merging the PR after review.  
**Related item:** OPEN-Q-09 — automatic speech extraction from video — remains separate from OPEN-Q-08 and is CLOSED FOR DOCUMENTATION only in its own canonical decision; implementation remains unverified.

## Decision summary

YemReact search must help users find the **specific reaction itself**, not search by situation. The search system should not depend on editors manually entering keywords. It should use available trusted source fields and controlled derived data, combining direct text retrieval, flexible matching, and semantic retrieval.

## 1. Searchable source fields

Index available and sufficiently reliable fields, as applicable:

1. Speech embedded in a video, when a transcript is available and sufficiently reliable.
2. Reaction title.
3. Reaction description.
4. Confirmed character name, when applicable.
5. Quality-controlled alternate search forms derived automatically, where useful.
6. A semantic representation of the reaction to support retrieval when the query wording differs from indexed text.

Not every reaction must have every field. Failure to obtain one field must not prevent indexing other valid fields.

## 2. Controlled automation and data provenance

- Automatically index trusted data; route doubtful data for appropriate review.
- Keep original source data separate from derived data.
- Record the source, processing type, and verification status for derived data.
- Do not attribute AI-generated text to a speaker as verbatim speech without supporting evidence.
- Evaluate confidence per data type rather than applying one universal confidence threshold.
- Allow incorrect derived data to be disabled without destroying original data.
- Design reprocessing to be retry-safe and idempotent, and refresh indexes when source data changes.
- A failed extraction in one field must not block valid data from other fields.

These are requirements, not proof that the corresponding automation exists or has been tested.

## 3. Text normalization and matching tiers

Use three complementary tiers:

1. **Safe normalization:** automatically normalize only spelling variations considered safe, while preserving the original text.
2. **Flexible matching:** when direct matching is insufficient, tolerate suitable spelling errors and near variants while avoiding conflation of terms with different meanings.
3. **Semantic retrieval:** help find the same reaction when the user’s wording differs from the indexed wording, while retaining a strong preference for trustworthy direct textual matches.

Do not introduce a broad Yemeni dialect transformation dictionary without grounding it in real library data and evaluating whether it improves retrieval without changing meaning.

## 4. Ranking

Use a composite relevance score based on match strength and data reliability rather than a fixed ordering that ignores the query type. Relevant signals include:

- Direct match to available embedded speech.
- Title match.
- Confirmed character-name match.
- Description match.
- Flexible textual match.
- Quality-controlled derived alternate forms, weighted according to their reliability.
- Semantic similarity.

Trustworthy direct textual matches receive a strong preference, especially distinctive phrases spoken in the reaction. A semantic result may outrank a text-matched result only when evaluation shows it is clearly closer to the intended reaction.

Do not lock numeric weights until testing on a representative evaluation set.

## 5. Weak or missing results

- If there is no direct match, show the best available flexible and semantic results without presenting them as confirmed matches.
- If relevance is weak, communicate that the results may not match exactly; do not imply unjustified confidence.
- If there are no useful results, show a clear message and let the user revise the query.
- Failed or unhelpful queries may be used to identify indexing gaps and improve search, subject to privacy controls.
- A failed query must not trigger arbitrary automatic keyword additions. New derived data remains subject to provenance, reliability, and review controls.

## 6. Evaluation before numeric tuning or launch claims

Create a fixed evaluation set representative of real use, covering:

- Exact phrases from embedded speech.
- Spelling mistakes and variations in writing Yemeni dialect.
- Title and confirmed character-name queries.
- Queries whose wording differs from the indexed text but refer to the same reaction.
- Queries with no suitable reaction in the library.
- Cases where multiple reactions share the same or similar phrase.

Evaluate at least:
1. Whether the intended reaction appears among the first results.
2. Whether the intended reaction ranks ahead of less relevant results.
3. Whether weakly related results are misleadingly presented as correct.
4. Whether semantic retrieval improves discovery without undermining trustworthy direct textual matches.

Test each retrieval method separately and then test the hybrid system. This decision does not set numeric acceptance thresholds or final scoring weights; those require evidence from evaluation.

## 7. Speech extraction boundary — OPEN-Q-09 remains separate

OPEN-Q-08 defines that extracted speech may be used as a search source **when it is available and sufficiently reliable**. It does not choose, require, implement, or certify a video speech-extraction technology.

OPEN-Q-09 remains separate and CLOSED FOR DOCUMENTATION only in its own canonical document; its extraction method and accuracy challenges remain policy requirements, not verified implementation.

## 8. Closure and verification boundary

This decision resolves the product/design question OPEN-Q-08 for documentation purposes. It does not mean search indexing, transcription, semantic retrieval, ranking, analytics, or evaluation tooling has been implemented, tested, or verified.

Stage 5 remains OPEN. Do not create Stage 5.3 or start Stage 6. OPEN-Q-09 is closed for documentation only in its separate document; this does not verify extraction implementation. SEC-06, server-side upload enforcement, route behavior, tests, builds, and runtime remain unverified unless separately verified.

## Review outcome

The delegated review found the proposed policy coherent and sufficiently bounded to record: it preserves the product requirement to search for the reaction itself, separates source data from derived data, gives trustworthy direct text strong priority, requires evaluation before numeric tuning, and keeps speech extraction outside this decision. The policy is accepted with the boundaries and verification limits above.

## Current status reconciliation — 2026-10-30
The OPEN / Stage 5 OPEN wording above records the state when this decision was drafted and accepted on 2026-10-28; it is retained as historical context, not the current state. As of 2026-10-30, OPEN-Q-08 is **CLOSED FOR DOCUMENTATION ONLY** and Stage 5 is **CLOSED FOR DOCUMENTATION ONLY** under the explicit closure record in `stage-2-reformation/STAGE-5-DOCUMENTATION-CLOSEOUT-RECORD.md`. OPEN-Q-09 remains a separate decision and is also closed for documentation only in its own document. Search/indexing and speech-extraction implementation, tests, quality, security, and runtime remain unverified/deferred. This addendum does not authorize implementation.

## Current status reconciliation — 2026-10-30
The OPEN / Stage 5 OPEN wording above records the state when this decision was drafted and accepted on 2026-10-28; it is retained as historical context, not the current state. As of 2026-10-30, OPEN-Q-08 is **CLOSED FOR DOCUMENTATION ONLY** and Stage 5 is **CLOSED FOR DOCUMENTATION ONLY** under the explicit closure record in `stage-2-reformation/STAGE-5-DOCUMENTATION-CLOSEOUT-RECORD.md`. OPEN-Q-09 remains a separate decision and is also closed for documentation only in its own document. Search/indexing and speech-extraction implementation, tests, quality, security, and runtime remain unverified/deferred. This addendum does not authorize implementation.
