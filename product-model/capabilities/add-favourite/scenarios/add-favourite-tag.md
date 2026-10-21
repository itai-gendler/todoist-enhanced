---
kind: alternate
routes:
  web: Connected account
steps:
- text: The User chooses Add to favourites on the tag
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
    - Favourite
  actor: user
  contexts:
    web:
      place: web::connected::tags
- text: The Product stars the tag
  kind: product
  entities:
  - entity: tag
    effect: changes
    facts:
    - Favourite
  actor: user
  contexts:
    web:
      place: web::connected::tags
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/FavouriteStar.tsx
---

# Add to favourites for a tag

## Trigger

The User chooses Add to favourites on a tag that is not starred.

## Outcome

The tag is starred.
