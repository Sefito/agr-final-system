# Backend source root

Status: source-layout boundary selected.

Keep deployable Python application source under [agr](agr/README.md). Tests stay outside this directory. Do not make relative filesystem parent counts part of the import contract; choose proper package installation when implementation begins.

This root does not hold client documents, runtime state, generated reports or infrastructure definitions. Packaging metadata belongs to `apps/backend/` when tooling is selected.
