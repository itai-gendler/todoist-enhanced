---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Keep on the task
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::someday
- text: The Product records today as the day the task was kept, on this device
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Kept on
  actor: user
  contexts:
    web:
      place: web::connected::someday
references:
- kind: code
  role: implementation
  target: src/store/dust.ts
- kind: code
  role: implementation
  target: src/domain/views.ts
---

# Keep in Someday

## Trigger

The User chooses Keep on a task in Gathering dust.

## Outcome

The task leaves Gathering dust and stays in Someday; it comes back only after another full delay. The Keep is remembered on this device only.
