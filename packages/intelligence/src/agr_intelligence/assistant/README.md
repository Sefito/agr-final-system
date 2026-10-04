# Assistant consultations

Status: use-case boundary selected; conversation/event contracts proposed.

## Responsibility

Own consultation conversations, question handling, evidence-backed answers and their citations. Retrieval supplies authorized evidence; model adapters perform inference; identity supplies current access context.

## Decisions

- A consultation is an ordinary use case; no graph engine is required merely to search and answer.
- Conversation ownership and fixed scope are validated before streaming begins.
- Privacy, missing evidence and unauthorized requests fail closed. Model confidence does not override a missing source.
- Only cite labels present in the returned evidence set. Preserve exact names, dates and figures.
- Bound context and model output. Optional search planning has a deterministic fallback for invalid output.
- Persist safe conversation history and explicit completion/cancellation state. Scope/ceiling changes must not reuse unauthorized history.
- Provider/model selection is explicit; the presence of a credential does not authorize sending customer content.

## Request lifecycle

Authenticate and validate ownership/scope; evaluate guards; retrieve evidence; select context; generate and validate an answer; persist answer/citations/usage; emit a terminal outcome. Public events are authorized projections, not raw prompts or internal workflow state.

A cancelled or disconnected consultation is not reported as successfully completed without a defined continuation policy. Consultation semantics may differ from a durable document job.

## Acceptance cases

Foreign conversation access fails before HTTP streaming; unsupported claims produce an insufficient-evidence response; invalid citation labels are rejected; provider outage is explicit; lowered access cannot recover protected facts from old history.

## Open decisions

Choose history retention, disconnect/cancellation behavior, exact stream event schemas and whether structured responses need a bounded validation retry. Keep these policies explicit instead of relying on SDK defaults.
