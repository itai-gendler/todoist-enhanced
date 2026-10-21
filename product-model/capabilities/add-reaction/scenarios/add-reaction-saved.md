---
kind: primary
routes:
  web: Connected account
steps:
- text: The User picks an emoji reaction on a comment
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
- text: The Product adds the User’s reaction to the comment
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

# Add reaction

## Trigger

The User picks an emoji on a comment in a task’s discussion.

## Outcome

The comment shows the User’s reaction with the others. The request goes to Todoist directly rather than through the queue of task changes.
