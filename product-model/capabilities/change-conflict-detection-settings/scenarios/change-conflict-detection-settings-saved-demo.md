---
kind: primary
routes:
  web: Demo
steps:
- text: The Visitor turns individual conflict checks on or off
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Conflict checks
  actor: visitor
  contexts:
    web:
      place: web::public::conflicts
- text: The Product saves which checks are on in the settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Conflict checks
  actor: visitor
  contexts:
    web:
      place: web::public::conflicts
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

# Change Conflict detection settings in the demo

## Trigger

The Visitor turns a check on or off in Conflict detection. The visitor is using the disposable demo.

## Outcome

Things to settle reports only the contradictions whose checks are on: an estimate mismatch, a date with the week label, several estimates, a quick task that is too long, a parent and its subtasks, an invalid estimate. Changes affect demonstration work only; no request is sent to Todoist.
