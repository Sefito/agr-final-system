# Azure runtime adapters

Status: customer-local resource access selected; concrete adapters conditional.

## Responsibility

Connect runtime operations to selected Azure data resources and approved telemetry. Bicep resource provisioning belongs to `infra/azure/`, not this adapter folder.

## Decisions

- Use runtime identities with resource-specific grants. Deployment/support roles are separate.
- Resource configuration identifies the customer-local endpoint; code contains no customer-specific names.
- Introduce Blob operations only if source mirroring or a measured storage requirement needs them.
- Keep protected originals behind document authorization. A stored object key is not an access decision.
- Renew credentials/tokens correctly for long-lived connection paths. Do not assume a token acquired once at startup is permanent.
- Provider failures are mapped to typed unavailable/uncertain outcomes without raw secret-bearing errors.

## Acceptance cases

Credentials refresh without crossing customer resources; a provider timeout does not create a business success; retrying an optional mirror operation has deterministic object/version identity; logs contain no source content or credentials.

## Open decisions

List the exact runtime Azure services and SDK versions after infrastructure selection. Select passwordless PostgreSQL connection handling, optional mirror consistency/cleanup and telemetry destinations. No Azure resource is provisioned by this documentation.
