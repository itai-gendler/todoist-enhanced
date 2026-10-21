---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor opens the tag catalogue
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: visitor
  contexts:
    web:
      place: web::public::tags
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
  actor: visitor
  contexts:
    web:
      place: web::public::tags
references:
- kind: code
  role: implementation
  target: src/views/LabelsView.tsx
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
---

# Browse tags in the demo

## Trigger

The Visitor opens Tags. The visitor is using the disposable demo.

## Outcome

Every tag is listed in its saved order with its colour and favourite status.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
