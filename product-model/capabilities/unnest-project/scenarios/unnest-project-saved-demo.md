---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor moves the nested project to the top level
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
- text: The Product takes the project out of its parent, at the top level of its workspace
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Parent
    - Order
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

# Move project to top level in the demo

## Trigger

The Visitor moves a nested project to the top level. The visitor is using the disposable demo.

## Outcome

The project is no longer nested and sits at the top level of its space. Changes affect demonstration work only; no request is sent to Todoist.
