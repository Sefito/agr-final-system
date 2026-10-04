# Concrete adapters package

Status: adapter package boundary selected; SDK/persistence selection open.

Implement ports owned by access, documents, intelligence, commercial, CRM and usage. Adapters depend on these public interfaces; business packages do not depend on adapters. API/worker bootstrap injects implementations.

[src/agr_adapters](src/agr_adapters/README.md) groups concrete persistence, Azure, SharePoint and model transports. Keep provider payloads and database connection objects behind adapter boundaries. No end-user authorization, approval or pricing rule originates here.

Package public exports expose factories/adapters required for composition. Optional source/provider dependencies must be selective so an API installation does not need every extraction/synchronization SDK. Exact extras/split criteria will be measured with the first slice.

If this package acquires genuinely incompatible/heavy dependency sets, split a measured adapter family into another package. Do not pre-create one package per SDK. No shared runtime-framework package or universal repository is selected.
