---
references:
- kind: code
  role: implementation
  target: src/domain/sidebar.ts
relations:
- entity: project
  verb: contains
  cardinality: one-to-many
---

# Folder

A named grouping of projects supplied by Todoist or the demo.

## Information kept

- **Name** — The displayed folder name.
- **Workspace** — The space holding the folder.
- **Order** — The folder’s position.
- **Expanded** — Whether its projects are currently revealed.
