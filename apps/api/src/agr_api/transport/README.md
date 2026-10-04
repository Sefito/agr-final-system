# HTTP and streaming API

Status: transport boundary selected; endpoint/event schemas proposed.

## Responsibility

Map authenticated requests to typed application use cases and translate outcomes into HTTP responses or authorized events. Own transport validation and contract documentation, not business transactions or workflow progression.

## Decisions

- Separate request/response models from domain types and provider SDK payloads.
- Authenticate and check conversation/resource ownership before opening a stream where possible. After response headers, failures need an explicit terminal event contract.
- Mutation requests carry operation identity and expected version where relevant. Approval identifies the reviewed proposal, not arbitrary free-form instructions.
- Downloads pass through an authorized operation. Do not expose filesystem paths, bearer tokens in query strings or unrestricted storage URLs.
- Public stream events contain intentional projections. Raw checkpoints, source text, prompts, principal objects and provider errors are not forwarded.
- HTTP schemas and streaming schemas have separate versioned contracts. Generated HTTP clients do not automatically type SSE.
- Diagnostic endpoints disclose only what their audience is authorized to see. Liveness must not return document counts, credentials or model/database diagnostics.

## Proposed contract families

Current actor/scopes; consultations; document catalogue/uploads/downloads; commercial runs/proposals/approvals; CRM commands; authorized usage views. Exact routes and naming are open. Define non-disclosing not-found, conflict, invalid-input and unavailable outcomes consistently.

## Acceptance cases

Authorization fails before streaming; duplicate mutation returns a defined result; a dropped stream can be reconciled against business status; an unknown event is handled according to compatibility rules; a protected filename never leaks through an error.

## Open decisions

Select FastAPI or another transport library with the first implementation. Define authentication topology, cookie/CSRF handling if applicable, request limits, stream event IDs/replay and API evolution policy. A progress event is not proof of a committed business operation.
