# Scripts

Add small development, verification and maintenance entry points here when executable tooling exists. Scripts call application operations rather than duplicating business logic. Commands that write data must identify their environment and customer target explicitly.

## Decisions and next gate

No executable scripts are added in this iteration. Future commands distinguish read-only validation from mutation, print a safe target summary and use the same application operations as HTTP/jobs. Migration, extraction and release commands must not silently target production or infer customer credentials. A dry run must actually avoid writes. Select command/task tooling with the first runnable slice.
