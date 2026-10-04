# Cross-project verification

Status: planned system verification.

Individual packages and applications own local tests. [system](system/README.md) covers collaboration, shared transactions and compatible host behavior. Avoid relocating every unit test into one central suite that hides ownership.

Workspace import-boundary checks and isolated package installs complement behavior tests. All ordinary fixtures are synthetic; live-client validation requires explicit authorization.
