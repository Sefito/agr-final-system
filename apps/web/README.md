# Web application

The intended frontend is React with TypeScript. Tooling, dependencies and runnable commands are not installed yet.

`src/app/` owns routing and application composition. `src/features/` groups user-facing functionality by product area. `src/shared/` holds reusable presentation components and the typed API client; it does not duplicate backend business policy.

HTTP types should be generated from the backend's implemented contract. Streaming events need their own versioned schema. Scope caches by user and authorization context. Production failures show explicit unavailable states; fictional demonstration data belongs to an explicit demo mode.

## Decisions and next gate

Read the [source index](src/README.md) and feature READMEs. Frontend state follows backend resource/proposal versions; it does not invent successful commits from progress events. Initial screens need accessible navigation, explicit conflicts and safe session cache invalidation. Build, forms/query and testing tools remain open.
