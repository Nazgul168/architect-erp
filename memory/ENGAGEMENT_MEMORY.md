# ENGAGEMENT_MEMORY.md

- **MEMORY_VERSION:** `1.5`
- **LAST_RECONCILED:** `2026-09-10`
- **SOURCE_PARTS_BASELINE:** Current Project Sources `Part 00 — Scope & Architecture Principles` and `Part 01 — Business Analysis` have been rewritten and semantically synchronized against this Engagement state as of 2026-09-10. `Part 02 — Process Architecture` and `Part 03 — System Analysis` remain the pre-rewrite baselines pending controlled rewrite/synchronization.
- **BOOTSTRAP / RECONCILIATION reference:** QA Bootstrap Batches 1–8 + accepted Global Reconciliation, 2026-09-08.

## Engagement Identity / Status

- **Engagement:** NURA ERP Architecture
- **Engagement ID:** `ENG-NURA-ERP-001`
- **Status:** ACTIVE
- **Memory status:** CONSOLIDATED WORKING VERSION — ISSUES #1, #2, #3/#16, #4, #5, #6, #7, #8, #11/#12 RESOLVED AT ARCHITECTURE-DECISION LEVEL; PARTS 00–01 REWRITTEN / SEMANTICALLY SYNCHRONIZED; PARTS 02–03 CONTROLLED REWRITE / SYNCHRONIZATION PENDING
- **Current architecture state:** Part 00 and Part 01 have been rewritten and passed semantic consistency review against the accepted Engagement architecture state. Part 02 and Part 03 remain materially stale against accepted post-v1.2/post-v1.3 decisions and are pending controlled rewrite/synchronization. This v1.5 incorporates the two accepted post-v1.4 refinements recorded in Decisions 66–67 below. Transition readiness remains governed by `ENGAGEMENT_CONTROL.md`. The master architecture structure includes future Part 07 — Solution Architecture and renumbers Enterprise Architecture to Part 08.
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

Core lifecycle / route model:

NURA ERP does **not** assume one universal upstream sequence. The applicable route depends on the business scenario. Established route families include internal grants, external grant-funded research, Research Contracts, and consortium / collaboration arrangements. Depending on the route, upstream steps may include Funding Opportunity / Call, Application / Proposal / Bid, external or internal evaluation, Funding Decision, Agreement / Contract preparation, and one or more authorizing instruments.

Once a Project exists, ERP manages the applicable Project Setup / administration, satisfaction of the `Authorizing Basis Requirement`, Budget, Project Execution / Procurement / Services, Payment, Reporting and Project Closure according to the relevant rules.

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

Application preserves its own lifecycle, identifiers, Final Submitted Version, outcome, and links/history for the applicable Pre-Award Application Check, external submission and scientific / external evaluation. An Awarded / Approved Application can provide source data for Project creation without re-entry, but the Project is a separate Business Object with its own lifecycle and administration.

### Application, Pre-Award Application Check, External Evaluation and Handover

Application lifecycle is separate from Pre-Award administrative support/check, external submission, scientific evaluation, Funding Decision and downstream handover.

Pre-Award Application Check is an administrative/technical support process and must not be named or modeled as scientific Review. For external state-funded applications it is available and recommended but is not a universal submission gate. For internal programmes it may be mandatory where Programme Rules require it.

External scientific / peer evaluation is a separate external process. ERP stores available evaluation evidence/results without pretending that NURA controls the external review lifecycle.

Pre-Award Complete is a handover/readiness outcome. After a successful Funding Decision, Pre-Award must assemble the applicable Award / Handover Package and transfer it to the relevant downstream roles.

Work Assignment / Responsibility History must preserve which employee/unit held an object, when responsibility started/ended, and applicable waiting periods. Elapsed responsibility time must not be misrepresented as actual labor hours.

### Person, User and Project Participation

**Person ≠ User Account ≠ Project Participation.**

PI, Co-PI, RA, Researcher and similar labels are contextual Project Roles / Participations, not separate Person entities. Employment Contract / Service Agreement is separate from Project Participation.

### Funding Decision, Authorizing Basis Requirement, Project Lifecycle and Operational Authorization

**Funding Decision, Authorizing Basis Requirement / authorizing instruments, and Project are distinct conceptual roles / objects; they are not required to be represented by different real-world documents.** One official instrument may perform more than one role. For example, an internal Research Council Decision may both record the funding decision and satisfy the Project's Authorizing Basis Requirement.

A Funding Decision / Award may justify creation of a Project record before the Project's applicable **Authorizing Basis Requirement** is satisfied. This allows Legal, Post-Award and PI to perform Project Setup and other preparatory work in one Project context.

Each Project Type / Scenario must define its applicable **Authorizing Basis Requirement**. A Project becomes business-active when that requirement is satisfied by the required valid official instrument or combination of instruments and the relevant facts are recorded in ERP. Satisfaction is not necessarily based on a Funding Agreement and is not determined by actual cash receipt.

Established examples:

- external grant: Funding Decision recorded, but the required signed + registered Funding Agreement is not yet recorded in ERP → Project lifecycle = `Setup`;
- external grant: signed + registered Funding Agreement recorded in ERP with its official registration details → the applicable Authorizing Basis Requirement is satisfied → Project lifecycle = `Active`;
- internal grant: Research Council Decision serves as the required authorizing instrument and satisfies the applicable Authorizing Basis Requirement → Project lifecycle = `Active`.

Other Project Types / Scenarios use the applicable approved agreement(s), decision(s) or other official instrument(s). The exact configurable `Project Type / Scenario → Authorizing Basis Requirement` mapping remains to be formalized during rule / data design and is tracked separately as a deferred modeling/configuration item. This does not reopen the resolved architectural concept or Agreement taxonomy decision.

Actual Funding receipt is separate from Project lifecycle. A delayed or missing tranche does not make an otherwise authorized Project non-active.

`Project Created` is a creation event, not a persistent business lifecycle state. A newly created Project immediately has the lifecycle state implied by the recorded business facts: for example, `Setup` for an external Award awaiting its registered Agreement, or `Active` for an internal grant created from the Research Council Decision.

`Setup Complete` is a readiness outcome, not a Project lifecycle status. Normal expenditure authorization is blocked until all Mandatory Setup Checks are complete.

