---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Mark as read, or Mark all as read, on the notifications
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
- text: The Product marks the notifications read
  kind: product
  entities:
  - entity: notification
    effect: changes
    facts:
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

# Mark notification read

## Trigger

The User chooses Mark as read on a notification, or Mark all as read.

## Outcome

The chosen notification, or every unread one, shows as read.
