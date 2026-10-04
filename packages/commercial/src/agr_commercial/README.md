# Commercial workflows

Status: business scope selected; orchestration and execution engine proposed/open.

## Responsibility

Coordinate drafting, edit proposals, simple supported import and final publication through public document, retrieval, CRM and usage operations. Own commercial conversation/run/proposal/approval records. Do not own document version storage or duplicate CRM command rules.

## Initial use cases

| Use case | Lifecycle |
|---|---|
| Draft | Resolve scope/type, gather authorized facts, identify missing information, generate, review and save after required confirmation |
| Edit | Select an authorized base version, propose bounded changes, show the proposal and apply it after explicit approval |
| Import | Stage and validate an agreed supported file, associate it with the correct document/version and confirm its treatment |
| Publish | Revalidate version/evidence/permissions, confirm and atomically change publication state |
| CRM action | Invoke the same authorized command used by the UI, with a reviewable payload and explicit confirmation for writes |

Complex-file reconstruction is outside this iteration. Talent/HR, methodology agents and every future roadmap workflow are not implied by this folder.

## Decisions

- Store a proposal identity/version and a structured approval action. Free-form model text cannot grant permission to commit.
- Bind approval to actor, scope, expected document version, proposal content and evidence revision. Expired or changed inputs require renewed review.
- Reauthorize references at evaluation and commit. Before validation, reference content is unavailable; formatting references contribute structure rather than substantive evidence.
- No credentials or actor/ceiling snapshots in a checkpoint are trusted as current authorization.
- A pending approval is persisted data, not a process that waits indefinitely.
- Keep progress, business state and technical execution state separate with an explicit authority for each. Avoid two unrelated mirrors of the entire run.
- LangGraph and Durable Functions remain alternatives. Do not introduce both into production for the same workflow.

## Transaction and recovery

Long generation produces durable step results or a proposal. The eventual save command shares a transaction with document writes and any required usage receipt. Use an operation identity to return a previously committed result after retries. A checkpoint alone cannot guarantee exactly-once provider calls or business effects.

Task ownership, cancellation, bounded retries and restart recovery belong to a defined execution contract. Browser disconnect must have an explicit policy per operation; it must not accidentally save or charge unwanted work.

## Acceptance cases

Crash mid-generation; duplicate/stale approval; another user changes the base version; permission revoked while waiting; commit succeeds before the response is delivered; a deployment changes executable workflow versions; extraction/model output fails validation.

## Open decisions

Select one workflow engine from a complete failure-tested slice. Define which actions continue after disconnect, who may approve someone else's proposal, pending-task retention and the exact initial import semantics.
