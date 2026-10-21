---
kind: primary
routes:
  web: Connected account
steps:
- text: Open the selected tag
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::tag
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
  actor: user
  contexts:
    web:
      place: web::connected::tag
references:
- kind: code
  role: implementation
  target: src/views/LabelsView.tsx
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
---

# Read a selected tag’s work

## Trigger

The person opens a tag from the catalogue or sidebar.

## Outcome

The selected tag’s work is shown with the chosen scope and totals.
