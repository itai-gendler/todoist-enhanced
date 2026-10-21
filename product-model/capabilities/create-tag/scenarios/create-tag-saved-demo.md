---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor enters a name for a new tag
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::tags
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
  target: src/components/overlays/TagSheet.tsx
---

# Create tag in the demo

## Trigger

The Visitor creates a tag. The visitor is using the disposable demo.

## Outcome

The new tag appears in the catalogue. A name matching an existing tag, ignoring case, creates nothing new. Changes affect demonstration work only; no request is sent to Todoist.
