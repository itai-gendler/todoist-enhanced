---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor changes urgency, importance or inclusion in the matrix settings
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Matrix rules
  actor: visitor
  contexts:
    web:
      place: web::public::matrix
- text: The Product saves the matrix settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Matrix rules
  actor: visitor
  contexts:
    web:
      place: web::public::matrix
references:
- kind: code
  role: implementation
  target: src/components/EisenhowerDisplayMenu.tsx
- kind: code
  role: implementation
  target: src/domain/eisenhower.ts
---

# Change Eisenhower matrix settings in the demo

## Trigger

The Visitor changes the rules of the Eisenhower matrix. The visitor is using the disposable demo.

## Outcome

The matrix sorts its quadrants by the new rules: how close a due date counts as urgent, which priorities are important, and whether future and Someday work count. Changes affect demonstration work only; no request is sent to Todoist.
