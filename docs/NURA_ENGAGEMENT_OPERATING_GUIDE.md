\
# NURA ERP — ENGAGEMENT CONTROL OPERATING GUIDE

This is the user-facing operating guide for maintaining the NURA ERP Engagement control artifacts.

**Do not add this guide to ChatGPT Project Sources unless deliberately desired.**

Runtime-critical rules belong in:

- `00_ENGAGEMENT_MANIFEST.md`;
- `runtime/ENGAGEMENT_CONTROL.md`.

---

## 1. Canonical Control Stack

```text
nura-erp-architecture/
├── 00_ENGAGEMENT_MANIFEST.md
├── memory/
│   ├── ENGAGEMENT_MEMORY.md
│   └── LEARNING_CANDIDATES.md
├── runtime/
│   ├── ARCHITECT_PROFESSIONAL_BACKGROUND.md
│   └── ENGAGEMENT_CONTROL.md
├── context/
├── working/
└── outputs/
```

Functions:

- `ENGAGEMENT_MEMORY.md` = established NURA ERP / architecture knowledge;
- `LEARNING_CANDIDATES.md` = transferable learning candidates, not permanent EKB;
- `ARCHITECT_PROFESSIONAL_BACKGROUND.md` = runtime professional profile;
- `ENGAGEMENT_CONTROL.md` = phase, consolidation, checkpoint, delta-reporting and transition-readiness control;
- `00_ENGAGEMENT_MANIFEST.md` = binds roles, files and authority boundaries.

---

## 2. What "Last System Update" Means

Do **not** interpret “last system update” as the latest modification time of any one system file.

The reporting baseline is the latest **verified coherent System State Checkpoint**.

Example:

`CP-NURA-001`

A Control-only edit, formatting edit or partial persistence cycle does not create a new checkpoint.

---

## 3. Current Bootstrap State

Do not call the currently edited Manifest / Control / Candidates `CP-NURA-001` yet.

There is already unreviewed material delta after `ENGAGEMENT_MEMORY.md v1.3`.

Current expected state:

```text
SYSTEM_STATE_CHECKPOINT_STATUS = BOOTSTRAP_PENDING
UNCHECKPOINTED_MATERIAL_DELTA = YES
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = YES
CONSOLIDATION_STATE = DUE
NEXT_PHASE_GATE = NOT_READY
```

First:

1. run the catch-up Learning & Change Review;
2. update Engagement Memory;
3. update Learning Candidates where applicable;
4. assess Professional Background implications;
5. assess permanent ARCHITECT implications;
6. complete Memory consistency verification;
7. finalize required Control / Manifest state;
8. only then prepare `CP-NURA-001`.

If the exact pre-delta bundle revision cannot be verified, do not invent it.

Use `ENGAGEMENT_MEMORY.md v1.3` as the conservative semantic bootstrap baseline and keep exact bundle precision `UNVERIFIED`.

---

## 4. Three Different State Questions

### A. Is there uncheckpointed material delta?

`UNCHECKPOINTED_MATERIAL_DELTA = YES`

means something material happened after the current reporting baseline and must appear in a future delta review.

It does **not** automatically mean consolidation is already due.

### B. Is there significant accepted work that remains unconsolidated?

`UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = YES`

means semantic significance threshold has been reached and this accepted state has not yet been consolidated.

Therefore:

```text
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = YES
⇒
UNCHECKPOINTED_MATERIAL_DELTA = YES
AND
CONSOLIDATION_STATE = DUE
```

### C. Is consolidation due?

`CONSOLIDATION_STATE = DUE`

means ARCHITECT should initiate the applicable review at the next reasonable stopping point.

It may become DUE because of:

- semantic significance;
- volume proxy;
- degradation symptoms.

---

## 5. After Successful Consolidation but Before Checkpoint Finalization

This intermediate state is valid:

```text
UNCHECKPOINTED_MATERIAL_DELTA = YES
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = NO
CONSOLIDATION_STATE = CURRENT
NEXT_PHASE_GATE = NOT_READY
```

Meaning:

- the significant work has been reviewed and consolidated;
- the coherent system-state update has not yet completed checkpoint finalization;
- phase readiness may still be blocked.

