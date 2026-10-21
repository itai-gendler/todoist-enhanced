---
entities:
- entity: task
  shows:
  - Title
  - Estimate
  - Tags
  - Native duration
  - Due date
- entity: settings
  shows:
  - Estimate storage
references:
- kind: code
  role: implementation
  target: src/components/overlays/EstimateConversion.tsx
---

# Estimate conversion

Preview and apply an explicit conversion of existing estimates. This context uses disposable demonstration work.
