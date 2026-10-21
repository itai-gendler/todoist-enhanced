---
kind: validation
routes:
  web: Demo
steps:
- kind: actor
  actor: visitor
  text: The Visitor opens the filter’s editing form
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
    - Query
    - Frozen
  contexts: &id001
    web:
      place: web::public::filters
- kind: condition
  text: The returned filter has Frozen set to true.
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
    - Query
    - Frozen
  contexts: *id001
- kind: product
  actor: visitor
  text: The editing form shows its existing values with editing disabled.
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
    - Query
    - Frozen
  contexts: *id001
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/overlays/FilterSheet.tsx
---

# Read a frozen filter in the demo

## Trigger

The returned filter has Frozen set to true.

## Outcome

The editing form shows its existing values with editing disabled.