Do not treat these states as contradictory.

---

## 6. Delta Reporting

Learning & Change Review should report:

> what materially changed after the reporting baseline

not the whole history of NURA ERP.

Expected structure:

```text
REVIEW_FROM_CHECKPOINT
REVIEW_FROM_GIT_REF
REVIEW_TO

1. New accepted decisions
2. Changed / corrected / superseded decisions
3. Issues resolved / reopened / deferred
4. New cross-Part implications
5. Engagement Memory delta
6. Learning Candidates delta
7. Professional Background assessment
8. Permanent ARCHITECT assessment
9. Required system-state updates
10. Checkpoint readiness
```

If an old decision is unchanged, it is background, not a new report item.

---

## 7. Consolidation Pressure Sensor

The sensor is **not** a real context-window meter.

It uses observable proxies:

- approximate dialogue volume;
- semantic / decision density;
- context-degradation symptoms.

### Initial NURA volume calibration

- GREEN < ~12k substantive words;
- YELLOW ~12k–20k;
- ORANGE ~20k–25k;
- RED > ~30k.

These numbers are provisional.

Semantic signal is primary.

Degradation symptoms are a lagging emergency backstop.

---

## 8. What ARCHITECT Should Signal to You

At YELLOW, briefly:

> Consolidation pressure is YELLOW. After the current question I should assess whether a checkpoint is approaching.

When consolidation becomes DUE:

> Material accepted state has accumulated. I should consolidate it before the next substantial block.

You should not need to tell ARCHITECT “remember to update Memory.”

---

## 9. System State Bundle

Checkpoint bundle:

```text
00_ENGAGEMENT_MANIFEST.md
runtime/ENGAGEMENT_CONTROL.md
memory/ENGAGEMENT_MEMORY.md
memory/LEARNING_CANDIDATES.md
runtime/ARCHITECT_PROFESSIONAL_BACKGROUND.md
+ Runtime Deployment Record pointer where available
```

Parts 00–03 are **not** bundle members.

But keep their exact revisions as checkpoint dependency evidence.

---

## 10. Git Checkpoint — A → B → C → D Finalization

Do not put a checkpoint commit hash inside the same Control revision that creates that commit.

Use a logical checkpoint ID and a later finalization record.

### Phase A — Prepare

Example:

```text
PENDING_CHECKPOINT_ID = CP-NURA-001
PENDING_CHECKPOINT_GIT_REF = refs/tags/nura-checkpoint/CP-NURA-001
CHECKPOINT_FINALIZATION_STATE = PREPARED
```

Then:

1. save the coherent checkpoint-candidate files;
2. Commit them;
3. Push the commit if desired as part of the normal persistence workflow.

Do **not** yet call CP-NURA-001 VERIFIED.

### Phase B — Create and Verify the Checkpoint Tag

After the checkpoint candidate commit exists, create an annotated tag.

Command-line example from inside the repository:

```bash
git tag -a nura-checkpoint/CP-NURA-001 -m "System State Checkpoint CP-NURA-001"
git push origin nura-checkpoint/CP-NURA-001
```

Resolve and record the intended local checkpoint commit:

```bash
git rev-parse nura-checkpoint/CP-NURA-001^{commit}
```

For an **annotated tag**, verify the remote **peeled target commit**, not merely the existence of the tag object:

```bash
git ls-remote --tags origin 'refs/tags/nura-checkpoint/CP-NURA-001^{}'
```

The commit hash returned for the remote peeled target must equal the intended checkpoint commit from:

```bash
git rev-parse nura-checkpoint/CP-NURA-001^{commit}
```

You may also confirm the tag object itself exists remotely:

```bash
git ls-remote --tags origin refs/tags/nura-checkpoint/CP-NURA-001
```

but this second command alone is **not sufficient** to prove that the annotated tag resolves to the intended checkpoint commit.

Then verify required Project Sources / runtime-visible checkpoint-bundle files against the intended checkpoint state.

If all Phase B evidence passes:

```text
CHECKPOINT_FINALIZATION_STATE = EXTERNAL_VERIFICATION_PASSED
```

The checkpoint is **still not VERIFIED**.

