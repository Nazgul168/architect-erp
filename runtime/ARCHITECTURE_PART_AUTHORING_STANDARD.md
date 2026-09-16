# ARCHITECTURE_PART_AUTHORING_STANDARD.md

- **STANDARD_VERSION:** `1.1`
- **STATUS:** `ACTIVE — ENGAGEMENT-CONTROLLED AUTHORING STANDARD`
- **ENGAGEMENT_ID:** `ENG-NURA-ERP-001`
- **EFFECTIVE_DATE:** `2026-09-16`
- **APPLIES_TO:** `Parts 04–08 and any material revision of Parts 00–03`

## 1. Purpose

This standard defines how NURA ERP Architecture Parts are authored so that they remain clear human-readable architecture while also becoming reliable upstream sources for the later `Architecture-to-Delivery Layer`.

The Parts must support future derivation of:

- Requirements & Rules Catalogue;
- Traceability Model;
- Delivery / Increment Model;
- Implementation Specification Standard and per-increment Packs;
- Acceptance Scenarios;
- Architecture Conformance Rules;
- machine-readable Architecture Control Model;
- deterministic / automated conformance checks and, where useful, optional AI-assisted assurance.

The standard does **not** require the Parts themselves to contain the future DSL, executable control model, implementation specifications, test cases or code-level checks.

## 2. Authority and scope

This is an Engagement-specific controlled authoring standard. It governs the method used to write NURA ERP Architecture Parts but does not override:

1. applicable authoritative NURA / NU / legal / institutional sources;
2. accepted architecture decisions in current Parts and `ENGAGEMENT_MEMORY.md`;
3. higher ARCHITECT governing sources.

`ENGAGEMENT_MEMORY.md` remains the controlled source for accepted Engagement architecture decisions. `ENGAGEMENT_CONTROL.md` remains authoritative for phase / completion-gate state.

If this standard conflicts with an accepted architecture decision, the conflict must be surfaced and reconciled; the standard must not silently change business meaning.

## 3. Core authoring principle

> Human-readable architecture remains the source of architectural meaning. Material architectural assertions must be precise enough that downstream delivery artifacts can derive implementation obligations, acceptance criteria and conformance checks without inventing new business meaning.

This means the Parts are **verification-aware but implementation-neutral at their own architectural layer**.

## 4. Layer discipline

Each Part must solve the decisions that belong to its layer and must not prematurely absorb work belonging to a later layer.

For the current architecture structure:

- **Part 04 — Data Architecture:** Data Domains, data classes, authority / Systems of Record, ownership/stewardship, provenance/lineage, lifecycle/temporal semantics, quality/reconciliation and governance. Do not turn it into the detailed logical ER model or choose physical persistence technology.
- **Part 05 — Data Model:** conceptual/logical entities, relationships, cardinalities, attributes, identifiers, temporal structures and dictionaries. Do not choose database products or physical deployment merely to close a modeling question.
- **Part 06 — Information Architecture:** taxonomy, metadata, document classification, naming, multilingual information model, search/navigation semantics. Do not absorb application/runtime architecture.
- **Part 07 — Solution Architecture:** application/module boundaries, stack/persistence approach, integrations, deployment, security/operations, capacity and other solution-level technical choices justified by requirements.
- **Part 08 — Enterprise Architecture:** capability/application/data landscape, target-state relationships, enterprise integration context and implementation roadmap; do not rewrite detailed solution design already owned by Part 07.

A downstream Part may refine an earlier statement only when the earlier layer intentionally left that detail open. It must not silently contradict an established upstream invariant.

## 5. Required authoring workflow

For substantial work on a Part, use the following sequence proportionally:

1. **Source-derived extraction** — derive the architecture from current Parts, Engagement Memory and authoritative evidence before asking the user to redesign it from scratch.
2. **Layer-boundary pass** — identify what belongs in the current Part and what must remain for a later Part.
3. **Gap / authority analysis** — separate professional decisions ARCHITECT can make from user-only facts, institutional authority decisions and unresolved technical evidence.
4. **Targeted questions only** — ask the user only where missing user-only knowledge or high-impact ambiguity materially changes the result.
5. **Architecture synthesis** — make professional recommendations where evidence is sufficient; preserve unresolved authority explicitly where it is not.
6. **Semantic V&V** — verify fit to Parts 00–03 / current upstream Parts, Engagement Memory, open issues and accepted distinctions.
7. **Architecture-to-Delivery Readiness Pass** — test whether material statements can later be translated into requirements / acceptance / conformance without semantic invention.
8. **Language editing / Russian prose pass** — align the final text with the established Parts style without changing architecture semantics.

