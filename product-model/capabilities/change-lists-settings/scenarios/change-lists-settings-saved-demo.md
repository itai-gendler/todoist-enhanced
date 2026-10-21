---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor changes what list rows show and how they open
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Lists
  actor: visitor
  contexts:
    web:
      place: web::public::lists
- text: The Product saves the Lists settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Lists
  actor: visitor
  contexts:
    web:
      place: web::public::lists
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

# Change Lists settings in the demo

## Trigger

The Visitor changes a setting in Lists. The visitor is using the disposable demo.

## Outcome

List rows show the chosen task details, and opening one follows the chosen preference. Changes affect demonstration work only; no request is sent to Todoist.
