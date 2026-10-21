---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses their own reaction on a comment
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
- text: The Product removes the User’s reaction from the comment
  kind: product
  entities:
  - entity: comment
    effect: changes
    facts:
    - Reactions
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

# Remove reaction

## Trigger

The User chooses their own reaction on a comment.

## Outcome

The User’s reaction is gone from the comment; the reactions of others remain.
