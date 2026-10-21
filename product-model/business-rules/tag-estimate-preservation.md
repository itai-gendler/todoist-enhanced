---
appliesTo:
- type: entity
  id: task
  facts:
  - Estimate
  - Tags
  - Native duration
references:
- kind: code
  role: implementation
  target: src/domain/estimates.ts#estimatePatch
- kind: code
  role: implementation
  target: src/domain/estimate-conversion.ts#planEstimateConversion
---

# Tag estimate edits preserve native calendar duration

Ordinary estimate writes and clears in tag mode change estimate labels only. Explicit conversion to tags clears native durations on untimed tasks while retaining timed blocks. Native conversion removes estimate tags after requesting the corresponding duration.
