---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/components/overlays/EstimateConversion.tsx
- kind: code
  role: implementation
  target: src/domain/estimate-conversion.ts
- kind: code
  role: implementation
  target: src/store/estimate-safety.ts
domain: features
---

# Convert estimates

Preview and explicitly apply an estimate conversion for existing open work, including subtasks, while skipping ambiguous values.
