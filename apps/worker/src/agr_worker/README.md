# Worker host package

[jobs](jobs/README.md) maps claimed work to package use cases. [bootstrap](bootstrap/README.md) composes resources and lifecycle.

Workload concurrency, execution retries and shutdown belong to this host's execution contract. It cannot bypass package authorization, version validation or business idempotency.
