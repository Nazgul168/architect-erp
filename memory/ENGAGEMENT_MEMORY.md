# ENGAGEMENT_MEMORY.md

- **MEMORY_VERSION:** `1.1`
- **LAST_RECONCILED:** `2026-09-08`
- **SOURCE_PARTS_BASELINE:** Current Project Sources `Part 00 — Scope & Architecture Principles`, `Part 01 — Business Analysis`, `Part 02 — Process Architecture`, `Part 03 — System Analysis`, fully reviewed during Global Reconciliation on 2026-09-08.
- **BOOTSTRAP / RECONCILIATION reference:** QA Bootstrap Batches 1–8 + accepted Global Reconciliation, 2026-09-08.

## Engagement Identity / Status

- **Engagement:** NURA ERP Architecture
- **Engagement ID:** `ENG-NURA-ERP-001`
- **Status:** ACTIVE
- **Memory status:** UPDATED WORKING VERSION — POST-BASELINE PROJECT LIFECYCLE / SETUP / AUTHORIZATION REVIEW INCORPORATED
- **Current architecture state:** Parts 00–03 developed; controlled normalization is required before Part 04.
- **Purpose of this memory:** compact working memory of the current NURA ERP architecture. It is not a transcript, Bootstrap ledger, or substitute for the architecture Parts.
- **Canonical baseline persistence:** baseline `ENGAGEMENT_MEMORY.md` v1.0 is user-confirmed as canonically persisted in the canonical Engagement Git repository. The same confirmation applies to the baseline `ARCHITECT_PROFESSIONAL_BACKGROUND.md` and updated `00_ENGAGEMENT_MANIFEST.md` referenced by this Engagement.
- **Canonical persistence:** Canonical persistence of the current version is determined by the canonical Engagement repository and its version history. This runtime has no verified canonical write path and does not claim to perform canonical writes.

### Working source discipline

For current Engagement truth, use the following working order:
1. applicable authoritative NURA / NU / legal / institutional sources for the claim in question;
2. current accepted architecture Parts and controlled Engagement Memory;
3. verified supporting evidence;
4. historical QA only for rationale, lineage, rejected/superseded alternatives, and unresolved conflicts.

Do not use QA chronology alone to infer current truth. Do not treat an expert-originated recommendation as user-originated merely because it appears in a later draft.

### Accepted correction pending propagation

If an accepted / reconciled correction is explicitly recorded in this Engagement Memory as **not yet propagated to a Part**, that Part is treated as **stale for that specific claim only** until synchronization. This is an Engagement-level state of **accepted but not yet implemented**.

In all other Part ↔ Engagement Memory conflicts, do not silently prefer either source. Keep the discrepancy as an explicit conflict until it is reconciled.

---

## Current Scope

NURA ERP is the NURA-owned operational information system for end-to-end **Research Administration**.

Core lifecycle:

**Funding Opportunity / Call → Application → Funding Decision → Project Setup / Administration → Funding / Agreements → Budget → Project Execution / Procurement / Services → Payment → Reporting → Project Closure.**

The system is **Project-centered but not Project-only**. Material objects with their own identity, lifecycle, history, authority, or reporting value remain independent Business Objects.

NURA ERP does **not** replace:

- 1C accounting;
- EDMS official registration / approval / signing processes where EDMS remains authoritative;
- corporate HR as a complete HR system;
- grantor / state submission systems;
- external tender platforms;
- institutional Research Repository;
- source-code repository;
- other enterprise systems that remain authoritative for specific facts or processes.

ERP links authoritative external facts into a unified operational Research Administration context while preserving provenance and source boundaries.

---

## Canonical Definitions

### Application and Project

**Application ≠ Project.**

Application preserves its own lifecycle, review history, identifiers, Final Submitted Version, and outcome. An Awarded / Approved Application can provide source data for Project creation without re-entry, but the Project is a separate Business Object with its own lifecycle and administration.

### Person, User and Project Participation

**Person ≠ User Account ≠ Project Participation.**

