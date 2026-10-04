# Web-local shared composition

Status: narrowed boundary after package separation.

Keep app-specific glue here: session-aware query hooks, feature navigation helpers and application error presentation. Reusable UI primitives belong to `packages/ui/`; generic typed HTTP/event transport belongs to `packages/api-client/`.

Do not create parallel copies of either package. Hooks compose public client/UI exports with the web session; backend business authorization remains server-side.

Actor/scope changes clear affected caches. Mutation retries use operation identities and declared contracts. Open: query/forms/session libraries and actual hooks; no implementation exists.
