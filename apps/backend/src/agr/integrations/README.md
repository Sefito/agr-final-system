# External integrations

Status: adapter boundary selected; individual SDKs open.

External integrations implement narrow interfaces required by application use cases. They translate provider authentication, pagination, errors and payloads into application-owned results. They do not authorize end users, decide document publication or commit business charges.

- [azure](azure/README.md): runtime access to selected Azure resources.
- [sharepoint](sharepoint/README.md): optional source catalogue/content synchronization.
- [models](models/README.md): generation, structured output and embeddings.

Retries/timeouts have one explicit owner per operation. Distinguish transient failure, permanent rejection and uncertain completion. No provider-specific object crosses into a domain record. Use synthetic fixtures and contract doubles before live-client validation.

Persistence internal to a module is not automatically an external integration. Module-owned SQL adapters stay with their module when implemented. Avoid routing all infrastructure into one miscellaneous adapter file.
