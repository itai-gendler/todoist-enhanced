---
appliesTo:
- type: entity
  id: filter
  effect: changes
  facts:
  - Name
  - Query
  - Description
  - Colour
references:
- kind: code
  role: implementation
  target: src/components/overlays/FilterSheet.tsx
permits:
- actors:
  - user
  - visitor
  when:
  - fact: Frozen
    is: false
---

# Users edit fields only on unfrozen filters

A filter whose frozen status is reported by Todoist has its editing form disabled. This governs the form fields rather than promising server-wide filter permissions.
