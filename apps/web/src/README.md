# Web application source

[app](app/README.md) composes routes/session/providers. [features](features/README.md) owns product interactions. [shared](shared/README.md) owns web-specific glue.

Reusable presentation comes from `@agr/ui`; transport/types come from `@agr/api-client`. Features must not deep-import their private implementation. Backend domain policy is not copied into TypeScript.

Client state is scoped by actor and relevant access context, with explicit invalidation on session change. The monorepo task graph rebuilds/checks web when client/UI/contracts change.
