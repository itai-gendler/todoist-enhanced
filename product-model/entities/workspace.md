---
references:
- kind: code
  role: implementation
  target: src/domain/types.ts
relations:
- entity: project
  verb: contains
  cardinality: one-to-many
- entity: folder
  verb: contains
  cardinality: one-to-many
---

# Workspace

An existing Todoist team space used to scope work and place projects. This product does not create team workspaces.

## Information kept

- **Name** — The reported workspace name.
- **Default access** — The workspace’s default project visibility, falling back to Team when absent.
