# AGR backend package

Status: package boundary selected; packaging tooling open.

This future Python package groups business modules, external integrations, HTTP transport and runtime composition. It is not yet importable application code.

- [modules](modules/README.md) owns business operations.
- [integrations](integrations/README.md) implements external-service boundaries.
- [api](api/README.md) exposes authorized HTTP and streaming contracts.
- [runtime](runtime/README.md) wires dependencies and process entry points.

Domain logic never imports transport, configuration globals or provider SDKs. Runtime chooses concrete adapters; request-specific identity is passed explicitly. Avoid mutable shared turn objects that become implicit dependencies of every module.

Open: packaging/build tools, supported Python version, dependency pins and executable entry points. Select these together when the first vertical slice is implemented.
