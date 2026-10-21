---
kind: alternate
routes:
  web: Demo
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
      place: web::public::task
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
      place: web::public::task
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

# Keep a fully estimated parent equal to its children in the demo

## Trigger

All open subtasks have estimates and the app is ready with no pending writes or drag operation. The visitor is using the disposable demo.

## Outcome

In tag storage, the app writes their recursive sum to the parent as its estimate label. Incomplete child coverage keeps the parent’s own estimate, or shows a partial computed sum when none exists. Changes affect demonstration work only; no request is sent to Todoist.

The demonstration follows its selected estimate representation locally.
