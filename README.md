# AGR Final System

A new foundation for AGR's assistant, commercial workflows, document explorer and CRM, deployed in each customer's Azure tenant and subscription.

This repository currently contains a folder scaffold and architectural boundaries. It has no runnable application, installed dependencies, database schema or deployed resources.

## Workspace

```text
apps/
  backend/
    src/agr/
      api/                 HTTP and streaming transport
      runtime/             Configuration, dependency wiring and job entry points
      modules/
        identity/          Principals, memberships and access policies
        documents/         Catalogue, folders, originals, versions and publication
        retrieval/         Authorized evidence search and citation locators
        assistant/         Consultation use cases
        commercial/        Drafting, editing and approval use cases
        crm/               Commercial records and commands
        usage/             Usage records and business charge receipts
      integrations/
        azure/             Azure resource adapters
        sharepoint/        Optional source connector
        models/            Model-provider adapters
    tests/
      unit/
      integration/
      contracts/
  web/
    src/
      app/                 Application composition, routing and providers
      features/
        assistant/
        commercial/
        documents/
        crm/
      shared/              Reusable presentation components and HTTP client
    tests/
db/migrations/             Versioned schema changes
infra/azure/
  modules/                 Reusable Bicep resource modules
  environments/            Synthetic deployment parameter examples
clients/examples/          Synthetic customer configuration examples
scripts/                   Development and maintenance commands
docs/
  architecture/
  decisions/
```

Folders belong to one application unless a measured need justifies a separate service. API routes and agent tools invoke the same typed application use cases. Background jobs reuse backend modules.

Read [the architecture](docs/architecture/overview.md), [the decision record](docs/decisions/0001-modular-monolith.md) and [the repository contract](AGENTS.md) before implementation.

## Initial decisions

- Python backend and a React/TypeScript frontend; dependencies and tool versions will be selected when implementation begins.
- PostgreSQL with pgvector for business data and initial retrieval. Preserve the existing document identity concepts and provisionally retain platform-file bytes in PostgreSQL with the 25 MiB limit.
- Customer-owned Azure deployment, with repeatable Bicep provisioning. Deployment federation and optional Lighthouse support access have separate responsibilities.
- An authorized folder/file explorer and uploads are in scope. SharePoint is an optional integration.
- LangGraph is not a required dependency. Durable execution must be demonstrated before choosing a workflow engine.
- Complex document processing is outside the initial scope.

## Scaffold verification

Every folder is retained by its local README. No application tests or CI checks exist yet; documented acceptance cases do not establish test coverage.

## Folder specifications

Each folder now contains a README explaining its responsibility and design decisions. Follow the [architecture index](docs/architecture/README.md), [use-case paths](docs/architecture/use-case-paths.md), [delivery sequence](docs/architecture/delivery-sequence.md) and [decision register](docs/decisions/README.md). These are specifications; no application code has been added.
