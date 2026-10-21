---
kind: primary
routes:
  web: Demo
steps:
- text: Open the selected tag
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::tag
- text: Read the tag and matching tasks, with page selection criteria and totals
  kind: product
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
    - Colour
    - Favourite
    - Order
    - Reserved
  - entity: task
    effect: reads
    facts:
    - Title
    - Tags
    - Due date
    - Estimate
    - Priority
  actor: visitor
  contexts:
    web:
      place: web::public::tag
references:
- kind: code
  role: implementation
  target: src/views/LabelsView.tsx
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
---

# Read a selected tag’s work in the demo

## Trigger

The person opens a tag from the catalogue or sidebar.

## Outcome

The selected tag’s work is shown with the chosen scope and totals.
