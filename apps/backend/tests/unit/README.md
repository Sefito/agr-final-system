# Unit verification

Status: planned suite.

Test domain rules and typed use cases with deterministic in-memory doubles. No PostgreSQL server, Azure resource or model endpoint is required.

Initial scenarios: scope narrowing; document identity distinct from hash; proposal/version validation; insufficient evidence and invalid citations; duplicate operation receipts; unknown usage distinct from zero; typed provider failure.

Prefer observable outcomes and invariant enforcement. Do not write tests that merely mirror a function's body or assert an arbitrary folder layout. Add the smallest meaningful cases alongside each implementation. Framework and fixture conventions remain open.
