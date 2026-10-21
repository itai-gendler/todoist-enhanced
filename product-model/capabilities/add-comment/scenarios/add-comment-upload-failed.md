---
kind: edge
routes:
  web: Connected account
steps:
- text: Choose a file for the comment
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
- text: The upload cannot be completed
  kind: condition
  entities: []
  contexts:
    web:
      place: web::connected::task
- text: Keep the comment draft available
  kind: product
  entities:
  - entity: comment
    effect: reads
    facts:
    - Text
    - Attachment
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

# Keep the draft after an upload fails

## Trigger

A selected file cannot be uploaded to Todoist.

## Outcome

The app reports the failure and does not claim an attached file. A refused comment submission restores its text and attachment draft.
