# API composition

Status: thin-host composition proposed.

Validate settings/client configuration, construct resources through adapter factories and inject public package use cases into transport. Own process startup/readiness/shutdown, safe telemetry and HTTP resource budgets.

Do not duplicate worker dispatch, source synchronization or business approval logic. API and worker may reuse concrete adapter factories; neither imports the other host. A real job execution mechanism is selected separately.

Invalid configuration or incompatible schema fails readiness. Keep deployment/resource identity distinct from current actor identity. Connection budgets account for all processes and any chosen checkpoint pool. No provider is enabled implicitly by a credential.

Open: API framework, auth topology, configuration validation and graceful shutdown policy. No runtime library/configuration is implemented here.
