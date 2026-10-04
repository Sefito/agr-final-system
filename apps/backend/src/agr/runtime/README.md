# Runtime composition and execution

Status: shared application runtime selected; execution mechanism open.

## Responsibility

Load validated settings/client configuration, construct adapters, wire use cases, manage process resources and provide HTTP/job entry points. Runtime coordinates technical lifecycle; modules own business policy.

## Decisions

- Invalid/missing required configuration fails startup without exposing secrets. No implicit provider switch based on which credential happens to exist.
- Separate deployment identity, runtime resource identity and request principal. A managed identity does not represent the end user.
- HTTP and jobs reuse modules. They may run in separate processes/images only when justified by isolation, resources or recovery.
- A waiting approval persists without a busy process. Executable jobs need explicit claims/leases, bounded retries, operation IDs and recovery.
- Long computations do not hold SQL transactions or document locks for their full duration. Recheck state at the short business commit.
- Browser lifetime and job lifetime are distinct. Define cancellation/continuation per operation and expose reconciliation status.
- Configure database connection budgets across all replicas/processes, including any workflow-specific pool.
- Emit correlation IDs, timings and safe failure categories. Detailed content-bearing logs are not central fleet telemetry.

## Failure behavior

Define startup compatibility checks, readiness, graceful shutdown and in-flight task ownership. A worker losing its claim cannot commit as if it still owns the task. Keep a clear distinction between a provider timeout, a database outage, a concurrency conflict and a user cancellation.

## Open decisions

Select workflow/job execution, connection management, configuration validation and telemetry libraries. Define retries without multiplying SDK and application retry loops. Decide checkpoint retention and workflow version compatibility if an engine is selected.