Operational permission to initiate expenditures is a separate management control. Head of Post-Award must explicitly grant **Operational Authorization** after the Mandatory Setup Checks are complete. Operational Authorization should remain conceptually separate from dynamic Operational Restrictions rather than using a combined lifecycle/status such as `Granted with Restrictions`.

If Agreement preparation for an external Award is formally discontinued before the Authorizing Basis Requirement is satisfied, the Project becomes `Not Proceeded` rather than being deleted. `Not Proceeded` is inactive for normal work but supports controlled reopening of the same Project, with the same Project identity and history, when the same Award resumes. A genuinely new Funding Decision / Award creates a new Project.

### Agreements / Contracts and Authorizing Basis Requirements

Agreement / Contract Type classifies the legal document. Purpose, conditional effect, obligations, Post-Award relevance and authorizing effect are separate structured dimensions.

Standard Agreement Types use configured profiles/defaults. Variable Agreement Types use controlled selections rather than repeated free-text entry.

Authorizing Basis Requirement is a Project-level rule defining which official instruments are required for the relevant Project Type / Scenario. The requirement may be composite. Individual decisions, agreements or other official instruments may satisfy the requirement fully or partially.

Post-Award Handover Required, Authorizing Basis Requirement Satisfied and Operational Authorization Granted are separate controls.

### Funding Agreement Amendment

**Funding Agreement Amendment** is a separate Business Entity related `1:N` to Funding Agreement. It has its own lifecycle, legal dates, proposed/effective terms, history and causal consequences.

### Agreement Processing, Legal Effect, Termination and Administrative Closeout

Agreement / Amendment preparation is not one universal linear lifecycle. The system must support meaningful work/action history including `Draft Preparation`, `Internal Coordination`, `EDMS Coordination / Approval / NURA Signature` and applicable Counterparty exchange / coordination evidence.

The order may vary by funder / legal case and may repeat. `Counterparty Coordination` is not a mandatory system lifecycle state where ERP cannot reliably observe the external/manual activity. Counterparty changes may require a new EDMS document version and repetition of formal coordination/signature steps.

Agreement registration facts include the NURA registration number/date and may include separate funder/partner number/date. Independent identifiers and dates must remain separate structured facts. These official identifiers may be displayed together after registration, but they are not assumed to exist when the draft Agreement is first generated.

Amendment follows the same general preparation model and remains linked to its parent Agreement; in EDMS it may be initiated from that Agreement rather than created as an unrelated new document.

Preparation that is permanently discontinued before conclusion records the Agreement preparation outcome as `Not Concluded`. Where applicable, the linked pre-active Project follows the established `Not Proceeded` rule.

Legal effect is separate from preparation workflow. `Effective` condition is derived from applicable legal/document facts and terms rather than maintained as a generic manual processing status.

Agreement administrative closeout is separate from Project Closure. Target administrative states are:

`Open → Pending Closeout → Closed`.

Agreement Closeout is confirmed by **Head of Post-Award + Legal** using the applicable obligation checklist, with completion evidence determined automatically or manually as appropriate.

An open related Project does not automatically block Agreement Closure. An unresolved Agreement obligation or consequence remains closure-blocking where it can still produce a penalty, refund, claim, dispute or other contractual consequence. The same underlying obligation may therefore be non-blocking for Project Closure while remaining Agreement-Closure-Blocking.

Early Termination / Early Cessation is a formal event with its own reason/basis, initiator, effective date, supporting/authorizing documents and consequences. Reason/basis and consequences must be stored separately. Early termination of legal effect does not itself mean Agreement `Closed`; the Agreement remains `Pending Closeout` until applicable contractual, financial, reporting, dispute and settlement obligations are resolved.

For internal grants where no Agreement exists, early cessation is a Project event and may be supported by the applicable Research Council Decision or other required authorizing evidence.

### Funding, Budget and Accounting

**Funding ≠ Budget ≠ Commitment ≠ Operational Actual ≠ Accounting Actual.**

- Funding describes contracted / planned / received / recognized contributions and schedules.
- Budget describes approved allocation authority and its governed revisions / versions.
- Commitment / Encumbrance reserves future financial obligation.
- Operational Actual is an operational fact used for current administration.
- Accounting Actual is the authoritative accounting fact from 1C.

### External Project Spending Gate

For external grants, no Project expenditure or financial commitment may be initiated before the Funding Agreement is signed. In ERP, expenditure initiation is additionally gated by the applicable Authorizing Basis Requirement being satisfied and explicit Operational Authorization; for the normal external-grant case this means the signed + registered Funding Agreement is recorded in ERP.

Retroactive contractual `Effective From` does not by itself authorize NURA to incur Project expenditures before the actual legal/administrative activation basis exists. Scientific work may in practice begin earlier on available resources, but this does not create expenditure authority under the grant.

Imported Accounting Actuals / 1C facts that imply Project expenditure before the applicable external-grant authorization gate must be automatically identifiable for reconciliation / investigation. The authoritative 1C fact is preserved; ERP flags the business-control inconsistency rather than overwriting the accounting record.

### Budget Authorization, Allocation, Revision and Version

Budget may be prepared as Draft during Project Setup / readiness work before the applicable Authorizing Basis Requirement is satisfied, where the Project Type and process allow such preparation. For the normal external-grant case this includes Budget preparation before the Funding Agreement is signed and registered.

Formal Budget Approval occurs only after the applicable Project Authorizing Basis Requirement is satisfied and the relevant authorizing instrument(s) are recorded in ERP. For the normal external-grant case this means the signed + registered Funding Agreement is recorded; for an internal grant the Research Council Decision satisfies the applicable requirement. The curating Post-Award Manager explicitly approves the Budget, and Budget Approval is a Mandatory Setup Check.

A Budget may be approved with only part of the total applicable Funding / authorized amount allocated to specific Budget Categories / Lines. The model must distinguish at least:

- total applicable Funding / authorized amount;
- Approved Budget Allocations;
- Unallocated Amount;
- Available Budget within approved allocations.

Unallocated Amount is visible to PI and Post-Award but is not spendable until allocated to an applicable Budget Category / Line and approved. Full allocation of the total Funding Agreement amount is not required for `Setup Complete`.

**Budget Revision** is a controlled proposed change to an existing approved Budget. Any change to an already Approved Budget requires the applicable Budget Revision / Approval process before changed amounts become effective.

**Budget Version** is an immutable approved/effective or historical state produced by the governed Budget lifecycle.

