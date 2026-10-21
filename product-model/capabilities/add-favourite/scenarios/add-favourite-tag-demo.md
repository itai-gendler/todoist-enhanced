---
kind: alternate
routes:
  web: Demo
steps:
- text: The Visitor chooses Add to favourites on the tag
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
- text: The Product stars the tag
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

# Add to favourites for a tag in the demo

## Trigger

The Visitor chooses Add to favourites on a tag that is not starred. The visitor is using the disposable demo.

## Outcome

The tag is starred. Changes affect demonstration work only; no request is sent to Todoist.
