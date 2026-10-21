---
kind: primary
routes:
  web: Connected account
steps:
- text: The User confirms deleting the comment
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
- text: The Product deletes the comment
  kind: product
  entities:
  - entity: comment
    effect: removes
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

# Delete comment

## Trigger

The User chooses Delete on a comment and confirms.

## Outcome

The comment leaves the discussion; the confirmation says this cannot be undone.
