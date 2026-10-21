---
kind: edge
routes:
  web: Connected account
steps:
- text: Move selected tasks under a parent
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Parent
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Submit the task placement changes
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Parent
    - Project
    - Section
    - Order
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Some task moves are refused
  kind: condition
  entities:
  - entity: task
    effect: reads
    facts:
    - Parent
  contexts:
    web:
      place: web::connected::task
- text: Request restoration of accepted task moves and report failure
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Parent
    - Project
    - Section
    - Order
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Recover a partially refused nesting request

## Trigger

Todoist refuses part of a multi-task nesting request.

## Outcome

The app attempts compensating moves for the accepted part and reports failure; it does not treat a batch as an external atomic transaction.
