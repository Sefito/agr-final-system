# API application

Status: thin HTTP host selected; framework proposed/open.

Own HTTP/SSE routes, request/response projection, authentication transport and dependency composition. Business commands live in packages. The API can depend on every required public business interface and concrete adapters; business packages cannot import this application.

[src](src/README.md) defines the future application package. [tests](tests/README.md) verifies routing/authentication/streaming wiring. FastAPI is a suitable proposal, but no dependency or endpoint is implemented.

Produce reviewed OpenAPI artifacts for `contracts/http/`. Event compatibility has its own contract. Do not let API hosting decide business commit, pricing, approval or document access semantics.
