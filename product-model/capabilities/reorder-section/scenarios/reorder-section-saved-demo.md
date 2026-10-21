---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor drags the section to a new place among the sections
  kind: actor
  entities:
  - entity: section
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::project
- text: The Product saves the section’s place among the project’s active sections
  kind: product
  entities:
  - entity: section
    effect: changes
    facts:
    - Order
  - entity: project
    effect: reads
    facts:
    - Name
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
  target: src/components/SectionMenu.tsx
---

# Reorder section in the demo

## Trigger

The Visitor drags a section to a new place. The visitor is using the disposable demo.

## Outcome

The section sits at its new place among the project’s active sections. Changes affect demonstration work only; no request is sent to Todoist.
