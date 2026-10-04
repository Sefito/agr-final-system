# Worker composition

Status: proposed host composition.

Construct validated client settings, database transaction/adapter factories, approved model/source adapters and job execution resources. Reuse adapter factories with the API rather than copying provider setup. Host-specific assembly remains explicit.

Allocate connection/CPU/memory budgets across replicas. Shutdown stops new claims and has a defined policy for in-flight work. Startup checks configuration/schema compatibility. A runtime service identity does not replace the actor/authorization context needed by a protected job.

No separate runtime-framework package is selected. Extract a shared composition helper only when a concrete duplication warrants it; keep business rules out of it.
