---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses another space for the project
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
- text: The Product moves the project to that workspace or to personal space and clears its former parent
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Workspace
    - Parent
  - entity: workspace
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
  target: src/components/ProjectMenu.tsx
---

# Move project in the demo

## Trigger

The Visitor moves a project to another space. The visitor is using the disposable demo.

## Outcome

The project sits at the top level of its new space: a team workspace or personal space. Changes affect demonstration work only; no request is sent to Todoist.
