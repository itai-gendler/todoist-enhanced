---
kind: alternate
routes:
  web: Demo
steps:
- text: The Visitor chooses Remove from favourites on the tag
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
    - Favourite
  actor: visitor
  contexts:
    web:
      place: web::public::tags
- text: The Product removes the star from the tag
  kind: product
  entities:
  - entity: tag
    effect: changes
    facts:
    - Favourite
  actor: visitor
  contexts:
    web:
      place: web::public::tags
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/FavouriteStar.tsx
---

# Remove from favourites for a tag in the demo

## Trigger

The Visitor chooses Remove from favourites on a starred tag. The visitor is using the disposable demo.

## Outcome

The tag is no longer starred. Changes affect demonstration work only; no request is sent to Todoist.
