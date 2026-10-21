---
kind: primary
routes:
  web: Connected account
steps:
- text: The User confirms deleting the tag
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
- text: The Product deletes the tag and takes it off the tasks that carried it
  kind: product
  entities:
  - entity: tag
    effect: removes
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

# Delete tag

## Trigger

The User chooses Delete on a tag and confirms.

## Outcome

The tag is gone from the catalogue and from every task that carried it.
