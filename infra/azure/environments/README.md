# Environment parameters

Status: configuration boundary selected; examples not implemented.

Hold non-secret, invented deployment examples only. Real customer parameters remain outside Git; `private/` is ignored for optional local use.

Decisions: separate development/demo, staging and production targets; identify tenant/subscription/resource scope explicitly; version application image and client configuration together; do not duplicate subscription-level free allowances in per-client budgets. A real customer deployment does not inherit a demo principal switcher or fictional fallback data.

Parameter examples eventually cover region, resource sizes, resource naming, enabled optional integrations and approved model deployment references. Secrets and client documents are not values here. Defaults cannot authorize external processing.

Acceptance: a validated target/configuration summary precedes mutation; staging uses synthetic data unless authorized; a release records the version/configuration digest actually deployed.

Open: exact environment count, sizing, region, release approval policy, rollback strategy and customer-specific network constraints.
