---
kind: alternate
routes:
  web: Demo
steps:
- text: The Visitor chooses Add to favourites on the filter
  kind: actor
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
    - Favourite
  actor: visitor
  contexts:
    web:
      place: web::public::filters
- text: The Product stars the filter
  kind: product
  entities:
  - entity: filter
    effect: changes
    facts:
    - Favourite
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
  target: src/components/FavouriteStar.tsx
---

# Add to favourites for a filter in the demo

## Trigger

The Visitor chooses Add to favourites on a filter that is not starred. The visitor is using the disposable demo.

## Outcome

The filter is starred. Changes affect demonstration work only; no request is sent to Todoist.
