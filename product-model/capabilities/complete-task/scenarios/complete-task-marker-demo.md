---
kind: validation
routes:
  web: Demo
steps:
- kind: actor
  actor: visitor
  text: The Visitor opens the task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Completable
  contexts: &id001
    web:
      place: web::public::task
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
  actor: visitor
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

# Read a task with completion disabled in the demo

## Trigger

The title has the product’s uncompletable marker.

## Outcome

The task remains readable without a completion action.
