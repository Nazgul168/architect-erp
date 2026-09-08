# ENGAGEMENT_MEMORY.md

- **MEMORY_VERSION:** `1.2`
- **LAST_RECONCILED:** `2026-09-08`
- **SOURCE_PARTS_BASELINE:** Current Project Sources `Part 00 — Scope & Architecture Principles`, `Part 01 — Business Analysis`, `Part 02 — Process Architecture`, `Part 03 — System Analysis`, fully reviewed during Global Reconciliation on 2026-09-08.
- **BOOTSTRAP / RECONCILIATION reference:** QA Bootstrap Batches 1–8 + accepted Global Reconciliation, 2026-09-08.

## Engagement Identity / Status

- **Engagement:** NURA ERP Architecture
- **Engagement ID:** `ENG-NURA-ERP-001`
- **Status:** ACTIVE
- **Memory status:** UPDATED WORKING VERSION — OPEN ISSUE #1 PROJECT LIFECYCLE / SETUP / OPERATIONAL CONTROL RESOLVED; PART PROPAGATION PENDING
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

### Funding Decision, Authorizing Basis, Project Lifecycle and Operational Authorization

**Funding Decision ≠ Authorizing Basis ≠ Project.**

A Funding Decision / Award may justify creation of a Project record before the Project has the applicable official basis to operate. This allows Legal, Post-Award and PI to perform Project Setup and other preparatory work in one Project context.

Each Project Type must define its applicable **Authorizing Basis**. A Project becomes business-active when that valid official basis exists and is recorded in ERP. The Authorizing Basis is not necessarily a Funding Agreement and is not determined by actual cash receipt.

Established examples:

- external grant: Funding Decision recorded, but no signed + registered Funding Agreement recorded in ERP → Project lifecycle = `Setup`;
- external grant: signed + registered Funding Agreement recorded in ERP with its official registration details → Project lifecycle = `Active`;
- internal grant: Research Council Decision is the Authorizing Basis and is functionally equivalent, for Project activation semantics, to the registered external Funding Agreement → Project lifecycle = `Active`.

Other Project Types must use the applicable approved agreement, decision or other official basis; the exact `Project Type → Authorizing Basis` taxonomy remains to be completed with the broader Agreement taxonomy.

Actual Funding receipt is separate from Project lifecycle. A delayed or missing tranche does not make an otherwise authorized Project non-active.

`Project Created` is a creation event, not a persistent business lifecycle state. A newly created Project immediately has the lifecycle state implied by the recorded business facts: for example, `Setup` for an external Award awaiting its registered Agreement, or `Active` for an internal grant created from the Research Council Decision.

`Setup Complete` is a readiness outcome, not a Project lifecycle status. Normal expenditure authorization is blocked until all Mandatory Setup Checks are complete.

Operational permission to initiate expenditures is a separate management control. Head of Post-Award must explicitly grant **Operational Authorization** after the Mandatory Setup Checks are complete. Operational Authorization should remain conceptually separate from dynamic Operational Restrictions rather than using a combined lifecycle/status such as `Granted with Restrictions`.

If Agreement preparation for an external Award is formally discontinued before the Authorizing Basis exists, the Project becomes `Not Proceeded` rather than being deleted. `Not Proceeded` is inactive for normal work but supports controlled reopening of the same Project, with the same Project identity and history, when the same Award resumes. A genuinely new Funding Decision / Award creates a new Project.

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

For external grants, no Project expenditure or financial commitment may be initiated before the Funding Agreement is signed. In ERP, expenditure initiation is additionally gated by the Project having the applicable recorded Authorizing Basis and explicit Operational Authorization; for the normal external-grant case this means the signed + registered Funding Agreement is recorded in ERP.

Retroactive contractual `Effective From` does not by itself authorize NURA to incur Project expenditures before the actual legal/administrative activation basis exists. Scientific work may in practice begin earlier on available resources, but this does not create expenditure authority under the grant.

