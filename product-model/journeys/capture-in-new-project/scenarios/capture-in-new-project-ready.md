---
kind: primary
result: achieved
routes:
  web: Connected account
steps:
- kind: actor
  text: Start capture
  actor: user
  capability: create-task
  entities: []
  contexts:
    web:
      place: web::connected::task
- kind: actor
  text: Choose to create a new destination
  actor: user
  capability: create-project
  entities: []
  contexts:
    web:
      place: web::connected::project
- kind: product
  text: Create the project and select it in the preserved capture draft
  actor: user
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
      place: web::connected::project
- kind: actor
  text: Finish the task draft in that project
  actor: user
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
      place: web::connected::task
- kind: product
  text: Create the task in the chosen project
  actor: user
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
      place: web::connected::task
references:
- kind: code
  role: implementation
  target: src/components/overlays/Composer.tsx
- kind: code
  role: implementation
  target: src/components/overlays/ProjectSheet.tsx
---

# Capture work in a new project

## Trigger

Task capture needs a project that does not yet exist.

## Outcome

The created project is selected in the preserved draft, and the saved task belongs to it.
