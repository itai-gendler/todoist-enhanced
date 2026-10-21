---
entities:
- entity: task
  shows:
  - Title
  - Estimate
  collects:
  - Estimate
references:
- kind: code
  role: implementation
  target: src/components/overlays/Unestimated.tsx
---

# Estimate tasks

Fill missing estimates for the selected work and save the valid drafts together.
