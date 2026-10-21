---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor adds a section at a chosen position
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
- text: The Product creates the section at that position in the project
  kind: product
  entities:
  - entity: section
    effect: creates
    facts:
    - Name
    - Description
    - Project
    - Order
    to: Active
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

# Create section in the demo

## Trigger

The Visitor adds a section between two others, or at the end of a project. The visitor is using the disposable demo.

## Outcome

The new section appears where it was added; without a name it starts with a placeholder name, ready to edit. Changes affect demonstration work only; no request is sent to Todoist.
