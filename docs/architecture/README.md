# Architecture index

Status: mixed-language monorepo design; no implementation or enforcement yet.

Read the [functional requirements](../requirements/functional-requirements.md) first for intended product behavior. Architecture explains implementation responsibility rather than defining additional product scope.

Then read in order:

1. [Overview](overview.md): packages versus apps versus deployments.
2. [Monorepo design](monorepo.md): uv, pnpm, Nx, builds and releases.
3. [Dependency rules](package-dependencies.md): allowed imports and enforcement.
4. [Use-case paths](use-case-paths.md): public operations and shared commits.
5. [Delivery sequence](delivery-sequence.md): next design/implementation gates.
6. [Decision register](../decisions/README.md): selected/provisional/open status.

## Folder specifications

| Area | Specification |
|---|---|
| Business and adapter packages | [Package index](../../packages/README.md) |
| API host | [API](../../apps/api/README.md) |
| Background host | [Worker](../../apps/worker/README.md) |
| Frontend | [Web](../../apps/web/README.md) |
| Cross-language contracts | [Contract index](../../contracts/README.md) |
| Coordinated verification | [System tests](../../tests/system/README.md) |
| Schema history | [Migrations](../../db/migrations/README.md) |
| Customer resources | [Azure](../../infra/azure/README.md) |
| Client profiles | [Configuration](../../clients/README.md) |

Every folder contains local design documentation. Package-local tests verify ownership; system tests verify collaboration. Empty source folders retained by READMEs are proposed package boundaries, not installed packages.
