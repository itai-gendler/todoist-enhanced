---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor drags the tag to a new place in the catalogue
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::tags
- text: The Product saves the new order of the tags
  kind: product
  entities:
  - entity: tag
    effect: changes
    facts:
    - Order
  actor: visitor
  contexts:
    web:
      place: web::public::tags
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/overlays/TagSheet.tsx
---

# Reorder tags in the demo

## Trigger

The Visitor drags a tag to a new place. The visitor is using the disposable demo.

## Outcome

The tags are listed in the new order. Changes affect demonstration work only; no request is sent to Todoist.