The previous verified checkpoint / reporting baseline remains active until Phase C succeeds.

### Phase C — Canonicalize VERIFIED State

After Phase B reaches `EXTERNAL_VERIFICATION_PASSED`, update the **current** Control in a later administrative commit with:

```text
LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID = CP-NURA-001
LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_GIT_REF = refs/tags/nura-checkpoint/CP-NURA-001
LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_COMMIT = <resolved commit hash>
SYSTEM_STATE_CHECKPOINT_STATUS = VERIFIED
CHECKPOINT_FINALIZATION_STATE = VERIFIED
```

This avoids self-reference because the hash points to the earlier checkpoint candidate commit.

The later finalization-record commit is not itself the CP-NURA-001 checkpoint snapshot.

**Only after this Phase C administrative Control commit succeeds in the canonical repository is `CP-NURA-001` operationally and canonically VERIFIED.**

At that point:

```text
LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID = CP-NURA-001
SYSTEM_STATE_CHECKPOINT_STATUS = VERIFIED
CHECKPOINT_FINALIZATION_STATE = VERIFIED
REPORTING_WINDOW_START = CP-NURA-001
```

and the reporting / sensor counters may reset.

If the Phase C commit fails:

```text
CHECKPOINT_FINALIZATION_STATE = EXTERNAL_VERIFICATION_PASSED
```

or `FAILED` if a truthful failure state can be persisted.

Do not:

- call the checkpoint VERIFIED;
- advance the previous verified baseline;
- reset counters;
- create a new checkpoint.

Repair/retry Phase C.

### Phase D — Synchronize the Current Control to ChatGPT Project Sources

After the successful Phase C administrative Control commit is canonically persisted, the checkpoint is already canonically `VERIFIED`.

Then:

1. replace the `ENGAGEMENT_CONTROL.md` Project Source with the new post-finalization version;
2. verify that the active runtime sees the finalized state (`CP-NURA-001`, `VERIFIED`, current reporting-window baseline) rather than the older `BOOTSTRAP_PENDING / PREPARED` state;
3. only then continue normal work in a new chat/runtime session.

This synchronization:

- does not create `CP-NURA-002`;
- does not change `CP-NURA-001`;
- does not reset counters or the reporting window again;
- is only synchronization of the **current control state** after checkpoint finalization.

---

## 11. Tag Protection / Integrity

A normal Git tag can technically be moved if repository permissions allow it.

Preferred GitHub setup:

- protect / restrict updates to the tag namespace `nura-checkpoint/*` using repository rules where available.

Even with a tag, record the resolved commit hash in the later finalization record.

If:

```text
current tag target ≠ recorded checkpoint commit hash
```

treat it as:

`CHECKPOINT_INTEGRITY_FAILURE`

and do not trust the tag until reconciled.

---

## 12. If Checkpoint Finalization Fails

If any step required before canonical checkpoint verification fails:

- checkpoint candidate commit not created;
- tag not created;
- tag push fails;
- remote annotated tag peeled target does not resolve to the intended commit;
- checkpoint-bundle runtime/source verification fails;
- integrity verification fails;
- Phase C canonical administrative Control commit fails;

then:

Use the latest truthful state, for example:

```text
CHECKPOINT_FINALIZATION_STATE = PREPARED
```

or:

```text
CHECKPOINT_FINALIZATION_STATE = EXTERNAL_VERIFICATION_PASSED
```

or `PENDING / FAILED`, depending on where failure occurred.

Do not:

- advance the last verified checkpoint;
- reset the reporting baseline;
- reset delta/sensor counters;
- call the checkpoint VERIFIED.

This failure class is:

`CHECKPOINT_FINALIZATION_FAILURE`

If the checkpoint itself is already verified but the later post-finalization `ENGAGEMENT_CONTROL.md` cannot be synchronized to Project Sources, treat that separately as:

`CURRENT_CONTROL_RUNTIME_SYNC_FAILURE`

Do not create a new checkpoint. Fix the Project Source synchronization before continuing material work in that stale runtime.

---

## 13. When a Checkpoint Really Resets the Window

Only after successful **Phase C canonicalization of the VERIFIED checkpoint state**:

