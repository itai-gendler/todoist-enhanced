---
actors:
- user
- visitor
references:
- kind: code
  role: implementation
  target: src/components/TimePanel.tsx
- kind: code
  role: implementation
  target: src/components/overlays/Unestimated.tsx
---

# Estimate work so it can fit

## Goal

Supply the estimates that keep work out of the available-time result.

## Success criterion

The app carries the unestimated selection into a batch estimate pass and saves the valid drafts for that work.
