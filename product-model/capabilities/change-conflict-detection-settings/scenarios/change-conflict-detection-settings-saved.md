---
kind: primary
routes:
  web: Connected account
steps:
- text: The User turns individual conflict checks on or off
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Conflict checks
  actor: user
  contexts:
    web:
      place: web::connected::conflicts
- text: The Product saves which checks are on in the settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Conflict checks
  actor: user
  contexts:
    web:
      place: web::connected::conflicts
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

# Change Conflict detection settings

## Trigger

The User turns a check on or off in Conflict detection.

## Outcome

Things to settle reports only the contradictions whose checks are on: an estimate mismatch, a date with the week label, several estimates, a quick task that is too long, a parent and its subtasks, an invalid estimate.
