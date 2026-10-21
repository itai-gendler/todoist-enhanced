---
appliesTo:
- type: entity
  id: project
  effect: changes
  facts:
  - Shared with me
references:
- kind: code
  role: implementation
  target: src/domain/sharing.ts
permits:
- actors:
  - user
  when:
  - fact: Shared with me
    is: true
---

# Active non-creators leave projects shared with them

The Leave action needs an active current membership and an active different creator. Without those returned facts the product does not assume the project can be left.
