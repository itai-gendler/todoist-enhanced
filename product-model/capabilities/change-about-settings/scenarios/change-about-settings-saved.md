---
kind: primary
routes:
  web: Connected account
steps:
- text: The User switches “What’s new after an update”
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Release notices
  actor: user
  contexts:
    web:
      place: web::connected::about
- text: The Product saves the choice in the settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Release notices
  actor: user
  contexts:
    web:
      place: web::connected::about
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

# Change About settings

## Trigger

The User turns “What’s new after an update” on or off in About.

## Outcome

The choice is saved with the other settings: when it is on, a release that brings something new is announced once with a short list of what changed.
