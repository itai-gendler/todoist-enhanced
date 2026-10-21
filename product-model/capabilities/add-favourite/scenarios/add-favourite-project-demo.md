---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Add to favourites on the project
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
- text: The Product stars the project
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

# Add to favourites for a project in the demo

## Trigger

The Visitor chooses Add to favourites on a project that is not starred. The visitor is using the disposable demo.

## Outcome

The project is starred. Changes affect demonstration work only; no request is sent to Todoist.
