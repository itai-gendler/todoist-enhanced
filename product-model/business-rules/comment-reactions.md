---
appliesTo:
- type: entity
  id: comment
  effect: changes
  facts:
  - Reactions
references:
- kind: code
  role: implementation
  target: src/components/CommentThread.tsx
permits:
- actors:
  - user
---

# Connected users change their comment reactions

The connected person can add or remove their own emoji reactions. A failed direct request restores the preceding reaction set.
