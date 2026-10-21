---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens the list of filters
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
- text: The Product lists the saved filters with their queries and match counts
  kind: product
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
    - Query
    - Description
    - Colour
    - Favourite
    - Order
    - Frozen
  - entity: task
    effect: reads
    facts:
    - Title
    - Due date
    - Tags
    - Priority
    - Estimate
    - Completed on
  actor: visitor
  contexts:
    web:
      place: web::public::filters
references:
- kind: code
  role: implementation
  target: src/views/FiltersView.tsx
- kind: code
  role: implementation
  target: src/hooks/useFilterResult.ts
---

# Browse filters in the demo

## Trigger

The Visitor opens Filters. The visitor is using the disposable demo.

## Outcome

Every saved filter is listed with its name, query and favourite status, and with its number of matches where it is known.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
