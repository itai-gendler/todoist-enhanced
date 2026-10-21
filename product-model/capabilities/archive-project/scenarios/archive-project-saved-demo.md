---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses Archive on the project
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Inbox
  actor: visitor
  contexts:
    web:
      place: web::public::project
- text: The Product archives the project
  kind: product
  entities:
  - entity: project
    effect: changes
    facts: []
    from: Active
    to: Archived
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
  target: src/components/ProjectMenu.tsx
---

# Archive project in the demo

## Trigger

The Visitor chooses Archive on a project. The visitor is using the disposable demo.

## Outcome

The project is archived, not deleted, and leaves the project lists; a message names it. Changes affect demonstration work only; no request is sent to Todoist.
