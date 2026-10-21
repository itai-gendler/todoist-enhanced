---
kind: primary
routes:
  web: Connected account
steps:
- text: The User writes a comment, attaches a file, or both
  kind: actor
  entities:
  - entity: comment
    effect: reads
    facts:
    - Text
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: The Product posts the comment on the task
  kind: product
  entities:
  - entity: comment
    effect: creates
    facts:
    - Text
    - Posted on
    - Author
    - Attachment
    - Reactions
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/CommentThread.tsx
- kind: code
  role: implementation
  target: src/store/tasks.ts
---

# Add comment

## Trigger

The User writes in the discussion of an open task.

## Outcome

The comment appears in the task’s discussion with its text, its file, or both.
