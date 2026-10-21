---
kind: primary
result: achieved
routes:
  web: Connected account
steps:
- text: Choose Edit estimate
  kind: actor
  actor: user
  capability: browse-conflicts
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  contexts:
    web:
      place: web::connected::issues
- text: Open the affected task
  kind: product
  actor: user
  capability: browse-conflicts
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  contexts:
    web:
      place: web::connected::task
- text: Enter a valid task estimate
  kind: actor
  actor: user
  capability: edit-task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  contexts:
    web:
      place: web::connected::task
- text: Save the task estimate
  kind: product
  actor: user
  capability: edit-task
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
  target: src/components/overlays/Issues.tsx
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Correct an estimate

## Trigger

Things to settle offers Edit estimate.

## Outcome

The task has the chosen valid estimate and its contradictory estimate tag is replaced.
