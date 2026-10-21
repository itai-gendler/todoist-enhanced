---
kind: edge
routes:
  web: Connected account
steps:
- text: Change the comment reaction
  kind: actor
  entities:
  - entity: comment
    effect: reads
    facts:
    - Reactions
  actor: user
  contexts:
    web:
      place: web::connected::task
- text: Try the comment reaction change
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
- text: The external request fails
  kind: condition
  entities: []
  contexts:
    web:
      place: web::connected::task
- text: Restore the comment reactions
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

# Restore reactions after a failed request

## Trigger

The direct reaction request is refused or cannot reach Todoist.

## Outcome

The previous reaction set is restored and the person sees an error; this request is not queued like task edits.