PI, Co-PI, RA, Researcher and similar labels are contextual Project Roles / Participations, not separate Person entities. Employment Contract / Service Agreement is separate from Project Participation.

### Funding Decision, Funding Agreement, Project Lifecycle and Operational Authorization

**Funding Decision ≠ Funding Agreement ≠ Project.**

For external funding, a Funding Decision / Award may justify creation of the Project record before the Funding Agreement is signed. This allows Legal, Post-Award and PI to perform Project Setup and other preparatory work in one Project context.

For external funding:

- Funding Decision recorded, Funding Agreement not yet signed → Project business lifecycle = `Setup`;
- Signed Funding Agreement recorded → Project business lifecycle = `Active`.

Actual Funding receipt is separate from Project lifecycle. A delayed or missing tranche does not make a signed external Project non-active.

Project business lifecycle must be derived from recorded business facts and must not be freely assigned through a generic status field.

`Setup Complete` is a readiness outcome, not a Project lifecycle status.

Operational permission to initiate expenditures is a separate management control. Head of Post-Award must explicitly authorize expenditure initiation after all Mandatory Setup Checks are complete.

The final terminology and detailed state model for Operational Authorization / restricted operation remain open within Project lifecycle normalization.

### Funding Agreement Amendment

**Funding Agreement Amendment** is a separate Business Entity related `1:N` to Funding Agreement. It has its own lifecycle, legal dates, proposed/effective terms, history and causal consequences.

### Funding, Budget and Accounting

**Funding ≠ Budget ≠ Commitment ≠ Operational Actual ≠ Accounting Actual.**

- Funding describes contracted / planned / received / recognized contributions and schedules.
- Budget describes approved allocation authority and its governed revisions / versions.
- Commitment / Encumbrance reserves future financial obligation.
- Operational Actual is an operational fact used for current administration.
- Accounting Actual is the authoritative accounting fact from 1C.

### External Project Spending Gate

For external grants, no Project expenditure or financial commitment may be initiated before the Funding Agreement is signed.

Retroactive contractual `Effective From` does not by itself authorize NURA to incur Project expenditures before the actual signing of the Funding Agreement. Scientific work may in practice begin earlier on available resources, but this does not create expenditure authority under the grant.

Imported Accounting Actuals / 1C facts that imply Project expenditure before the required signed Funding Agreement must be automatically identifiable for reconciliation / investigation.

### Budget Authorization, Allocation, Revision and Version

Budget may be prepared as Draft during Project Setup before the Funding Agreement is signed.

Formal Budget Approval occurs only after the applicable Funding Agreement has been signed and recorded in ERP. The curating Post-Award Manager explicitly approves the Budget, and Budget Approval is a Mandatory Setup Check.

A Budget may be approved with only part of the total Funding Agreement amount allocated to specific Budget Categories / Lines. The model must distinguish at least:

- total applicable Funding / Agreement Amount;
- Approved Budget Allocations;
- Unallocated Amount;
- Available Budget within approved allocations.

Unallocated Amount is visible to PI and Post-Award but is not spendable until allocated to an applicable Budget Category / Line and approved. Full allocation of the total Funding Agreement amount is not required for `Setup Complete`.

**Budget Revision** is a controlled proposed change to an existing approved Budget. Any change to an already Approved Budget requires the applicable Budget Revision / Approval process before changed amounts become effective.

**Budget Version** is an immutable approved/effective or historical state produced by the governed Budget lifecycle.

One underlying structured Project Budget may support multiple controlled reporting / management views through versioned mappings.

### Research Need

**Research Need** is a PI-oriented structured statement of a planned material procurement need and planning input. Its exact own lifecycle versus derived downstream procurement progress remains unresolved and must be normalized before Data Architecture / Data Model finalization.

### Procurement Plan

Target taxonomy:

**Initial Procurement Plan → Procurement Plan Amendment(s) → Procurement Plan Version(s) → Consolidated Current Procurement Plan.**

