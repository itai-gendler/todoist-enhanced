---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Accept on the invitation notification
  kind: actor
  entities:
  - entity: notification
    effect: reads
    facts:
    - Message
  actor: user
  contexts:
    web:
      place: web::connected::issues
- text: The Product sends the acceptance and shows the notification as accepted and read
  kind: product
  entities:
  - entity: notification
    effect: changes
    facts:
    - Invitation answer
    - Read
  actor: user
  contexts:
    web:
      place: web::connected::issues
references:
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
- kind: code
  role: implementation
  target: src/domain/notifications.ts
- kind: code
  role: implementation
  target: src/store/collab.ts
---

# Accept invitation

## Trigger

A notification carries an unanswered project invitation that can be answered.

## Outcome

The acceptance is sent to Todoist, and the notification shows the invitation as accepted and is marked read. If Todoist refuses, the Accept and Decline choices come back with a message.
