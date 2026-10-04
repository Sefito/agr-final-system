# API client package

Status: frontend transport package selected; generation tool open.

Future workspace name: `@agr/api-client`. Export the generated HTTP client/types and a separately typed event-stream transport. Consume reviewed `contracts/http/` and `contracts/events/` artifacts, not Python source files.

The API remains authority for HTTP schema. Event schema is language-neutral and versioned. Handwritten transport/session policy is separated from generated files so regeneration does not erase it.

No React dependency or UI workflow belongs here. Do not infer write success from progress events or automatically retry a mutation without its idempotency contract. Credentials/session handling follows the selected authentication topology.

Open: generator, output location and event parser. A task dependency must ensure schema production precedes client generation and web type-check/build. No generated code is added in this iteration.
