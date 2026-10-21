---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Add to favourites on the project
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
    - Favourite
  actor: user
  contexts:
    web:
      place: web::connected::project
- text: The Product stars the project
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Favourite
  actor: user
  contexts:
    web:
      place: web::connected::project
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/FavouriteStar.tsx
---

# Add to favourites for a project

## Trigger

The User chooses Add to favourites on a project that is not starred.

## Outcome

The project is starred.