- Current Operational Truth is structured data.
- Approved versions are immutable historical records.
- Official Word/PDF documents are generated representations where required.
- Procurement Planning is permitted during Project `Setup`.
- Research Needs and Procurement Plan represent planning / forecast information and do not by themselves authorize expenditure or create a procurement commitment.
- An Approved Procurement Plan may exist before Project Operational Authorization.
- A formal Procurement Request remains required to initiate procurement.
- Where a Procurement Request is created from an approved Procurement Plan Item, it may bypass repeat manual Post-Award review and proceed to Procurement Office only after automatic validation against the current approved Budget, applicable limits, existing Commitments and Operational Restrictions.

### Procurement Request and Procurement Case

**Procurement Request ≠ Procurement Case.**

- Procurement Request represents what the Project / Research Team requested and remains active until all Request Items reach a valid final outcome.
- Procurement Case represents the concrete Procurement Office execution context.

Request↔Case relationships must be stored at Item / Quantity allocation level and support both split and consolidation.

Whether **Procurement Procedure** is a separate first-class Business Object or is represented through Procurement Case + Procurement Method-specific workflow remains unresolved.

### Delivery and Acceptance

**Delivery ≠ Acceptance.**

Delivered Quantity and Accepted Quantity are separate facts. A delivery may be fully delivered but only partially accepted or rejected.

### Change, Correction, Reconciliation and Override

**Business Change ≠ Data Correction ≠ Reconciliation Exception ≠ Controlled Exception Override.**

- Business Change represents a real change in the business fact and uses the applicable governed workflow.
- Data Correction repairs an incorrectly recorded fact without creating false business history.
- Reconciliation Exception records a mismatch between operational interpretation and authoritative accounting data.
- Controlled Exception Override permits an approved deviation from an applicable rule for one specific case without changing the rule itself.

### Business Object, Document and File

**Business Object ≠ Document ≠ File.**

Structured business facts are primary where search, control, automation, audit or reporting require them. Word/PDF/Excel may be official documents, generated representations, input/output formats or transitional interfaces, but should not become the sole operational source of structured facts.

### Audit / External Review

**Audit / External Review** is a separate Business Entity, not a Project status. It may have explicit object scope or criteria-based scope and may involve one or many Projects / Funding Agreements.

---

## Established Architectural Decisions

1. **Real business before generic ERP patterns.** Existing work is analyzed and improved before automation. Generic ERP conventions do not override NURA business semantics.

2. **Enter Once, Reuse Everywhere.** Structured data already available in ERP or authoritative systems should be reused downstream rather than re-entered.

3. **Business Object First.** Architecture starts from identity, lifecycle, relationships, authority, history and business meaning rather than screens, files or database tables.

4. **Full History.** Significant approved/effective facts are not silently overwritten. Material historical states, decisions, actors, reasons and evidence should remain reconstructable **subject to applicable retention, privacy, legal and institutional requirements**. Full History does not override authoritative deletion, minimization or retention obligations.

5. **Current / Proposed / Effective separation.** Pending Amendments, Project Changes, Budget Revisions and similar changes do not replace current effective values until the governing event occurs.

6. **Legal / decision dates and effective dates are separate.** Signature, registration, decision and `Effective From` may differ, including legitimate retroactive conditions.

7. **Independent lifecycles + causal links.** Agreement, Amendment, Funding, Project, Budget, Team and other governed domains maintain independent histories. One event may trigger another process but must not silently mutate unrelated domain facts.

8. **Action-driven state transitions.** Business status changes through permitted Business Actions and validations, not unrestricted status-field editing.

9. **Business lifecycle ≠ operational progress ≠ child-object state ≠ event/action.** Not every process step belongs in the top-level Business Object lifecycle.

10. **Same underlying truth, role-appropriate representation.** Different roles may see different depth and presentation of the same underlying process/data without creating parallel facts.

11. **Explicit handovers.** Cross-functional handover should be recorded as a system event / state transition rather than relying on email, folders or personal knowledge.

12. **Processing time ≠ waiting time.** Process analytics should distinguish actual processing from waiting and attribute delay to the relevant party/stage.

