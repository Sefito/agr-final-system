# Access package

Status: reusable Python package boundary selected; implementation pending.

Own principal and policy values. The [detailed specification](src/agr_access/README.md) defines use cases, invariants and open decisions. Public import namespace will be `agr_access`; direct allowed business dependencies: none.

Business interfaces are public and narrow. Concrete adapters are injected through owned ports; no import of applications, adapters or provider SDKs is allowed. Cross-package consumers never reach into private implementation.

A package manifest will declare its direct dependencies and uv workspace sources. Package-local tests cover invariants; system tests cover coordinated transactions/host behavior. No distribution is published or installed yet.
