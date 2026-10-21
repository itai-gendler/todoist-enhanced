---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses another destination for the section
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
- text: The Product moves the section with its tasks to the end of the chosen project
  kind: product
  entities:
  - entity: section
    effect: changes
    facts:
    - Project
    - Order
  - entity: task
    effect: changes
    facts:
    - Project
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

# Move section in the demo

## Trigger

The Visitor moves a section to another project. The visitor is using the disposable demo.

## Outcome

The section and its tasks appear at the end of the other project. Changes affect demonstration work only; no request is sent to Todoist.
