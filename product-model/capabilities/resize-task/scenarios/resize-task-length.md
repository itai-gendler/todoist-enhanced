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
- text: Save the task time and estimate in tags
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
    - Estimate
    - Tags
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

# Resize a scheduled task

## Trigger

The person resizes a real open calendar task.

## Outcome

The task gets the chosen time and estimate with a minimum 15-minute length. A new timed placement without an estimate starts from 30 minutes.

## Decision points

### Estimate storage

Which storage is selected?

- Tags or an explicitly free account → save estimate tags and keep native duration.
- Eligible native duration mode → request and verify native duration through the same estimate-write process.
