# ADR 0005: Preserve document identity and separate catalogue from index

Status: identity and explorer selected; PostgreSQL bytes provisional; upload destination proposed.

## Context

The existing document model separates shared content from occurrences/access, logical documents and versions/renditions. Customers need folder navigation and uploads. SharePoint is possible, and complex-file processing is excluded initially.

## Decision

Retain these identity distinctions. Represent folders/sources by stable identity and parentage rather than paths. Catalogue presence and user access are separate from extraction/search readiness.

Provisionally keep platform bytes in PostgreSQL under the 25 MiB cap to preserve the business transaction boundary. Use optional Blob mirrors for external sources only when needed. Proposed uploads belong to AGR; SharePoint write-back requires an explicit destination/authority decision.

## Consequences

An authorized unsupported file can be visible without being searchable. Original bytes have their own disclosure rules; sanitized extracted text does not sanitize the original. Publication controls the active corpus version. Source reclassification/deletion, historical citation retention and staging expiry require explicit policies before real-client rollout.
