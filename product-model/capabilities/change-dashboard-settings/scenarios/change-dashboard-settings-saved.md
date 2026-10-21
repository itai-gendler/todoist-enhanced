---
kind: primary
routes:
  web: Connected account
steps:
- text: The User moves the dashboard cards, or resets them
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts:
    - Dashboard arrangement
  actor: user
  contexts:
    web:
      place: web::connected::insights
- text: The Product saves the card order and choices in the settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Dashboard arrangement
  actor: user
  contexts:
    web:
      place: web::connected::insights
references:
- kind: code
  role: implementation
  target: src/views/InsightsView.tsx
- kind: code
  role: implementation
  target: src/components/DashboardDisplayMenu.tsx
- kind: code
  role: implementation
  target: src/domain/dashboard.ts
---

# Change dashboard settings

## Trigger

The User chooses Edit layout on the dashboard, or Reset to default.

## Outcome

The dashboard shows its cards in the chosen order; Reset to default puts them back.
