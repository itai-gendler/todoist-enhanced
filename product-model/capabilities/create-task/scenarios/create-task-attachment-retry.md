---
kind: edge
routes:
  web: Connected account
steps:
- text: Save a task with files
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
- text: Create the task before attaching its uploaded files
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
- text: An uploaded file cannot be attached
  kind: condition
  entities: []
  contexts:
    web:
      place: web::connected::task
- text: Retry the remaining attachment
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Create the remaining comment on the existing task
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  - entity: comment
    effect: creates
    facts:
    - Text
    - Posted on
    - Author
    - Attachment
    - Reactions
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

# Retry an attachment on the task already created

## Trigger

Files were uploaded but attaching one as a comment fails after task creation.

## Outcome

The composer retains the created task identity and unsent files for retry; it does not intentionally create the same task again.
