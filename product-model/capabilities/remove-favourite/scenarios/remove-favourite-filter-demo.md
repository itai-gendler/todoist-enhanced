---
kind: alternate
routes:
  web: Demo
steps:
- text: The Visitor chooses Remove from favourites on the filter
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
- text: The Product removes the star from the filter
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

# Remove from favourites for a filter in the demo

## Trigger

The Visitor chooses Remove from favourites on a starred filter. The visitor is using the disposable demo.

## Outcome

The filter is no longer starred. Changes affect demonstration work only; no request is sent to Todoist.
