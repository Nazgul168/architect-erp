# NURA ERP Architecture — Task-Specific ARCHITECT Engagement

Canonical private Engagement repository for `ENG-NURA-ERP-001`.

This repository contains NURA ERP-specific state, evidence, architecture outputs, learning candidates and runtime/control records. It is separate from the clean ARCHITECT repository.

## RF v4.5 relationship

```text
clean ROLE
Nazgul168/architect
        ↓ parent of
task-specific ROLE / Engagement
Nazgul168/nura-erp-architecture
```

The Engagement is an **ACTIVE RF-managed task-specific ARCHITECT system**.

Current operational parent binding:

- parent role: `architect`;
- parent repository: `Nazgul168/architect`;
- bound release: `ARCH-0.2.1-RC5`;
- bound revision: `6f843575253c35312d24d03bd6fe9560045b8e95`;
- binding origin: existing operational baseline imported into RF;
- parent update policy: `CONTROLLED_UPDATE`;
- runtime synchronization evidence: tracked separately and currently `UNKNOWN` / not verified.

This RF migration does not block normal NURA ERP work. Future clean ARCHITECT releases are handled later as separate controlled updates through Role Updater.

See `00_ENGAGEMENT_MANIFEST.md` and `runtime/RUNTIME_DEPLOYMENT_RECORD.md`.

## Canonical Engagement artifacts

- `00_ENGAGEMENT_MANIFEST.md` — task-specific ROLE identity, parent binding, authority boundaries and canonical paths;
- `memory/ENGAGEMENT_MEMORY.md` — established Engagement knowledge;
- `memory/LEARNING_CANDIDATES.md` — transferable-learning candidates using the RF lifecycle;
- `memory/ROLE_PERFORMANCE_LOG.md` — feedback about ARCHITECT behavior/performance only;
- `memory/ROLE_CHANGE_LOG.md` — parent-role adoption/change lineage;
- `memory/role_learning_exports/` — exports approved for Role Updater review;
- `runtime/ARCHITECT_PROFESSIONAL_BACKGROUND.md` — Engagement runtime professional profile;
- `runtime/ENGAGEMENT_CONTROL.md` — phase/checkpoint/consolidation control;
- `runtime/RUNTIME_DEPLOYMENT_RECORD.md` — ChatGPT runtime binding/sync evidence.

## Learning boundary

ARCHITECT may recommend learning for clean-role review but may not self-approve or self-promote it.

Only the current human owner may explicitly set a candidate to `APPROVED_FOR_ROLE_REVIEW` in the current single-user deployment.

Only approved-for-review candidates may be exported to Role Updater. Role Updater then independently returns one of:

- `NO_ROLE_CHANGE`;
- `REQUEST_MORE_EVIDENCE`;
- `ROLE_CHANGE_PROPOSAL`.

No Engagement learning automatically changes the clean ARCHITECT ROLE.

## Engagement isolation

NURA-specific truth, raw evidence, outputs and decisions remain in this repository. Parent clean-role updates must not overwrite Engagement Memory, sources, outputs, learning/feedback records, update policy or update authority.
