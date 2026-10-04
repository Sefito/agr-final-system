# ADR 0003: Reviewable proposals and optional execution engine

Status: proposed; workflow engine open.

## Context

Commercial actions require pauses, user review and recovery. The earlier application already uses LangGraph, but its recorded pilot improved recovery without reducing code size. Copying that integration is not a requirement for the new system.

## Decision

Persist proposal identity/version, scope, expected base and evidence revision. Approval is an explicit application command, not model-generated authorization. Waiting requires persisted state rather than an active process.

Evaluate one complete slice with ordinary application commands and recoverable jobs against a suitable existing durable runtime. Include process death, duplicate/stale approval, permission change, lost response after commit and executable-version change. Do not select an engine solely because the host is Azure.

## Consequences

A simple fixed workflow may need less machinery; substantial recovery/branching can justify an established engine. Avoid writing a generic replay/scheduler framework to remove a dependency. Choose one production engine after evaluation. LangGraph, Durable Functions, retry and checkpoint guarantees are not implemented here.
