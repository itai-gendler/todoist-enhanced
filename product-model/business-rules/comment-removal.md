---
appliesTo:
- type: entity
  id: comment
  effect: removes
references:
- kind: code
  role: implementation
  target: src/components/CommentThread.tsx
permits:
- related:
  - verb: authors
    entity: user
---

# Only a comment author deletes it

The product offers comment deletion to its author and asks for confirmation.
