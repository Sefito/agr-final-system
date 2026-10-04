# Optional SharePoint source connector

Status: optional capability; connector contract proposed.

## Responsibility

Read selected SharePoint libraries/folders and register stable source metadata/content changes through documents and retrieval operations. It is not the document domain or the user-facing explorer itself.

## Decisions

- Configure explicit sites/libraries. Prefer selected-site permissions with a separate grant for each selected resource; directory consent alone is insufficient.
- Start with read-only synchronization. Upload write-back is a separate client decision and permission grant.
- Track stable site/drive/item identity, parent identity, source version/change markers, source URL and synchronization cursor. A path is not primary identity.
- Handle pagination, throttling, retry limits and cursor expiry. Advance a cursor only after its corresponding updates are durably accounted for.
- Treat content change, rename/move, deletion and access/classification change as different effects. Metadata-only change does not require re-extracting unchanged bytes.
- Preserve source file visibility independently of extraction success. Outside-scope formats get a not-indexed status.
- Site-level service access does not reproduce each user's source ACLs. Configure application authorization and any required source-permission mapping explicitly.
- An optional Blob copy is a mirror, not an independently writable source of truth.

## Synchronization cycle

Enumerate the configured root; reconcile folders/items; register additions and changes; process deletions under the agreed retention policy; schedule supported extraction; persist progress. Recover with a full reconciliation if incremental state becomes invalid. Repeated observations must be idempotent.

## Acceptance cases

Rename retains identity; two identical files retain separate occurrences; cursor failure does not silently lose items; throttling is bounded; permission reduction removes visibility even with unchanged bytes; unsupported files remain correctly represented.

## Open decisions

Select source ACL versus application classification mapping, synchronization interval, source deletion policy and upload destination. Confirm a customer's SharePoint licensing/setup; it is not included implicitly in Azure infrastructure costs.

Microsoft references: [selected permissions](https://learn.microsoft.com/en-us/graph/permissions-selected-overview), [folder listing](https://learn.microsoft.com/en-us/graph/api/driveitem-list-children?view=graph-rest-1.0).
