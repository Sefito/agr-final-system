# Backend

One Python application with HTTP and background execution entry points. `src/agr/` is the future package root; this scaffold does not yet configure package installation or runnable commands.

- `api/`: request/response contracts, route handlers and authorized streaming projections. Transport calls use cases rather than writing business tables directly.
- `runtime/`: settings, composition, process startup and job entry points. This is the place that chooses adapters and wires dependencies.
- `modules/`: business ownership. Each module exposes typed application operations. Add internal files and layers only when needed.
- `integrations/`: external SDKs, provider requests and source connectors behind application-owned interfaces.
- `tests/unit/`: deterministic domain/use-case tests with doubles.
- `tests/integration/`: persistence and adapter checks against explicitly provisioned disposable resources.
- `tests/contracts/`: HTTP/SSE contracts and shared behavior across adapter implementations.

The API and agent use the same document and CRM operations. A worker is an entry point of this application, not an independently designed copy of its business logic.
