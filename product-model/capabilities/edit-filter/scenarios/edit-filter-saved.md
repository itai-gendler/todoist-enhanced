---
kind: primary
routes:
  web: Connected account
steps:
- text: The User changes the filter’s name, query, description or colour
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
- text: The Product saves the changed fields of the filter
  kind: product
  entities:
  - entity: filter
    effect: changes
    facts:
    - Name
    - Query
    - Description
    - Colour
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

# Edit filter

## Trigger

The User edits a filter.

## Outcome

The changed fields are saved; the fields that were not touched keep their values.
