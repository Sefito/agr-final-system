# Cross-language contracts

Status: contract artifact boundaries selected; no schemas generated.

[http](http/README.md) receives OpenAPI from the API's implemented public models. [events](events/README.md) owns language-neutral event schemas. [fixtures](fixtures/README.md) contains invented compatibility examples.

Contracts connect independently typed Python and TypeScript packages. They are not a shared business-domain package, and frontend consumers do not import Python records. Validate deliberate schema changes and generation drift through the task graph.
