# Application shell

Status: responsibility selected; routing/state libraries open.

Own startup, authenticated session presentation, routing, global providers, navigation and deployment feature configuration. Compose feature screens without reaching into their internal state.

Decisions: expose only implemented/enabled capabilities; clear actor/scope-dependent caches on session change; represent unavailable/offline/unauthenticated states explicitly; keep demo mode identifiable and isolated. Fictional seed data must not replace failed production requests.

The backend supplies authorized capabilities and scope options. Hidden navigation is a presentation choice, not security enforcement. Deep links resolve authorized resources and do not restore an old actor's cached data.

Acceptance: sign-out removes protected client state; another actor cannot see previous citations/files; a direct route to a disabled feature has a clear result; API outage shows unavailable content.

Open: router, session topology, configuration bootstrapping and frontend build/deployment strategy.
