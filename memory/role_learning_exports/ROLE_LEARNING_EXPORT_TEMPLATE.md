# Role Learning Export — ARCHITECT

```yaml
export_id:
created_at:
target_role_id: architect
source_engagement_id: ENG-NURA-ERP-001
source_parent_release:
source_parent_revision:
exported_by: RF_OWNER_CURRENT_HUMAN
candidate_count:
```

## Export Preconditions

- [ ] Every included candidate is `APPROVED_FOR_ROLE_REVIEW`.
- [ ] `approved_by` and `approved_at` are recorded for every candidate.
- [ ] Required confidentiality/transfer permission is satisfied.
- [ ] Raw identifying/sensitive evidence remains Engagement-side.
- [ ] Transferable content is de-identified or uses safe opaque references.
- [ ] Export does not claim clean-role promotion or release approval.

## Candidates

For each candidate include:

```yaml
candidate_id:
status: APPROVED_FOR_ROLE_REVIEW
approved_by:
approved_at:
proposed_transferable_learning:
recognition_cues:
applicability:
limits:
confidence:
evidence_summary_or_opaque_refs:
affected_existing_role_knowledge_or_behavior:
expected_behavioral_impact:
privacy_provenance_state:
```

## Role Updater disposition

To be completed from the Role Updater result:

```yaml
disposition: NO_ROLE_CHANGE | REQUEST_MORE_EVIDENCE | ROLE_CHANGE_PROPOSAL
role_updater_evidence_ref:
recorded_at:
notes:
```
