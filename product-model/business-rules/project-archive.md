---
appliesTo:
- type: entity
  id: project
  effect: changes
  to: Archived
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

# Users and demo visitors archive non-Inbox projects

Archive is offered on ordinary projects; the Inbox stays the fixed capture project. An archived project is not deleted, and bringing it back is left to Todoist.
