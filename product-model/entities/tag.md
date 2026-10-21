---
references:
- kind: code
  role: implementation
  target: src/domain/types.ts
domain: tags
---

# Tag

A Todoist label that can be created, edited, ordered and attached to work.

## Information kept

- **Name** — The label name, used on tasks.
- **Colour** — The chosen label colour.
- **Favourite** — Whether the tag is starred.
- **Order** — The tag’s saved position.
- **Reserved** — Whether its name is a planning-system label, the configured week label, or starts with est-.
