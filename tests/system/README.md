# System verification

Status: planned cross-package/application suite.

[unit](unit/README.md) checks coordination with doubles; [integration](integration/README.md) proves coordinated persistence/recovery on disposable resources; [contracts](contracts/README.md) checks public compatibility across hosts/packages.

Package-local tests own domain invariants and adapter contracts. System checks focus on effects no single package can prove: shared save/charge transaction, API/worker interoperability, schema upgrades and commit-before-delivery recovery.

Do not report design documentation as test coverage or mocked execution as proven restart recovery.
