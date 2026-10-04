# Reusable workspace packages

Status: logical package boundaries selected; manifests/builds pending.

| Package | Future import/name | Reason for boundary |
|---|---|---|
| [access](access/README.md) | `agr_access` | Stable policy vocabulary reused everywhere |
| [documents](documents/README.md) | `agr_documents` | One owner of identity/bytes/version/publication invariants |
| [intelligence](intelligence/README.md) | `agr_intelligence` | Retrieval and consultation share evidence/model policy |
| [commercial](commercial/README.md) | `agr_commercial` | Proposal/approval coordination evolves independently of transport |
| [crm](crm/README.md) | `agr_crm` | UI/agent share agreed record commands |
| [usage](usage/README.md) | `agr_usage` | Inference attempts and immutable charge receipts have distinct lifecycle |
| [adapters](adapters/README.md) | `agr_adapters` | Concrete SDK/SQL mechanisms implement business-owned ports |
| [api-client](api-client/README.md) | `@agr/api-client` | Web transport generated from actual HTTP/event contracts |
| [ui](ui/README.md) | `@agr/ui` | Presentation primitives independent of product state |

Python packages use `src/` layout and package-local tests. Their manifests will declare direct workspace dependencies explicitly. TypeScript packages have declared public exports. Keep one coherent release rather than an independent publishing pipeline per package.

Do not create a package per entity, one per CRUD operation, or an unbounded common/shared-kernel package. Assistant/retrieval remain internal submodules of intelligence. A package can grow internal modules without becoming another service.

See [dependency rules](../docs/architecture/package-dependencies.md). Package paths alone do not enforce isolation; verification must inspect actual imports and build dependencies.
