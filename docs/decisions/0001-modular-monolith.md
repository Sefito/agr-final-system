# ADR 0001: Modular monolith with optional workflow engine

Status: modular-monolith decision retained; application-local module placement superseded by ADR 0006.

## Context

The previous proof of concept accumulated large workflow files and overlapping orchestration/business state. Customer-owned Azure deployment and document identity must be preserved. Complex files are outside initial scope and CRM redesign is allowed.

## Decision

Use a modular Python business architecture and a React/TypeScript frontend. UI, API, agent and worker share public commands. Do not mandate LangGraph or Durable Functions before evaluating durable execution.

The initial application-local folder placement has been replaced by thin hosts and reusable packages in [ADR 0006](0006-monorepo-and-packages.md). Packaging does not require microservices.

## Consequences

Enforce dependency/write ownership and shared transaction/recovery contracts. Package-local tests and cross-package verification must establish behavior; documentation and package naming alone do not.
