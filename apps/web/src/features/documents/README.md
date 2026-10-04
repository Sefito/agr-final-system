# Document explorer

Status: folder navigation and upload capability required; interactions proposed.

Show the authorized hierarchy, stable breadcrumbs, file metadata, version/publication state, source and extraction/indexing status. Support allowed upload destinations and original/rendition downloads.

Decisions: filenames/folder names are protected data; use backend lists and counts rather than filtering an unrestricted client catalogue. Not-indexed is different from missing/inaccessible. Show upload staging/processing/failure states honestly. Shared bytes do not merge separately authorized occurrences.

Initial proposal: upload into AGR with explicit scope/folder association. SharePoint write-back and folder mutation permissions remain open. A source rename should preserve navigation identity where possible.

Acceptance: empty authorized folder differs from inaccessible folder; unsupported file remains visible when authorized; rejected upload explains a safe actionable reason; failed indexing does not pretend content is searchable; download reauthorizes at request time.

Open: folder create/move affordances, version history presentation, initial formats and synchronous/asynchronous upload readiness.