One underlying structured Project Budget may support multiple controlled reporting / management views through versioned mappings.

### Expense Purpose versus Financial Attribution

A later expenditure may be related to an obligation/output of one Project while being funded from a different authorized Funding Source / Funding Code / Budget.

Related Project / Obligation identifies business purpose and traceability.  
Funding Source / Funding Code / Budget identifies actual financial attribution.

Use of NURA Own Funds or another alternative source requires the applicable Funding Authorization.

### Research Need

**Research Need** is a PI-oriented structured statement of a planned material procurement need and planning input.

Research Need has its own lifecycle and must not use downstream Procurement execution stages as its lifecycle states. `Procurement Request Created`, `Procurement Case`, `Supplier Selected`, `Contract Signed`, `Delivered`, `Accepted` and `Paid` are downstream progress facts derived through related objects.

One Research Need may be satisfied through multiple downstream Procurement Requests / Item Allocations. For quantity-based material needs, ERP should derive progress using applicable quantities such as `Need Quantity`, `Requested Quantity`, `Contracted Quantity`, `Delivered Quantity`, `Accepted Quantity` and `Remaining Need Quantity`. Fulfilment is based on satisfaction of the need, normally sufficient Accepted Quantity, rather than Payment.

Research Need may be revised or cancelled with history preserved. If downstream Procurement already exists, the change must use the applicable downstream change / withdrawal process rather than silently rewriting existing Procurement facts.

After Supplier Contract signature, PI may still request a material change or withdrawal, but it requires a **Formal Request to Procurement**. Procurement Office may approve or reject it based on supplier agreement, amendment/termination feasibility, penalties/cost and other contractual consequences. Contract signature is therefore not an absolute prohibition on change; it is the boundary after which change becomes a controlled downstream obligation-change process.

Exact final Research Need lifecycle labels and unresolved reverse cardinalities are deferred to Part 05 / Issue #17 and do not reopen the resolved architectural concept.

### Procurement Plan

Procurement Plan is primarily a planning and operational monitoring instrument, not transaction authorization.

The model distinguishes:

- **Procurement Plan** — persistent logical planning context;
- **Effective Procurement Plan** — latest current structured operational truth;
- **Approved Procurement Plan Version** — immutable formally approved snapshot;
- **Procurement Plan Amendment** — formal delta document/package submitted for periodic approval;
- **Consolidated Approved Procurement Plan** — consolidated representation of the latest formally approved state, generatable as Word/PDF where required.

Effective Procurement Plan may be newer than the latest Approved Procurement Plan Version because accepted operational additions/changes may occur between formal Directorate approvals.

After a Research Need has passed the required Post-Award and Procurement approvals, its applicable Plan Item is reflected automatically in the Effective Procurement Plan. No additional `Approve inclusion into Effective Plan` action is required.

Operational changes do not create a new physical Procurement Plan Version after every edit. Formal immutable Versions are created only through the applicable formal approval process. `Approved` and `Effective` are separate semantics.

Procurement Planning is permitted during Setup/readiness work before Operational Authorization, including an external Project in lifecycle `Setup` and an `Active` Project whose readiness is not yet complete. Research Needs and Procurement Plan represent planning / forecast information and do not by themselves authorize expenditure or create a procurement commitment.

A formal Procurement Request remains required to initiate procurement. For a normal Procurement Request, the corresponding Research Need must be reflected in the current Procurement Plan. An urgent procurement may follow a separate out-of-plan route only where an established justification exists and the required special approval is completed. Inclusion of a Research Need in the Procurement Plan does not by itself authorize expenditure. Where a Procurement Request is created from an applicable approved/planned Item, it may bypass repeat manual Post-Award review only where the established rules allow and after automatic validation against the current approved Budget, applicable limits, existing Commitments and Operational Restrictions.

### Procurement Request and Procurement Case

**Procurement Request ≠ Procurement Case.**

- Procurement Request represents what the Project / Research Team requested and remains active until all Request Items reach a valid final outcome.
- Procurement Case represents the Procurement Office execution / sourcing / consolidation context. It is not synonymous with an Announcement.

Request↔Case relationships must be stored at Item / Quantity allocation level and support both split and consolidation. ERP may identify and propose consolidation candidates across Requests / Projects, but Procurement makes the final consolidation decision.

Announcement, sourcing round or other market-facing activity is an activity or artifact within the applicable Case / Method.

**Procurement Procedure is not modeled as a separate first-class Business Object.** Procurement Method and applicable configurable rules determine Case execution.

A failed/non-resulting attempt for an Item preserves its outcome in the original Case. Remaining need may subsequently be allocated to another Procurement Case.

The architecture must not force one Procurement Case to exactly one Supplier Contract. A Case may result in zero, one or multiple Supplier Contracts depending on Lots, Winners, Method and outcome. Exact logical cardinalities remain subject to Part 05 / Issue #17.

Detailed heterogeneous progress belongs primarily to Case Items / Lots / Allocations and downstream objects. Case-level progress/state should be coarse or derived where Items are at different execution stages.

### Delivery and Acceptance

**Delivery ≠ Acceptance.**

Delivered Quantity and Accepted Quantity are separate facts. Acceptance is recorded at **Delivery Item / Quantity** level. One Delivery may contain Items for multiple Projects and may be accepted by multiple actual receivers.

Applicable receivers may include PI, Project Administrator, Procurement staff and an RA explicitly designated by the PI as a procurement assistant / receiver, together with other roles where later rules permit. The system should normally route users to the Items relevant to their Project / assignment while preserving who actually confirmed receipt.

Aggregate Delivery outcomes such as `Accepted / Partially Accepted / Rejected` should be derived from underlying item/quantity acceptance facts where possible rather than maintained as an independent manual truth. Where useful, distinguish `Remaining to Deliver` from `Delivered but Not Yet Accepted`.

Where applicable, standard Supplier Contract terms should require **Advance Delivery Notice** identifying the relevant Contract, goods / Contract Lines, quantities and expected delivery date/time, together with applicable shipment/delivery references. ERP should use this information to identify affected Projects and notify relevant potential receivers.

Lack of advance notification must not prevent registration of an actual Delivery. The system must support fallback operational handling when Supplier provides only a Contract reference or otherwise insufficient advance detail.

Unresolved rejected/non-conforming quantities may create Delivery Exceptions and may affect Payment / closure according to the applicable rules.

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

