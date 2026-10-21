---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses a parent for the project
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
- text: The Product places the project under the chosen project or folder
  kind: product
  entities:
  - entity: project
    effect: changes
    facts:
    - Parent
    - Order
  - entity: folder
    effect: reads
    facts:
    - Name
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

# Nest project in the demo

## Trigger

The Visitor drags a project a little to the right under another, or chooses a parent for it. The visitor is using the disposable demo.

## Outcome

The project is nested under the chosen project or folder, in the same workspace. Changes affect demonstration work only; no request is sent to Todoist.
