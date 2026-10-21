---
appliesTo:
- type: entity
  id: comment
  effect: changes
  facts:
  - Text
references:
- kind: code
  role: implementation
  target: src/components/CommentThread.tsx
permits:
- related:
  - verb: authors
    entity: user
---

# Only a comment author edits its text

The comment editor is offered for the current person’s own comments. Todoist still accepts or refuses the outbound write.
