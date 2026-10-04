# Web application

Status: React/TypeScript host selected; tooling implementation pending.

Own the application shell, authenticated session presentation and assistant/commercial/documents/CRM feature interactions. Depend on public `@agr/api-client` and `@agr/ui`; keep application-specific hooks/state local.

The proposed pnpm workspace owns one JavaScript lockfile across web/client/UI. Nx runs host checks after dependent package/contract tasks. No framework versions, manifests or build tasks are configured yet.

Read [source](src/README.md) and [tests](tests/README.md). UI follows backend versions/approvals and never treats progress as committed success. Production errors do not become synthetic fallback records.
