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
  target: src/domain/estimates.ts#readEstimate
---

# The selected estimate source wins with a fallback

Tags use the first valid positive whole-minute est- label; native durations count only when positive and measured in minutes. Tags win in tag mode, native minutes win in duration mode, and the other source is a fallback when the preferred one is absent. Invalid and multiple tags remain visible as conflicts.
