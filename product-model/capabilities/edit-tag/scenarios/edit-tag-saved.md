---
kind: primary
routes:
  web: Connected account
steps:
- text: The User enters a new name or colour for the tag
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
- text: The Product saves the tag and renames it on every task that carries it
  kind: product
  entities:
  - entity: tag
    effect: changes
    facts:
    - Name
    - Colour
  - entity: task
    effect: changes
    facts:
    - Tags
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

# Edit tag

## Trigger

The User renames a tag or changes its colour.

## Outcome

The tag shows its new name or colour, and every task carrying it shows the new name.