## 6. How material architectural rules are written

Where a statement materially constrains implementation, acceptance or future architecture, write it so that the reader can determine, where applicable:

- **subject / object / fact** — what the rule concerns;
- **condition / applicability** — when it applies;
- **required / permitted / prohibited behavior** — what must, may or must not happen;
- **authority** — who or which system is authoritative for the claim / decision;
- **temporal effect** — when the rule becomes applicable or effective;
- **exception / override semantics** — whether and how an exception is allowed;
- **required evidence / provenance** — what must be retained to explain or verify the result;
- **unresolved authority** — what remains `TO_CONFIRM` rather than being invented.

Not every rule requires every field. Use the smallest sufficient formulation.

### Example

Weak narrative statement:

> Accounting Actual comes from 1C.

Architecture-ready statement:

> `Accounting Actual` is an authoritative accounting fact from 1C. NURA ERP must not create or correct it as its own authoritative fact. ERP may store and use a replicated representation with required source identity / provenance; authoritative correction is performed in the applicable System of Record.

The Part should contain the second kind of architectural statement. The later Requirement ID, implementation obligation, acceptance scenario and machine-readable conformance rule are created downstream rather than embedded here.

## 7. Stable identifiers and traceability

Use stable identifiers for material principles, rules, requirements or controlled classifications **where they improve future traceability**.

Rules:

- do not assign IDs to every paragraph merely for appearance;
- an ID must continue to identify the same semantic rule across editorial rewrites;
- material semantic replacement should be recorded as a supersession/revision, not hidden behind the same identifier;
- later Architecture-to-Delivery artifacts should reference the originating Part / section / rule ID.

Existing identifiers such as `BR-*`, `FR-*`, `PP-*`, `DA-*` or analogous Part-specific IDs may continue when they serve this purpose.

## 8. Rule, rationale and example must remain distinct

Do not let explanatory prose silently broaden a normative rule.

Where useful, distinguish:

- **Rule / architectural constraint** — normative meaning;
- **Rationale** — why the architecture chose it;
- **Example** — illustrates application but does not redefine the rule;
- **Open / deferred item** — not yet decided or not owned by this layer.

A downstream specification must not have to decide whether a sentence was a mandatory rule or merely an example.

## 9. Uncertainty and authority discipline

Do not convert missing evidence into false precision.

Use explicit states such as:

- `TO_CONFIRM`;
- `AUTHORITATIVE POLICY TO_CONFIRM`;
- `TECHNICAL CAPABILITY TO_VERIFY`;
- `DEFERRED TO PART 05/06/07/08`;
- other controlled unresolved markers where appropriate.

An unresolved institutional policy, System-of-Record capability, retention rule or platform constraint must remain unresolved until the appropriate evidence/authority is available.

Professional recommendation is allowed where the decision belongs to architecture and evidence is sufficient, but it must remain distinguishable from verified institutional fact.

## 10. Verification-aware, technology-neutral writing

The Parts should make future verification possible without prematurely selecting how verification will be implemented.

Therefore:

- formulate constraints precisely enough for later deterministic / formal / automated or evidence-based checking;
- do not embed Lean, TLA+, Alloy, Z3, YAML/JSON DSL or another formal technology into the Parts merely because it may later be useful;
- do not assume AI is necessary for conformance verification;
- when a requirement is inherently runtime/manual/contextual, preserve that fact rather than pretending it is statically provable;
- future Architecture Control Model technology is a downstream decision.

## 11. Language and editorial style

Parts 00–03 establish the editorial baseline.

Apply the following style:

- Russian is the primary language of explanation and professional prose;
- retain accepted English terms of the architecture model where translation would reduce precision or break cross-Part consistency, e.g. `Project`, `Business Object`, `Agreement`, `Commitment`, `System of Record`, `Data Correction`, `Operational Authorization`;
- avoid unnecessary English phrases and literal calques when natural Russian is clearer;
- headings should normally name the subject, rule or design principle rather than pose conversational questions;
- keep terminology consistent across Parts; do not introduce a synonym merely for stylistic variety;
- write for a non-technical business reader to understand the meaning while preserving enough precision for analysts, architects and developers;
- do not sacrifice architecture semantics for stylistic simplification.

A dedicated Russian prose pass is required before a Part is treated as final.

## 12. Target-reader fit

Each Part has a primary reader, but must remain usable by adjacent roles.

