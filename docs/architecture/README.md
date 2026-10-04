# Architecture index

Status: analyzed folder responsibilities; no runtime implemented.

Read in order:

1. [Overview](overview.md): application shape and module ownership.
2. [Use-case paths](use-case-paths.md): commands and cross-module handoffs.
3. [Delivery sequence](delivery-sequence.md): step-by-step design and implementation gates.
4. [Decision register](../decisions/README.md): statuses and open decisions.

## Folder-level specifications

| Area | Specification |
|---|---|
| Backend package | [Source/package boundary](../../apps/backend/src/agr/README.md) |
| Business ownership | [Module index](../../apps/backend/src/agr/modules/README.md) |
| Transport | [API](../../apps/backend/src/agr/api/README.md) |
| Process lifecycle | [Runtime](../../apps/backend/src/agr/runtime/README.md) |
| External dependencies | [Integrations](../../apps/backend/src/agr/integrations/README.md) |
| Frontend | [Source/features](../../apps/web/src/README.md) |
| Database | [Migrations](../../db/migrations/README.md) |
| Customer resources | [Azure](../../infra/azure/README.md) |
| Client profiles | [Configuration](../../clients/README.md) |
| Verification | [Backend](../../apps/backend/tests/README.md), [frontend](../../apps/web/tests/README.md) |

Local READMEs specify responsibility, selected/proposed decisions, acceptance scenarios and open questions. These documents define design intent; future checks must demonstrate the actual behavior.
