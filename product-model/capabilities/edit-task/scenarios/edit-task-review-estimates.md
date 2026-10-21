---
kind: alternate
routes:
  web: Connected account
steps:
- text: Fill estimates for the tasks in the review
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  actor: user
  contexts:
    web:
      place: web::connected::review
- text: Save the entered task estimates
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
  actor: user
  contexts:
    web:
      place: web::connected::review
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

# Fill missing estimates during review

## Trigger

The review reaches its missing-estimates step.

## Outcome

Draft estimates remain in place until Save; the saved values apply to the still-open tasks in one batch.

## Decision points

### Estimate storage

Which storage is selected?

- Tags → update estimate labels and retain native calendar duration.
- Native duration with eligible account status → request native minutes, remove estimate labels and verify the returned value; refusal follows the estimate recovery path.
