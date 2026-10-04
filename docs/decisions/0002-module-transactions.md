# ADR 0002: Explicit module commands and shared transactions

Status: proposed.

## Context

Separating commercial, documents and usage code can accidentally replace one atomic save with several independent commits. Agent and UI commands can also diverge if each writes tables directly.

## Decision

Each module owns its invariants and typed public commands. Transport/agent tools call these commands. A coordinating use case passes one transaction context to the participants of an atomic business operation; participants do not independently commit.

Model calls, extraction and rendering finish outside long-held locks. The final transaction revalidates permissions, proposal/evidence revisions and expected document version, then records bytes/version/citations, any business receipt and the committed operation outcome.

## Consequences

Cross-package SQL transactions are allowed without abandoning write ownership. Operation identity permits recovery after commit-before-response failure. A separate storage service or distributed workflow checkpoint cannot silently replace SQL atomicity; any future move requires a consistency/reconciliation design.

The transaction API, persistence library and actual command schemas remain open. No generic repository or distributed event infrastructure is mandated.
