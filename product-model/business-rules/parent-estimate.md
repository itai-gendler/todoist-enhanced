---
appliesTo:
- type: entity
  id: task
  facts:
  - Estimate
  - Parent
references:
- kind: code
  role: implementation
  target: src/domain/estimates.ts#effectiveEstimate
- kind: code
  role: implementation
  target: src/hooks/useParentEstimates.ts
---

# Fully estimated open children determine the parent estimate

When every open child has a complete estimate, their recursive sum takes precedence and is written to the parent. Otherwise the parent’s own estimate takes precedence; without one, a partial child sum is shown as computed rather than a complete child estimate.