### Project Closure, Closure-Blocking Obligations and Post-Closure Obligations

Project End Date is not itself Closed status. Factual early completion of works does not by itself shorten the official Project Period or permit early `Closed`. Closure becomes applicable when the effective Project End Date is reached, when an approved change makes an earlier End Date effective, or after a formal Termination. Reaching the effective End Date normally moves an Active Project to `Pending Closure` unless all applicable Closure-Blocking Conditions are already satisfied, in which case ERP may close the Project automatically at that point. If a Project in `Pending Closure` receives an effective extension of its official Project Period, ERP returns it to `Active` automatically.

Only obligations classified by applicable rules as Closure-Blocking prevent administrative closure. Long-duration Post-Closure Obligations may remain active after the Project becomes Closed.

Termination is a formal early-cessation event/reason, not an alternative final state to Closed.

A correctly Closed Project remains Closed for later Audit, Review, Correspondence, Corrective Action or other Post-Closure Activity; such normal post-closure activity does not itself reopen the Project. A closure proven erroneous may be reopened by Head of Post-Award through a controlled Reopen Project action with mandatory Reason. ERP derives the correct resulting state from current authoritative facts: normally `Pending Closure` if the official End Date has already passed, or `Active` if an effective official extension means the Project Period is still running.

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

### Configurable Business Policy / Rule Framework

Variable institutional/domain policy must be represented through controlled, versioned rule families with explicit applicability, conditions, outcomes, effective dates, authority/source, explanation and override semantics.

Stable fundamental invariants may remain Hard Business Validations. Configurability must not become an unrestricted general-purpose low-code/rules platform.

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

12. **Responsibility / processing duration ≠ waiting time ≠ labor effort.** Process analytics should distinguish time an object is held in an internal responsibility / processing stage from time spent waiting on another party or external system, and attribute elapsed time to the relevant party/stage. These elapsed durations must not be represented as actual employee labor hours unless effort is captured separately.

13. **One underlying Project Budget, multiple controlled views.** External and internal reporting forms use mappings/views rather than independent copies of the Budget.

14. **Project Change Management.** Significant changes after activation use controlled requests, Current/Proposed comparison, approval route, evidence, decision and Effective From.

15. **Funding Agreement Amendment is first-class.** An Effective Amendment may trigger Funding Update, Budget Revision, Project Change or other domain processes through explicit causal links.

16. **Funding, Budget and Accounting remain separate layers.** Contracted / planned / received Funding, Budget, Commitments, Operational Actuals, Accounting Actuals and Available Budget must not collapse into one amount.

17. **Procurement Request continues after Case formation.** Request remains active until all Items reach final outcomes. Detailed progress is derived primarily from Request Items / Allocations / Cases / Contracts / Deliveries / Acceptance / Payments.

18. **Procurement split/consolidation preserves source allocation.** Multi-project / multi-request procurement must preserve Project, source Request/Line, quantity, amount, Budget Line and Funding Source and prevent double allocation.

19. **Goods Acceptance is confirmed by the actual receiver.** PI may participate but is not automatically the mandatory acceptance approver.

20. **Project Closure is distinct from Project End Date and Funding Agreement Closeout.** Factual early completion does not itself close the Project. Once Closure is applicable because the effective Project End Date has been reached, an approved earlier End Date has become effective, or a formal Termination has occurred, Project closure is automatic when all applicable Closure-Blocking Conditions are satisfied; Funding Agreement closeout is separate.

21. **Normal Post-Closure activity does not itself reopen a correctly Closed Project.** Later dissemination, outputs, audit, reviews or impact relations may point to a Closed Project while financial attribution remains with the actual authorized Funding Source / Funding Code / Budget. Controlled Reopen is reserved for correction of an erroneous Closure under Decision 48.

22. **Accounting reconciliation preserves authoritative facts.** Imported 1C facts are not manually overwritten in ERP. Discrepancies create Reconciliation Exceptions and corrections occur in the authoritative accounting source.

23. **Controlled Exception Override is rule-specific.** There is no universal `Override Everything` permission.

24. **Specialized domain UX + shared infrastructure.** Travel, Services, Procurement, Reporting and other domains may use specialized interfaces while reusing shared platform capabilities.

25. **Workflow is controlled but configurable.** v1 does not require a general-purpose unrestricted workflow / low-code builder. Stable domain logic remains controlled; selected routes, thresholds, templates, mappings and rule parameters may be configurable.

26. **Scientific Reports / Research Outputs are structured where operationally valuable.** Official submitted versions become immutable; institutional repositories remain authoritative storage/publication locations where applicable.

27. **Target integration style:** controlled interfaces, API-first where available, with adapters/import/synchronization fallback where legacy systems cannot support the desired API contract. External systems do not directly update/delete ERP database tables.

28. **Project-centered, not Project-only.** Project is the principal operational context, but independent business objects retain their own identity and lifecycle.

29. **Project lifecycle, readiness and expenditure authorization are separate controls.** Project business lifecycle is derived from business facts; Setup readiness and Operational Authorization must not be collapsed into one status.

30. **Project business activation is based on satisfaction of the applicable Authorizing Basis Requirement, not cash receipt.** Each Project Type / Scenario has an applicable authorization requirement that may be satisfied by one or more official instruments. For the normal external-grant case, a signed + registered Funding Agreement recorded in ERP satisfies the requirement and makes the Project business-active; for an internal grant, the Research Council Decision satisfies the requirement. Delayed Funding is managed separately.

31. **Expenditure initiation requires explicit Operational Authorization.** Head of Post-Award performs a final explicit authorization after all Mandatory Setup Checks are complete. Normal authorization is blocked until those checks pass.

32. **Operational Authorization gates expenditure initiation, not planning.** Non-expenditure Setup/readiness work, including Research Needs and Procurement Planning, remains available before Operational Authorization regardless of whether the Project lifecycle is still `Setup` or is already `Active` because its Authorizing Basis Requirement is satisfied.

33. **Budget authority may be partial.** Only approved allocations are spendable; unallocated Funding remains visible but unavailable for expenditure. Full allocation of the Agreement Amount is not required for `Setup Complete`.

34. **Changed underlying conditions do not silently remove explicit management restrictions.** A relevant change, such as receipt of delayed Funding, may trigger notification / review, but an explicit Operational Restriction remains until an authorized management action changes or removes it.

