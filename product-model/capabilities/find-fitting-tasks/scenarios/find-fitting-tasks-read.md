---
kind: primary
routes:
  web: Connected account
steps:
- text: The User picks a duration in I have time, for this page or everywhere
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::time
- text: The Product lists the open top-level tasks whose estimate fits the duration
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Estimate
    - Due date
    - Tags
    - Priority
  actor: user
  contexts:
    web:
      place: web::connected::time
references:
- kind: code
  role: implementation
  target: src/components/TimePanel.tsx
- kind: code
  role: implementation
  target: src/domain/fits.ts
---

# Find tasks that fit

## Trigger

The User chooses I have time and picks how long they have.

## Outcome

The tasks that fit are listed by when they are due: overdue, today, tomorrow, this week, no date. The page behind stays as it was, and nothing is remembered after a reload.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
