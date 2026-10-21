---
kind: primary
result: achieved
routes:
  web: Demo
steps:
- text: Choose Edit estimate
  kind: actor
  actor: visitor
  capability: browse-conflicts
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  contexts:
    web:
      place: web::public::issues
- text: Open the affected task
  kind: product
  actor: visitor
  capability: browse-conflicts
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  contexts:
    web:
      place: web::public::task
- text: Enter a valid task estimate
  kind: actor
  actor: visitor
  capability: edit-task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  contexts:
    web:
      place: web::public::task
- text: Save the task estimate
  kind: product
  actor: visitor
  capability: edit-task
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
  target: src/components/overlays/Issues.tsx
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Correct an estimate in the demo

## Trigger

Things to settle offers Edit estimate.

## Outcome

The task has the chosen valid estimate and its contradictory estimate tag is replaced.
