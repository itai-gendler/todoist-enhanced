---
appliesTo:
- type: capability
  id: convert-estimates
  contexts:
  - place: web::connected::conversion
references:
- kind: code
  role: implementation
  target: src/components/overlays/EstimateConversion.tsx
- kind: code
  role: implementation
  target: src/domain/estimate-conversion.ts
---

# Native conversion requests require eligible account status

Conversion to native minutes is offered only with eligible reported account status and verifies each request. Conversion to tags may clear untimed durations on any connected account. Timed native blocks are retained.
