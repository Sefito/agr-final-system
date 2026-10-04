# Business modules

Status: ownership map selected.

Each child owns a specific business vocabulary, its authorized application operations and its writes. Read its README before changing it.

| Folder | Public responsibility |
|---|---|
| [identity](identity/README.md) | Current principal, membership and access policy |
| [documents](documents/README.md) | Catalogue, versions, originals and publication |
| [retrieval](retrieval/README.md) | Authorized evidence and derived indexes |
| [assistant](assistant/README.md) | Consultation conversations and answers |
| [commercial](commercial/README.md) | Document proposals, approvals and workflow coordination |
| [crm](crm/README.md) | Agreed commercial record commands |
| [usage](usage/README.md) | Provider usage and business receipts |

Module-to-module interactions use explicit application interfaces. A coordinated SQL transaction may span module-owned writes through a shared transaction context; each module still controls its own invariants. Avoid cyclic orchestration: commercial/assistant coordinate operations, while documents/retrieval/identity do not call those product coordinators back.

Introduce internal subpackages only when concrete code warrants them. This documentation pass does not create empty domain/application/repository layers. Dependency enforcement and exact public interfaces remain implementation work.