13. **One underlying Project Budget, multiple controlled views.** External and internal reporting forms use mappings/views rather than independent copies of the Budget.

14. **Project Change Management.** Significant changes after activation use controlled requests, Current/Proposed comparison, approval route, evidence, decision and Effective From.

15. **Funding Agreement Amendment is first-class.** An Effective Amendment may trigger Funding Update, Budget Revision, Project Change or other domain processes through explicit causal links.

16. **Funding, Budget and Accounting remain separate layers.** Contracted / planned / received Funding, Budget, Commitments, Operational Actuals, Accounting Actuals and Available Budget must not collapse into one amount.

17. **Procurement Request continues after Case formation.** Request remains active until all Items reach final outcomes. Detailed progress is derived primarily from Request Items / Allocations / Cases / Contracts / Deliveries / Acceptance / Payments.

18. **Procurement split/consolidation preserves source allocation.** Multi-project / multi-request procurement must preserve Project, source Request/Line, quantity, amount, Budget Line and Funding Source and prevent double allocation.

19. **Goods Acceptance is confirmed by the actual receiver.** PI may participate but is not automatically the mandatory acceptance approver.

20. **Project Closure is distinct from Project End Date and Funding Agreement Closeout.** Current target direction is automatic Project closure when all mandatory closure conditions are satisfied; Funding Agreement closeout is separate.

21. **Post-Closure activity does not reopen the Project.** Later dissemination, outputs, audit, reviews or impact relations may point to a Closed Project while financial attribution remains with the actual Funding Project / Budget.

22. **Accounting reconciliation preserves authoritative facts.** Imported 1C facts are not manually overwritten in ERP. Discrepancies create Reconciliation Exceptions and corrections occur in the authoritative accounting source.

23. **Controlled Exception Override is rule-specific.** There is no universal `Override Everything` permission.

24. **Specialized domain UX + shared infrastructure.** Travel, Services, Procurement, Reporting and other domains may use specialized interfaces while reusing shared platform capabilities.

25. **Workflow is controlled but configurable.** v1 does not require a general-purpose unrestricted workflow / low-code builder. Stable domain logic remains controlled; selected routes, thresholds, templates, mappings and rule parameters may be configurable.

26. **Scientific Reports / Research Outputs are structured where operationally valuable.** Official submitted versions become immutable; institutional repositories remain authoritative storage/publication locations where applicable.

27. **Target integration style:** controlled interfaces, API-first where available, with adapters/import/synchronization fallback where legacy systems cannot support the desired API contract. External systems do not directly update/delete ERP database tables.

28. **Project-centered, not Project-only.** Project is the principal operational context, but independent business objects retain their own identity and lifecycle.

29. **Project lifecycle, readiness and expenditure authorization are separate controls.** Project business lifecycle is derived from business facts; Setup readiness and Operational Authorization must not be collapsed into one status.

30. **External Project business activation is based on signed legal basis, not cash receipt.** A signed external Funding Agreement makes the Project business-active; delayed Funding is managed as a separate Funding / operational risk.

31. **Expenditure initiation requires explicit Operational Authorization.** Head of Post-Award performs a final explicit authorization after all Mandatory Setup Checks are complete. Normal authorization is blocked until those checks pass.

32. **Operational Authorization gates expenditure initiation, not planning.** Non-expenditure Setup work, including Research Needs and Procurement Planning, remains available before Operational Authorization.

33. **Budget authority may be partial.** Only approved allocations are spendable; unallocated Funding remains visible but unavailable for expenditure. Full allocation of the Agreement Amount is not required for `Setup Complete`.

34. **Funding recovery does not silently remove management restrictions.** Receipt of delayed Funding triggers notification / review for a restricted Project, but explicit restrictions remain until an authorized decision changes them.

35. **Procurement Plan approval is planning approval, not purchase authorization.** A formal Procurement Request remains required; planned requests may use a simplified route subject to automated current-Budget and restriction validation.

---

## Architecture Principles

