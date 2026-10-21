---
kind: primary
routes:
  web: Connected account
steps:
- text: The User changes the mode, grouping, sorting or inclusions of the page
  kind: actor
  entities:
  - entity: display-preferences
    effect: reads
    facts:
    - Page
  actor: user
  contexts:
    web:
      place: web::connected::display
- text: The Product remembers these display preferences for the page
  kind: product
  entities:
  - entity: display-preferences
    effect: changes
    facts:
    - Page
    - Mode
    - Grouping
    - Sorting
    - Filters
    - Calendar
    - Table
  actor: user
  contexts:
    web:
      place: web::connected::display
references:
- kind: code
  role: implementation
  target: src/components/DisplayMenu.tsx
- kind: code
  role: implementation
  target: src/components/TableColumnEditor.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
- kind: code
  role: implementation
  target: src/store/prefs.ts
---

# Change Display settings

## Trigger

The User changes the Display control on a task page.

## Outcome

The page shows its tasks in the chosen mode, grouping, sorting and filters, remembered for that page.
