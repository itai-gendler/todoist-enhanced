---
kind: primary
routes:
  web: Connected account
steps:
- text: The User drags the filter to a new place in the list
  kind: actor
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::filters
- text: The Product saves the new order of the filters
  kind: product
  entities:
  - entity: filter
    effect: changes
    facts:
    - Order
  actor: user
  contexts:
    web:
      place: web::connected::filters
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/overlays/FilterSheet.tsx
---

# Reorder filters

## Trigger

The User drags a filter to a new place.

## Outcome

The filters are listed in the new order.
