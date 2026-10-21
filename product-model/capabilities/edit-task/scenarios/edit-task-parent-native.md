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
- text: Request and verify the computed task estimate as native minutes
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
    - Native duration
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

# Maintain the parent’s native estimate

## Trigger

Native duration storage is selected, and the account reports duration storage available. All open subtasks are estimated and the parent sum needs updating while the app is ready.

## Outcome

The app requests the intended native minutes, removes estimate tags and verifies the external result. Unavailable verification remains pending; a dropped or refused duration follows the estimate recovery path.
