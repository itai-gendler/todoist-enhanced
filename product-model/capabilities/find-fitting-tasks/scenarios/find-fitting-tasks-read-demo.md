---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor picks a duration in I have time, for this page or everywhere
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: visitor
  contexts:
    web:
      place: web::public::time
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
  actor: visitor
  contexts:
    web:
      place: web::public::time
references:
- kind: code
  role: implementation
  target: src/components/TimePanel.tsx
- kind: code
  role: implementation
  target: src/domain/fits.ts
---

# Find tasks that fit in the demo

## Trigger

The Visitor chooses I have time and picks how long they have. The visitor is using the disposable demo.

## Outcome

The tasks that fit are listed by when they are due: overdue, today, tomorrow, this week, no date. The page behind stays as it was, and nothing is remembered after a reload.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
