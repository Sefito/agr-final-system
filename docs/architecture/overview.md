# Architecture and ownership

## Application shape

Use a modular monolith with separate web and backend applications. The backend has HTTP and background execution entry points sharing the same business modules. Deployment units are an operational choice; module names do not imply microservices.

## Module responsibilities

| Module | Owns |
|---|---|
| Identity | Tenant/user identity, memberships, scope and access-policy evaluation |
| Documents | Source catalogue and hierarchy, originals, content/occurrence identity, versions, renditions and publication |
| Retrieval | Authorized search, index lifecycle and evidence/citation locators |
| Assistant | Consultation and answer-generation use cases over authorized evidence |
| Commercial | Draft/edit proposals, workflow progression and approval requests |
| CRM | Agreed commercial entities, their commands, concurrency and activity history |
| Usage | Model usage attribution and idempotent business charge receipts |

Authorization applies before evidence reaches the model and before protected metadata or originals are returned. Document commands own version/publication writes; commercial workflows coordinate them. Cross-module transactions use explicit composition and shared transaction boundaries where required, not independent commits hidden behind each call.

## Dependency direction

Transport and runtime depend on module application interfaces. Application use cases depend on domain rules and explicit ports. External adapters implement those ports and are wired at startup. Modules do not import runtime or transport. Provider SDKs do not become domain types.

Start with ordinary typed files inside each module. Add internal `domain/` or `application/` packages when the code warrants them. Avoid a universal `utils`, shared mutable workflow context or a generic repository abstraction that obscures ownership.

## Documents and sources

Preserve the existing distinctions between content blob, occurrence, logical document, version and rendition. A content hash does not define access rights. Model source folders with stable identifiers and parent relationships; paths can change.

The product requires an authorized explorer and uploads. SharePoint is optional behind a source adapter. Unsupported or failed-extraction files may remain visible to authorized users without being searchable or citable. Initially, proposed uploads belong to AGR; writing them back to SharePoint is a separate configured capability.

Provisionally retain platform-file bytes in PostgreSQL with the 25 MiB cap. Optional external-source mirrors may use Blob. Complex document processing is outside initial scope; retaining an original is different from promising advanced extraction or editing support.

## Workflow execution

LangGraph is optional. Persist proposals and approval identity/version explicitly. A waiting approval does not require a running Python process. Long-running jobs still require durable progress, task ownership, retry limits and idempotent effects.

Before choosing a workflow engine, compare one full draft/edit/approve/save slice under process failure, duplicate approval, permission revocation, client disconnect and commit-before-delivery failure. A prototype may compare engines; production should not maintain two equivalent workflow engines.

## Azure and rollout

Deploy each customer instance in that customer's tenant/subscription with versioned infrastructure and client configuration. Integrate real Entra identity before real-client users. Deployment federation, optional Lighthouse support and runtime permissions are independent.

Start with module/use-case boundaries, one reproducible customer deployment, the explorer/uploads and agreed commercial use cases. Add SharePoint only when selected. Define CRM from actual requirements. Production code must distinguish real capabilities from explicit synthetic demo behavior.

This document specifies ownership and intent. The folder scaffold implements none of these runtime guarantees yet.
