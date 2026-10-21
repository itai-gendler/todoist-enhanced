---
kind: primary
routes:
  web: Demo
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
  actor: visitor
  contexts:
    web:
      place: web::public::task
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
  actor: visitor
  contexts:
    web:
      place: web::public::task
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

# Resize a scheduled task in the demo

## Trigger

The person resizes a real open calendar task. The visitor is using the disposable demo.

## Outcome

The task gets the chosen time and estimate with a minimum 15-minute length. A new timed placement without an estimate starts from 30 minutes. Changes affect demonstration work only; no request is sent to Todoist.

## Decision points

### Estimate storage

Which storage is selected?

- Tags or an explicitly free account → save estimate tags and keep native duration.
- Eligible native duration mode → update native duration in the local demonstration.
