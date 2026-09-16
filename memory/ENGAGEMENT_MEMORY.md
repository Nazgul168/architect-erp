# ENGAGEMENT_MEMORY.md

- **MEMORY_VERSION:** `2.2`
- **LAST_RECONCILED:** `2026-09-16`
- **SOURCE_PARTS_BASELINE:** Current Project Sources `Part 00 — Scope & Architecture Principles`, `Part 01 — Business Analysis`, `Part 02 — Process Architecture` and `Part 03 — System Analysis` have been rewritten / synchronized and are the current working baselines. Accepted Decisions 68–86 are reflected in the current Parts 00–03 where applicable. `Part 04 — Data Architecture` is the active architecture-development phase. In addition, Decisions 87–99 below establish the accepted post-architecture `Architecture-to-Delivery Layer` objective and the verification-aware Part-authoring rules needed to support it. These decisions guide how Parts 04–08 are written but do not replace the Parts themselves. `ARCHITECTURE_PART_AUTHORING_STANDARD.md v1.1` is the active Engagement authoring standard for Parts 04–08.
- **BOOTSTRAP / RECONCILIATION reference:** QA Bootstrap Batches 1–8 + accepted Global Reconciliation, 2026-09-08.

## Engagement Identity / Status

- **Engagement:** NURA ERP Architecture
- **Engagement ID:** `ENG-NURA-ERP-001`
- **Status:** ACTIVE
- **Memory status:** CONSOLIDATED WORKING VERSION — PARTS 00–03 REWRITTEN / SYNCHRONIZED CURRENT WORKING BASELINES; ARCHITECTURE-NORMALIZATION ISSUES #1, #2, #3/#16, #4, #5, #6, #7, #8, #11/#12, #14 AND #35 PROPAGATED; PART 04 DATA ARCHITECTURE ACTIVE; POST-ARCHITECTURE ARCHITECTURE-TO-DELIVERY OBJECTIVE ACCEPTED
- **Current architecture state:** Parts 00–03 are the current rewritten / synchronized working baselines and Part 04 is active. The Calendar Plan / Milestone / Deliverable, Research Output / Outcome / TRL, lead/co-executor, Contract Financial Direction, Legal-led Incoming / Authorizing Agreement, Project Closure and procurement normalizations are reflected across the applicable Parts. A material transition V&V found no known semantic contradiction that blocks Part 04. Remaining issues are intentionally deferred data / relationship / institutional / technical questions and must be resolved at the layer where they become decision-relevant. The approved master architecture structure includes Part 07 — Solution Architecture and renumbers Enterprise Architecture to Part 08. After Parts 00–08, the Engagement will develop an `Architecture-to-Delivery Layer` that converts human-readable architecture into implementation specifications, independently acceptable end-to-end increments, acceptance/conformance controls and a machine-readable Architecture Control Model. Parts 04–08 are therefore authored under `ARCHITECTURE_PART_AUTHORING_STANDARD.md v1.1`: human-readable architecture remains the source of meaning, while material rules are written precisely enough for later traceability, implementation specification, acceptance and deterministic/formal or evidence-based conformance without inventing new business meaning.
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

### Active source-set boundary

For runtime/source consistency work, an artifact is part of the active source set only when it is actually present in the current Project Sources / verified supplied source set. A filename or canonical path mentioned inside another artifact does not by itself make that referenced artifact an active source.

Historical attachments, earlier chat-generated files and proposed replacement artifacts must not be treated as current sources unless the user has actually added them to the active source set.

### Accepted correction propagation rule

If an accepted / reconciled correction is explicitly recorded in this Engagement Memory as **not yet propagated to a Part**, that Part is treated as **stale for that specific claim only** until synchronization. This is an Engagement-level state of **accepted but not yet implemented**.

In all other Part ↔ Engagement Memory conflicts, do not silently prefer either source. Keep the discrepancy as an explicit conflict until it is reconciled.

As of Memory v1.9, there is **no known accepted architecture correction pending propagation to Parts 00–03**. Any new discrepancy found during Part 04 work must be recorded explicitly rather than silently treated as already synchronized.

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

Agreement / Contract Type classifies the legal document. Purpose, conditional effect, obligations, Post-Award relevance, authorizing effect and **Contract Financial Direction** are separate structured dimensions.

**Contract Financial Direction** is defined relative to NURA and must not be inferred only from Agreement / Contract Type:

