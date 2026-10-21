---
kind: primary
routes:
  web: Connected account
steps:
- text: The User marks the notification unread
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
- text: The Product marks the notification unread
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

# Mark notification unread

## Trigger

The User marks a read notification unread.

## Outcome

The notification shows as unread again.
