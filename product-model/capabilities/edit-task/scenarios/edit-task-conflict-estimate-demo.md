---
kind: alternate
routes:
  web: Demo
steps:
- text: Choose the intended task estimate
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
  actor: visitor
  contexts:
    web:
      place: web::public::issues
- text: Save the chosen task estimate
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
  actor: visitor
  contexts:
    web:
      place: web::public::issues
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

# Choose one intended estimate in the demo

## Trigger

Things to settle offers competing or invalid estimates. The visitor is using the disposable demo.

## Outcome

The selected valid estimate is saved in the configured storage, or the estimate is cleared when that is chosen. Changes affect demonstration work only; no request is sent to Todoist.

The demonstration follows its selected estimate representation locally.
