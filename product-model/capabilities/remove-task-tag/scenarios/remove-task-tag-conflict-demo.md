---
kind: alternate
routes:
  web: Demo
steps:
- text: Choose the task label to remove
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Tags
  actor: visitor
  contexts:
    web:
      place: web::public::issues
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
  actor: visitor
  contexts:
    web:
      place: web::public::issues
references:
- kind: code
  role: implementation
  target: src/components/BulkBar.tsx
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Remove a contradictory planning tag in the demo

## Trigger

The person chooses to remove a week or quick label from a conflict. The visitor is using the disposable demo.

## Outcome

Only the chosen planning label is removed; the date and other task facts remain. Changes affect demonstration work only; no request is sent to Todoist.
