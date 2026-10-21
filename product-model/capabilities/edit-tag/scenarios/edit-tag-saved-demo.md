---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor enters a new name or colour for the tag
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

# Edit tag in the demo

## Trigger

The Visitor renames a tag or changes its colour. The visitor is using the disposable demo.

## Outcome

The tag shows its new name or colour, and every task carrying it shows the new name. Changes affect demonstration work only; no request is sent to Todoist.
