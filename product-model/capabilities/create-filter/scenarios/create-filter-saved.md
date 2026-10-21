---
kind: primary
routes:
  web: Connected account
steps:
- text: The User enters a name and a query for a new filter
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
- text: The Product creates the filter
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

# Create filter

## Trigger

The User creates a filter.

## Outcome

The filter is saved with its name and query, and Todoist evaluates the query each time the filter is opened.
