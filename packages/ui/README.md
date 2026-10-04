# UI primitives package

Status: presentation package selected; design-system library open.

Future workspace name: `@agr/ui`. Export accessible primitives useful across document, assistant, CRM and commercial screens. Keep feature state, record commands, pricing and authorization outside this package.

Start with actual reusable components rather than copying a full catalogue. React is a peer/runtime contract to decide with frontend tooling; do not bundle independent incompatible React copies. The UI package does not depend on api-client or applications.

Open: component framework, styling/tokens, export surface and visual/accessibility verification. No UI implementation is added here.
