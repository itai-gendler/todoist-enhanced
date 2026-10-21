---
appliesTo:
- type: entity
  id: settings
  effect: changes
  facts:
  - Estimate storage
references:
- kind: code
  role: implementation
  target: src/store/preferences.ts
- kind: code
  role: implementation
  target: src/domain/estimates.ts#canStoreDurations
---

# Native storage selection respects the reported account eligibility

The app keeps explicitly free accounts in tag mode, including when settings are changed. Unknown plans are allowed a checked attempt; this rule does not grant a Todoist entitlement.
