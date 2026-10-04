# Architecture and ownership

Status: package-based monorepo design; implementation/enforcement pending.

## Three different boundaries

A **package** owns reusable code, public interfaces, dependencies and tests. An **application** composes packages into an executable host. A **deployment** decides which processes/resources run together. These are different boundaries.

Use a mixed Python/TypeScript monorepo and a modular-monolith business architecture. API and worker share business packages and one coordinated PostgreSQL history. They may share a container image; business packages are not microservices.

## Package ownership

| Package | Owns |
|---|---|
| access | Authenticated principal vocabulary, membership and access policies |
| documents | Source hierarchy, originals, document identities, versions and publication |
| intelligence | Retrieval/index/evidence and consultation submodules |
| commercial | Document proposals, approval/run coordination |
| CRM | Agreed commercial record commands and activity views |
| usage | Provider-attempt attribution and immutable business charge receipts |
| adapters | Concrete SQL, resource, source and inference port implementations |
| api-client | Generated HTTP transport and typed streaming contract consumption |
| UI | Accessible presentation primitives independent of product state |

Apps own composition and transport, not domain state. Commercial coordinates public document/CRM/usage operations; documents still owns version/publication invariants. Intelligence groups related retrieval/assistant behavior without making each helper a package.

## Dependency and transaction direction

Follow the [dependency matrix](package-dependencies.md). Business packages cannot import concrete adapters or hosts. Adapters implement business-owned ports; host bootstrap injects them. Each package owns its writes, while one coordinated SQL transaction can include several package participants without independent commits.

Do not expose ORM/provider objects as public domain types. Avoid a generic shared kernel, global turn context and package-per-entity proliferation. Public API and dependency checks need real enforcement when source exists.

## Customer and document constraints

Each customer owns its Azure deployment. Identity, membership and model-processing consent remain explicit. Preserve blobs/occurrences/logical documents/versions/renditions and authorized citation locators. Provisionally keep platform bytes in PostgreSQL under the 25 MiB cap. Catalogue visibility is independent of indexing status.

Explorer/uploads are required; SharePoint is optional. Complex processing is outside initial scope. No workflow engine is selected; compare a full failure-tested approval slice. Never treat Azure hosting, workspace metadata or a progress event as a security/consistency guarantee.

Read the [monorepo design](monorepo.md), [use-case paths](use-case-paths.md) and [delivery sequence](delivery-sequence.md).
