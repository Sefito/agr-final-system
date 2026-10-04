# AGR Final System

A mixed Python/TypeScript monorepo for customer-owned Azure deployments of AGR. The runtime architecture remains a modular monolith: packages are code/dependency boundaries, not independently deployed business services.

This repository contains design documentation only. Workspace manifests, application code, package builds, lockfiles, CI and Azure resources are not implemented.

## Structure

```text
apps/
  api/src/agr_api/             HTTP/SSE transport and composition
  worker/src/agr_worker/       Recoverable job entry points and composition
  web/src/                    React application and product features
packages/
  access/src/agr_access/      Identity and authorization contracts
  documents/src/agr_documents/ Catalogue, originals, versions and publication
  intelligence/src/agr_intelligence/
    retrieval/               Evidence search and index lifecycle
    assistant/               Consultation use cases
  commercial/src/agr_commercial/ Proposals, approvals and workflow coordination
  crm/src/agr_crm/            Agreed commercial records and shared commands
  usage/src/agr_usage/        Inference attribution and business receipts
  adapters/src/agr_adapters/  Concrete persistence, Azure, source and model adapters
  api-client/                Generated HTTP client and event transport
  ui/                        Reusable presentation primitives
contracts/
  http/                      Reviewed OpenAPI artifacts from API contracts
  events/                    Language-neutral streaming event specifications
  fixtures/                  Invented compatibility examples
tests/system/                Cross-package and application verification
db/migrations/               One coordinated PostgreSQL schema history
infra/azure/                 Customer-local Bicep resource design
clients/examples/            Invented configuration examples
scripts/                     Workspace maintenance entry points
docs/                        Architecture and decisions
```

Each package/application owns local specifications and planned tests. Every folder has a README. Detailed ownership and allowed dependencies are in the [architecture index](docs/architecture/README.md).

## Workspace tooling proposal

- **uv workspace**: Python applications/packages, member manifests and one Python lockfile.
- **pnpm workspace**: web, API client and UI, member manifests and one JavaScript lockfile.
- **Nx**: one task graph across both ecosystems; explicit Python/schema dependency edges and reproducible local caching.
- **Import Linter and TypeScript import restrictions**: enforce public interfaces and forbidden dependency directions. Workspaces alone do not enforce architectural isolation.

These tools are recommended, not installed/configured. Exact versions are pinned when implementation begins. No remote build cache or customer-data-bearing cached task is selected.

## Product boundaries

Preserve document identity and provisionally keep platform bytes in PostgreSQL under the 25 MiB cap. Provide an authorized explorer/uploads; SharePoint is optional. Keep complex-file processing outside initial scope. LangGraph remains optional. Deploy in each customer's tenant/subscription with separate runtime, deployment and support access.

Read the [monorepo design](docs/architecture/monorepo.md), [dependency rules](docs/architecture/package-dependencies.md), [delivery sequence](docs/architecture/delivery-sequence.md), [decision register](docs/decisions/README.md) and [repository contract](AGENTS.md).
