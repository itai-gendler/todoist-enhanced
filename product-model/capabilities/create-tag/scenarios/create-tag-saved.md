---
kind: primary
routes:
  web: Connected account
steps:
- text: The User enters a name for a new tag
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::tags
- text: The Product creates the tag, with spaces turned into hyphens
  kind: product
  entities:
  - entity: tag
    effect: creates
    facts:
    - Name
    - Colour
    - Favourite
    - Order
    - Reserved
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
  target: src/components/overlays/TagSheet.tsx
---

# Create tag

## Trigger

The User creates a tag.

## Outcome

The new tag appears in the catalogue. A name matching an existing tag, ignoring case, creates nothing new.
