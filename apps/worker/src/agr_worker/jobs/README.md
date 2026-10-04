# Job entry points

Status: proposed job responsibilities.

Initial candidates: extraction/index enrichment, optional SharePoint reconciliation, commercial generation and index rebuild. Add only jobs required by implemented use cases; do not build a universal scheduler framework.

An entry point resolves an explicit customer/operation target, validates its task claim, invokes package use cases and records safe progress/outcome. Persist sufficient step results for the agreed recovery behavior. A lost claim prevents writes; retry limits include adapter/SDK retry behavior.

Open: engine/queue, task version compatibility, cancellation, claim renewal and which commercial operations continue after browser loss. Never retry a committed business result as a fresh approval/charge.
