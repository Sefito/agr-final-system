# Decision register

Status refers to design intent, not implementation. Selected reflects customer direction or the accepted scaffold; provisional is the current working choice; proposed needs design validation; open has no selected option.

## Recorded decisions

| Record | Status | Decision |
|---|---|---|
| [0001](0001-modular-monolith.md) | Selected for scaffold | Modular Python backend and feature-based frontend |
| [0002](0002-module-transactions.md) | Proposed | Module-owned commands participate in explicit shared business transactions |
| [0003](0003-proposals-and-execution.md) | Proposed; engine open | Persist reviewable proposals; choose execution engine from a full recovery slice |
| [0004](0004-customer-owned-azure.md) | Customer ownership selected; operation pattern proposed | Customer-local resources with separate deployment/support/runtime access |
| [0005](0005-document-lifecycle.md) | Identity/explorer selected; storage provisional | Preserve identity and originals; optional sources independent from indexing |

## Decisions still required

| Topic | Current position | Resolve before |
|---|---|---|
| Authentication | Entra required for real users; API topology open | Production identity integration |
| Membership/entitlement authority | Open | Protected use-case implementation |
| Workflow execution | LangGraph optional; no engine selected | Recoverable commercial workflow implementation |
| CRM entities | Redesign allowed; minimal first model proposed | First CRM schema/forms |
| File formats/readiness | Complex files excluded; simple-format list/readiness open | Upload/extraction contract |
| Source access | SharePoint optional; application/source ACL mapping open | Connector rollout |
| SharePoint write-back | Not selected; AGR uploads proposed | Any remote upload feature |
| Retention/deletion | Policies open for sources, originals, proposals, history and checkpoints | Storing real-client material |
| Embeddings/models | Provider/model/policy approval and index space open | Model enablement or reindex |
| Business pricing | Existing tariff is migration evidence, not new pricing | Charge implementation |
| Azure availability/sizing | Lean start proposed; SLA/region/SKUs open | Infrastructure deployment |
| Migration/tooling | New schema baseline and runner open | First executable migration |

Resolve decisions at their relevant step rather than blocking this documentation pass on every future choice. Record the rationale, evidence and consequences; update superseded statuses when a decision changes.