Imported Accounting Actuals / 1C facts that imply Project expenditure before the applicable external-grant authorization gate must be automatically identifiable for reconciliation / investigation. The authoritative 1C fact is preserved; ERP flags the business-control inconsistency rather than overwriting the accounting record.

### Budget Authorization, Allocation, Revision and Version

Budget may be prepared as Draft during Project Setup / readiness work before the applicable Authorizing Basis exists, where the Project Type and process allow such preparation. For the normal external-grant case this includes Budget preparation before the Funding Agreement is signed and registered.

Formal Budget Approval occurs only after the applicable Project Authorizing Basis has been recorded in ERP. For the normal external-grant case this means the signed + registered Funding Agreement is recorded; for an internal grant the Research Council Decision provides the applicable basis. The curating Post-Award Manager explicitly approves the Budget, and Budget Approval is a Mandatory Setup Check.

A Budget may be approved with only part of the total applicable Funding / authorized amount allocated to specific Budget Categories / Lines. The model must distinguish at least:

- total applicable Funding / authorized amount;
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
- Procurement Planning is permitted during Setup/readiness work before Operational Authorization, including an external Project in lifecycle `Setup` and an `Active` Project whose readiness is not yet complete.
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
- Controlled Exception Override permits an authorized deviation from an explicitly overrideable operational rule / restriction for one specific case without changing the underlying rule or Project-wide restriction.
- Hard Business Validation is distinct from an overrideable Operational Restriction. A case-specific exception must not bypass a rule classified as non-overrideable / hard validation.

### Business Object, Document and File

**Business Object ≠ Document ≠ File.**

Structured business facts are primary where search, control, automation, audit or reporting require them. Word/PDF/Excel may be official documents, generated representations, input/output formats or transitional interfaces, but should not become the sole operational source of structured facts.

### Audit / External Review

**Audit / External Review** is a separate Business Entity, not a Project status. It may have explicit object scope or criteria-based scope and may involve one or many Projects / Funding Agreements.

### Operational Restrictions, Suspension and Case-Specific Exceptions

Operational Restrictions are a separate dynamic management-control layer over an `Active` Project. They are universal and are not limited to Funding Delay. They may be introduced, changed or removed during the life of an Active Project for an applicable management reason.

A restriction may constrain, where relevant:

- expenditure / commitment type or category;
- amount;
- date / period;
- specific classes of expenditure initiation;
- another explicitly modeled operational scope.

Operational Restrictions govern **new expenditure initiatives and new obligations**. They do not automatically cancel, invalidate or stop performance of obligations that were already validly created before the restriction.

An expenditure initiative that already exists but has not yet reached the applicable obligation-forming event must be suspended when a new Project restriction prohibits it. For Procurement, the established example is: if the supplier contract has not yet been signed, the affected Procurement Request / execution path is suspended; a signed existing obligation continues through fulfillment, acceptance and payment. The equivalent obligation-forming point for other expenditure domains must be defined in the applicable domain process.

`Suspended Requests` / equivalent queues are system views over the underlying expenditure objects, not separate parallel registers. The source object retains the suspension state/reason, the causal link to the Project restriction, the date/time and relevant history. Post-Award, PI and responsible operational offices must be able to see affected suspended items according to their role/context.

Head of Post-Award has cross-project operational visibility over expenditure initiatives needed to administer Project restrictions and may grant a **case-specific exception** to one suspended initiative without removing the Project-wide restriction. The exception requires a mandatory `Reason`, does not require a separate approval, and must be fully audit-logged.

A case-specific exception applies only to the relevant overrideable Operational Restriction. It does not bypass Hard Business Validation.

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

30. **Project business activation is based on the applicable Authorizing Basis, not cash receipt.** Each Project Type has an applicable official activation basis. For the normal external-grant case, a signed + registered Funding Agreement recorded in ERP makes the Project business-active; for an internal grant, the Research Council Decision is the Authorizing Basis. Delayed Funding is managed separately.

