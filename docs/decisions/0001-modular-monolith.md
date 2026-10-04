# ADR 0001: Modular monolith with optional workflow engine

Status: accepted for repository scaffolding.

## Context

The previous proof of concept accumulated large workflow files and overlapping orchestration/business state. Customer-owned Azure deployments, document identity and user-visible file structure must be preserved. The new scope excludes complex-file processing and permits CRM redesign.

## Decision

Use one Python backend organized by business module and one React/TypeScript frontend organized by feature. Separate transport, runtime composition and external integrations from module logic. Keep migrations and Azure infrastructure outside application source.

Do not introduce LangGraph or Durable Functions as a scaffold dependency. Evaluate durable execution using a complete use case before selecting an engine. Retaining LangGraph in an incremental legacy deployment is distinct from selecting it for this new repository.

## Consequences

UI, agent and jobs share typed use cases and module-owned writes. Module boundaries require enforcement when implementation exists. We avoid independent service infrastructure per module, but still need explicit transaction, recovery and authorization contracts. Empty folders provide organization, not those guarantees.
