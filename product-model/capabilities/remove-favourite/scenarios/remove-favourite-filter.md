---
kind: alternate
routes:
  web: Connected account
steps:
- text: The User chooses Remove from favourites on the filter
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
- text: The Product removes the star from the filter
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

# Remove from favourites for a filter

## Trigger

The User chooses Remove from favourites on a starred filter.

## Outcome

The filter is no longer starred.
