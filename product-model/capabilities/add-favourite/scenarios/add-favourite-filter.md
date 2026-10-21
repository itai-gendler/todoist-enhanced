---
kind: alternate
routes:
  web: Connected account
steps:
- text: The User chooses Add to favourites on the filter
  kind: actor
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
    - Favourite
  actor: user
  contexts:
    web:
      place: web::connected::filters
- text: The Product stars the filter
  kind: product
  entities:
  - entity: filter
    effect: changes
    facts:
    - Favourite
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
  target: src/components/FavouriteStar.tsx
---

# Add to favourites for a filter

## Trigger

The User chooses Add to favourites on a filter that is not starred.

## Outcome

The filter is starred.
