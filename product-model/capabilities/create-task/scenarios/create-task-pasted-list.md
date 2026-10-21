---
kind: alternate
routes:
  web: Connected account
steps:
- text: Confirm creation from pasted task lines
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Create open tasks from the independently interpreted lines
  kind: product
  entities:
  - entity: task
    effect: creates
    facts:
    - Title
    - Description
    - Priority
    - Due date
    - Repeat rule
    - Deadline
    - Tags
    - Estimate
    - Native duration
    - Project
    - Section
    - Parent
    - Assignee
    - Order
    - Created on
    - Completed on
    - Kept on
    - Completable
    to: Open
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/Composer.tsx
- kind: code
  role: implementation
  target: src/domain/shorthand.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/domain/dnd.ts
---

# Create independent tasks from pasted lines

## Trigger

The person pastes a list into the composer and confirms creation.

## Outcome

Each line is parsed independently; composer field selections are not copied into the lines. Declining the prompt preserves the paste as text.
