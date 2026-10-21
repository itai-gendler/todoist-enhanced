---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Keep both, or Keep the parent estimate
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::issues
- text: The Product leaves the task as it is and sets the conflict aside
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Tags
    - Estimate
  actor: user
  contexts:
    web:
      place: web::connected::issues
references:
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
- kind: code
  role: implementation
  target: src/domain/conflicts.ts
---

# Keep conflicting values

## Trigger

Things to settle lists a conflict that offers Keep both or Keep the parent estimate.

## Outcome

Nothing is written to the task, and the conflict leaves the list for now.