35. **Procurement Plan approval is planning approval, not purchase authorization.** A formal Procurement Request remains required; planned requests may use a simplified route subject to automated current-Budget and restriction validation.

36. **Operational Restrictions are universal and dynamic.** They are not a special Funding Delay status and may be introduced, changed or removed throughout the life of an `Active` Project without changing the Project business lifecycle.

37. **Restrictions govern future commitment formation, not existing obligations.** An Operational Restriction blocks affected new expenditure initiatives / obligations. Obligations validly created before the restriction continue to execution, acceptance and payment unless another independent authoritative process changes them.

38. **Pre-obligation expenditure initiatives may be suspended by Project restriction.** Existing Requests / initiatives that have not yet reached their applicable obligation-forming event become `Suspended by Project Restriction` when the restriction applies. Suspension is represented on the source object and exposed through derived operational views, not a parallel register.

39. **Case-specific exception preserves the Project-wide restriction.** Head of Post-Award may resume one suspended expenditure initiative through an explicit rule-specific exception with mandatory Reason and audit trail, without an additional approval and without removing the underlying Project restriction. Hard Business Validations remain non-bypassable through this mechanism.

40. **Agreement-preparation timing uses controlled thresholds, not observed averages as rules.** The Agreement workflow should distinguish configurable `Target Duration` from `Critical Escalation Threshold`; exceeding the target notifies/reminds the responsible Legal user, while exceeding the critical threshold escalates to COO and Director. Actual average duration remains an analytical KPI.

41. **Legal records discontinuation; Legal does not originate the refusal decision.** Closing unsuccessful Agreement preparation requires a structured reason and supporting evidence/documents. No separate approval of Legal's recording action is required. Closure stops the Agreement-preparation timing/escalation path and notifies Post-Award, COO and Director. The earlier requirement that a NURA refusal letter to the funder be mandatory evidence is superseded by Decision 67.

42. **Unsuccessful pre-active Project history is retained and reopenable.** If the same Award resumes after `Not Proceeded`, the same Project is reopened with the same identity and prior Setup history. Setup information is not copied into a separate archive or deleted; archival presentation is a view/access state over retained history.

43. **`Project Created` is an event, not a lifecycle state.** A Project immediately receives the lifecycle state implied by its business facts and whether the applicable Authorizing Basis Requirement is satisfied.

44. **Project End Date, Pending Closure and Closed are distinct semantics.** `Period Ended` is a derived fact, not a persistent lifecycle state. Factual early completion of works does not change the lifecycle by itself; without an effective End-Date change or formal Termination, the Project remains `Active` until its official End Date.

45. **Closure eligibility is rule-driven.** Only Closure-Blocking Conditions prevent `Closed`; long-term Post-Closure Obligations may outlive Project closure.

46. **Business purpose and financial attribution are independent.** A post-period expense may remain related to the original Project / Obligation while using another authorized Funding Source / Funding Code.

47. **Termination is a causal early-cessation event followed by Closure, not a terminal alternative to `Closed`.**

48. **Correctly Closed Projects do not reopen for Audit / Post-Closure activity; erroneous Closure may be corrected through Head-of-Post-Award Reopen with mandatory Reason and preserved history.**

49. **Application lifecycle is separate from Pre-Award administrative checking/support, external submission, scientific evaluation and Award handover.**

50. **Object responsibility duration is a first-class process-analytics fact.** Responsibility time and waiting time must be measurable without being misrepresented as actual employee effort hours.

51. **Grant-funded research and Research Contract routes are different business patterns and must not be forced through one universal Grant Application / Funding Agreement lifecycle.**

52. **Agreement Type, agreement obligations, conditional effect, Post-Award relevance and authorizing effect are independent dimensions.**

53. **Authorizing Basis Requirement may be composite and is satisfied by one or more applicable official instruments.**

54. **Variable business policy uses a versioned configurable Business Policy / Rule framework with applicability, conditions, outcomes, explanation and explicit overrideability.**

55. **NURA ERP master architecture includes a distinct Solution Architecture layer between Information Architecture and Enterprise Architecture.**

56. **Agreement preparation is variable and action-based.** Preparation may follow different and repeated sequences; external/manual Counterparty Coordination is not forced into a mandatory lifecycle state where ERP cannot reliably observe it.

57. **Agreement processing, legal/document facts, legal effect and administrative closeout are separate dimensions.**

58. **Agreement Closure is separate from Project Closure and is obligation-driven.** Head of Post-Award and Legal jointly confirm administrative closeout against the applicable obligation checklist.

59. **Agreement early termination is a causal event, not a substitute final status.** It preserves basis, effective date, evidence and consequences; termination of legal effect does not itself mean Agreement `Closed`.

60. **Research Need has its own lifecycle; Procurement execution progress is represented through related downstream objects and quantities.**

61. **Effective Procurement Plan ≠ Approved Procurement Plan Version.** `Effective Procurement Plan` is current operational truth; `Approved Procurement Plan Version` is a formal immutable snapshot; `Consolidated Approved Procurement Plan` is the latest formally approved consolidated representation.

62. **Procurement Case is the Procurement Office execution/consolidation context; Procurement Procedure is not a separate first-class Business Object.** Procurement Method-specific rules govern Case execution.

63. **Heterogeneous Procurement Case / Request progress is primarily item/allocation-level.** Where Items can be at different stages simultaneously, aggregate progress/state should be concise and derived rather than manually pretending all Items share one detailed stage.

64. **Goods Acceptance is item/quantity-based and one Delivery may have multiple actual receivers.** Aggregate acceptance outcomes should be derived from the underlying Item/Quantity facts where possible.

65. **Advance Delivery Notice is a target supplier-control and ERP capability.** Where applicable, Supplier Contract terms should require advance identification of planned delivery contents and timing; ERP must still support fallback handling for unannounced/insufficiently described deliveries.

66. **Normal Procurement Request requires a current Procurement Plan entry; urgent procurement uses a controlled exception route.** For a normal Procurement Request, the corresponding Research Need must be reflected in the current Procurement Plan. Urgent procurement may proceed outside the normal planning route only with an established justification and the required special approval. Inclusion in the Procurement Plan is not by itself authorization to spend.

