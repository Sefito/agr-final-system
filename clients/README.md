# Customer configuration

`examples/` is reserved for invented configuration examples with non-functional identifiers. Client-specific branding, document specifications and feature configuration are configuration concerns rather than conditionals scattered through backend modules.

Real identifiers, prompts containing customer information, documents and credentials stay outside the public repository. `private/` is ignored for optional local configuration. Configuration schemas and deployment validation will be introduced with the first implemented client setup.

## Decisions and next gate

Read [synthetic examples](examples/README.md). Validate branding, document specifications and capability configuration against a versioned schema. Identity and processing permission cannot be overridden by presentation configuration. Real client resources/configuration require an explicit target and authorized provisioning process.
