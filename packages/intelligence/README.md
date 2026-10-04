# Intelligence package

Status: package grouping selected; implementation pending.

Own authorized retrieval and consultation as related internal modules. They share evidence locators, budgets and model-facing contracts, so separate distributable packages would add coordination without a demonstrated independent lifecycle.

Public interfaces: retrieve authorized evidence; consult within a fixed conversation scope; index/reconcile derived content; validate evidence/citation projections. Internal [retrieval](src/agr_intelligence/retrieval/README.md) and [assistant](src/agr_intelligence/assistant/README.md) specifications preserve distinct ownership within the package.

Allowed business dependencies: access, documents and usage public interfaces. Model/embedding/extraction ports are owned here where required; concrete implementations live in adapters. Do not import commercial, CRM, concrete SDKs or application hosts.

Package-local tests cover relevance/evidence policy and consultation behavior; system tests cover database/index integration and shared operation paths. No workflow engine is required for ordinary consultation.
