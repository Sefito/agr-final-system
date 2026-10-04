# Database

`migrations/` owns versioned schema changes for the new system. No legacy schema or migration has been copied and no database is provisioned.

PostgreSQL/pgvector is the initial target. Preserve document identity and original-byte behavior during migration. Separate application persistence from any future workflow-engine tables. Choose the migration tool before creating the first executable migration.

Document and test data migration separately from schema creation. Do not introduce reset, truncate or reseed behavior into production migration commands.
