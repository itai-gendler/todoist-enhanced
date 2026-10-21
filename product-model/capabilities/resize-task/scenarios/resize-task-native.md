---
kind: primary
routes:
  web: Connected account
steps:
- text: Resize the task’s scheduled length
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Estimate
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Request and verify the computed task estimate as native minutes
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Estimate
    - Tags
    - Native duration
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/CalendarSurface.tsx
- kind: code
  role: implementation
  target: src/store/calendar.ts
- kind: code
  role: implementation
  target: src/domain/calendar.ts
---

# Resize a native estimate

## Trigger

Native duration storage is selected, and the account reports duration storage available. The person resizes a real open calendar task.

## Outcome

The app requests the intended native minutes, removes estimate tags and verifies the external result. Unavailable verification remains pending; a dropped or refused duration follows the estimate recovery path.