- **Incoming Contract** — NURA receives funding / remuneration or another incoming financial contribution and, in return, performs research, services, works or other contractual obligations.
- **Outgoing Contract** — NURA acquires goods, services or works and assumes an obligation to pay or otherwise finance the Counterparty.
- **Non-monetary Agreement** — the agreement creates relevant obligations without a direct payment flow between NURA and the Counterparty.
- **Mixed Agreement** — the same agreement contains materially relevant incoming and outgoing financial obligations and therefore cannot be truthfully reduced to one direction.

Financial direction is an operational / architectural characteristic and does not by itself determine the accounting classification of income, revenue, grant funding or expense.

Incoming Contracts are normally initiated / prepared through the Legal-led agreement route and may exist without an Application. They may become the basis for Project creation, Funding, Calendar Plan and NURA performance / reporting obligations.

Outgoing Contracts arise from the applicable expenditure, Project Services or Procurement process. Their business preparation is owned by the responsible Post-Award or Procurement route, while Legal participates where the Contract Type, risk, template, EDMS route or other Business Rules require legal review / coordination. An Outgoing Contract must preserve the applicable Budget, Commitment, Project, Business Purpose and Financial Attribution context.

The same research collaboration can have opposite financial directions for different organizations. A co-executor Contract is outgoing for the lead organization that pays the co-executor and incoming for the co-executor that receives the payment. Therefore financial direction is always modeled from NURA's perspective.

Shared Agreement / Contract data, templates, EDMS integration, legal facts and versioning do not imply one universal contract-creation workflow. Common legal/document capabilities may be reused while the process entry point, responsible function, controls and downstream consequences remain route-specific.

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

### Calendar Plan, Calendar Plan Items, Milestones and Planned Results

A **Calendar Plan** is a formal, versioned plan of Project work within a specific Agreement / Contract / Authorizing context. For grant-funded routes it normally originates from the successful Application and, where applicable, becomes an appendix or other formally incorporated part of the governing Agreement / Contract.

A Calendar Plan must not be treated as an ordinary freely editable task list. Within one Calendar Plan, approved changes create a new **Calendar Plan Version** rather than silently overwriting the previously effective plan. At any point in time, the applicable business rules determine which version is effective.

One Project may require more than one Calendar Plan where NURA has more than one distinct contractual / authorizing execution context. A Calendar Plan attached to a principal funding Agreement and a Calendar Plan attached to a separate service / co-executor Contract are separate plans, not versions of one another, even when the second covers a subset of work from the first.

For a multi-organization externally funded Project where NURA is the lead organization, NURA may administer the full Project Calendar Plan under the principal Agreement and separate Calendar Plans under Contracts with co-executors. Where NURA is itself a co-executor, NURA administers the scope and Calendar Plan of its own Contract; the ERP must not require NURA to administer the complete external consortium Project if NURA is not responsible for it.

The same external research initiative may therefore map to different NURA administrative scenarios depending on NURA's legal / contractual role. Where NURA is the lead organization and direct grant recipient, the route is the applicable external-grant route. Where NURA is a co-executor engaged by another lead organization under a service / research contract, NURA administers that contracted scope as a Research Contract / service-delivery context rather than pretending to own the full external grant.

For the currently known state-funded consortium pattern, the grantor contracts with one lead organization, while co-executors are engaged through separate contracts. This is a confirmed current business pattern, not a permanent universal legal invariant; future Programme Rules may require a different route.

Agreement / Contract creation is not dependent on an Application. Legal / other authorized roles must be able to create and process an Agreement / Contract independently; an Application / Award link is recorded only when it exists in the real business context.

A **Calendar Plan Item / Task** is a hierarchical work item within the plan. It may have child Tasks to arbitrary practical depth and normally carries a planned period / deadline plus the applicable planned direct result. The architecture must not hard-code a three-level maximum solely because current documents commonly stop at `N.N.N`.

A **Milestone** in NURA ERP is primarily an administrative control point meaningful to Research Administration — for example a report due date, governing-body decision, act-signing point, expected tranche, or other control event. It is not a synonym for a scientific Task / subtask in the Calendar Plan.

A **Deliverable** is not established as a universal first-class Business Object. Where Programme Rules, an Agreement or another governing source uses that term, ERP preserves it as the applicable obligation / planned-result terminology. Core modeling distinguishes the planned result from the actual Research Output and from formal acceptance of a reporting period / work package.

A formal change to an approved Calendar Plan is a managed **Project Change**. For an external Project, the applicable Business Rules determine whether the change requires funder approval and / or Agreement Amendment. For an internal grant, the applicable Research Council decision / approval governs the change. Operational clarification that does not alter the approved Calendar Plan is not a Project Change merely because work details evolved.

### Research Outputs, Outcomes, TRL and Institutional Result Knowledge

