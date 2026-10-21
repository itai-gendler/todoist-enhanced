---
kind: primary
result: achieved
routes:
  web: Connected account
steps:
- capability: find-fitting-tasks
  kind: actor
  actor: user
  text: Choose to estimate the unestimated tasks
  contexts:
    web:
      place: web::connected::time
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
- capability: find-fitting-tasks
  kind: product
  actor: user
  text: Carry exactly those tasks into the estimate pass
  contexts:
    web:
      place: web::connected::estimates
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
- capability: edit-task
  kind: actor
  actor: user
  text: Enter estimates for the offered tasks
  contexts:
    web:
      place: web::connected::estimates
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
- capability: edit-task
  kind: product
  actor: user
  text: Save the valid task estimates
  contexts:
    web:
      place: web::connected::estimates
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

# Estimate work so it can fit

## Trigger

I have time reports tasks without estimates. The person follows the estimate action, using tag storage.

## Outcome

The carried selection receives the saved estimates and can be considered in subsequent fitting results.
