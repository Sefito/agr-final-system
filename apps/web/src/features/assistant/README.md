# Assistant interface

Status: consultation interface proposed.

Show scope selection, conversation history, answer progress, exact citations and authorized source navigation. Scope is fixed after a conversation begins; changing it starts another conversation.

Decisions: display privacy/insufficient-evidence outcomes distinctly; do not treat partial text as a complete persisted answer; use the stream's authorized source set; clear high-ceiling history when access changes. A citation opens an authorized backend operation rather than reconstructing a storage URL.

Acceptance: failed connection has a recoverable state; cancellation is visible; a completed answer has only valid source labels; inaccessible historical evidence is not revealed by cached previews.

Open: presentation, stream reconciliation, retention and whether consultation continues after browser disconnect. Follow the backend's decision rather than inventing independent frontend semantics.
