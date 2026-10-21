---
kind: edge
routes:
  web: Connected account
steps:
- text: Open a filter
  kind: actor
  entities:
  - entity: filter
    effect: reads
    facts:
    - Name
    - Query
  actor: user
  contexts:
    web:
      place: web::connected::filter
- text: The external query request fails
  kind: condition
  entities: []
  contexts:
    web:
      place: web::connected::filter
- text: Show a stale cached result or the query refusal
  kind: product
  entities:
  - entity: filter
    effect: reads
    facts:
    - Query
  - entity: task
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    web:
      place: web::connected::filter
references:
- kind: code
  role: implementation
  target: src/hooks/useFilterResult.ts
- kind: code
  role: implementation
  target: src/api/filters.ts
- kind: code
  role: implementation
  target: src/views/SimpleListView.tsx
---

# Keep the last answer after a network failure

## Trigger

A saved query cannot be refreshed.

## Outcome

The last cached answer remains marked stale. A rejected query instead displays Todoist’s error and has no successful result list.
