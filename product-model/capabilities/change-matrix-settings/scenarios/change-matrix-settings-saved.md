---
kind: primary
routes:
  web: Connected account
steps:
- text: The User changes urgency, importance or inclusion in the matrix settings
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Matrix rules
  actor: user
  contexts:
    web:
      place: web::connected::matrix
- text: The Product saves the matrix settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Matrix rules
  actor: user
  contexts:
    web:
      place: web::connected::matrix
references:
- kind: code
  role: implementation
  target: src/components/EisenhowerDisplayMenu.tsx
- kind: code
  role: implementation
  target: src/domain/eisenhower.ts
---

# Change Eisenhower matrix settings

## Trigger

The User changes the rules of the Eisenhower matrix.

## Outcome

The matrix sorts its quadrants by the new rules: how close a due date counts as urgent, which priorities are important, and whether future and Someday work count.
