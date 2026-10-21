---
kind: primary
routes:
  web: Connected account
steps:
- text: The User chooses the mode, accent colour and other appearance settings
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Appearance
  actor: user
  contexts:
    web:
      place: web::connected::appearance
- text: The Product applies and saves the appearance settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Appearance
  actor: user
  contexts:
    web:
      place: web::connected::appearance
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

# Change Appearance settings

## Trigger

The User changes Appearance in Settings.

## Outcome

The app is drawn at once in the chosen light, dark or system mode and accent colour, and the choice is saved with the other settings.
