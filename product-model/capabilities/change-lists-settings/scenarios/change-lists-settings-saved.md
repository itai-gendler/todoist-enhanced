---
kind: primary
routes:
  web: Connected account
steps:
- text: The User changes what list rows show and how they open
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Lists
  actor: user
  contexts:
    web:
      place: web::connected::lists
- text: The Product saves the Lists settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Lists
  actor: user
  contexts:
    web:
      place: web::connected::lists
references:
- kind: code
  role: implementation
  target: src/views/SettingsView.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
- kind: code
  role: implementation
  target: src/store/prefs.ts
---

# Change Lists settings

## Trigger

The User changes a setting in Lists.

## Outcome

List rows show the chosen task details, and opening one follows the chosen preference.
