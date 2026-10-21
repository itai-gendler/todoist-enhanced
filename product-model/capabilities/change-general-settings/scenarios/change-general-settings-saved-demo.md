---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor changes the language, homepage, formats or another General setting
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Language
  actor: visitor
  contexts:
    web:
      place: web::public::general
- text: The Product saves the General settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Language
    - General
  actor: visitor
  contexts:
    web:
      place: web::public::general
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

# Change General settings in the demo

## Trigger

The Visitor changes a setting in General. The visitor is using the disposable demo.

## Outcome

The app uses the chosen language, homepage, date and time formats and other General choices, saved with the other settings. Changes affect demonstration work only; no request is sent to Todoist.
