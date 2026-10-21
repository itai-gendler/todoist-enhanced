---
kind: primary
routes:
  web: Connected account
steps:
- text: The User changes the language, homepage, formats or another General setting
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Language
  actor: user
  contexts:
    web:
      place: web::connected::general
- text: The Product saves the General settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Language
    - General
  actor: user
  contexts:
    web:
      place: web::connected::general
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

# Change General settings

## Trigger

The User changes a setting in General.

## Outcome

The app uses the chosen language, homepage, date and time formats and other General choices, saved with the other settings.