A **Research Output** is a durable structured Business Object representing an actual research result created or evidenced by NURA research activity. Examples include Publication, Dataset, Software, Patent / IP, Prototype, Method / Protocol, Report and other material research results.

Research Output exists for more than current-project administration. It supports institutional knowledge and multi-year result analytics, including the ability to explain in understandable language what the University actually created, developed or advanced — not only how many Projects, publications or patents were recorded.

Research Output must therefore not be constrained conceptually to exactly one Project. It may be linked to the Project(s), Calendar Plan Item(s), Project Obligation(s), Report(s), repository record(s) and other evidence that establish its origin, contribution or later development. Exact cardinalities, lineage and temporal constraints are deferred to Parts 04–05.

The architecture distinguishes:
- **planned result** — what an Application / Calendar Plan / Agreement says should be achieved;
- **Research Output** — what was actually created;
- **Research Outcome** — observed use, adoption, effect or other higher-level result enabled by one or more Outputs;
- **formal acceptance / reporting outcome** — whether an authorized external or internal body accepted the applicable report, work period or other formal obligation.

Formal acceptance of a Project reporting period must not automatically be modeled as an independent `Accepted` lifecycle state for every Research Output. Where a Programme or Agreement requires separate acceptance of a specific result, that requirement is applied explicitly.

Where TRL or another maturity scale is required by Programme Rules, Application, Agreement, Calendar Plan or reporting requirements, ERP should store the relevant declared / target / reported / externally confirmed value as applicable, together with source and supporting evidence. NURA ERP does not independently determine scientific or technological maturity where that determination belongs to PI, scientific evaluation, the funder or another authorized body.

Structured institutional result data must remain usable without dependency on AI availability. AI may assist by extracting candidate Outputs, summaries or attributes from reports and other evidence, especially for historical data, but AI-generated proposals are not authoritative facts by themselves. Provenance must be preserved and material extracted facts should be confirmed or otherwise validated through an authorized business process before they become trusted institutional records.

### Reporting-period acceptance for current grant scenarios

For applicable external state-funded grant routes, the user-confirmed current process is period-level rather than per-Output acceptance: the annual scientific report undergoes the applicable external scientific expertise; the competent scientific body (currently NNS in the described route) makes the applicable continuation / termination / final-report decision; and the grantor records acceptance of the period's work through the applicable act. The grantor's act must not be treated as independent from the preceding required scientific decision where current law / Programme Rules make that decision a prerequisite.

For internal grants, annual reporting is submitted to Research Council, which may decide continuation, stopping / termination or another applicable outcome under the institution's internal rules. The route is more configurable and must not be hard-coded as identical to the external state-funded route.

Because the statement about what a state body may legally accept is a legal / Programme Rule claim, the exact authoritative legal basis and current wording must be verified before implementing a non-configurable hard validation. The Engagement-level business semantics are nevertheless clear: formal acceptance is primarily a reporting-period / work-acceptance process, not an automatic independent acceptance lifecycle for each Research Output.

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

40. **Legal-led Incoming / Authorizing Agreement preparation uses controlled thresholds, not observed averages as rules.** That route should distinguish configurable `Target Duration` from `Critical Escalation Threshold`; exceeding the target notifies/reminds the responsible Legal user, while exceeding the critical threshold escalates to COO and Director. Actual average duration remains an analytical KPI. These thresholds do not automatically govern Outgoing Contracts prepared through Post-Award or Procurement routes unless their own Business Rules explicitly establish equivalent controls.

41. **For Legal-led Incoming / Authorizing Agreement preparation, Legal records discontinuation; Legal does not originate the refusal decision.** Closing unsuccessful preparation requires a structured reason and supporting evidence/documents. No separate approval of Legal's recording action is required. `Not Concluded` stops the applicable Target Duration / Critical Escalation path and notifies Post-Award, COO and Director. The earlier requirement that a NURA refusal letter to the funder be mandatory evidence is superseded by Decision 67.

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

67. **Legal-led Incoming / Authorizing Agreement-preparation discontinuation evidence is not limited to a mandatory refusal letter.** When that preparation route is permanently discontinued, Legal records the `Not Concluded` outcome, structured reason and supporting evidence/documents. Legal records the decision but does not replace the role authorized to make the refusal decision. This supersedes only the mandatory-refusal-letter aspect of Decision 41; the remaining route-specific timing, escalation and notification semantics remain in force.

68. **Calendar Plan is formal, contextual and versioned.** A Calendar Plan belongs to a specific Agreement / Contract / Authorizing context; approved changes create Calendar Plan Versions rather than silently overwriting the effective plan. Distinct contractual plans are separate Calendar Plans, not versions of one another.

