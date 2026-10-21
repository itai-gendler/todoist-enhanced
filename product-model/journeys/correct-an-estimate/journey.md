---
actors:
- user
- visitor
references:
- kind: code
  role: implementation
  target: src/components/overlays/Issues.tsx
- kind: code
  role: implementation
  target: src/components/overlays/TaskDetail.tsx
---

# Correct an estimate

## Goal

Follow an invalid-estimate prompt into the affected work and supply a valid value.

## Success criterion

The task has the chosen valid estimate and its contradictory estimate tag is replaced.
