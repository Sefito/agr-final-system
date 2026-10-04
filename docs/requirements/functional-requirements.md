# AGR Final System — Functional Requirements

Version: 0.1. Date: 4 October 2026. Status: draft for product and customer review.

This document specifies the intended product, not implemented capabilities. It is the proposed functional baseline for the new system. It draws on customer direction, the earlier AGR system's behavior and the current design discussions. Approval of the architecture does not automatically approve every proposed product rule below.

## 1. Purpose and outcomes

AGR enables authorized client users to find and consult organizational knowledge, navigate and contribute files, create and revise commercial documents, review and publish versions, and manage the agreed commercial records. Answers and documents must remain attributable to authorized evidence. Users must be able to distinguish a proposal from a saved document and a saved document from a published version.

Success means a user can complete these activities with clear scope, permissions, provenance, version/conflict handling and recoverable outcomes. A model's confident answer or a displayed progress event is not evidence that an operation has committed.

## 2. Scope and requirement status

| Status | Meaning |
|---|---|
| Confirmed | Explicit customer direction or agreed scope in the design conversation |
| Baseline | Existing safety/business invariant intended to be preserved; verify migration parity |
| Proposed | Recommended behavior requiring product review before implementation |
| Optional | Capability included only when selected by a customer/product decision |
| Deferred | Outside the initial release; not a promise of implementation |

All requirements belong to this draft. Status distinguishes their basis; it does not claim customer acceptance of the complete document. Acceptance scenarios describe future observable behavior, not tests already run.

### Initial scope

- Customer-owned deployment and separation between customers.
- Real authenticated users with authorized organization/project scope and security limits.
- Assistant consultations with traceable evidence.
- Authorized folder/file explorer, uploads and downloads.
- Commercial drafting, bounded editing, review, supported simple import and publication.
- Preservation of document identity, originals, occurrences, versions and representations.
- CRM designed around agreed business use cases, with shared behavior across interface and agent.
- Clear activity, usage and committed-operation outcomes.

SharePoint is optional. Its selection does not remove the need for a file explorer. Complex-file handling is deferred and reviewed with the customer later. The first CRM entity scope is confirmed: organizations, projects and document attachments only. Their exact fields/actions and the initial file formats remain open.

### Exclusions from the initial baseline

Advanced OCR/layout reconstruction and arbitrary Office round-trip compatibility; full HR/talent management; autonomous outbound sales/email; payments, invoicing and tax processing; cross-customer knowledge sharing; automatic SharePoint write-back; guaranteed integration with an external CRM; unrestricted autonomous writes; and opportunity, contact, pipeline-stage or task management in the first release.

Monorepo tools, package layout, PostgreSQL/Blob placement and workflow engines are architectural decisions. They are not functional requirements.

## 3. Users and capability profiles

These profiles describe responsibility, not a selected RBAC implementation. Capabilities may be combined per user and scoped by organization/project/classification. An administrative capability does not implicitly authorize reading every document.

| Profile | Expected activities | Limits |
|---|---|---|
| Knowledge reader | Browse permitted files, consult evidence and download allowed originals/representations | No write or approval capability implied |
| Document contributor | Upload and associate files in permitted destinations | Cannot widen destination access or publish without that capability |
| Commercial author | Generate drafts and propose edits using authorized evidence | Generation does not grant permission to commit or publish |
| Reviewer/publisher | Review and approve specified document actions | Current permission and reviewed version must still be valid |
| CRM editor | Create/update the agreed commercial records | Same validation for interface and agent |
| Customer administrator | Configure permitted product access and customer options | Membership authority and administrative UI scope remain open |
| Service operator | Assist deployment/support and inspect permitted operational status | Infrastructure access is not an application-reader role |

## 4. Domain terms

