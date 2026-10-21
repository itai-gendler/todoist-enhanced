---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor enters a name and a query for a new filter
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
- text: The Product creates the filter in the demo
  kind: product
  entities:
  - entity: filter
    effect: creates
    facts:
    - Name
    - Query
    - Description
    - Colour
    - Favourite
    - Order
    - Frozen
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

# Create filter in the demo

## Trigger

The Visitor creates a filter. The visitor is using the disposable demo.

## Outcome

The filter is saved in the demo with its name and query; only the supplied example queries return matches. Changes affect demonstration work only; no request is sent to Todoist.