67. **Agreement-preparation discontinuation evidence is not limited to a mandatory refusal letter.** When Agreement preparation is permanently discontinued, Legal records the `Not Concluded` outcome, structured reason and supporting evidence/documents. Legal records the decision but does not replace the role authorized to make the refusal decision. This supersedes only the mandatory-refusal-letter aspect of Decision 41; the remaining Decision 41 timing, escalation and notification semantics remain in force.

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
- Project Closure, Post-Closure traceability and Audit after closure without reopening a correctly Closed Project solely because of post-closure activity; controlled Reopen remains available to correct an erroneous Closure.
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
- Mandatory manual Head-of-Post-Award button for every normal Project Closure — superseded by automatic closure when all applicable Closure-Blocking Conditions are satisfied, subject to final cross-Part normalization.
- Treating all procurement fulfillment stages as one honest top-level Procurement Request status — rejected; detailed progress belongs primarily to underlying Items / Cases / downstream objects and may be aggregated for user presentation.
- `Pending Activation` as a Project lifecycle status — superseded; Project business activity follows satisfaction of the applicable Authorizing Basis Requirement, while Setup readiness, Operational Authorization, Funding condition and Operational Restrictions are represented separately.
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
- `Period Ended` as a persistent Project lifecycle status — rejected; it is derived from the effective Project End Date.
- `Terminated` as an alternative final Project state to `Closed` — rejected; Termination is a causal event/reason followed by Closure.
- Treating every Mandatory Project Obligation as Closure-Blocking — rejected.
- Manual discretionary `Closure Hold` as a substitute for a complete Closure Checklist — rejected.
- Open Audit / Audit Finding automatically blocking Project Closure — rejected.
- Absolute prohibition of any new expense initiative after Project End Date — rejected; business purpose may remain linked to the Project while financial attribution uses another authorized source.
- `Closed Project can never be reopened` as an absolute rule — superseded; erroneous Closure may be corrected through controlled Reopen.
- `Under Technical Review` / `Under Peer-Review` as core Application lifecycle states — superseded.
- Mandatory Pre-Award administrative check as a universal gate for external submission — rejected.
- Designing NURA ERP around expected NCSTE status integration/API — rejected for the current target.
- Using `Review` as the primary term for Pre-Award administrative/technical application checking — superseded to avoid confusion with scientific evaluation.
- Treating private/quasi-state Research Contracts as ordinary grant routes — rejected.
- `Project Agreement` as a necessary user-facing umbrella business term — not adopted.
- Determining Authorizing Basis solely from Agreement Type/name — rejected.
- Assuming Authorizing Basis must consist of one document — superseded by composite Authorizing Basis Requirement.
- `Has any obligation = Post-Award Handover Required` — rejected as too broad.
- `Only financial obligations = Post-Award Handover Required` — rejected as too narrow.
- Hard-coding Research Contract ↔ Project as permanently 1:1 — rejected.
- Treating Matching / Co-funding as necessarily a top-level Agreement Type — superseded; it is primarily a Funding Mechanism.
- Fixed universal Agreement / Amendment chain `Draft → Internal Review → Counterparty Review → EDMS → Signed/Registered → Effective` — superseded by variable/cyclic action history, separate legal/document facts, legal effect and administrative closeout.
- Mandatory `Counterparty Coordination` as a system lifecycle status — rejected where the external/manual activity is not reliably observable.
- Treating Agreement `Effective` as merely the last manual workflow status — rejected; legal effect is derived from applicable facts and terms.
- Treating Project Closure as Agreement Closure — rejected.
- Closing an Agreement while an outstanding obligation can still create contractual penalty/refund/claim/dispute consequences — rejected.
- Treating Supplier Contract signature as an absolute prohibition on later Procurement Request / Research Need change — rejected; post-contract change remains possible through Formal Request to Procurement and contractual assessment.
- Research Need lifecycle continuing through Supplier Selection, Contract, Delivery, Acceptance, Payment and `Closed` — superseded; those are downstream progress facts.
- Treating Approved Procurement Plan and Effective Procurement Plan as interchangeable concepts — rejected.
- `Consolidated Current Procurement Plan` as the operational current truth — superseded by `Effective Procurement Plan` plus `Consolidated Approved Procurement Plan`.
- Procurement Procedure as a required separate first-class Business Object — not adopted.
- Procurement Case as merely an Announcement — rejected as too narrow.
- One manually maintained aggregate Acceptance / Procurement Case detailed-progress state as the sole truth for heterogeneous Items — superseded by Item/Quantity-level facts and derived aggregate views.
- Keeping Solution Architecture only implicitly distributed across Parts 00/03 — superseded by an explicit Part 07 Solution Architecture.

---

## Open Issues / Conflicts

Items below are either intentionally unresolved or explicitly marked as resolved but pending propagation to the architecture Parts.

### Architecture normalization required before Part 04

1. **RESOLVED — propagated to Parts 00–01; pending propagation to Parts 02–03:** Project lifecycle / Setup readiness / Operational Authorization / Operational Restriction semantics.

   Established target model:
   - each Project Type / Scenario has an applicable `Authorizing Basis Requirement`;
   - `Project Created` is an event, not a persistent lifecycle status;
   - external Award may create the Project before the Authorizing Basis Requirement is satisfied → `Setup`;
   - normal external-grant requirement is satisfied by the signed + registered Funding Agreement recorded in ERP → `Active`;
   - internal-grant requirement is satisfied by the Research Council Decision → `Active`;
   - other Project Types / Scenarios use the applicable approved agreement(s), decision(s) or other official instrument(s); the requirement may be composite;
   - Funding receipt / delay does not determine `Active` status;
   - `Setup Complete` is readiness, not lifecycle;
   - normal Operational Authorization is blocked until all Mandatory Setup Checks are complete;
   - Head of Post-Award explicitly grants Operational Authorization;
   - Operational Restrictions are a separate universal dynamic control throughout Active Project life;
   - restrictions affect new obligations / expenditure initiatives, not already validly created obligations;
   - affected pre-obligation initiatives are suspended on the source object and surfaced through system views;
   - Head of Post-Award may grant a case-specific exception with mandatory Reason and audit trail, without a separate approval; hard validations remain non-bypassable;
   - unsuccessful Agreement preparation may move a pre-active Project to `Not Proceeded`; the same Project may be reopened if the same Award resumes;
   - Legal closure of unsuccessful Agreement preparation records the outcome with structured Reason + supporting evidence/documents;
   - Agreement-preparation timing uses configurable Target and Critical escalation thresholds.

   Pending implementation only:
   - propagate the accepted semantics consistently through Parts 02–03;
   - select final UI labels where wording remains implementation-level rather than business-semantic.

   Issue #1 remains resolved at the architectural-concept level. Detailed `Project Type / Scenario → Authorizing Basis Requirement` rule mapping is tracked separately as a modeling/configuration item and does not reopen Issue #1.
2. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** Application lifecycle is separated from Pre-Award Application Check, external submission, scientific evaluation, Funding Decision and Handover.
3. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** Research Need has its own lifecycle; downstream Procurement execution is represented through related objects / quantities rather than Research Need lifecycle states. Exact final lifecycle labels and unresolved reverse cardinalities remain Part 05 detail under Issue #17.
4. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** Procurement Plan semantics are normalized: `Effective Procurement Plan` is current operational truth; `Approved Procurement Plan Version` is a formal immutable snapshot; `Procurement Plan Amendment` is the formal delta; `Consolidated Approved Procurement Plan` is the latest formally approved consolidated representation.
5. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** Procurement Procedure is not a separate first-class Business Object; target execution is `Procurement Case + Procurement Method-specific rules/workflow`.
6. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** Goods Acceptance is item/quantity-level, supports multiple actual receivers in one Delivery, and uses derived aggregate outcomes where possible. Advance Delivery Notice is added as a target supplier-control / ERP capability with operational fallback.
7. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** Project Closure semantics, closure-blocking vs post-closure obligations, Termination, Audit relationship, extension and controlled erroneous-closure reopening are established.
8. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** Agreement / Amendment preparation is variable/cyclic and action-based; processing, registration/signature facts, legal effect, `Not Concluded`, early-termination event and separate Agreement administrative closeout are established.

### Business clarification required

9. Can one Person hold multiple simultaneous Project Roles within the same Project, and if so how should role assignments be modeled?
10. Define the exact incompatible-role / Separation-of-Duties matrix.
11. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** one Project may require/link multiple Agreements/official instruments; one Agreement may also cover multiple Projects where the business model requires it. Type-specific constraints remain for Part 05.
12. **RESOLVED — propagated to Parts 00–01; pending propagation/full rewrite of Parts 02–03:** Agreement/Contract Type is separated from purpose, obligations, conditional effect, Post-Award relevance and Authorizing Basis role; Authorizing Basis Requirement may be composite.
13. Confirm formal Process Owners / process accountability.
14. Confirm the exact Calendar Plan / Milestone / Deliverable business structure.

### Data / financial logic still to formalize

15. Finalize exact Commitment → Actual → Available Budget calculation and double-counting prevention. Established constraint: Unallocated Funding is not Available Budget and must not become spendable until it is allocated and approved.
16. **RESOLVED at architecture-concept level:** Research Need owns only its own lifecycle; downstream procurement progress belongs to related Procurement objects / quantities. Exact Part 05 relationship/cardinality implementation remains under Issue #17.
17. Final cardinalities and temporal constraints for unresolved relationships before Part 05. Scope explicitly includes unresolved reverse Research Need ↔ Procurement Request Item relationships, Procurement Case ↔ Supplier Contract cardinalities/constraints, Agreement closeout-obligation relationships and Delivery / Acceptance / Receiver / Advance Delivery Notice cardinalities.
31. Determine the exact Part 04–05 representation for external research activities known to NURA but not administratively managed by NURA. Established principle: known by NURA ≠ administered by NURA.
32. Formalize the configurable `Project Type / Scenario → Authorizing Basis Requirement` mapping, including applicable composite requirement structures, during rule / data design. The architectural concept is resolved; this is a deferred modeling/configuration detail needed for later Parts.

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

Rewritten and semantically synchronized working baseline. It reflects the accepted Project / Authorizing Basis / Operational Authorization model, Project Closure semantics, Agreement / Contract classification and closeout, normalized Research Need / Procurement Plan / Procurement Case / Goods Acceptance semantics, and the Configurable Business Policy / Rule framework. Part 00 passed the Part 00 ↔ Part 01 consistency review on 2026-09-10.

### Part 01 — Business Analysis

Rewritten and semantically synchronized working baseline covering business context, stakeholders, Business Requirements, Business Rules and glossary. It incorporates the accepted Project authorization, Application / Pre-Award, Closure, Agreement / Contract, Research Need / Procurement Plan / Procurement Case / Goods Acceptance and Configurable Business Policy / Rule semantics. Current operating-scale values remain planning estimates; formal Process Ownership and specified deferred cardinalities remain unresolved. Part 01 passed the Part 00 ↔ Part 01 ↔ Engagement Memory semantic consistency review on 2026-09-10, subject to Decisions 66–67 now incorporated in this v1.5.

### Part 02 — Process Architecture

