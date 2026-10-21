---
kind: validation
routes:
  web: Connected account
steps:
- text: Enter a tag name
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
- text: Reject the rename without changing the tag
  kind: product
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
    - Reserved
  actor: user
  contexts:
    web:
      place: web::connected::tags
references:
- kind: code
  role: implementation
  target: src/store/structure.ts
- kind: code
  role: implementation
  target: src/components/overlays/TagSheet.tsx
---

# Keep a rejected tag name unchanged

## Trigger

The proposed name is empty, duplicates another tag, or involves a reserved system name.

## Outcome

The app explains the rejected rename and preserves the previous tag and task references.
