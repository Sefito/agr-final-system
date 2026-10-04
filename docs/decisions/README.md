# Decision register

Statuses describe design intent, not implemented guarantees. Selected reflects customer direction; provisional is a working choice; proposed needs validation; open has no option selected.

| Record | Status | Decision |
|---|---|---|
| [0001](0001-modular-monolith.md) | Modular monolith retained; placement superseded | Shared business architecture, optional workflow engine |
| [0002](0002-module-transactions.md) | Proposed | Package-owned commands share explicit business transactions |
| [0003](0003-proposals-and-execution.md) | Proposed; engine open | Persistent proposals and failure-tested execution choice |
| [0004](0004-customer-owned-azure.md) | Ownership selected; operations proposed | Separate deployment/support/runtime access |
| [0005](0005-document-lifecycle.md) | Identity/explorer selected; storage provisional | Catalogue distinct from indexing; retain originals/identity |
| [0006](0006-monorepo-and-packages.md) | Separation requested; tooling/design proposed | Thin hosts, public packages, uv/pnpm/Nx and import verification |

## Remaining decisions

Authentication topology and membership authority; organization/project fields and CRM command details; simple file formats/upload readiness; source ACL mapping/write-back/deletion; retention; approved models/embedding space; business tariffs; Azure region/sizing/recovery requirements; migration/persistence tools; exact dependency pins and workflow engine.

Package separation and task scheduling must not silently settle these product/security choices. Resolve them before the relevant implementation/real-client gate in the [delivery sequence](../architecture/delivery-sequence.md).

## Functional baseline

The [functional requirements draft](../requirements/functional-requirements.md) records confirmed scope, inherited rules, proposed behavior and optional SharePoint capabilities. First-release CRM scope is now confirmed: organizations, projects and document attachments only. Opportunity/contact/pipeline/task management is outside this release. Architecture decisions do not imply acceptance of the whole functional draft.
