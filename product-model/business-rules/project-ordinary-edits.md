---
appliesTo:
- type: entity
  id: project
  effect: changes
  facts:
  - Name
  - Description
  - Colour
  - Favourite
  - Workspace
  - Parent
  - Order
  - Default view
references:
- kind: code
  role: implementation
  target: src/components/ProjectMenu.tsx
- kind: code
  role: implementation
  target: src/store/structure.ts
permits:
- actors:
  - user
  - visitor
  when:
  - fact: Inbox
    is: false
---

# Users and demo visitors change non-Inbox project fields

Project editing and structural actions are offered for ordinary projects. The Inbox remains the fixed capture project.
