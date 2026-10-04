# Applications

Status: two application boundaries selected.

[backend](backend/README.md) owns authorized business operations and HTTP/job entry points. [web](web/README.md) owns user interactions and consumes public contracts.

Decisions: backend behavior is shared by UI, agent and jobs; separate folders do not require separate business microservices. Each application will own its dependency manifest/lockfile when tooling is selected. Root task orchestration is open; do not copy the previous monorepo tooling automatically.

Implement one end-to-end use case across both applications before adding generic shared packages. Do not create a third application for a worker that merely reuses backend entry points.
