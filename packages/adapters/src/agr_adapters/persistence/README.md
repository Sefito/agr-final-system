# Persistence adapters

Status: SQL/transaction implementation proposed; library open.

Implement the data ports owned by business packages, grouped internally by owning vocabulary. Do not turn this folder into a generic CRUD repository or relocate business rules here.

One short coordinated SQL transaction can bind document bytes/version/citations, usage receipt and committed operation result. Adapter factories bind each participant to that transaction; they do not independently commit. Business packages own preconditions and command semantics.

A minimal transaction interface may become shared only if actual public signatures require it. Avoid creating a broad kernel package for timestamps/UUID helpers. Never leak psycopg/ORM connection types through business interfaces.

Open: SQL library/ORM choice, transaction protocol, schema mapping and connection pooling. Database migrations remain coordinated at `db/migrations/`. Verification must demonstrate rollback, conflicts and commit-before-response recovery on disposable PostgreSQL.
