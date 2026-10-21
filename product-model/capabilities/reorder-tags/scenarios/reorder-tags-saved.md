---
kind: primary
routes:
  web: Connected account
steps:
- text: The User drags the tag to a new place in the catalogue
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::tags
- text: The Product saves the new order of the tags
  kind: product
  entities:
  - entity: tag
    effect: changes
    facts:
    - Order
  actor: user
  contexts:
    web:
      place: web::connected::tags
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/overlays/TagSheet.tsx
---

# Reorder tags

## Trigger

The User drags a tag to a new place.

## Outcome

The tags are listed in the new order.
