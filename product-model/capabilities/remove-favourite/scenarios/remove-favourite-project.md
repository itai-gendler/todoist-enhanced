---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses Remove from favourites on the project
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
- text: The Product removes the star from the project
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

# Remove from favourites for a project

## Trigger

The User chooses Remove from favourites on a starred project.

## Outcome

The project is no longer starred.
