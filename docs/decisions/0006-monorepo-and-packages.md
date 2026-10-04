# ADR 0006: Package-based mixed-language monorepo

Status: package separation requested; detailed package/tooling design proposed.

## Context

The first scaffold placed all backend modules inside an application. That documents responsibilities but makes reusable business code subordinate to the API host and does not establish build/dependency boundaries.

## Decision

Use thin API/worker/web hosts and reusable access, documents, intelligence, commercial, CRM, usage, adapters, API-client and UI packages. Combine assistant/retrieval inside intelligence; avoid package-per-entity expansion. Preserve one modular-monolith business architecture and coordinated schema/release history.

Recommend uv for Python, pnpm for JS and Nx for cross-language task scheduling/affected checks. Add import/public-export verification and isolated package installs; workspace membership alone does not enforce dependency isolation. Select exact tool pins and configure executable targets during implementation.

## Consequences

Each package owns public operations, dependencies and local tests. The API and worker compose the same operations without importing each other. Public contract generation connects Python/TypeScript without sharing domain code. Additional metadata/build ownership is justified by reusable host code and dependency enforcement, not by independent public distribution.

ADR 0001's modular-monolith decision remains. Its placement of all Python modules under one application is superseded. No framework engine or separate always-on worker service is selected by this decision.
