---
kind: primary
result: achieved
routes:
  web: Demo
steps:
- kind: actor
  text: Start capture
  actor: visitor
  capability: create-task
  entities: []
  contexts:
    web:
      place: web::public::task
- kind: actor
  text: Choose to create a new destination
  actor: visitor
  capability: create-project
  entities: []
  contexts:
    web:
      place: web::public::project
- kind: product
  text: Create the project and select it in the preserved capture draft
  actor: visitor
  capability: create-project
  entities:
  - entity: project
    effect: creates
    facts:
    - Name
    - Workspace
    - Parent
    to: Active
  contexts:
    web:
      place: web::public::project
- kind: actor
  text: Finish the task draft in that project
  actor: visitor
  capability: create-task
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  - entity: project
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::task
- kind: product
  text: Create the task in the chosen project
  actor: visitor
  capability: create-task
  entities:
  - entity: task
    effect: creates
    facts:
    - Title
    - Project
    to: Open
  - entity: project
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::public::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/Composer.tsx
- kind: code
  role: implementation
  target: src/components/overlays/ProjectSheet.tsx
---

# Capture work in a new project in the demo

## Trigger

Task capture needs a project that does not yet exist.

## Outcome

The created project is selected in the preserved draft, and the saved task belongs to it.
