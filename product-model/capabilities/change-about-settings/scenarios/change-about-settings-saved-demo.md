---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor switches “What’s new after an update”
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Release notices
  actor: visitor
  contexts:
    web:
      place: web::public::about
- text: The Product saves the choice in the settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Release notices
  actor: visitor
  contexts:
    web:
      place: web::public::about
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

# Change About settings in the demo

## Trigger

The Visitor turns “What’s new after an update” on or off in About. The visitor is using the disposable demo.

## Outcome

The choice is saved with the other settings: when it is on, a release that brings something new is announced once with a short list of what changed. Changes affect demonstration work only; no request is sent to Todoist.
