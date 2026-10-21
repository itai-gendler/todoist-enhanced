---
references:
- kind: code
  role: implementation
  target: src/domain/types.ts
domain: projects
relations:
- entity: task
  verb: contains
  cardinality: one-to-many
---

# Section

An individually named and addressable division of a project.

## Information kept

- **Name** — The section name.
- **Description** — Optional section description.
- **Project** — The project containing the section.
- **Order** — The position among that project’s sections.

## States

### Active

A section used for current work.

### Archived

A section removed from the active project presentation.
