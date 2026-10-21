---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens the Eisenhower matrix
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::matrix
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
  actor: visitor
  contexts:
    web:
      place: web::public::matrix
references:
- kind: code
  role: implementation
  target: src/views/EisenhowerView.tsx
- kind: code
  role: implementation
  target: src/domain/eisenhower.ts
---

# Browse Eisenhower matrix in the demo

## Trigger

The Visitor opens the Eisenhower matrix. The visitor is using the disposable demo.

## Outcome

Each task sits in one quadrant: urgent and important, important but not urgent, urgent but not important, or neither. Urgency comes from the due date and importance from priority, as the matrix settings define them; future and Someday work appear only when those settings include them.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
