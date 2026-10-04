# API host verification

Status: planned tests, no executable suite.

Verify authentication and ownership before streaming, HTTP error mapping, safe event projections, upload limits and dependency wiring using synthetic package/adapter doubles.

Business invariants are tested in their owning packages. Cross-package database/recovery paths belong to `tests/system/`. Do not duplicate every domain test through HTTP.
