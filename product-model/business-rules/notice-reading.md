---
appliesTo:
- type: entity
  id: notification
  effect: changes
  facts:
  - Read
references:
- kind: code
  role: implementation
  target: src/store/collab.ts
permits:
- actors:
  - user
---

# Connected users change notification read status

A connected person marks one or all of their returned notices read, or marks a selected notice unread.
