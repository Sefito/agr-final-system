# Product features

Status: initial feature grouping selected.

[assistant](assistant/README.md), [commercial](commercial/README.md), [documents](documents/README.md) and [crm](crm/README.md) own their screens, local interaction state and API hooks.

A feature consumes public backend contracts and shared presentation/transport utilities. Cross-feature navigation passes stable identifiers; it does not duplicate another feature's domain records or authorization logic.

Add new features only for agreed use cases. The presence of a folder does not mean a capability is live. Framework/library and per-feature internal file layouts stay open until implementation.
