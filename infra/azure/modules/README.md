# Azure resource modules

Status: Bicep modularization proposed; no templates written.

## Responsibility

Define reusable resource groups/components for the selected customer-local deployment. A module has clear inputs/outputs and owns a meaningful resource boundary, not one wrapper per every Azure property.

## Initial resource candidates

Container Apps runtime/environment; PostgreSQL Flexible Server and access configuration; Basic ACR; bounded monitoring; runtime identities and role grants. Batch jobs and Blob mirrors are conditional on processing/source needs. Do not provision a workflow service before its decision.

## Decisions

- Customer-specific values are parameters. Names, tenant/subscription and region are not hard-coded.
- Separate runtime grants from deployment/support access. Bootstrap role assignments have different authorization from ordinary releases.
- Use direct authenticated ingress initially unless customer controls require additional networking. Premium edge/messaging/HA are escalation options, not folder-structure requirements.
- Secrets are references/secure parameters, not template outputs or committed parameter values.
- Specify deletion/retention behavior for stateful resources. Infrastructure replacement is not a database migration.
- Lighthouse delegation is optional operations setup; it does not grant Microsoft Graph or Entra directory authority.

## Acceptance and open decisions

Review planned changes before deployment; demonstrate repeatable synthetic deployment; prevent unintended stateful replacement; validate identity/resource scope. Choose regions/SKUs/availability after measured workload and customer requirements. No availability or recovery SLA is promised yet.