| Term | Definition |
|---|---|
| Customer | Organization owning a distinct deployment and data boundary |
| Organization/project scope | Authorized business context inside a customer's deployment |
| Security ceiling | Maximum permitted information classification for an actor/request |
| Content blob | Identical stored bytes, potentially shared by multiple separately authorized occurrences |
| File occurrence | A file's identity and context in a source/location/access scope |
| Logical document | Stable identity connecting versions of a business document |
| Version | A specific content revision with its own provenance and lifecycle |
| Rendition | A representation of a version, such as an original or generated delivery format |
| Evidence | Authorized source material with identity, revision and location sufficient to support a claim |
| Proposal | Reviewable intended content/change associated with scope, base version and evidence |
| Approval | Explicit authorization for a particular reviewed proposal/action |
| Committed operation | A durably recorded successful business change, distinguishable from its response delivery |
| Usage attempt | Provider processing measurement, which may exist even if no document is saved |
| Business receipt | Record of an applicable application charge, distinct from provider cost or an invoice |

## 5. Access and scope

| ID | Status | Requirement and observable acceptance |
|---|---|---|
| FR-ACC-001 | Confirmed | The system shall keep each customer's users/data separate. A user in customer A cannot discover, consult or change customer B's resources through any product entry point. |
| FR-ACC-002 | Baseline | Protected operations shall require a real authenticated actor in production. Missing/invalid authentication cannot be replaced by a client-supplied demo identity. |
| FR-ACC-003 | Baseline | The system shall authorize capabilities, organization/project scope and classification before returning protected information or preparing model context. Filenames, counts, previews and activity can also be protected. |
| FR-ACC-004 | Baseline | The system shall allow a requested scope/ceiling to narrow access only. A user cannot obtain a broader result by changing a filter, deep link or agent instruction. |
| FR-ACC-005 | Baseline | A conversation shall retain its selected organization/project scope. Changing scope starts a different conversation; reduced access cannot reuse protected prior context. |
| FR-ACC-006 | Baseline | Sensitive actions shall recheck current permission at execution. A proposal approved before revocation cannot subsequently create a version, publish or deliver protected originals using stale authority. |

The authority for memberships/product entitlements and the timing of revocation are open decisions OD-01/OD-02. Access denials must disclose no protected resource details; exact error presentation can vary by operation.

## 6. Document explorer and contribution

| ID | Status | Requirement and observable acceptance |
|---|---|---|
| FR-DOC-001 | Confirmed | Users shall navigate an authorized folder/file hierarchy with understandable breadcrumbs and source context. Names, counts and children outside their access are absent. |
| FR-DOC-002 | Confirmed | The system shall preserve stable file/document identity separately from names, paths and content hashes. Rename/move does not unintentionally create a new source identity; equal bytes in different scopes remain separately authorized. |
| FR-DOC-003 | Confirmed | Authorized contributors shall upload a file into an explicit permitted scope/destination. Missing or inaccessible destinations cannot create an unrestricted attachment. |
| FR-DOC-004 | Proposed | Upload shall validate supported format, size and safe container expansion, and expose accepted/processing/ready/failed/not-indexed outcomes as applicable. The current 25 MiB platform-file limit is provisional, not a final customer-wide file-size requirement. |
| FR-DOC-005 | Baseline | The system shall preserve the accepted original and distinguish it from extracted/sanitized text or generated renditions. A sanitized model representation must not make an otherwise restricted original downloadable. |
| FR-DOC-006 | Proposed | Authorized files outside the extraction scope shall remain visible with a not-indexed explanation. They cannot produce fabricated searchable content or citations. |
| FR-DOC-007 | Baseline | Users shall download only currently authorized originals/renditions, associated with the correct occurrence/version. A copied historical link does not bypass a later permission change. |
| FR-DOC-008 | Baseline | Upload/index readiness shall be explicit. A successful response cannot imply that evidence is searchable when only original bytes were saved. The release must select synchronous readiness or a documented asynchronous status contract. |

Folder creation/move permissions, upload destination, formats, readiness and retention are OD-03 through OD-06. The system must distinguish an empty authorized folder from an inaccessible resource without disclosing the latter's contents.

