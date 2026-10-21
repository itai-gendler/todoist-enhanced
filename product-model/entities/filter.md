---
references:
- kind: code
  role: implementation
  target: src/domain/types.ts
domain: filters
---

# Filter

A saved Todoist query, whose matching tasks are requested from Todoist.

## Information kept

- **Name** — The saved filter name.
- **Query** — The query, with top-level comma-separated parts treated as separate lists.
- **Description** — Optional descriptive text and icon marker.
- **Colour** — The chosen colour.
- **Favourite** — Whether the filter is starred.
- **Order** — The saved position.
- **Frozen** — The frozen status reported by Todoist.
