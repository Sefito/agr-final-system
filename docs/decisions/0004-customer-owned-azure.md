# ADR 0004: Customer-owned deployment and separated operational access

Status: customer ownership selected; Bicep/federation/Lighthouse pattern proposed.

## Context

The customer owns its tenant and deployment resources. We deploy or assist deployment and may provide ongoing operations across customer subscriptions.

## Decision

Keep application data/runtime resources in the customer subscription. Use versioned Bicep and per-customer validated configuration. Customer administration authorizes bootstrap and required role assignments. Subsequent GitHub releases may use a customer-local federated identity scoped to approved deployment resources.

Optional Azure Lighthouse delegation supports provider-side resource management with revocable customer control. It does not replace directory/Graph grants and does not guarantee that privileged management roles cannot obtain data. Runtime, deployment and support permissions remain distinct.

## Consequences

No central customer-data platform is required. Customer offboarding removes our access while leaving customer-owned resources/data intact. Additional services, networking, licensing, support and availability requirements change cost; no earlier budget is a committed quote.

Microsoft references: [onboarding](https://learn.microsoft.com/en-us/azure/lighthouse/how-to/onboard-customer), [roles](https://learn.microsoft.com/en-us/azure/lighthouse/concepts/tenants-users-roles), [federation](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-create-trust-user-assigned-managed-identity).
