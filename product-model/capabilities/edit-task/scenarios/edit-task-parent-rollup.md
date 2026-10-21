---
kind: alternate
routes:
  web: Connected account
steps:
- text: A fully estimated task branch has a different parent estimate
  kind: condition
  entities:
  - entity: task
    effect: reads
    facts:
    - Estimate
    - Parent
  unattended: true
  contexts:
    web:
      place: web::connected::task
- text: Write the computed parent task estimate
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
- kind: code
  role: implementation
  target: src/components/Checklist.tsx
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/domain/estimates.ts
- kind: code
  role: implementation
  target: src/store/estimate-safety.ts
- kind: code
  role: implementation
  target: src/components/overlays/Unestimated.tsx
---

# Keep a fully estimated parent equal to its children

## Trigger

All open subtasks have estimates and the app is ready with no pending writes or drag operation.

## Outcome

In tag storage, the app writes their recursive sum to the parent as its estimate label. Incomplete child coverage keeps the parent’s own estimate, or shows a partial computed sum when none exists.

## Decision points

### Estimate storage

Which storage is selected?

- Tags → update estimate labels and retain native calendar duration.
- Native duration with eligible account status → request native minutes, remove estimate labels and verify the returned value; refusal follows the estimate recovery path.
