# Frontend verification

Status: planned suite.

Use synthetic identities, documents and API/event fixtures. Verify user-visible flows: authorized navigation, file status, proposal review, explicit approval, conflict recovery and production unavailable states.

Test session switching/cache clearing, interrupted streams, duplicate clicks and commit-before-response failure. Contract fixtures must reflect implemented backend schemas rather than handwritten guesses.

Accessibility and keyboard navigation matter for folder trees, dialogs and approval controls. Choose component/browser test tools during implementation. No browser or UI test has been run for this documentation scaffold.
