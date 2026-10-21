---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor confirms deleting the filter
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
- text: The Product deletes the filter and leaves the tasks it matched untouched
  kind: product
  entities:
  - entity: filter
    effect: removes
  - entity: task
    effect: reads
    facts:
    - Title
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

# Delete filter in the demo

## Trigger

The Visitor chooses Delete on a filter and confirms. The visitor is using the disposable demo.

## Outcome

The filter is gone from the list of filters; the tasks it matched remain. Changes affect demonstration work only; no request is sent to Todoist.
