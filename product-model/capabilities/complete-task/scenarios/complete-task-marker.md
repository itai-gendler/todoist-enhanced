---
kind: validation
routes:
  web: Connected account
steps:
- kind: actor
  actor: user
  text: The User opens the task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Completable
  contexts: &id001
    web:
      place: web::connected::task
- kind: condition
  text: The title has the product’s uncompletable marker.
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Completable
  contexts: *id001
- kind: product
  actor: user
  text: The task remains readable without a completion action.
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Completable
  contexts: *id001
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Read a task with completion disabled

## Trigger

The title has the product’s uncompletable marker.

## Outcome

The task remains readable without a completion action.
