---
kind: alternate
routes:
  web: Connected account
steps:
- text: Undo the task deletion
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
- text: Create replacement tasks and comments
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
  - entity: comment
    effect: creates
    facts:
    - Text
    - Posted on
    - Author
    - Attachment
    - Reactions
    with: task
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/store/ui.ts
- kind: code
  role: implementation
  target: src/store/tasks.ts
- kind: code
  role: implementation
  target: src/store/tasks-move.ts
---

# Restore a deleted branch as copies

## Trigger

The deletion has already been sent and its undo is still in the session history.

## Outcome

The app creates replacement tasks with their subtask relationships and available comments and attachments, and tells the person they were restored as copies.

## Edge cases

- Before a pending deletion is sent, undo restores the same tasks.
- Undoing bulk completion reopens one-off tasks; recurring tasks have already advanced.
