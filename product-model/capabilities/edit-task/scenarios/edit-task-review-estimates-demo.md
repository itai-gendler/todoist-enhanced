---
kind: alternate
routes:
  web: Demo
steps:
- text: Fill estimates for the tasks in the review
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
      place: web::public::review
- text: Save the entered task estimates
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
      place: web::public::review
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

# Fill missing estimates during review in the demo

## Trigger

The review reaches its missing-estimates step. The visitor is using the disposable demo.

## Outcome

Draft estimates remain in place until Save; the saved values apply to the still-open tasks in one batch. Changes affect demonstration work only; no request is sent to Todoist.

The demonstration follows its selected estimate representation locally.
