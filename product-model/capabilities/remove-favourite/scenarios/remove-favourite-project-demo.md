---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Remove from favourites on the project
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
    - Favourite
  actor: visitor
  contexts:
    web:
      place: web::public::project
- text: The Product removes the star from the project
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Favourite
  actor: visitor
  contexts:
    web:
      place: web::public::project
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/FavouriteStar.tsx
---

# Remove from favourites for a project in the demo

## Trigger

The Visitor chooses Remove from favourites on a starred project. The visitor is using the disposable demo.

## Outcome

The project is no longer starred. Changes affect demonstration work only; no request is sent to Todoist.
