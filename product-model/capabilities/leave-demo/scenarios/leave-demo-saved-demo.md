---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Leave demo
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::account
- text: The Product discards the demonstration account and its work
  kind: product
  entities:
  - entity: account
    effect: removes
  actor: visitor
  contexts:
    web:
      place: web::public::account
references:
- kind: code
  role: implementation
  target: src/store/sync.ts
---

# Leave demo in the demo

## Trigger

The Visitor chooses Leave demo.

## Outcome

The demonstration work is discarded and Connect is shown again.
