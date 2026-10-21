---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor confirms deleting the tag
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
- text: The Product deletes the tag and takes it off the tasks that carried it
  kind: product
  entities:
  - entity: tag
    effect: removes
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

# Delete tag in the demo

## Trigger

The Visitor chooses Delete on a tag and confirms. The visitor is using the disposable demo.

## Outcome

The tag is gone from the catalogue and from every task that carried it. Changes affect demonstration work only; no request is sent to Todoist.