- User Value First.
- Optimize Before Automating.
- Enter Once, Reuse Everywhere.
- Business Object First.
- Claim-specific authoritative source / System of Record.
- Structured Data Over Document-Only Data.
- Full History and Auditability.
- Current / Proposed / Effective separation.
- Explicit causal traceability.
- Stable internal identity + separate Business Numbers + separate External Identifiers.
- Contextual access and Least Privilege.
- Separation of Duties and no uncontrolled self-approval.
- Preserve historically relevant records **subject to applicable retention, privacy, legal and institutional requirements**; do not delete material history merely to simplify the current operational state.
- Configurable where variability is real; controlled where domain integrity matters.
- Do not invent business states for architectural symmetry.
- Do not confuse current operational representation with historical approved snapshots.
- Reduce parallel Excel / personal registers as a normal operating model.
- Reuse shared capabilities rather than duplicate mechanisms across domains.
- Maintain economic and implementation proportionality.
- Preserve uncertainty explicitly when business / institutional / technical evidence is insufficient.

---

## Material Requirements

- Unified Project / portfolio operational view according to permissions and context.
- Final Submitted Application and other material submitted / approved versions retained.
- Project Setup and structured Project Obligations.
- Funding schedules, tranches, multiple Funding Sources, matching/co-funding and non-cash contributions.
- Structured Budget, Budget Revision / Version history, reporting mappings, Commitments and availability controls.
- Structured Research Needs and Procurement planning.
- Request↔Case split/consolidation at Item / Quantity level.
- Procurement Method rules and controlled exceptions.
- Supplier Portal with scoped external access, supplier verification and proposal submission.
- Delivery, Acceptance and Delivery Exceptions.
- Common Payment architecture with authoritative 1C payment confirmation.
- Scientific and Financial Reporting.
- Approved Reporting Form / Mapping operational consumption through Reporting / My Reports: select form + scope + period → apply mapping → interactive result → drill/filter/recalculate/export / official output as applicable.
- Structured Research Output records linked to Project / Obligation / Report and institutional repository records where applicable.
- Audit entity with explicit and criteria-based scope; started criteria-based Audit retains its resolved population and scope history.
- Project Closure, Post-Closure traceability and Audit after closure without reopening the Project.
- Role + assignment + context + delegation authorization.
- Temporary scoped read-only External Auditor access.
- Search by structured metadata and identifiers in v1.
- Full Business History and Privileged Administration Log.
- Controlled integrations with queue/retry/error monitoring where appropriate.
- Test / Training environment and maintainability documentation.
- RU/EN UI target for v1; data model must not prevent multilingual official values including Kazakh where process requirements need them.
- Configuration interfaces for selected business rules, routing, thresholds, templates, reporting mappings and reference data without turning the ERP into a general-purpose low-code platform.

---

## Material Constraints

- 1C remains authoritative for Accounting Actuals, payment facts and authoritative accounting corrections.
- EDMS remains authoritative for official registration / approval / signed documents in applicable processes.
- Corporate HR is not replaced; only necessary Person / employment / payroll facts should be consumed where available and authorized.
- Corporate Identity Provider is the preferred target for internal authentication, subject to actual NU capability and institutional policy.
- Existing Research Repository / source-code repository should remain authoritative for supported artifacts rather than being duplicated in ERP.
- Initial architecture must remain proportionate to the current project funding envelope; avoid unnecessary commercial licensing, overengineering and duplicated enterprise capabilities.
- Migration away from EDMS in selected processes is evolutionary and subject to institutional / technical approval.
- Actual EDMS, 1C, SSO / IdP and repository technical capabilities are not yet verified.
- Exact retention, WORM, personal-data, accessibility and institutional security requirements require authoritative-source verification.
- Production deployment is expected to be University-controlled / on-premise or equivalent institutionally controlled infrastructure unless separately approved.

---

## Confirmed Assumptions

### Established / confirmed current assumptions

- KZT is the currently established base currency for Project Budget calculations.

### Current working targets / planning assumptions