## 7. Assistant consultations

| ID | Status | Requirement and observable acceptance |
|---|---|---|
| FR-AST-001 | Baseline | Users shall ask questions within an authorized scope and receive evidence-backed answers or a clear refusal/insufficient-evidence outcome. No unsupported fact is presented as a sourced answer. |
| FR-AST-002 | Baseline | Each emitted citation shall refer to an authorized returned source with a meaningful locator. Every cited label belongs to the answer's source set; exact names, figures and dates remain faithful to evidence. |
| FR-AST-003 | Baseline | Consultation shall not reveal or reconstruct prohibited personal information. Privacy/access rules apply to retrieved material, generated text and conversation reuse. |
| FR-AST-004 | Proposed | Users shall see progress and distinguish partial, completed, failed and cancelled answers. Loss of connection shall not be displayed as successful completion without reconciliation. |
| FR-AST-005 | Baseline | Users shall reopen only permitted conversations and evidence links. Another actor's conversation identifier or a lowered security ceiling cannot expose prior content. |

Partial-text retention, consultation cancellation/continuation and history retention are OD-06/OD-07. Insufficient evidence is a valid business outcome, not necessarily a provider error.

## 8. Commercial documents

| ID | Status | Requirement and observable acceptance |
|---|---|---|
| FR-COM-001 | Proposed | An authorized author shall initiate a draft for an enabled document type and scope. The system shall ask for necessary missing inputs rather than invent required customer facts. |
| FR-COM-002 | Baseline | Draft generation shall use permitted evidence and validated references. Before reference validation only permitted metadata is available; format references supply structure rather than unapproved substantive content. |
| FR-COM-003 | Baseline | The system shall present generated content or proposed edits for review before a write requiring approval. A model response or ambiguous conversational confirmation cannot independently authorize that write. |
| FR-COM-004 | Baseline | Approval shall identify the reviewed proposal/action and its scope, base version and relevant evidence revision. Changed inputs invalidate the old approval and require renewed review. |
| FR-COM-005 | Baseline | Applying an edit shall create the intended version against the expected base. A newer concurrent version produces a conflict, never silent overwrite. |
| FR-COM-006 | Proposed | Users shall import an agreed supported simple file into an authorized document/version relationship after review. The system shall state what it can preserve/extract and reject unsupported advanced processing honestly. |
| FR-COM-007 | Baseline | Publishing shall explicitly identify a current authorized version. Creating a draft shall not retire the previous published version; changing the active final version happens only through publication. |
| FR-COM-008 | Baseline | Users shall distinguish discarded proposals, saved drafts and published versions. Discarding an uncommitted proposal shall not create a published document or a success charge. |
| FR-COM-009 | Baseline | Repeating an approved save/publication request shall not create duplicate business results. A committed result shall remain discoverable even if response delivery failed. |

Document types, approver delegation, simple import semantics and the relationship between publication and search readiness remain OD-08/OD-09. Editing a published document cannot silently change the content represented by that published version.

## 9. CRM and agent actions

CRM scope is confirmed for the first release: organizations, projects and document attachments only. Opportunities, contacts, pipeline stages and tasks are outside this release. Specific fields, edit permissions and activity behavior below remain proposed where marked. This resolves OD-10.

| ID | Status | Requirement and observable acceptance |
|---|---|---|
| FR-CRM-001 | Proposed | Permitted users shall list and create the agreed organization/project records needed for commercial scope and attachment. Required fields and destination access shall be validated before creation. |
| FR-CRM-002 | Proposed | Permitted users shall update agreed editable fields with conflict handling and an attributable activity record. A concurrent update cannot be silently overwritten. |
| FR-CRM-003 | Baseline | The interface and agent shall apply the same business validation and access rules for a CRM operation. Agent instructions do not bypass required fields, permissions or confirmation. |
| FR-CRM-004 | Baseline | Document attachment/listing shall respect both project access and document permissions. An inaccessible project cannot reveal attachment metadata through an empty or partially populated response. |
| FR-CRM-005 | Proposed | Protected fields shall remain protected in history, exports and aggregates if such fields are introduced. Unknown/redacted values are not shown or counted as zero. |

