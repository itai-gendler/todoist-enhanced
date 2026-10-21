---
kind: primary
routes:
  web: Connected account
steps:
- text: The User types what they are looking for
  kind: actor
  entities: []
  actor: user
  contexts:
    web:
      place: web::connected::search
- text: The Product matches task titles and descriptions, projects, sections when included, tags and the app’s pages
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Description
  - entity: project
    effect: reads
    facts:
    - Name
  - entity: section
    effect: reads
    facts:
    - Name
  - entity: tag
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    web:
      place: web::connected::search
references:
- kind: code
  role: implementation
  target: src/components/overlays/Search.tsx
- kind: code
  role: implementation
  target: src/views/SearchView.tsx
- kind: code
  role: implementation
  target: src/domain/search.ts
---

# Search work

## Trigger

The User presses ⌘K, or starts typing outside a field.

## Outcome

Matching tasks, projects, sections, tags and pages are listed by kind, ignoring case and accents; choosing one goes straight to it.

## Edge cases

- An empty selection is shown as no matching work; the product does not invent tasks.