```text
CURRENT_SYSTEM_UPDATE = CLEAN
UNCHECKPOINTED_MATERIAL_DELTA = NO
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = NO
CONSOLIDATION_STATE = CURRENT
REPORTING_WINDOW_START = CP-NURA-00X
```

Then volume / decision / issue counters start again from zero.

An individual file edit does not reset them.

---

## 14. Before a Material Phase Transition

Examples:

- reconciliation → full rewrite;
- rewrite → cross-Part V&V;
- V&V → Part 04 Data Architecture;
- Part 04 → Part 05 Data Model;
- architecture → implementation handoff.

Before the transition:

1. `CONSOLIDATION_STATE` must be `CURRENT`;
2. required checkpoint/system-state finalization must be complete;
3. transition exit criteria must pass;
4. required canonical and runtime-visible revisions must be identifiable;
5. a separate verification pass must be recorded;
6. only then may `NEXT_PHASE_GATE = READY`.

You do not manually approve every ordinary gate merely because you are ARCHITECT Maintainer.

---

## 15. When the New Phase Actually Starts

As one of the first control actions:

1. old `NEXT_PHASE` becomes new `CURRENT_PHASE`;
2. define the next material `NEXT_PHASE`;
3. set the new gate to `NOT_READY`;
4. define appropriate exit criteria.

Do not continue materially while Control still shows the previous phase as current.

---

## 16. Role Boundaries

- NURA business decision → applicable Engagement / business authority;
- confidentiality / transfer permission → Engagement Confidentiality Authority;
- permanent ARCHITECT governance, EKB promotion and governing-behavior change → ARCHITECT Maintainer.

Ordinary checkpoint or phase-gate verification does not create authority over another domain.

---

## 17. Behavioral Failures to Watch For

- old unchanged decisions reported as new → `DELTA_REPORTING_FAILURE`;
- checkpoint advanced because Control was merely edited → `CHECKPOINT_ADVANCEMENT_FAILURE`;
- unreviewed pre-bootstrap delta disappeared → `BOOTSTRAP_BASELINE_FAILURE`;
- `UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = YES` while consolidation remains CURRENT → `STATE_SEMANTICS_FAILURE`;
- ARCHITECT claims actual context occupancy from word estimates → `SENSOR_FRAMING_FAILURE`;
- checkpoint loses active Part revisions → `DEPENDENCY_EVIDENCE_FAILURE`;
- checkpoint declared VERIFIED before Phase B evidence passes **or before the Phase C canonical finalization commit succeeds** → `CHECKPOINT_FINALIZATION_FAILURE`;
- remote annotated tag exists but its peeled commit was not verified against the intended checkpoint commit → `CHECKPOINT_FINALIZATION_FAILURE`;
- post-finalization Control commit is not synchronized to the active runtime / Project Sources → `CURRENT_CONTROL_RUNTIME_SYNC_FAILURE`;
- tag resolves to a commit different from recorded checkpoint hash → `CHECKPOINT_INTEGRITY_FAILURE`.

Repeated materially similar failures should become Slow-Loop evidence rather than triggering ad hoc permanent-ARCHITECT edits.

---

## 18. Current Live Behavioral Test

After these files are installed and visible to the runtime:

do **not** remind ARCHITECT to:

- check Control;
- update Memory;
- run the sensor;
- perform a delta review.

Continue naturally.

Expected current behavior:

```text
BOOTSTRAP_PENDING
→ ARCHITECT notices consolidation is DUE
→ catch-up delta review from v1.3 conservative baseline
→ updated Memory / Candidates / assessments
→ Phase A checkpoint candidate
→ Phase B external evidence passes
→ EXTERNAL_VERIFICATION_PASSED, still not VERIFIED
→ Phase C canonicalizes VERIFIED state and resets the reporting window
→ Phase D synchronizes current verified Control to runtime
→ phase gate verification
→ rewrite begins only when READY
```

After CP-NURA-001, the next meaningful test is:

```text
ordinary work inside same phase
→ material delta accumulates
→ ARCHITECT independently raises consolidation pressure
→ sets DUE when threshold is reached
→ performs delta-only review
→ establishes CP-NURA-002
```