69. **One Project may have multiple Calendar Plans when distinct contractual execution contexts exist.** In a lead-organization scenario NURA may administer the full principal plan plus separate co-executor/service-contract plans; in a co-executor scenario NURA administers its own contractual scope and is not required to administer the complete external consortium Project.

70. **Agreement / Contract creation is independent of Application.** Legal / authorized roles must be able to create and process Agreements / Contracts without an Application link. Application / Award is one possible upstream source, not a mandatory parent.

71. **Calendar Plan Task and administrative Milestone are different concepts.** Calendar Plan Items / Tasks are hierarchical work items with planned timing and results; Milestones are administrative control points for Research Administration and are not automatically scientific Tasks.

72. **Deliverable is not a mandatory universal first-class Business Object.** Preserve the term where an authoritative Programme / Agreement uses it, but core modeling separates planned results, actual Research Outputs and formal reporting / acceptance outcomes.

73. **Research Output is a durable first-class Business Object with institutional analytical value.** It represents an actual research result, can outlive a Project and must not be conceptually constrained to exactly one Project. Exact cross-Project lineage / cardinalities are deferred to Parts 04–05.

74. **Planned result, Research Output, Research Outcome and formal acceptance are distinct.** The system must not infer that every Research Output has an independent `Accepted` lifecycle merely because a reporting period or Project work was formally accepted.

75. **TRL is a structured governed fact where applicable, not an ERP-generated scientific judgment.** Store applicable declared / target / reported / externally confirmed maturity information with provenance and evidence when required by Programme / Agreement / reporting rules.

76. **AI-assisted extraction is optional support, not the institutional source of truth.** Durable result analytics must rely on structured records with provenance and applicable business confirmation / validation. AI may propose extracted Outputs, summaries or attributes but the architecture must remain operational if AI is unavailable.

77. **NURA's contractual role determines the administrative route in multi-organization research.** When NURA is the lead organization / direct grant recipient, it administers the principal external-grant context and may contract co-executors. When NURA is a co-executor engaged by another lead organization, NURA administers its own Research Contract / service scope and Calendar Plan and is not required to own the full external grant administration.

78. **Formal acceptance is primarily period/work acceptance, not universal per-Output acceptance.** For the currently described state-funded route, annual scientific reporting, required scientific/expert decision and the grantor's act form the applicable acceptance chain; for internal grants Research Council applies the internal route. Individual Research Output acceptance is modeled only where a specific Programme / Agreement requires it.

79. **Contract Financial Direction is independent of Agreement / Contract Type.** NURA ERP must distinguish Incoming, Outgoing, Non-monetary and, where materially applicable, Mixed agreements from NURA's perspective. Financial direction is not inferred solely from the legal document type and does not itself define accounting revenue / expense classification.

80. **Decision 70 does not mean Legal prepares every Contract.** Incoming Contracts and other Legal-led agreements may be created independently of Application and are normally initiated / prepared through the Legal route. Outgoing Contracts arise from the applicable expenditure / service / procurement process and use the responsible Post-Award or Procurement route.

81. **Outgoing Contracts preserve expenditure controls and financial context.** Before an Outgoing Contract creates a valid financial / contractual obligation, the applicable Budget, Operational Authorization, Operational Restrictions, approval and other Business Rules must be satisfied. The Contract remains linked to the originating expense / procurement context, Commitment, Project, Business Purpose and Financial Attribution.

82. **The same research collaboration may be outgoing for one organization and incoming for another.** When NURA is the lead organization and pays a co-executor, the co-executor Contract is Outgoing for NURA. When NURA is the co-executor receiving payment from another lead organization, the corresponding Research / Service Contract is Incoming for NURA.

83. **Non-monetary and mixed agreements must not be forced into an artificial income/expense binary.** Where the real agreement has no direct payment flow or contains material two-way financial obligations, the model must preserve that fact and apply the appropriate route and controls.

84. **Shared Contract capabilities do not imply one universal Contract workflow.** Common structured data, templates, EDMS integration, legal facts, versioning and closeout may be reused across Contract categories, while process origin, responsible function, required validations and downstream consequences remain specific to the contract route.

85. **Agreement SLA / escalation controls are route-specific, not universal Contract controls.** `Target Duration`, Legal reminders, `Critical Escalation Threshold`, `Not Concluded` handling and the associated Post-Award / COO / Director notifications apply to the Legal-led Incoming / Authorizing Agreement preparation route described in Parts 01–03. Outgoing Contract routes use their own applicable timing and escalation Business Rules rather than inheriting the Legal-led route by default.

