---
kind: primary
routes:
  web: Demo
steps:
- text: Confirm deletion of the section
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
- text: Move tasks out of the section
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Section
  - entity: section
    effect: reads
    facts:
    - Project
  actor: visitor
  contexts:
    web:
      place: web::public::project
- text: Remove the empty section
  kind: product
  entities:
  - entity: section
    effect: removes
    from: Active
  actor: visitor
  contexts:
    web:
      place: web::public::project
references:
- kind: code
  role: implementation
  target: src/components/SectionMenu.tsx
- kind: code
  role: implementation
  target: src/store/structure.ts
---

# Delete a section and retain its tasks in the demo

## Trigger

The person confirms deletion of a section. The visitor is using the disposable demo.

## Outcome

The app requests moves for the contained work before deleting the section; tasks remain at the project root when those requests succeed. Changes affect demonstration work only; no request is sent to Todoist.
