---
appliesTo:
- type: entity
  id: filter
  effect: changes
  facts:
  - Favourite
  - Order
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
permits:
- actors:
  - user
  - visitor
---

# Users and demo visitors change ordinary filter fields

The product offers these ordinary edits in connected work and the disposable demo. Connected writes remain subject to Todoist’s responses.
