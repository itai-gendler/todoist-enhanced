---
kind: primary
routes:
  web: Connected account
steps:
- text: The User opens the tag catalogue
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::tags
- text: The Product lists the tags
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
  actor: user
  contexts:
    web:
      place: web::connected::tags
references:
- kind: code
  role: implementation
  target: src/views/LabelsView.tsx
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
---

# Browse tags

## Trigger

The User opens Tags.

## Outcome

Every tag is listed in its saved order with its colour and favourite status.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