Substantial expanded baseline covering Pre-Award, Agreement / Project Initiation, Funding, Budget, Project Change, Research Team, Procurement, Services, Reporting, Payment, Reconciliation, Closure and cross-functional controls. It requires full synchronization of the Pre-Award Application Check / external evaluation / Handover flow (#2), Project initiation and composite authorizing-instrument logic (#1, #11/#12), variable/cyclic Agreement preparation plus termination and Agreement closeout (#8), responsibility/waiting-time history, restriction/suspension handling, the automatic Project Closure / post-closure / erroneous-Reopen model (#7), and the normalized Procurement model (#3/#16, #4, #5, #6). Legacy `Pending Activation`, fixed Agreement chains, Research Need downstream pseudo-lifecycle, old Procurement Plan terminology and manual-normal-closure semantics are stale.

### Part 03 — System Analysis

Advanced system-behavior baseline covering Functional Requirements, Use Cases, System Context, State Models, Validation, Roles / Permissions, Integration Requirements and NFR. For Procurement, Part 03 remains the strongest current design baseline, but it must not be treated as internally authoritative where later accepted decisions corrected it. It requires full normalization of the Application model (#2), Project State Model and composite Authorizing Basis Requirement (#1, #11/#12), Project Closure / extension / controlled erroneous-Reopen behavior (#7), Agreement / Amendment action history, legal facts/effect and separate closeout (#8), Research Need lifecycle and downstream quantity progress (#3/#16), Effective versus Approved Procurement Plan semantics (#4), Procurement Case / Method boundary and heterogeneous item progress (#5), and item/quantity Goods Acceptance plus Advance Delivery Notice (#6). `Ready for Administration` as lifecycle status and other legacy mixed-state semantics are stale. Solution-level technical material currently embedded in Part 03 must later be normalized into the approved Part 07 Solution Architecture while preserving system-level requirements in Part 03.

### Part 04 — Data Architecture

Not started.

### Part 05 — Data Model

Not started.

### Readiness

The current semantic reconciliation / question cycle required before the Parts 00–03 rewrite is complete at the architecture-concept level. Remaining Open Issues are either deferred to their applicable later Parts / verification activities or do not currently block the rewrite unless later analysis proves otherwise.

Part 00 and Part 01 are now treated as semantically synchronized working source documents. Part 02 and Part 03 still require the controlled rewrite/synchronization pass rather than local patching. Their rewrite must preserve valid established content while incorporating all accepted lifecycle, terminology, rule-framework, process-route, authorization, agreement, procurement and closure corrections.

Transition readiness for the remaining rewrite is controlled by the current `ENGAGEMENT_CONTROL.md`. Architecture work may continue under the accepted deferred-checkpoint path while canonical Git checkpoint verification remains unavailable; no verified canonical checkpoint is claimed by this memory.

Only after the Part 02–03 rewrite and a cross-Part verification pass should Part 04 Data Architecture be formally developed.

The approved master structure is:

00 Scope & Architecture Principles  
01 Business Analysis  
02 Process Architecture  
03 System Analysis  
04 Data Architecture  
05 Data Model  
06 Information Architecture  
07 Solution Architecture  
08 Enterprise Architecture

## Important Cross-Part Dependencies

Parts 04–05 must preserve and explicitly model:

- Application and Project independent identity/history;
- Funding Decision / Award → Project creation versus Project-Type/Scenario-specific `Authorizing Basis Requirement` → satisfaction by one or more authorizing instruments → business `Active` distinction;
- Agreement / Amendment / Funding / Project / Budget independent lifecycles;
- Agreement preparation/action history versus registration/signature facts versus legal effect versus administrative closeout;
- `Not Concluded` Agreement-preparation outcome and causal relationship to pre-active Project `Not Proceeded`;
- Agreement early-termination event with separate reason/basis, effective date, evidence and consequences;
- Agreement closeout obligations / checklist and the possibility that the same underlying obligation has different closure significance for Project versus Agreement;
- Project business lifecycle versus Setup readiness versus Operational Authorization versus dynamic Operational Restrictions;
- `Project Created` as event, `Not Proceeded` pre-active outcome and controlled reopening of the same Project for the same Award;
- external-grant `signed + registered Agreement recorded in ERP` activation trigger versus retroactive `Effective From`;
- Operational Restriction scope/effective history, affected expenditure-object suspension, causal link to restriction, case-specific exception, mandatory Reason and audit trail;
- suspension as source-object state / progress with derived views rather than a separate register;
- Hard Business Validation versus overrideable Operational Restriction;
- Agreement-preparation Target / Critical escalation thresholds, discontinuation reason and supporting evidence/documents;
- Current / Proposed / Effective semantics;
- decision/signature/registration dates versus `Effective From`;
- causal links between formal changes and downstream consequences;
- Budget Draft / Approval / partial Approved Allocations / Unallocated Amount / Budget Revision / Budget Version semantics;
- Funding versus Budget versus Commitments versus Operational Actual versus Accounting Actual;
- authoritative versus derived / operational financial facts;
- 1C Transaction → zero/one/many controlled ERP allocations without altering the source transaction;
- Person / User Account / Project Participation separation;
- unresolved same-Project multi-role cardinality;
- Research Need own lifecycle versus downstream Procurement quantity/progress facts, including one Need feeding multiple downstream Request/Item allocations;
- Procurement Request / Request Item / Procurement Case / Case Item or Lot / Item Allocation structure;
- Procurement Case + Procurement Method-specific execution, with no separate required Procurement Procedure Business Object;
- failed/non-resulting Case Item outcome and later re-allocation of remaining need to a new Case;
- cross-project Request/Need consolidation while preserving source Project/Budget/Funding attribution;
- Procurement Case → zero/one/multiple Supplier Contracts as an allowed architecture direction, with exact constraints deferred to Issue #17;
- `Effective Procurement Plan` versus `Approved Procurement Plan Version` versus `Procurement Plan Amendment` versus `Consolidated Approved Procurement Plan`;
- Supplier Contract / Advance Delivery Notice / Shipment / Delivery / Acceptance / Payment distinctions;
- Delivery Item / Quantity-level Acceptance, multiple actual receivers and derived aggregate acceptance outcome;
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
- Project business activity and permission to initiate expenditures are different facts: satisfaction of the applicable Authorizing Basis Requirement makes the Project `Active`, while expenditure initiation remains subject to Setup readiness and explicit Operational Authorization.
- Planning approval is not expenditure authorization: Research Needs and Procurement Plan may be prepared/approved during Setup/readiness work before Operational Authorization, while a formal Procurement Request remains the expenditure-initiation boundary.
- Funding delay is a separate operational/financial condition; it should not distort the Project lifecycle merely to make the problem visible.
- For external grants, practical NURA lifecycle activation should wait for the signed + registered Agreement to be recorded with official registration details rather than introducing unnecessary transient states for a short signature-to-registration interval.
- Operational restrictions are management controls over future commitment formation, not a substitute Project lifecycle and not an automatic cancellation of existing obligations.
- In NURA's small-organization operating model, ERP should provide Head of Post-Award the functional control needed to administer restrictions/exceptions and rely on explicit Reason + audit trail rather than add approval layers whose only purpose is to police managerial good faith. Hard business validations remain a separate non-bypassable boundary.
- An archive view should not become a second data store: discontinued pre-active Projects retain their original Setup history and can be reopened when the same Award resumes.
- Process SLA thresholds and escalation limits are governed control parameters; observed average duration is an analytical KPI and should not itself become the process rule.
- An externally/manual activity that the ERP cannot reliably observe should not be forced into a mandatory lifecycle status merely because it is operationally useful to know that it happened; action/evidence history may be more truthful.
- Effective operational planning state and periodically approved immutable plan snapshots are different truths and must not be collapsed.
- A planning/demand change after a downstream contractual obligation exists is not a simple upstream edit; it must use the applicable controlled downstream change / termination path while preserving original history.
- Some ERP improvements require changes to the surrounding operating or contractual environment: Advance Delivery Notice is both a system capability and, where applicable, a Supplier Contract / process expectation.