Organization master-data authority, required fields, activity retention, undo and external CRM interoperability remain OD-11/OD-06. No generic undo or complete CRM feature set is promised by these requirements.

## 10. Optional SharePoint source

All requirements below are conditional on selecting SharePoint. They do not authorize remote writes or promise arbitrary-format processing.

| ID | Status | Requirement and observable acceptance |
|---|---|---|
| FR-SP-001 | Optional | An authorized customer setup shall select source sites/libraries/folders. Files outside the selected source grant shall not be imported. |
| FR-SP-002 | Optional | Users shall see authorized source hierarchy and file status, with stable source identity. Renames/moves retain that identity; unchanged bytes do not suppress access/classification changes. |
| FR-SP-003 | Optional | Synchronization shall account for additions, modifications, moves and deletions under the agreed lifecycle policy. Repeated reconciliation shall not duplicate documents; interrupted updates shall be recoverable. |
| FR-SP-004 | Optional | The system shall make source freshness and safe processing failure status available to permitted users/operators. An unsupported file can remain visible without being indexed. |

Source ACL versus application access mapping, sync cadence, deletion retention and write-back are OD-12/OD-13. A source service's ability to read a site does not grant every AGR user permission to its files.

## 11. Activity, usage and operation recovery

| ID | Status | Requirement and observable acceptance |
|---|---|---|
| FR-OPS-001 | Proposed | Users shall inspect the permitted state/outcome of their document/commercial operations and pending approvals. Operational status must not reveal another actor's protected content. |
| FR-OPS-002 | Baseline | The system shall distinguish provider-processing usage from a business charge. Known attempts are attributed; unknown measurement remains unknown even when no document was saved. |
| FR-OPS-003 | Baseline | If a business action is billable, its successful result and applicable charge receipt shall be recorded consistently without duplicate success charges. A failed business commit creates no success receipt. |
| FR-OPS-004 | Proposed | Authorized activity shall identify successful business actions and their actor/outcome without exposing restricted before/after values. The activity view is not unrestricted raw audit data. |
| FR-OPS-005 | Baseline | Recovering after interruption shall distinguish unfinished work from an already committed operation. A lost response cannot cause fresh publication/version creation or charging for the same action. |
| FR-OPS-006 | Proposed | Users shall receive clear outcomes for invalid input, insufficient evidence, stale approval, conflict, unavailable service, cancellation and uncertain completion. Recovery instructions shall match the actual business state. |

Business tariffs, billing events, usage-view access, cancellation and activity retention are OD-06/OD-07/OD-14. The earlier system's tariff is migration evidence, not an approved new price.

## 12. Customer configuration and administration

| ID | Status | Requirement and observable acceptance |
|---|---|---|
| FR-CFG-001 | Confirmed | The customer shall retain ownership/control of its deployment and data. Ending provider support shall not make customer information depend on continued access to a provider-owned shared data environment. |
| FR-CFG-002 | Proposed | Authorized customer setup shall select enabled capabilities, branding and document types. Invalid required configuration shall produce a visible setup failure rather than silently using another customer's profile. |
| FR-CFG-003 | Baseline | Customer-content processing shall occur only under the approved provider/data policy. Hosting in Azure or configuring a credential shall not silently authorize model, embedding or managed-extraction processing. |
| FR-CFG-004 | Baseline | Demonstration behavior shall be explicitly identified and separated from production. A production outage shall not return invented customer records as a fallback. |

An administrative UI is not automatically required: configuration may initially be assisted. Approval ownership and allowed configuration changes are OD-01/OD-08/OD-15. Infrastructure administration and application-data access remain separate responsibilities.

## 13. Primary use-case walkthroughs

