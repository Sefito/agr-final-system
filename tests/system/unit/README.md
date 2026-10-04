# Coordination checks with doubles

Status: planned suite.

Verify cross-package use-case coordination with deterministic synthetic implementations: current authorization is supplied to participants, stale proposals are rejected, and a committed operation is reconciled rather than repeated.

Single-package invariants stay with the package. These checks do not need PostgreSQL/Azure/providers and do not establish real transaction or restart guarantees.