- Web-based, desktop-first interaction is the current working target.
- Internal users are expected to require secure remote access, subject to institutional security policy.
- Tablet is expected to support most ordinary work; smartphone use is primarily targeted at lightweight actions, viewing and approvals rather than complex editing.
- Current Part 01 operating-volume figures are working planning estimates only, not verified institutional KPIs.
- Parts 04–05 are expected to formalize Data Domains, lineage, entities, cardinalities, constraints and financial logic from the reconciled Business / Process / System semantics; they must not invent independent semantics that contradict the reconciled Parts 00–03 state.

### PROVISIONAL IMPLEMENTATION ASSUMPTIONS

- **PostgreSQL + S3-compatible object storage** remain provisionally accepted implementation assumptions retained in the current architecture. They are not confirmed institutional facts and are not user-originated business decisions.
- **Modular Monolith** remains a provisionally accepted initial architecture-style assumption retained in the current architecture. It is not a confirmed institutional fact and must remain subject to later technical validation and implementation design.

---

## Rejected / Superseded Decisions

Only items worth retaining to prevent accidental reintroduction:

- PI / RA / Co-PI as independent Person entities — rejected; they are contextual Project Roles / Participations.
- Mechanical digitization of AS-IS Excel / email / paper processes — rejected.
- One universal process for all Project expenditures — rejected.
- Generic `My Tasks` as the primary operating model — rejected.
- One giant universal Expense Request form — rejected.
- Unrestricted visual Workflow Builder in v1 — rejected.
- Free Status dropdown, including unrestricted administrative status editing — rejected.
- Submitted Procurement Request ending at Procurement Case creation — superseded.
- `Rejected / Cancelled` added to the initial Procurement Plan lifecycle merely for workflow symmetry — rejected.
- PI as mandatory Goods Acceptance approver — superseded by the actual-receiver rule.
- Direct uncontrolled overwrite of approved/effective facts — rejected.
- Direct external-system writes to ERP database tables — rejected.
- Mandatory manual Head-of-Post-Award button for every normal Project Closure — superseded by closure based on mandatory conditions, subject to final cross-Part normalization.
- Treating all procurement fulfillment stages as one honest top-level Procurement Request status — rejected; detailed progress belongs primarily to underlying Items / Cases / downstream objects and may be aggregated for user presentation.
- `Pending Activation` as the Project lifecycle status for a signed external Project experiencing delayed Funding — superseded; the Project remains `Active` while Funding condition and Operational Restrictions are represented separately.
- `Ready for Administration` as a Project lifecycle status — superseded; use `Setup Complete` as a readiness outcome / concise system concept.
- Automatic Project expenditure authorization when Setup checks happen to become complete — rejected; explicit Head of Post-Award authorization is required.
- Automatic removal of Operational Restrictions when delayed Funding is received — rejected.
- Requirement to allocate the full Funding Agreement amount before `Setup Complete` — rejected.
- Treating Approved Procurement Plan as authorization to start procurement — rejected; a formal Procurement Request remains required.
- Blocking Research Needs / Procurement Planning until Operational Authorization — rejected; planning is allowed during `Setup`.

---

## Open Issues / Conflicts

These are intentionally not resolved in this memory.

### Architecture normalization required before Part 04

1. Complete Project lifecycle / readiness / Operational Authorization normalization across Parts 00–03.

   Established for external grants:
   - Project record may be created after Funding Decision before Funding Agreement;
   - before signed Funding Agreement: Project lifecycle = `Setup`;
   - signed Funding Agreement: Project lifecycle = `Active`;
   - Funding receipt/delay does not determine `Active` status;
   - `Setup Complete` is readiness, not lifecycle;
   - expenditure initiation requires explicit Head of Post-Award Operational Authorization;
   - normal authorization is blocked until all Mandatory Setup Checks are complete;
   - Operational Authorization may be restricted.

   Remaining:
   - finalize terminology for Operational Authorization / restricted operation and replacement of legacy `Pending Activation`;
   - define the precise restriction model and audit semantics;
   - verify/normalize lifecycle rules for internal grants and other Project types;
   - decide whether `Created` is a persistent business state or primarily a creation event / initial technical condition;
   - propagate the accepted semantics consistently through Parts 00–03.
