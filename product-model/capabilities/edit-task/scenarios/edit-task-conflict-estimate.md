---
kind: alternate
routes:
  web: Connected account
steps:
- text: Choose the intended task estimate
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
      place: web::connected::issues
- text: Save the chosen task estimate
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
      place: web::connected::issues
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

# Choose one intended estimate

## Trigger

Things to settle offers competing or invalid estimates.

## Outcome

The selected valid estimate is saved in the configured storage, or the estimate is cleared when that is chosen.

## Decision points

### Estimate storage

Which storage is selected?

- Tags → update estimate labels and retain native calendar duration.
- Native duration with eligible account status → request native minutes, remove estimate labels and verify the returned value; refusal follows the estimate recovery path.
