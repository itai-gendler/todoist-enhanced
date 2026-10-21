---
kind: primary
routes:
  web: Connected account
steps:
- text: The User edits the text of the comment
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
- text: The Product saves the new comment text
  kind: product
  entities:
  - entity: comment
    effect: changes
    facts:
    - Text
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

# Edit comment

## Trigger

The User edits a comment they posted.

## Outcome

The comment shows its revised text; a comment holding only a file may be left without text.
