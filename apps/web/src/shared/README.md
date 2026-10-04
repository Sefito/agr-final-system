# Shared frontend primitives

Status: boundary selected; component/query libraries open.

Own reusable presentation components, accessibility patterns, typed HTTP transport and streaming parsing. Keep feature-specific workflows and backend policy out of this folder.

Decisions: generate HTTP types from the implemented API; maintain separate versioned stream event types; normalize safe error presentation; never log tokens/source content. Query cache identity includes actor and relevant scope/classification context. A cache key is not an authorization check.

Centralize session handling without allowing a generic API wrapper to silently retry every business mutation. Retries follow idempotency contracts. Cookie-based authentication requires agreed origin/CSRF handling.

Acceptance: unknown events follow the compatibility policy; session change clears protected cached data; expired authentication is distinct from resource conflict/unavailability.

Open: design system, query/forms libraries and schema generation tooling. Select them with concrete screens and contract needs.
