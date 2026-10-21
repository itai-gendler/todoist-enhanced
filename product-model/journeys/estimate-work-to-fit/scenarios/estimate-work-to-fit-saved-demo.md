---
kind: primary
result: achieved
routes:
  web: Demo
steps:
- capability: find-fitting-tasks
  kind: actor
  actor: visitor
  text: Choose to estimate the unestimated tasks
  contexts:
    web:
      place: web::public::time
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
- capability: find-fitting-tasks
  kind: product
  actor: visitor
  text: Carry exactly those tasks into the estimate pass
  contexts:
    web:
      place: web::public::estimates
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
- capability: edit-task
  kind: actor
  actor: visitor
  text: Enter estimates for the offered tasks
  contexts:
    web:
      place: web::public::estimates
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
- capability: edit-task
  kind: product
  actor: visitor
  text: Save the valid task estimates
  contexts:
    web:
      place: web::public::estimates
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
references:
- kind: code
  role: implementation
  target: src/components/TimePanel.tsx
- kind: code
  role: implementation
  target: src/components/overlays/Unestimated.tsx
---

# Estimate work so it can fit in the demo

## Trigger

I have time reports tasks without estimates. The person follows the estimate action, using tag storage.

## Outcome

The carried selection receives the saved estimates and can be considered in subsequent fitting results.
