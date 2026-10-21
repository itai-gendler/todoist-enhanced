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
- text: Request and verify the computed task estimate as native minutes
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Estimate
    - Tags
    - Native duration
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

# Save review estimates as native minutes

## Trigger

Native duration storage is selected, and the account reports duration storage available. The person saves the valid missing-estimate drafts in a review.

## Outcome

The app requests the intended native minutes, removes estimate tags and verifies the external result. Unavailable verification remains pending; a dropped or refused duration follows the estimate recovery path.
