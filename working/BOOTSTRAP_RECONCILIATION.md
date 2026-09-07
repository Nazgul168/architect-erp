# Bootstrap Reconciliation — NURA ERP Architecture

Status: NOT STARTED

## Objective

Reconstruct how the current NURA ERP Architecture was produced and convert raw historical material into reliable Engagement Memory without losing rationale or preserving obsolete states as current truth.

## A. Inventory

Create an inventory of:
- current architecture Parts / deliverables;
- older versions where materially relevant;
- QA dialogue files;
- institutional/source documents;
- known decision records or specifications.

## B. Chronology / lineage

Reconstruct:
- which document/Part was being worked on;
- what question/problem triggered each major change;
- candidate alternatives considered;
- user acceptance/rejection/correction;
- later revisions that superseded earlier decisions.

Do not assume "later = correct" unless acceptance/current-state evidence supports it.

## C. Extract candidate Engagement knowledge

Classify extracted items as:

- CURRENT / ESTABLISHED
- SUPERSEDED
- REJECTED
- UNRESOLVED
- CONFLICT
- SOURCE_ONLY
- WORKING / HYPOTHESIS

Extract at minimum:
- definitions;
- architecture principles;
- decisions + rationale;
- rejected alternatives;
- confirmed assumptions;
- material constraints;
- unresolved questions;
- contradictions and resolutions;
- architecture/solution evolution;
- local lessons;
- possible transferable lessons (pointer only).

## D. Reconcile against current outputs

For each material item:
- locate supporting QA/source evidence;
- compare with current architecture documents;
- identify whether the current deliverable already implements it;
- identify unresolved discrepancies;
- avoid silently merging contradictory states.

## E. Populate canonical Engagement Memory

Only CURRENT / ESTABLISHED knowledge is written as current truth.

SUPERSEDED / REJECTED items are retained with causal links where they explain current architecture.

UNRESOLVED / CONFLICT items remain explicit.

Raw QA remains unchanged in `context/chat_qa/`.

## F. Bootstrap completion criteria

Bootstrap is complete when:
- current scope is explicit;
- glossary is coherent;
- material decisions have rationale/provenance;
- current Parts can be traced to major decisions;
- obsolete decisions are marked;
- open issues are explicit;
- Engagement Memory reflects the current state closely enough to continue work without rereading the full dialogue archive for ordinary tasks.
