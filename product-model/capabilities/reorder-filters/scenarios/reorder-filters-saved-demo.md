---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor drags the filter to a new place in the list
  kind: actor
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::filters
- text: The Product saves the new order of the filters
  kind: product
  entities:
  - entity: filter
    effect: changes
    facts:
    - Order
  actor: visitor
  contexts:
    web:
      place: web::public::filters
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/overlays/FilterSheet.tsx
---

# Reorder filters in the demo

## Trigger

The Visitor drags a filter to a new place. The visitor is using the disposable demo.

## Outcome

The filters are listed in the new order. Changes affect demonstration work only; no request is sent to Todoist.
