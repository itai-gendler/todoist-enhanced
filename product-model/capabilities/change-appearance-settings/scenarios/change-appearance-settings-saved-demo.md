---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor chooses the mode, accent colour and other appearance settings
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Appearance
  actor: visitor
  contexts:
    web:
      place: web::public::appearance
- text: The Product applies and saves the appearance settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Appearance
  actor: visitor
  contexts:
    web:
      place: web::public::appearance
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

# Change Appearance settings in the demo

## Trigger

The Visitor changes Appearance in Settings. The visitor is using the disposable demo.

## Outcome

The app is drawn at once in the chosen light, dark or system mode and accent colour, and the choice is saved with the other settings. Changes affect demonstration work only; no request is sent to Todoist.
