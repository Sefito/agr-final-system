# HTTP contract artifacts

Status: planned generated/reviewed OpenAPI.

Authority: implemented API request/response models. Produce a deterministic schema without customer secrets/content or live provider calls. Review its changes and generate `@agr/api-client` from it.

Do not hand-maintain another authoritative schema with the same meaning. Generation depends on the API project and relevant public package contracts. Runtime schema and deployed client versions require compatibility verification.