- Part 04: Data Architect / Solution Architect / System Analyst / integration-data engineers, with business owners/stewards able to understand authority and responsibility.
- Part 05: Data Modeler / backend and data engineers / integration and migration teams / QA.
- Part 06: Information/UX Architect / BA/Product / frontend/search/document teams.
- Part 07: Solution Architect / Tech Lead / developers / DBA / integration / DevOps / Security / vendor implementation team.
- Part 08: Enterprise Architect / IT leadership / programme leadership / integration/application governance.

The Part should not require its primary reader to reverse-engineer essential semantics from another layer, while avoiding duplication of details owned elsewhere.

## 13. Architecture-to-Delivery Readiness Check

Before a Part is considered semantically complete, review each material architectural assertion and ask:

1. Is its meaning clear enough that a later Requirements Catalogue can reference it without reinterpretation?
2. Can the required / permitted / prohibited behavior be identified where relevant?
3. Is authority / System of Record explicit where it materially matters?
4. Are lifecycle / temporal conditions explicit where they materially matter?
5. Are exceptions / overrides distinguished from hard invariants where applicable?
6. Are required provenance / audit / evidence obligations explicit where applicable?
7. Are unresolved authoritative inputs visibly unresolved?
8. Did the Part avoid choosing implementation detail that belongs to a later layer?
9. Could a future Implementation Specification derive a requirement without inventing new business meaning?
10. Could a future acceptance/conformance method determine what evidence would be relevant, even if the exact verification technology is not yet chosen?

Failure of a material applicable criterion means the Part needs revision before the next architecture phase is treated as ready.

## 14. Part completion gate

A Part is ready for phase transition only after the applicable combination of:

- semantic coverage review;
- cross-Part consistency review;
- open/deferred issue classification;
- Architecture-to-Delivery Readiness Check;
- Russian prose / terminology pass;
- Engagement Memory / Control synchronization where material decisions changed;
- required source/revision verification under the current Engagement Control rules.

Completion of drafting alone is not sufficient.

## 15. Learning Candidate / approval-trail check at Part completion

Before a Part is treated as ready for handoff or phase transition, perform a proportional learning check in addition to semantic V&V:

- identify whether significant work produced new transferable learning or materially changed an existing Learning Candidate;
- update `LEARNING_CANDIDATES.md` where applicable;
- if a candidate led to creation or material change of an Engagement artifact, record the artifact change and why it was needed;
- record explicit user approval / hold / rejection when it occurs;
- do not infer approval from silence, continued work, or acceptance of unrelated architecture content;
- preserve `NOT_REVIEWED` where no explicit user disposition exists.

This check exists so that Parts written in different chats preserve a continuous learning and approval trail without relying on conversational memory. It does not require a Learning Candidate for every Part edit or NURA-specific architecture decision.

## 16. Handoff package for a new Part chat/runtime

A chat/runtime asked to write a subsequent Part should receive, at minimum, the current runtime-visible versions of:

1. relevant completed upstream Parts;
2. `ENGAGEMENT_MEMORY.md`;
3. `ENGAGEMENT_CONTROL.md`;
4. `00_ENGAGEMENT_MANIFEST.md`;
5. `ARCHITECTURE_PART_AUTHORING_STANDARD.md`;
6. `ARCHITECT_PROFESSIONAL_BACKGROUND.md`;
7. `LEARNING_CANDIDATES.md` when learning review / transferability context is relevant.

The new runtime must not treat the authoring standard as authority to overwrite accepted business architecture. It is a method for producing the next Part consistently.

## 17. Anti-patterns

Do not:

- write attractive narrative that cannot later be translated into an implementation obligation where one is intended;
- turn every sentence into a pseudo-formal requirement;
- mix rationale/examples into the normative rule so that obligation becomes ambiguous;
- resolve `TO_CONFIRM` items by model invention;
- design Part 05 while claiming to write Part 04, or Part 07 while claiming to write Part 05;
- optimize the architecture around a vendor platform before architecture fit has been assessed;
- embed a future Architecture Control Model implementation into the human-readable Parts;
- assume that AI output is proof of conformance;
- claim a Part is complete without the applicable semantic, cross-Part and downstream-readiness checks.

## 18. Design intent

The standard exists to preserve a deliberate separation:

```text
Human-readable Architecture
        ↓ preserves meaning
Architecture-to-Delivery Layer
        ↓ formalizes / traces / specifies
Implementation + Acceptance + Conformance
```

The architecture should be strong enough to govern downstream work, while the downstream control system should not become a competing source of business meaning.
