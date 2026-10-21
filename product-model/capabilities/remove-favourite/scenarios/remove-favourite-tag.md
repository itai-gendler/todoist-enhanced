---
kind: alternate
routes:
  web: Connected account
steps:
- text: The User chooses Remove from favourites on the tag
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
- text: The Product removes the star from the tag
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

# Remove from favourites for a tag

## Trigger

The User chooses Remove from favourites on a starred tag.

## Outcome

The tag is no longer starred.
