# Integration verification

Status: planned suite; disposable resources required.

Verify module-owned persistence and external adapter behavior with explicit test targets. Tests must not discover and use an existing customer database from ambient credentials.

Initial database cases: shared version/bytes/receipt transaction; concurrent expected-version conflicts; duplicate approval; source metadata visibility change; migration upgrade/fresh-install parity; task claim loss and recovery if jobs are implemented.

Provider contract doubles remain the default. Azure/SharePoint live tests need a separately provisioned synthetic environment and explicit authorization. Record resources used and cleanup requirements. Never label a synthetic integration check as a real-client acceptance battery.
