---
kind: primary
routes:
  web: Connected account
steps:
- text: The User opens the Eisenhower matrix
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::matrix
- text: The Product sorts the open tasks into four quadrants by the matrix settings
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Priority
    - Tags
    - Estimate
  - entity: settings
    effect: reads
    facts:
    - Matrix rules
  actor: user
  contexts:
    web:
      place: web::connected::matrix
references:
- kind: code
  role: implementation
  target: src/views/EisenhowerView.tsx
- kind: code
  role: implementation
  target: src/domain/eisenhower.ts
---

# Browse Eisenhower matrix

## Trigger

The User opens the Eisenhower matrix.

## Outcome

Each task sits in one quadrant: urgent and important, important but not urgent, urgent but not important, or neither. Urgency comes from the due date and importance from priority, as the matrix settings define them; future and Someday work appear only when those settings include them.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
