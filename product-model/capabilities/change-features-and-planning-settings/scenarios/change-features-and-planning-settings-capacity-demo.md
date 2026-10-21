---
kind: alternate
routes:
  web: Demo
steps:
- text: Enter daily capacities and an optional weekly override
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::features
- text: Save the capacity settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Daily capacity
    - Weekly override
  actor: visitor
  contexts:
    web:
      place: web::public::features
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

# Set available hours in the demo

## Trigger

The person edits weekday capacities or chooses a custom weekly total. The visitor is using the disposable demo.

## Outcome

Valid positive durations are saved. Weekly capacity is the positive override when selected, otherwise the sum of all seven days. Reset restores five hours per day and removes the override. Changes affect demonstration work only; no request is sent to Todoist.

## Edge cases

- Invalid or zero duration input is refused with an explanation and the previous value is retained.
- Changing the week-label name changes the reading of commitments; it does not migrate labels on existing tasks.
