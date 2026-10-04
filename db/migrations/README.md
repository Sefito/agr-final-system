# Schema migrations

Status: migration responsibility selected; runner/version scheme open.

## Decisions

- This is a new schema history; do not pretend the old application's migration numbering applies here.
- Store reviewed, ordered schema changes and migration metadata. Do not copy customer data, dumps or destructive reset scripts.
- Once released, a migration is immutable. Correct it through a new forward migration.
- The runner must serialize application, record successful versions and safely handle interruption/retry. Idempotency is a runner/migration contract, not a blanket requirement to rerun every SQL file forever.
- Fresh install and upgrade paths must converge to the same supported schema. Runtime checks compatibility before serving dependent operations.
- Prefer expand/backfill/switch/contract changes when old and new application versions overlap. Cleanup that deletes data requires separate explicit authorization.
- Separate legacy data mapping/import from schema creation. Preserve document IDs, occurrences, citation locators, originals and committed usage records where migrated.

## Verification

Use disposable PostgreSQL instances to verify fresh install, upgrade, failed/retried application and compatibility with the intended application versions. Data migration has reconciliation counts/checksums and an explicit rollback/recovery plan; code rollback alone does not undo committed data.

## Open decisions

Choose the migration runner, schema names, numbering/version convention and baseline creation. Decide whether workflow-engine tables exist only after the engine decision. Define deployment ordering and backup/restore acceptance before live migration.
