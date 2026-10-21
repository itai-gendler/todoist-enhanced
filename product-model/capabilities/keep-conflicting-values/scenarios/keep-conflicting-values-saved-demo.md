---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Keep both, or Keep the parent estimate
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: visitor
  contexts:
    web:
      place: web::public::issues
- text: The Product leaves the task as it is and sets the conflict aside
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Tags
    - Estimate
  actor: visitor
  contexts:
    web:
      place: web::public::issues
references:
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
- kind: code
  role: implementation
  target: src/domain/conflicts.ts
---

# Keep conflicting values in the demo

## Trigger

Things to settle lists a conflict that offers Keep both or Keep the parent estimate. The visitor is using the disposable demo.

## Outcome

Nothing is written to the task, and the conflict leaves the list for now.