86. **Project Closure checks use Project Obligations / Planned Results, not a universal Deliverable entity.** Closure-Blocking Conditions may include required Project Obligations / Planned Results and may include Deliverables only where an applicable Programme Rule or Agreement uses that term. This preserves Decision 72: Deliverable is not a mandatory universal first-class Business Object.

87. **Architecture must leave verifiable assertions, not only narrative descriptions.** Parts 00–08 remain human-readable architecture, but material requirements, invariants, authority rules, lifecycle/state constraints, permissions, integration boundaries, audit/provenance obligations and other consequential rules should be stated precisely enough to be translated into implementation requirements and objective conformance checks.

88. **A post-architecture `Architecture-to-Delivery Layer` is an accepted Engagement objective.** After Parts 00–08, NURA will build a controlled layer that connects architecture to implementation specification, delivery decomposition, acceptance, traceability and automated architecture-conformance verification. This layer is downstream of the Parts and must not replace or silently reinterpret them.

89. **`Implementation Specification Standard` and per-increment `Implementation Specification Pack` are distinct.** The Standard defines the mandatory structure, traceability and evidence expectations for any implementation specification. A Pack is the concrete developer-facing specification/evidence set for one independently acceptable end-to-end increment. NURA should not create one monolithic implementation specification for the entire ERP.

90. **Delivery is decomposed into independently acceptable end-to-end increments.** Increments may reuse technical foundations created earlier, but acceptance of an increment must not depend on future, not-yet-delivered functionality. Each increment must deliver a usable end-to-end business procedure or coherent capability whose acceptance criteria can be satisfied at that stage; later increments add or improve capability rather than retroactively making earlier accepted work incomplete.

91. **`Architecture Control Model` is part of the Architecture-to-Delivery Layer.** It is the formal machine-readable representation of architectural requirements, invariants and constraints needed for automated or assisted conformance checking. It should cover, where applicable, Business Rules, allowed dependencies, lifecycle/state transitions, permissions, ownership/authority, Data Model constraints, API/data contracts, integration boundaries and mandatory audit/provenance requirements. It is a formalized representation of the architecture, not a second independent architecture.

92. **Architecture conformance uses multiple evidence levels.** Verification may combine static code/schema analysis, automated tests, API/integration tests, runtime evidence and business acceptance scenarios. A conformance mechanism must distinguish at least `PASS`, `VIOLATION`, `NOT IMPLEMENTED`, `INSUFFICIENT EVIDENCE`, and `MANUAL / RUNTIME VERIFICATION REQUIRED`; it must not claim that a requirement is proven merely because it cannot detect a violation in source code.

93. **`Architecture Conformance Engine` is a consumer of the Architecture Control Model; AI is optional rather than constitutive.** The conformance mechanism examines submitted implementation artifacts such as code, database schema, APIs, tests, configuration, deployment artifacts and runtime evidence against the governed control model and produces traceable findings. AI may later assist with mapping, investigation, explanation or analysis of unstructured evidence, but it is not the source of architecture truth and is not required for rules that can be verified deterministically.

94. **Deterministic / formal conformance is preferred where the rule can be expressed objectively.** The future Architecture Control Model and Conformance Engine should support deterministic constraint checking, model/state validation, static analysis, automated tests and other non-AI verification mechanisms where suitable. AI-assisted assurance may supplement these mechanisms but must not override a deterministic violation or convert absence of detected defects into proof.

95. **Parts are verification-aware but technology-agnostic.** Parts 00–08 remain human-readable architecture. They should express material rules precisely enough for later formalization, but they must not embed or prematurely select the future Architecture Control Model language, Lean/TLA+/Alloy/Z3, YAML/JSON DSL or another specific conformance technology merely to appear machine-readable.

96. **`ARCHITECTURE_PART_AUTHORING_STANDARD.md` is the controlled Engagement method for Parts 04–08.** The standard governs source-derived extraction, layer boundaries, targeted questioning, formulation of material architectural assertions, stable identifiers where useful, explicit uncertainty/authority, Architecture-to-Delivery Readiness and the final Russian prose/terminology pass. It does not override accepted architecture decisions.

97. **Normative rule, rationale, example and unresolved item must remain distinguishable.** A downstream specification must be able to determine what is required / permitted / prohibited without guessing whether an explanatory example was intended as a mandatory rule. Examples illustrate; they do not silently broaden architecture.

