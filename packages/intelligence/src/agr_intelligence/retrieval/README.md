# Retrieval and evidence

Status: PostgreSQL/pgvector starting point selected; ranking and extraction choices proposed.

## Responsibility

Own authorized search, derived chunks/structured facts, index revisions, evidence selection and stable source locators. Return evidence to assistant/commercial use cases rather than composing user responses.

## Decisions

- Apply organization/project/classification filters in the query before evidence enters model context.
- Combine lexical, exact-figure and vector retrieval where useful. Vector failure need not disable usable lexical evidence.
- Track embedding provider/model/revision with the index. Equal vector dimensions do not make two models compatible.
- Preserve document/version/occurrence identity and page, sheet, row or section locators. A hash or filename alone is insufficient.
- Distinguish no authorized evidence, insufficient evidence and unavailable search infrastructure.
- Planner filters can narrow the authorized scope; they cannot authorize a new scope.
- Index publication, deletion and classification changes explicitly. Content can be unchanged while visibility changes.

## Data flow

Documents/source adapter records a change. An extraction/index operation creates versioned derived material. Search builds an authorized query, ranks candidates, applies context budgets and returns evidence with source revision. Calling use cases validate citations and recheck evidence as needed before durable actions.

Index readers do not reconstruct original bytes from chunks. Source operations belong to documents; retrieval must not independently rename or publish documents.

## Acceptance cases

Exact figures remain exact; cross-project candidates never reach the model; lexical search works when embedding enrichment fails; a metadata-only classification change updates index visibility; stale revisions invalidate a pending proposal; changing embedding models has a reindex and rollback plan.

## Open decisions

Select extraction tooling for the agreed simple formats, chunking rules, model/dimensions, relevance thresholds and reindex promotion criteria. Define full deletion versus historical evidence retention in collaboration with documents. Azure AI Search is not selected by this scaffold.
