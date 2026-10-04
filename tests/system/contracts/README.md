# Contract verification

Status: planned suite.

Verify public HTTP errors/results, streaming event schemas and provider/source adapter behavior shared across implementations.

Initial cases: ownership denied before stream start; one terminal outcome per attempt; committed result reconciliation after a disconnected response; backward-compatible event handling; download authorization; UI/agent command parity; malformed provider output cannot become a business command.

Schema snapshots can detect deliberate interface changes but do not establish business correctness. Contract fixtures are invented and scrubbed. Select schema generation and compatibility policy before publishing the first client API.
