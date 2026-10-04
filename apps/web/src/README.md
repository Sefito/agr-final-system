# Frontend source

Status: feature-based source boundary selected.

[app](app/README.md) composes the shell/routes/providers; [features](features/README.md) owns product flows; [shared](shared/README.md) contains reusable UI/transport primitives.

Keep backend-owned business rules on the backend. UI validation helps users but does not authorize operations. Tenant/user/scope changes invalidate affected client state. Source configuration can personalize presentation without altering access invariants.
