# CRM

Status: redesign authorized; initial entity model proposed.

## Responsibility

Own the agreed commercial records, commands, relationships and activity history. The UI and agent call one set of application commands. Documents owns file identity/content and is referenced through its public operations.

## Initial proposal

Start with organization/customer and project records sufficient for scope selection and document attachment. Add opportunities, contacts, tasks or funnel stages only when the agreed initial use cases need them. Do not reproduce the whole legacy mock-up as if it were implemented CRM scope.

## Decisions

- Validate project ownership and access before mutation or attachment.
- Resolve document attachment through documents rather than duplicating file storage.
- Use explicit create/update operations with typed inputs, validation and concurrency checks for editable records.
- Record actor, operation identity and an activity projection for successful changes. Full before/after audit data may need tighter access than the current entity.
- Hidden values remain hidden in lists, exports, history and aggregates. A redacted or unknown amount is not zero.
- Agent-generated requests have no special bypass around the UI's command validation.
- No generic undo is promised. A reversal is an explicit operation with current validation when needed.

## Acceptance cases

UI/agent enforce the same required fields and access; duplicate project requests have defined idempotency; concurrent updates produce a conflict; an inaccessible project reveals no attachment metadata; audit history does not reconstruct a protected field.

## Open decisions

Agree the first entities and workflows, field-level sensitivity if actually needed, ownership of organization master data, external CRM import/export and retention. Choose persistence conventions with the backend/database implementation, not independently here.