98. **Unresolved authority must remain explicit rather than being converted into false architectural precision.** Institutional policy, System-of-Record capability, retention/security rule or technical fact that lacks adequate authority/evidence remains `TO_CONFIRM`, `AUTHORITATIVE POLICY TO_CONFIRM`, `TECHNICAL CAPABILITY TO_VERIFY`, or another explicit deferred state until the appropriate layer/source resolves it.

99. **Part completion includes Architecture-to-Delivery Readiness, not drafting alone.** Before transition to the next architecture Part, material assertions must pass semantic/cross-Part V&V and a readiness check that a later Requirements Catalogue / Implementation Specification / Acceptance / Conformance artifact can derive its downstream obligation without inventing new business meaning. Exact downstream verification technology remains a later design decision.

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
- Structured durable Research Output records with understandable summaries, provenance/evidence, applicable Project / Calendar Plan / Obligation / Report / repository links, and support for cross-Project lineage where justified; institutional result analytics must not depend solely on AI extraction.
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


## Architecture-to-Delivery Objective

The accepted target delivery chain is:

```text
PARTS 00–08 — human-readable architecture
        ↓
ARCHITECTURE-TO-DELIVERY LAYER
        ├── Requirements & Rules Catalogue
        ├── Traceability Model
        ├── Delivery / Increment Model
        ├── Implementation Specification Standard + per-increment Packs
        ├── Acceptance Scenarios
        ├── Architecture Conformance Rules
        └── Architecture Control Model
                ↓
        Development / Acceptance / Conformance
                ├── deterministic / formal / automated verification where feasible
                ├── runtime / manual evidence where required
                └── optional AI-assisted assurance
```

Working design rule: every material architecture statement should be written so that a later delivery artifact can identify its source, implementation obligation, acceptance method and evidence type without inventing new business meaning. `ARCHITECTURE_PART_AUTHORING_STANDARD.md v1.1` operationalizes this rule for Parts 04–08.

The future `Architecture Control Model` remains subordinate to the approved human-readable architecture and must preserve traceability back to the originating Part / rule / requirement. It should support deterministic/formal verification where feasible and explicit evidence-based outcomes where a requirement cannot be proven statically; AI is an optional assurance aid rather than the authoritative verification kernel.


## Open Issues / Conflicts

Items below are either intentionally unresolved or resolved architecture-normalization items whose source propagation is complete in Parts 00–03. Open downstream modeling / institutional / technical questions remain active only where stated. None is currently classified as a semantic blocker to starting Part 04; if a Part 04 decision depends on unresolved authority or evidence, that claim must remain explicit and unresolved.

### Architecture normalization completed before Part 04

1. **RESOLVED — propagated to Parts 00–03:** Project lifecycle / Setup readiness / Operational Authorization / Operational Restriction semantics.

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

   Remaining downstream detail only:
   - select final UI labels where wording remains implementation-level rather than business-semantic.

   Issue #1 remains resolved at the architectural-concept level. Detailed `Project Type / Scenario → Authorizing Basis Requirement` rule mapping is tracked separately as a modeling/configuration item and does not reopen Issue #1.
2. **RESOLVED — propagated to Parts 00–03:** Application lifecycle is separated from Pre-Award Application Check, external submission, scientific evaluation, Funding Decision and Handover.
3. **RESOLVED — propagated to Parts 00–03:** Research Need has its own lifecycle; downstream Procurement execution is represented through related objects / quantities rather than Research Need lifecycle states. Exact final lifecycle labels and unresolved reverse cardinalities remain Part 05 detail under Issue #17.
4. **RESOLVED — propagated to Parts 00–03:** Procurement Plan semantics are normalized: `Effective Procurement Plan` is current operational truth; `Approved Procurement Plan Version` is a formal immutable snapshot; `Procurement Plan Amendment` is the formal delta; `Consolidated Approved Procurement Plan` is the latest formally approved consolidated representation.
5. **RESOLVED — propagated to Parts 00–03:** Procurement Procedure is not a separate first-class Business Object; target execution is `Procurement Case + Procurement Method-specific rules/workflow`.
6. **RESOLVED — propagated to Parts 00–03:** Goods Acceptance is item/quantity-level, supports multiple actual receivers in one Delivery, and uses derived aggregate outcomes where possible. Advance Delivery Notice is added as a target supplier-control / ERP capability with operational fallback.
7. **RESOLVED — propagated to Parts 00–03:** Project Closure semantics, closure-blocking vs post-closure obligations, Termination, Audit relationship, extension and controlled erroneous-closure reopening are established.
8. **RESOLVED — propagated to Parts 00–03:** Agreement / Amendment preparation is variable/cyclic and action-based; processing, registration/signature facts, legal effect, `Not Concluded`, early-termination event and separate Agreement administrative closeout are established.

