---
appliesTo:
- type: entity
  id: task
  effect: removes
references:
- kind: code
  role: implementation
  target: src/store/tasks.ts
permits:
- actors:
  - user
  - visitor
---

# Users and demo visitors remove tasks

The product offers removal with the confirmation and recovery behavior of the corresponding capability. External deletion is requested through Todoist.