| Use case | Preconditions | Main user/system interaction | Success | Alternative/failure | Requirements |
|---|---|---|---|---|---|
| UC-01 Browse files | Authenticated reader in permitted scope | Navigate folders and inspect metadata/status | Authorized hierarchy displayed | Inaccessible resource reveals no children; empty permitted folder is explicit | FR-ACC-003, FR-DOC-001/002/006 |
| UC-02 Upload original | Contributor and permitted destination | Select file/scope, validate and submit; follow readiness state | Original and relationship preserved with honest status | Invalid size/type, unavailable destination, failed extraction | FR-DOC-003/004/005/008 |
| UC-03 Consult knowledge | Reader and permitted conversation scope | Ask; inspect answer and sources | Evidence-backed response and authorized citations | Refusal, insufficient evidence, provider failure or cancellation | FR-ACC-005, FR-AST-001–005 |
| UC-04 Generate draft | Author, enabled type and permitted inputs | Resolve missing facts; generate; inspect proposal; approve save | Saved draft and applicable receipt | Missing facts, changed evidence, duplicate approval | FR-COM-001–004/009, FR-OPS-003 |
| UC-05 Edit version | Authorized editable base | Request changes; review; approve expected version | New saved version | Newer concurrent version, revoked rights, invalid proposal | FR-COM-003–005/009 |
| UC-06 Import supported file | Contributor and known document relationship | Stage; inspect treatment; confirm association/version | Original retained under selected import contract | Unsupported processing or incompatible target | FR-DOC-005, FR-COM-006 |
| UC-07 Publish | Publisher and current eligible version | Review final candidate; explicitly confirm | Intended active final version | Changed evidence/base, stale approval or revoked access | FR-COM-004/007/009 |
| UC-08 Maintain CRM record | CRM editor and agreed entity scope | Create/update through interface or agent | Validated record and authorized activity | Missing required values, conflict, inaccessible record | FR-CRM-001–005 |
| UC-09 Download artifact | Current access to occurrence/version/rendition | Open/download correct artifact | Authorized original/representation delivered | Stale link or changed access refuses delivery | FR-ACC-006, FR-DOC-005/007 |
| UC-10 Reconnect after loss | Access to prior operation | Read current status and committed result | Continue valid pending work or recover existing result | Stale approval or lost access blocks continuation | FR-COM-009, FR-OPS-001/005/006 |
| UC-11 Synchronize source | SharePoint selected and configured | Observe/reconcile source changes and status | Stable authorized catalogue with honest freshness | Throttling/interruption/deletion follows selected policy | FR-SP-001–004 |

## 14. Business lifecycle distinctions

The following are conceptual user-visible states, not a database enum or mandatory workflow engine.

| Object | Relevant lifecycle | Key rule |
|---|---|---|
| Uploaded file | Validating, accepted, processing, ready, not indexed, failed | Stored original and searchable evidence are different outcomes |
| Proposal | Preparing, reviewable, awaiting approval, invalidated, discarded, committed | Only the reviewed current proposal can authorize its action |
| Document version | Saved draft/provisional, published, superseded, discarded where applicable | Creating a draft does not replace the published version |
| Consultation | Preparing, answering, completed, cancelled, failed | Partial text is not silently marked completed |
| Business operation | Pending, executing, committed, failed, cancelled or uncertain | Response loss does not erase a committed result |

State presentation must explain what the user can do next. Revocation changes the permitted view/actions regardless of lifecycle. Retention/deletion and published-document reopening remain explicit product choices.

## 15. Release acceptance scenarios

Use invented data and at least two actors with different organization/project/classification access. The following scenarios form a proposed acceptance set, not an assertion of current coverage.