### Business clarification required

9. Can one Person hold multiple simultaneous Project Roles within the same Project, and if so how should role assignments be modeled?
10. Define the exact incompatible-role / Separation-of-Duties matrix.
11. **RESOLVED — propagated to Parts 00–03:** one Project may require/link multiple Agreements/official instruments; one Agreement may also cover multiple Projects where the business model requires it. Type-specific constraints remain for Part 05.
12. **RESOLVED — propagated to Parts 00–03:** Agreement/Contract Type is separated from purpose, obligations, conditional effect, Post-Award relevance and Authorizing Basis role; Authorizing Basis Requirement may be composite.
13. Confirm formal Process Owners / process accountability.
14. **RESOLVED — propagated to Parts 00–03:** Calendar Plan is contextual and versioned; Calendar Plan Items / Tasks are hierarchical; administrative Milestones are separate; Deliverable is not a mandatory universal first-class object; Research Output is a durable Business Object; NURA lead/co-executor route semantics and period-level acceptance semantics are established. Exact cardinalities / lineage remain deferred to Parts 04–05 under Issues #33–34.

35. **RESOLVED — propagated to Parts 00–03:** Contract Financial Direction is a separate dimension from Contract Type. Incoming / Authorizing Contracts use the applicable Legal-led route and may exist without Application; Outgoing Contracts originate from Post-Award / Procurement expenditure processes and retain Budget / Commitment / Financial Attribution controls. Non-monetary / Mixed agreements remain supported. Exact `Contract Type × Financial Direction × responsible route / approval profile` data/configuration formalization is deferred to Parts 04–05 where needed.

### Data / financial logic still to formalize

15. Finalize exact Commitment → Actual → Available Budget calculation and double-counting prevention. Established constraint: Unallocated Funding is not Available Budget and must not become spendable until it is allocated and approved.
16. **RESOLVED at architecture-concept level:** Research Need owns only its own lifecycle; downstream procurement progress belongs to related Procurement objects / quantities. Exact Part 05 relationship/cardinality implementation remains under Issue #17.
17. Final cardinalities and temporal constraints for unresolved relationships before Part 05. Scope explicitly includes unresolved reverse Research Need ↔ Procurement Request Item relationships, Procurement Case ↔ Supplier Contract cardinalities/constraints, Agreement closeout-obligation relationships and Delivery / Acceptance / Receiver / Advance Delivery Notice cardinalities.
31. Determine the exact Part 04–05 representation for external research activities known to NURA but not administratively managed by NURA. Established principle: known by NURA ≠ administered by NURA.
32. Formalize the configurable `Project Type / Scenario → Authorizing Basis Requirement` mapping, including applicable composite requirement structures, during rule / data design. The architectural concept is resolved; this is a deferred modeling/configuration detail needed for later Parts.
33. Formalize Calendar Plan / Calendar Plan Version / Calendar Plan Item cardinalities and temporal constraints, including links between principal Project plans and separate co-executor/service-contract plans. Business semantics are resolved under Decisions 68–71.
34. Formalize Research Output lineage and relationships across Project, Calendar Plan Item, Project Obligation, Report, repository/evidence, Research Outcome and maturity/TRL facts. The model must support cross-Project continuation without forcing every Output to belong to exactly one Project.


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

Rewritten and synchronized current working baseline. It preserves the accepted scope/boundaries, Project / Authorizing Basis / Operational Authorization model, Agreement / Contract taxonomy and Financial Direction, Calendar Plan / Planned Result / Research Output distinctions, Project Closure / Agreement Closeout separation, normalized procurement semantics, Systems-of-Record boundaries and the explicit Part 07 Solution Architecture layer.

### Part 01 — Business Analysis

Rewritten and synchronized current working baseline covering business context, stakeholders, Business Requirements, Business Rules and glossary. The final refinement set is propagated, including Legal-led Incoming / Authorizing Agreement timing / `Not Concluded` scope, Incoming vs Outgoing Contract routes, Calendar Plan / Milestone / Planned Result / Research Output semantics, TRL / AI-assisted extraction constraints and Project Closure obligations. Current operating-scale values remain planning estimates; formal Process Ownership, same-Project multi-role rules and institutional policy items remain open where listed below.

### Part 02 — Process Architecture

