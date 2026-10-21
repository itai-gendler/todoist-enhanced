---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor changes the section’s name or description
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
- text: The Product saves the section
  kind: product
  entities:
  - entity: section
    effect: changes
    facts:
    - Name
    - Description
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

# Edit section in the demo

## Trigger

The Visitor chooses Edit on a section. The visitor is using the disposable demo.

## Outcome

The section shows its new name and description. Changes affect demonstration work only; no request is sent to Todoist.
