---
kind: primary
routes:
  web: Connected account
steps:
- text: The User opens Upcoming
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::upcoming
- text: The Product lists future-dated tasks and forecasts of supported repeating tasks
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Repeat rule
    - Estimate
    - Priority
    - Project
  actor: user
  contexts:
    web:
      place: web::connected::upcoming
references:
- kind: code
  role: implementation
  target: src/views/UpcomingView.tsx
- kind: code
  role: implementation
  target: src/domain/projectOccurrences.ts
---

# Browse Upcoming

## Trigger

The User opens Upcoming.

## Outcome

Future-dated work is listed day by day and can be extended to later periods. Forecast occurrences of repeating tasks are shown read-only and are never saved as tasks.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
