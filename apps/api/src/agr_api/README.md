# API host package

[transport](transport/README.md) maps HTTP/SSE to public use cases. [bootstrap](bootstrap/README.md) constructs settings/resources/adapters and wires dependencies.

Transport does not obtain business access by importing a package's private repository. Bootstrap can import concrete adapters; it must not replicate document/CRM rules. The host publishes safe contract projections and owns process lifecycle, not customer state.
