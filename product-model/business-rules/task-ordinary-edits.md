---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Title
  - Description
  - Priority
  - Due date
  - Repeat rule
  - Deadline
  - Tags
  - Estimate
  - Project
  - Section
  - Parent
  - Order
  - Kept on
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/hooks/useParentEstimates.ts
permits:
- actors:
  - user
  - visitor
- unattended: true
---

# Users and demo visitors change ordinary task fields

These fields are editable in connected work and in the disposable demo. The product also maintains parent estimates automatically when its rollup conditions hold.
