---
appliesTo:
- type: entity
  id: filter
  effect: removes
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
permits:
- actors:
  - user
  - visitor
---

# Users and demo visitors remove filters

The product offers removal with the confirmation and recovery behavior of the corresponding capability. External deletion is requested through Todoist.
