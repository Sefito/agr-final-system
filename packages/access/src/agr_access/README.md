# Identity and access

Status: module boundary selected; production integration proposed.

## Responsibility

Resolve authenticated principals and evaluate product entitlements, organization/project membership and security ceilings. Provide policy inputs to every protected use case. This module does not own document contents or CRM writes.

## Decisions

- Principal identity includes customer tenant ID and user object ID. Email and display name are mutable attributes.
- A deployment serves one customer. Organizations and projects inside it are authorization scopes, not separate Azure tenants.
- Requested scopes and ceilings can narrow access; they cannot increase it.
- Conversations retain their selected organization/project. A different scope starts a different conversation.
- Authentication adapters resolve identity; document/CRM repositories apply authorized filters before reading protected data. A policy service alone is not enough if queries fetch unrestricted rows.
- Recheck current authorization when approving, publishing, downloading or resuming protected work. Historical approval does not grant permanent access.
- Demo identity simulation requires an explicit isolated demo mode and is unavailable in production.

## Use cases and interfaces

Resolve principal; list authorized organizations/projects; check a product entitlement; construct an authorized scope; reject access that changed during a job. Return immutable policy values, not HTTP headers, SDK objects or a mutable global principal.

An inaccessible resource may use a non-disclosing not-found response; unauthenticated requests use an authentication error. Final HTTP mappings belong to the API contract.

## Acceptance cases

A user cannot widen a project scope, enumerate another user's conversation, retrieve protected filenames through counts/search, or continue using high-classification history after a ceiling downgrade. Cached policy is invalidated or bounded so revocation has defined behavior.

## Open decisions

Choose bearer-token validation versus a non-bypassable platform-authenticated API topology. Define membership/entitlement authority, revocation latency and whether customer groups map directly to application roles. RLS is a separate defense-in-depth decision, not a substitute for application authorization.