2. Apply the corrected Application State Model and distinguish internal NURA review from external funder review; keep actions/events separate from persistent states.
3. Decide Research Need own lifecycle versus derived downstream Procurement progress.
4. Canonicalize Procurement Plan / Amendment / Version terminology across Parts.
5. Decide whether Procurement Procedure is a first-class Business Object or Method-specific execution within Procurement Case.
6. Propagate final Goods Acceptance rule consistently across all Parts.
7. Normalize Project Closure transition authority / automation across Parts.
8. Normalize Funding Agreement / Amendment state vocabulary across Process and System sections.

### Business clarification required

9. Can one Person hold multiple simultaneous Project Roles within the same Project, and if so how should role assignments be modeled?
10. Define the exact incompatible-role / Separation-of-Duties matrix.
11. Confirm whether one Project may have multiple independent Funding Agreements.
12. Define broader Agreement taxonomy beyond Funding Agreement where relevant (e.g. consortium / collaboration / research contract forms).
13. Confirm formal Process Owners / process accountability.
14. Confirm the exact Calendar Plan / Milestone / Deliverable business structure.

### Data / financial logic still to formalize

15. Finalize exact Commitment → Actual → Available Budget calculation and double-counting prevention. Established constraint: Unallocated Funding is not Available Budget and must not become spendable until it is allocated and approved.
16. Exact Research Need / Procurement downstream status ownership.
17. Final cardinalities and temporal constraints for unresolved relationships before Part 05.

### Institutional verification required

18. Applicable NURA / NU policy hierarchy, formal role names and internal regulations.
19. Retention periods, WORM / immutable record classes, personal-data requirements, accessibility obligations and institutional security requirements.
20. Institutional approval / exit criteria for moving selected workflows out of EDMS.
21. Refresh current project budget / scale assumptions if they become formal implementation constraints.

### Technical verification required

22. Actual EDMS API / integration capabilities.
23. Actual 1C interfaces, analytical granularity and outgoing/incoming data capabilities.
24. Actual NU SSO / Identity Provider protocol, JIT, claim and MFA/session feasibility.
25. External identity implementation approach.
26. Institutional Research Repository / source-code repository integration capabilities.
27. Final document-generation implementation engine.
28. Final MVP, implementation sequence, load targets and acceptance-level NFR values.

### Historical/source conflict retained for evidence

29. Procurement legacy numbering descriptions conflict across historical QA and require migration/source verification only if legacy mapping matters.
30. Historical operating-scale estimates differ across QA; current Part 01 values are working estimates, not authoritative KPIs.

---

## Current Solution State

### Part 00 — Scope & Architecture Principles

Substantial architecture baseline. Core scope, boundaries, principles and SoR model are usable. Contains several stale remnants / assertions that require controlled normalization before Part 04. In particular, Project creation / Setup / business-active / expenditure-authorization semantics must be synchronized with the accepted Engagement Memory correction.

### Part 01 — Business Analysis

Substantial business baseline covering context, stakeholders, business requirements, business rules and glossary. Current operating-scale values are planning estimates. Formal Process Ownership and some cardinalities remain unresolved.

### Part 02 — Process Architecture

Substantial expanded baseline covering Pre-Award, Agreement / Project Initiation, Funding, Budget, Project Change, Research Team, Procurement, Services, Reporting, Payment, Reconciliation, Closure and cross-functional controls. Several lifecycle/state semantics must be synchronized. PF-02 / Project initiation sequencing and the legacy `Pending Activation` treatment are stale against the accepted Project lifecycle / Operational Authorization semantics recorded in this memory.

### Part 03 — System Analysis

Advanced current system-behavior baseline covering Functional Requirements, Use Cases, System Context, State Models, Validation, Roles / Permissions, Integration Requirements and NFR. Most late validation corrections are incorporated. The Application State Model and several cross-Part terms still require normalization. The current Project State Model is stale where it treats `Ready for Administration` as a lifecycle status and does not cleanly separate business lifecycle, Setup readiness and expenditure Operational Authorization.

