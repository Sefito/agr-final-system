# Customer-owned Azure deployment

`modules/` will contain reusable Bicep resource definitions. `environments/` will contain synthetic parameter examples. Keep real client parameter files outside version control; `environments/private/` is ignored for local use.

The initial candidate resources are Container Apps, PostgreSQL Flexible Server with pgvector, Basic ACR and bounded telemetry. Jobs and optional Blob mirrors are added when a concrete processing/source use case needs them. This scaffold provisions nothing.

Customer administrators authorize bootstrap and role assignments. Subsequent releases can use a customer-local federated GitHub deployment identity. Optional Azure Lighthouse delegation supports fleet operations separately from deployment, runtime, Entra and SharePoint permissions.

Keep runtime identities separate from deployment/support access. Version each release and its client configuration. No mandatory Premium edge, messaging or workflow service is selected here.
