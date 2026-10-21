---
kind: primary
routes:
  web: Connected account
steps:
- text: The User confirms deleting the filter
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
- text: The Product deletes the filter and leaves the tasks it matched untouched
  kind: product
  entities:
  - entity: filter
    effect: removes
  - entity: task
    effect: reads
    facts:
    - Title
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

# Delete filter

## Trigger

The User chooses Delete on a filter and confirms.

## Outcome

The filter is gone from the list of filters; the tasks it matched remain.
