---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor confirms archiving the section
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
- text: The Product archives the section and offers Undo
  kind: product
  entities:
  - entity: section
    effect: changes
    facts: []
    from: Active
    to: Archived
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

# Archive section in the demo

## Trigger

The Visitor chooses Archive on a section and confirms. The visitor is using the disposable demo.

## Outcome

The section and its tasks leave the project’s page, and Todoist keeps the section among the project’s archived ones. Undo in the message brings it back. Changes affect demonstration work only; no request is sent to Todoist.
