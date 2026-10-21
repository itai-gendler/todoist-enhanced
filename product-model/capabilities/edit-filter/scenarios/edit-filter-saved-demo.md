---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor changes the filter’s name, query, description or colour
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

# Edit filter in the demo

## Trigger

The Visitor edits a filter. The visitor is using the disposable demo.

## Outcome

The changed fields are saved; the fields that were not touched keep their values. Changes affect demonstration work only; no request is sent to Todoist.
