---
kind: primary
routes:
  web: Connected account
steps:
- text: The User opens the notifications from Todoist
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
- text: The Product lists the notifications newest first
  kind: product
  entities:
  - entity: notification
    effect: reads
    facts:
    - Message
    - Sender
    - Subject
    - Received on
    - Read
    - Invitation answer
    - Answer available
  actor: user
  contexts:
    web:
      place: web::connected::issues
references:
- kind: code
  role: implementation
  target: src/domain/notifications.ts
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
---

# Browse notifications

## Trigger

The User opens the notices from Todoist in Things to settle.

## Outcome

Notifications are listed newest first, with sender, subject and time where Todoist supplies them; a kind the app does not recognize still reads as a plain description.
