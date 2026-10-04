# Synthetic client examples

Status: example boundary selected; schema and sample files pending.

Use invented identifiers, business names, roles and document specifications to demonstrate validated client configuration. Examples must not contain a real customer's prompts, documents, tenant IDs, subscription IDs, principals or credentials.

Configuration may select branding, copy, document types and enabled capabilities. It cannot disable access filtering, authorize unsupported provider processing or replace production behavior with fictional data.

Version the schema and configuration digest with application releases. A missing/invalid required configuration fails validation; silently loading another client's defaults is unacceptable.

Acceptance: examples validate without external services and make demo intent clear. Adding a client must not require customer-specific conditionals in domain code.

Open: configuration schema, secret reference mechanism, client-specific extraction rules and document type ownership. Do not carry arbitrary executable client plug-ins forward without a concrete need and trust boundary.
