# Role Learning Exports

This directory contains exports from `ENG-NURA-ERP-001` for Role Updater evaluation.

Only candidates whose current state is `APPROVED_FOR_ROLE_REVIEW` may be exported.

Exports must:

- target clean ROLE `architect`;
- preserve candidate IDs and human approval metadata;
- identify the current/legacy bound parent release/revision truthfully;
- contain de-identified transferable summaries rather than raw client/project evidence;
- retain opaque evidence references where needed;
- never claim that export equals promotion.

After successful handoff to Role Updater, the source candidate may be set to `EXPORTED_TO_ROLE_UPDATER`.

Use `_ROLE_LEARNING_EXPORT_TEMPLATE.md`.
