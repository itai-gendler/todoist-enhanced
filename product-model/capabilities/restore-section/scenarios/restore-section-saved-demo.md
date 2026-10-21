---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Undo after archiving the section
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
- text: The Product unarchives the section
  kind: product
  entities:
  - entity: section
    effect: changes
    facts: []
    from: Archived
    to: Active
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

# Restore section in the demo

## Trigger

The Visitor has just archived a section and chooses Undo in the message. The visitor is using the disposable demo.

## Outcome

The section is active in its project again. Changes affect demonstration work only; no request is sent to Todoist.
