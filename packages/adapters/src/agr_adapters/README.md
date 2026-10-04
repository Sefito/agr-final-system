# Adapter families

[persistence](persistence/README.md) implements module-owned data ports. [azure](azure/README.md) connects selected resource services. [sharepoint](sharepoint/README.md) connects optional sources. [models](models/README.md) transports approved inference/embedding requests.

Factories can be shared by API/worker composition. They receive validated settings rather than importing an application runtime singleton. Retries, token refresh and resource lifecycle have explicit owners.
