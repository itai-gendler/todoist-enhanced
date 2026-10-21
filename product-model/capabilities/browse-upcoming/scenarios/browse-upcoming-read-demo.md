---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens Upcoming
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::upcoming
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
  actor: visitor
  contexts:
    web:
      place: web::public::upcoming
references:
- kind: code
  role: implementation
  target: src/views/UpcomingView.tsx
- kind: code
  role: implementation
  target: src/domain/projectOccurrences.ts
---

# Browse Upcoming in the demo

## Trigger

The Visitor opens Upcoming. The visitor is using the disposable demo.

## Outcome

Future-dated work is listed day by day and can be extended to later periods. Forecast occurrences of repeating tasks are shown read-only and are never saved as tasks.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