Rewritten and synchronized current working baseline covering the Process Landscape, process-design principles, Pre-Award / Application, Agreement / Authorizing Basis / Project Initiation, Project Change and Funding, Budget and financial management, Research Team / Project Services, Goods Procurement, Reporting / Research Outputs / Closure / Audit, Research Administration Requests, cross-functional workflow controls, RACI, Process KPI and target end-to-end routes. The Legal-led Incoming / Authorizing Agreement route is explicitly separated from Outgoing Contract preparation, and Closure-Blocking Conditions use Project Obligations / Planned Results with Deliverables only where an applicable authoritative rule uses that term.

### Part 03 — System Analysis

Rewritten and synchronized current working baseline translating Parts 00–02 into system behavior. It covers Functional Requirements, Key Use Cases, System Context, State Models, Validation Rules, Roles & Permissions, Integration Requirements, NFR and derived System Design Principles. It reflects the accepted Project state/readiness/authorization separation, composite Authorizing Basis, action-based Agreement handling, route-specific Incoming / Outgoing Contract behavior, normalized procurement model, Calendar Plan / Research Output semantics, automatic Project Closure, Agreement Closeout, data/history/audit requirements and authoritative external-system boundaries. Exact technology stack, database, Application Architecture and deployment topology remain explicitly deferred to Part 07 Solution Architecture.

A material transition V&V across the current Parts 00–03 found no known cross-Part semantic contradiction that blocks Data Architecture. This is a transition-readiness judgment, not a claim that every later institutional, technical or data-model question is already resolved.

### Part 04 — Data Architecture

**CURRENT PHASE — working draft exists; completion / V&V / Architecture-to-Delivery readiness is in progress. Part 04 is not yet an accepted completed baseline, and Part 05 has not started.**

Part 04 must define the data-architecture view of the established business/system semantics: Data Domains, Master Data, Reference Data, claim-specific Systems of Record, Data Ownership / Stewardship boundaries, provenance / lineage, Data Lifecycle, Data Quality and Data Governance Rules. It must create a coherent basis for Part 05 without prematurely fixing physical database implementation.

Priority carry-forward questions include Issues #15, #17 and #31–34, plus ownership / authority questions when they become decision-relevant.

### Part 05 — Data Model

Not started. Exact conceptual/logical cardinalities, temporal constraints, entity/relationship catalogues and data dictionary follow Part 04.

### Readiness

Parts 00–03 are treated as the synchronized semantic baseline for Part 04. Architecture-normalization issues that previously blocked Part 04 have been propagated into the source Parts. Remaining Open Issues are intentionally carried into Data Architecture, Data Model, institutional verification or technical verification and are not currently semantic blockers to starting Part 04.

The approved master architecture structure is:

00 Scope & Architecture Principles  
01 Business Analysis  
02 Process Architecture  
03 System Analysis  
04 Data Architecture  
05 Data Model  
06 Information Architecture  
07 Solution Architecture  
08 Enterprise Architecture


Transition/control status is governed by the updated `ENGAGEMENT_CONTROL.md`. Canonical Git checkpoint verification remains unavailable in this runtime; no verified checkpoint or canonical write is claimed here.

## Important Cross-Part Dependencies

Parts 04–05 must preserve and explicitly model:

- Application and Project independent identity/history;
- Funding Decision / Award → Project creation versus Project-Type/Scenario-specific `Authorizing Basis Requirement` → satisfaction by one or more authorizing instruments → business `Active` distinction;
- Agreement / Amendment / Funding / Project / Budget independent lifecycles;
- Agreement preparation/action history versus registration/signature facts versus legal effect versus administrative closeout;
- `Not Concluded` Agreement-preparation outcome and causal relationship to pre-active Project `Not Proceeded`;
- Agreement early-termination event with separate reason/basis, effective date, evidence and consequences;
- Agreement closeout obligations / checklist and the possibility that the same underlying obligation has different closure significance for Project versus Agreement;
- Project Closure blockers expressed through Project Obligations / Planned Results, with Deliverable used only where an applicable Programme Rule / Agreement defines it;
- Project business lifecycle versus Setup readiness versus Operational Authorization versus dynamic Operational Restrictions;
- `Project Created` as event, `Not Proceeded` pre-active outcome and controlled reopening of the same Project for the same Award;
- external-grant `signed + registered Agreement recorded in ERP` activation trigger versus retroactive `Effective From`;
- Operational Restriction scope/effective history, affected expenditure-object suspension, causal link to restriction, case-specific exception, mandatory Reason and audit trail;
- suspension as source-object state / progress with derived views rather than a separate register;
- Hard Business Validation versus overrideable Operational Restriction;
- route-specific Legal-led Incoming / Authorizing Agreement Target / Critical escalation thresholds, `Not Concluded` reason and supporting evidence/documents; Outgoing Contract routes do not inherit these controls by default;
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
