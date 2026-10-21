---
appliesTo:
- type: entity
  id: project
  effect: removes
references:
- kind: code
  role: implementation
  target: src/components/ProjectMenu.tsx
permits:
- actors:
  - user
  - visitor
  when:
  - fact: Inbox
    is: false
---

# Users and demo visitors remove projects

The product offers removal with the confirmation and recovery behavior of the corresponding capability. External deletion is requested through Todoist.
