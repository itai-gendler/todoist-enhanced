---
kind: alternate
routes:
  web: Connected account
steps:
- text: Choose the task label to remove
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Tags
  actor: user
  contexts:
    web:
      place: web::connected::issues
- text: Remove the chosen task tag
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Tags
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::issues
references:
- kind: code
  role: implementation
  target: src/components/BulkBar.tsx
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Remove a contradictory planning tag

## Trigger

The person chooses to remove a week or quick label from a conflict.

## Outcome

Only the chosen planning label is removed; the date and other task facts remain.