31. **Expenditure initiation requires explicit Operational Authorization.** Head of Post-Award performs a final explicit authorization after all Mandatory Setup Checks are complete. Normal authorization is blocked until those checks pass.

32. **Operational Authorization gates expenditure initiation, not planning.** Non-expenditure Setup/readiness work, including Research Needs and Procurement Planning, remains available before Operational Authorization regardless of whether the Project lifecycle is still `Setup` or is already `Active` because its Authorizing Basis exists.

33. **Budget authority may be partial.** Only approved allocations are spendable; unallocated Funding remains visible but unavailable for expenditure. Full allocation of the Agreement Amount is not required for `Setup Complete`.

34. **Changed underlying conditions do not silently remove explicit management restrictions.** A relevant change, such as receipt of delayed Funding, may trigger notification / review, but an explicit Operational Restriction remains until an authorized management action changes or removes it.

35. **Procurement Plan approval is planning approval, not purchase authorization.** A formal Procurement Request remains required; planned requests may use a simplified route subject to automated current-Budget and restriction validation.

36. **Operational Restrictions are universal and dynamic.** They are not a special Funding Delay status and may be introduced, changed or removed throughout the life of an `Active` Project without changing the Project business lifecycle.

37. **Restrictions govern future commitment formation, not existing obligations.** An Operational Restriction blocks affected new expenditure initiatives / obligations. Obligations validly created before the restriction continue to execution, acceptance and payment unless another independent authoritative process changes them.

38. **Pre-obligation expenditure initiatives may be suspended by Project restriction.** Existing Requests / initiatives that have not yet reached their applicable obligation-forming event become `Suspended by Project Restriction` when the restriction applies. Suspension is represented on the source object and exposed through derived operational views, not a parallel register.

39. **Case-specific exception preserves the Project-wide restriction.** Head of Post-Award may resume one suspended expenditure initiative through an explicit rule-specific exception with mandatory Reason and audit trail, without an additional approval and without removing the underlying Project restriction. Hard Business Validations remain non-bypassable through this mechanism.

40. **Agreement-preparation timing uses controlled thresholds, not observed averages as rules.** The Agreement workflow should distinguish configurable `Target Duration` from `Critical Escalation Threshold`; exceeding the target notifies/reminds the responsible Legal user, while exceeding the critical threshold escalates to COO and Director. Actual average duration remains an analytical KPI.

41. **Legal records discontinuation; Legal does not originate the refusal decision.** Closing unsuccessful Agreement preparation requires a structured reason and the NURA refusal letter to the funder as mandatory evidence. No separate approval of Legal's recording action is required. Closure stops the Agreement-preparation timing/escalation path and notifies Post-Award, COO and Director.

42. **Unsuccessful pre-active Project history is retained and reopenable.** If the same Award resumes after `Not Proceeded`, the same Project is reopened with the same identity and prior Setup history. Setup information is not copied into a separate archive or deleted; archival presentation is a view/access state over retained history.

43. **`Project Created` is an event, not a lifecycle state.** A Project immediately receives the lifecycle state implied by its business facts and applicable Authorizing Basis.

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
- `Pending Activation` as a Project lifecycle status — superseded; Project business activity follows the applicable Authorizing Basis, while Setup readiness, Operational Authorization, Funding condition and Operational Restrictions are represented separately.
- `Ready for Administration` as a Project lifecycle status — superseded; use `Setup Complete` as a readiness outcome / concise system concept.
- Automatic Project expenditure authorization when Setup checks happen to become complete — rejected; explicit Head of Post-Award authorization is required.
- Automatic removal of Operational Restrictions when delayed Funding is received — rejected.
- Requirement to allocate the full Funding Agreement amount before `Setup Complete` — rejected.
- Treating Approved Procurement Plan as authorization to start procurement — rejected; a formal Procurement Request remains required.
- Blocking Research Needs / Procurement Planning until Operational Authorization — rejected; planning is allowed during `Setup`.
- `Signed Funding Agreement → Active` as a complete external-grant trigger — superseded by `signed + registered Funding Agreement recorded in ERP → Active`.
- `Created` as a persistent Project lifecycle status — rejected; Project creation is an event and the Project immediately takes the lifecycle state implied by business facts.
- `Activate with Restrictions` / `Granted with Restrictions` as the sole representation of restricted operation — superseded by separate Operational Authorization plus dynamic Operational Restrictions that may change throughout the Active Project lifecycle.
- Operational Restrictions automatically stopping obligations already validly created before the restriction — rejected; restrictions govern future obligation formation / affected new expenditure initiation.
- A separate manually maintained `Suspended Requests` register — rejected; suspension is stored on the source expenditure objects and exposed through system views.
- Requiring an additional approval for a Head-of-Post-Award case-specific restriction exception — rejected; mandatory Reason + audit trail are sufficient within the established role responsibility.
- Treating an overrideable Operational Restriction and a Hard Business Validation as the same control — rejected; case-specific exceptions cannot bypass hard validations.
- Deleting or copying unfinished Project Setup into a separate archive after Agreement preparation fails — rejected; retained Project history remains on the same Project, which becomes `Not Proceeded` and may be reopened for the same Award.