1. A user cannot enumerate another customer's data, protected filenames/counts or foreign conversations.
2. Upload retains original identity/bytes, correctly associates destination and reports true search readiness.
3. Equal bytes in two differently classified occurrences do not merge their access rights.
4. An answer preserves exact figures and includes only valid authorized citation labels; absent evidence yields an explicit outcome.
5. A draft asks for missing required facts and does not invent them.
6. Double approval creates one business result and at most one applicable success charge.
7. A changed base version/evidence revision invalidates the reviewed approval and produces a recoverable conflict.
8. Revoked access prevents resumed execution, protected history reuse and original downloads.
9. A new draft leaves the old final active until an authorized publication operation succeeds.
10. Process/browser interruption distinguishes unfinished work from a result committed before delivery; recovery creates no duplicate version/publication/charge.
11. CRM interface/agent apply identical command validation; activity reveals no restricted field values.
12. When SharePoint is selected, rename, unchanged-content access change, deletion and interrupted synchronization behave according to the selected source policy.
13. Production unavailability returns an honest unavailable state instead of demonstration records.
14. A provider policy denial blocks customer-content processing even if credentials/resources are configured.

Agree pass/fail examples and the release subset before implementation. Optional scenarios apply only when their capability is selected. Performance/load, accessibility and restore/security testing need additional non-functional acceptance criteria.

## 16. Product decisions and owners

### Recorded scope decision

OD-10 is resolved by the product owner: first-release CRM includes organizations, projects and document attachments only. Keep this identifier for traceability. Opportunity/contact/pipeline/task management requires a later scope change.

### Open decisions

Owners are suggested responsibilities, not named people or an approved organizational structure.

| ID | Decision | Suggested owner | Needed before |
|---|---|---|---|
| OD-01 | Membership/entitlement authority and administrative capabilities | Customer administrator + product owner | Real-user access design |
| OD-02 | Revocation timing and effects on active work/history | Customer security owner + product owner | Protected workflow acceptance |
| OD-03 | Who can create/move folders and upload to which destinations | Customer content owner | Explorer/contribution implementation |
| OD-04 | Initial simple formats, size/expansion limits and import fidelity | Customer content owner + product owner | Upload/import acceptance |
| OD-05 | Synchronous versus asynchronous indexing/publication readiness | Product owner | User-visible processing contract |
| OD-06 | Retention/deletion for originals, history, proposals, audit and source removals | Customer data owner | Real-client storage |
| OD-07 | Which operations continue after disconnect, cancellation effects | Product owner | Progress/recovery acceptance |
| OD-08 | Document types, required facts and who may approve/publish another user's work | Customer commercial owner | Commercial acceptance |
| OD-09 | Published-version edit/reopen behavior and search promotion | Customer content/commercial owner | Version/publication implementation |
| OD-11 | Organization/project fields and master data, sensitive fields, undo and external interoperability | Customer commercial owner | CRM command/history design |
| OD-12 | SharePoint selection, source grants and source ACL/application policy mapping | Customer content/security owner | Connector rollout |
| OD-13 | Synchronization cadence, deletion policy and any write-back authority | Customer content owner | Source lifecycle acceptance |
| OD-14 | Billable events, tariffs, quotas and access to usage summaries | Commercial/product owner | Charge/usage implementation |
| OD-15 | Approved model/data processing and who may change provider configuration | Customer data/security owner | Any real-content processing |

These decisions should not be silently settled by architecture or implementation defaults. Unresolved optional scope is not an accepted release commitment.

## 17. Relationship to architecture and non-functional requirements

This document specifies product behavior. The [architecture overview](../architecture/overview.md), [package dependency rules](../architecture/package-dependencies.md) and [decision register](../decisions/README.md) describe how implementation responsibilities may satisfy it. A package folder or selected tool is not proof that a requirement is met.

A separate non-functional baseline should define availability/recovery objectives, response/progress latency, concurrent workload, accessibility targets, operating cost limits, supported languages/locales, privacy/security verification, backup restore and support operations. No numeric SLA, complete retention policy or infrastructure cost guarantee is established by this functional draft.

Later implementation/test work should reference requirement IDs. Keep these IDs stable when clarifying wording; record substantive scope changes and superseded requirements explicitly. Proposed and optional requirements become release obligations only through an agreed baseline.
