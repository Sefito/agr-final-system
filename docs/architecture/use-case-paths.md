# Use-case paths and commit ownership

Status: proposed interaction contracts; method names and API schemas are not selected.

## Consultation

API resolves an authenticated actor and validates conversation ownership/scope. Assistant applies guards and asks retrieval for authorized evidence. A model adapter generates under the approved processing policy. Assistant validates answer/citations and records conversation results with attributed usage. Transport emits a safe event projection.

No commercial graph is required for this path. Reusing prior history must respect the actor's current ceiling. Cancellation and persistence semantics must be agreed before streaming implementation.

## Browse and upload

API asks documents for an authorized folder projection. Folder/file names, counts and indexing status are filtered at the backend. Upload staging validates size/type/archive constraints, scope and destination. A documents command stores the original and identity/relationship records; extraction/indexing produces derived retrieval state.

Choose readiness explicitly: preserve the legacy successful-response-with-lexical-evidence behavior or introduce an agreed asynchronous processing contract. A successful byte upload is not automatically an indexed file. Embedding failure is separate from successful lexical indexing.

## Draft, edit and approval

Commercial resolves the authorized scope/document type, obtains validated evidence and produces a versioned proposal. Model output supplies content, never write authorization. The user reviews an authorized projection and submits the proposal identity/expected version.

Commercial rechecks approval, identity and evidence. Documents checks the current base/publication state. Applicable usage receipts participate in the same transaction as document bytes/version/citations and the business operation outcome. Individual participants do not commit independently.

A successful commit followed by a lost response is reconciled by operation identity. Do not regenerate or charge again merely because the browser did not receive a terminal event. Model calls before commit may still have real costs and need attempt attribution.

## Publication

Commercial requests confirmation against the current version. Documents atomically changes the active published version after permission/evidence revalidation. A draft does not retire an earlier final document. Retrieval updates the published corpus under the chosen readiness contract.

If publication and minimum lexical index readiness must be atomic, their participants share the transaction. Later embedding enrichment is recoverable. Never hide a distributed consistency requirement behind independent module calls.

## CRM and attachments

UI and commercial agent invoke the same CRM command. CRM owns record validation, expected version and authorized activity projection. Document attachment invokes documents with an explicit authorized project relationship. Identity owns memberships; CRM owns organization/project business records, avoiding duplicate directory data.

## Optional source synchronization

SharePoint adapter reads configured sources and reports stable item/hierarchy changes. Documents applies occurrence/source-state changes; retrieval schedules/reconciles derived content. Synchronization records durable progress and safely retries repeated items. Source ACL changes are not assumed to arrive as content changes.

## Failure contracts shared by these paths

Define invalid input, no authorized resource, insufficient evidence, stale proposal, concurrency conflict, provider unavailable, cancellation and uncertain completion separately. Public errors disclose no protected titles/content. Recoverable task state identifies its authority and execution revision; business rows remain the authority for committed results.