---

## Open Issues / Conflicts

Items below are either intentionally unresolved or explicitly marked as resolved but pending propagation to the architecture Parts.

### Architecture normalization required before Part 04

1. **RESOLVED — pending propagation to Parts 00–03:** Project lifecycle / Setup readiness / Operational Authorization / Operational Restriction semantics.

   Established target model:
   - each Project Type has an applicable `Authorizing Basis`;
   - `Project Created` is an event, not a persistent lifecycle status;
   - external Award may create the Project before the Authorizing Basis exists → `Setup`;
   - normal external-grant Authorizing Basis = signed + registered Funding Agreement recorded in ERP → `Active`;
   - internal-grant Authorizing Basis = Research Council Decision → `Active`;
   - other Project Types use their applicable approved agreement / decision / official basis; exact taxonomy is deferred to Agreement taxonomy normalization;
   - Funding receipt / delay does not determine `Active` status;
   - `Setup Complete` is readiness, not lifecycle;
   - normal Operational Authorization is blocked until all Mandatory Setup Checks are complete;
   - Head of Post-Award explicitly grants Operational Authorization;
   - Operational Restrictions are a separate universal dynamic control throughout Active Project life;
   - restrictions affect new obligations / expenditure initiatives, not already validly created obligations;
   - affected pre-obligation initiatives are suspended on the source object and surfaced through system views;
   - Head of Post-Award may grant a case-specific exception with mandatory Reason and audit trail, without a separate approval; hard validations remain non-bypassable;
   - unsuccessful Agreement preparation may move a pre-active Project to `Not Proceeded`; the same Project may be reopened if the same Award resumes;
   - Legal closure of unsuccessful Agreement preparation records the outcome with structured Reason + mandatory refusal letter evidence;
   - Agreement-preparation timing uses configurable Target and Critical escalation thresholds.

   Pending implementation only:
   - propagate the accepted semantics consistently through Parts 00–03;
   - select final UI labels where wording remains implementation-level rather than business-semantic;
   - complete the broader `Project Type → Authorizing Basis` mapping together with Open Issue #12 Agreement taxonomy.
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

Substantial architecture baseline. Core scope, boundaries, principles and SoR model are usable. Contains several stale remnants / assertions that require controlled normalization before Part 04. In particular, Project creation, Authorizing Basis, `Setup` / `Active`, `Not Proceeded`, Setup readiness, Operational Authorization and dynamic Operational Restriction semantics must be synchronized with the resolved Open Issue #1 model.

### Part 01 — Business Analysis

Substantial business baseline covering context, stakeholders, business requirements, business rules and glossary. Current operating-scale values are planning estimates. Formal Process Ownership and some cardinalities remain unresolved. Project Authorizing Basis, activation, Setup-readiness and expenditure-control business rules require propagation from resolved Open Issue #1.

### Part 02 — Process Architecture

