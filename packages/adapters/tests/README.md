# Adapters package verification

Status: planned suite.

Verify this package's public contracts and owned invariants using deterministic synthetic fixtures and injected doubles. Tests need only the package's declared dependency closure. Provider/database behavior is separated from pure business tests.

Cross-package transaction/recovery and API/worker interoperability belong to `tests/system/`. Future CI also builds/installs the package in an isolated environment to detect undeclared dependencies hidden by the shared workspace.
