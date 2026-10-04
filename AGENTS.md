# Repository contract

## Scope

This is a new modular-monolith scaffold. Read `README.md` and `docs/architecture/overview.md` before implementation. Existing AGR behavior is migration evidence, not permission to copy customer data or import the legacy application wholesale.

## Boundaries

- Keep domain logic in `apps/backend/src/agr/modules/<module>/`.
- API routes, agent tools and background jobs call the same application use cases.
- Put external-service adapters in `integrations/`; compose dependencies in `runtime/`. Domain code does not import API, runtime or provider SDKs.
- Each module owns its writes. Cross-module operations use explicit public interfaces rather than reaching into another module's internals.
- Introduce `domain/`, `application/` and persistence adapter files inside a module when actual implementation needs them. Do not generate empty architectural layers or generic base repositories.
- Workflow-engine selection is open. Do not introduce LangGraph, Durable Functions or another engine merely to fill the scaffold.

## Data and authorization

- Each customer owns its deployment and data resources. Keep customer tenant and user object identity explicit.
- Authorize access before assembling model context, listing protected file metadata or downloading originals.
- Preserve distinctions between content blobs, file occurrences, logical documents, versions and renditions.
- Revalidate identity, permissions, evidence and version at approval and commit boundaries. Prevent duplicate business commits and charges.
- Do not send customer content to model or extraction providers without explicit authorization. Azure hosting alone does not authorize processing.
- Never commit credentials, real customer configuration, documents, extracted text, logs, checkpoints, generated reports or database dumps. `clients/examples/` contains synthetic examples only.
- No destructive data operation, resource deletion or real deployment without explicit authorization and a confirmed target.

## Work and verification

- Preserve unrelated changes and keep work narrowly scoped.
- Write code, identifiers, comments and technical documentation in English. User-facing product text may be Spanish.
- Prefer small typed functions and concrete names. Comment only non-obvious reasons.
- Pin direct dependencies when introduced. Commit appropriate lockfiles and add meaningful checks alongside runnable implementation.
- Tests use synthetic data and provider doubles by default. Clearly distinguish static inspection, unit tests, integration tests and live-client validation.
- Use `codex/` branches for changes after initial repository bootstrap. Never describe placeholder folders as implemented capabilities.
