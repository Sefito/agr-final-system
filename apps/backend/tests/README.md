# Backend verification

Status: verification responsibilities proposed; no tests implemented.

[unit](unit/README.md) covers deterministic rules/use cases; [integration](integration/README.md) covers real persistence/adapters on disposable resources; [contracts](contracts/README.md) covers stable public behavior.

Test critical outcomes rather than private function arrangement. Use invented customers/documents and multiple explicit identities. Real customer batteries require separate authorization and must be reported separately from data-free checks.

Before a runnable vertical slice is promoted, cover authorization, approval freshness, duplicate commits, concurrent edits and failure between business commit and delivery. CI commands, coverage targets and test tools are open until implementation exists.