### Part 04 — Data Architecture

Not started.

### Part 05 — Data Model

Not started.

### Readiness

**Parts 00–03 require a controlled normalization pass before Part 04.** No redesign is implied; the objective is to eliminate known semantic contradictions before they become formal Data Domains, entities, states, relationships and constraints. Open Issue #1 is substantially clarified but not yet closed; Parts remain unchanged until its remaining terminology / restriction-model questions are resolved.

---

## Important Cross-Part Dependencies

Parts 04–05 must preserve and explicitly model:

- Application and Project independent identity/history;
- Award/Funding Decision → Project creation versus signed-Agreement business activation distinction;
- Funding Agreement / Amendment / Funding / Project / Budget independent lifecycles;
- Project business lifecycle versus Setup readiness versus Operational Authorization / restrictions;
- Current / Proposed / Effective semantics;
- decision/signature/registration dates versus `Effective From`;
- causal links between formal changes and downstream consequences;
- Budget Draft / Approval / partial Approved Allocations / Unallocated Amount / Budget Revision / Budget Version semantics;
- Funding versus Budget versus Commitments versus Operational Actual versus Accounting Actual;
- authoritative versus derived / operational financial facts;
- 1C Transaction → zero/one/many controlled ERP allocations without altering the source transaction;
- Person / User Account / Project Participation separation;
- unresolved same-Project multi-role cardinality;
- Procurement Request / Request Item / Case / Item Allocation structure;
- unresolved Procurement Procedure boundary;
- Research Need versus downstream derived progress, while preserving Research Need / Procurement Planning availability during Project `Setup`;
- Procurement Plan / Amendment / Version / Consolidated Current Plan;
- Supplier Contract / Shipment / Delivery / Acceptance / Payment distinctions;
- Business Change / Data Correction / Reconciliation Exception / Controlled Exception Override distinctions;
- Audit criteria, Period Type, resolved/frozen population and M:N relationships;
- stable technical IDs, immutable Business Numbers and multiple External Identifiers;
- Structured Data versus Documents / Files / Generated Approved Snapshots;
- Systems of Record, source IDs, provenance, synchronization metadata and lineage;
- history/version/audit requirements and temporal validity;
- retention and deletion constraints;
- role / assignment / scope / delegation relationships relevant to access control;
- effective rule / template / mapping versions used by historical transactions and reports.

Do not finalize a Part 05 cardinality for any relationship that remains listed as unresolved here.

---

## Local NURA ERP Lessons

- Existing NURA vocabulary and AS-IS artifacts are evidence, not automatically the target ontology.
- A useful target Business Object may need to be introduced even if it is not separately maintained today; Procurement Case is the clearest example.
- Generic ERP symmetry is dangerous: a state belongs in the model only when a real NURA business event / condition justifies it.
- Persistent side Excel / personal registers are treated as evidence of missing ERP functionality, not a desirable permanent operating model.
- Different roles require different depth of representation over the same underlying facts.
- Project is the principal operational context, but forcing all objects/lifecycles into Project destroys legal, financial and audit history.
- A unified operational view is compatible with claim-specific authoritative systems; ERP may display authoritative external facts while preserving provenance.
- Current operational data, immutable approved snapshots and generated official documents are different functions and should not be conflated.
- Before formalizing the Data Model, lifecycle/state/event/progress semantics must be validated against the real business process.
- User corrections to actual NURA work take precedence over generic architecture patterns when they are credible and consistent with governing constraints.
- For external grants, legal/business Project activity and permission to initiate expenditures are different facts: a signed Funding Agreement can make a Project active while expenditure initiation remains subject to explicit Operational Authorization.
- Planning approval is not expenditure authorization: Research Needs and Procurement Plan may be prepared/approved during Setup, while a formal Procurement Request remains the expenditure-initiation boundary.
- Funding delay is a separate operational/financial condition; it should not distort the Project lifecycle merely to make the problem visible.