Substantial expanded baseline covering Pre-Award, Agreement / Project Initiation, Funding, Budget, Project Change, Research Team, Procurement, Services, Reporting, Payment, Reconciliation, Closure and cross-functional controls. Several lifecycle/state semantics must be synchronized. PF-02 / Project initiation sequencing, the legacy `Pending Activation` treatment, Agreement-preparation closure/escalation behavior and restriction/suspension handling are stale against the resolved Open Issue #1 model recorded in this memory.

### Part 03 — System Analysis

Advanced current system-behavior baseline covering Functional Requirements, Use Cases, System Context, State Models, Validation, Roles / Permissions, Integration Requirements and NFR. Most late validation corrections are incorporated. The Application State Model and several cross-Part terms still require normalization. The current Project State Model is stale where it treats `Ready for Administration` as a lifecycle status and does not model the resolved separation among Authorizing Basis-driven lifecycle, Setup readiness, Operational Authorization, dynamic Operational Restrictions, suspension and case-specific exceptions.

### Part 04 — Data Architecture

Not started.

### Part 05 — Data Model

Not started.

### Readiness

**Parts 00–03 require a controlled normalization pass before Part 04.** No redesign is implied; the objective is to eliminate known semantic contradictions before they become formal Data Domains, entities, states, relationships and constraints. Open Issue #1 is resolved at the architecture-decision level and is now **pending propagation to Parts 00–03**. Parts remain intentionally unchanged at this checkpoint; other related normalization issues, including Open Issue #7 Project Closure, remain separate.

---

## Important Cross-Part Dependencies

Parts 04–05 must preserve and explicitly model:

- Application and Project independent identity/history;
- Funding Decision / Award → Project creation versus Project-Type-specific `Authorizing Basis` → business `Active` distinction;
- Funding Agreement / Amendment / Funding / Project / Budget independent lifecycles;
- Project business lifecycle versus Setup readiness versus Operational Authorization versus dynamic Operational Restrictions;
- `Project Created` as event, `Not Proceeded` pre-active outcome and controlled reopening of the same Project for the same Award;
- external-grant `signed + registered Agreement recorded in ERP` activation trigger versus retroactive `Effective From`;
- Operational Restriction scope/effective history, affected expenditure-object suspension, causal link to restriction, case-specific exception, mandatory Reason and audit trail;
- suspension as source-object state / progress with derived views rather than a separate register;
- Hard Business Validation versus overrideable Operational Restriction;
- Agreement-preparation Target / Critical escalation thresholds, closure reason and refusal-letter evidence;
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
- Research Need versus downstream derived progress, while preserving Research Need / Procurement Planning availability during Setup/readiness work before Operational Authorization;
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
- Project business activity and permission to initiate expenditures are different facts: the applicable Authorizing Basis makes the Project `Active`, while expenditure initiation remains subject to Setup readiness and explicit Operational Authorization.
- Planning approval is not expenditure authorization: Research Needs and Procurement Plan may be prepared/approved during Setup/readiness work before Operational Authorization, while a formal Procurement Request remains the expenditure-initiation boundary.
- Funding delay is a separate operational/financial condition; it should not distort the Project lifecycle merely to make the problem visible.
- For external grants, practical NURA lifecycle activation should wait for the signed + registered Agreement to be recorded with official registration details rather than introducing unnecessary transient states for a short signature-to-registration interval.
- Operational restrictions are management controls over future commitment formation, not a substitute Project lifecycle and not an automatic cancellation of existing obligations.
- In NURA's small-organization operating model, ERP should provide Head of Post-Award the functional control needed to administer restrictions/exceptions and rely on explicit Reason + audit trail rather than add approval layers whose only purpose is to police managerial good faith. Hard business validations remain a separate non-bypassable boundary.
- An archive view should not become a second data store: discontinued pre-active Projects retain their original Setup history and can be reopened when the same Award resumes.
- Process SLA thresholds and escalation limits are governed control parameters; observed average duration is an analytical KPI and should not itself become the process rule.
