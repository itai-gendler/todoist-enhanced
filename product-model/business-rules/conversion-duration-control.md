---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Native duration
  contexts:
  - place: web::connected::conversion
  - place: web::public::conversion
references:
- kind: code
  role: implementation
  target: src/components/overlays/EstimateConversion.tsx
permits:
- actors:
  - user
  when:
  - entity: account
    fact: Duration storage allowed
    is: true
- actors:
  - user
  when:
  - entity: settings
    fact: Estimate storage
    is: Tags
- actors:
  - visitor
---

# Users and demo visitors apply the offered duration conversion

The target is captured from the chosen estimate storage when the preview opens. Users convert to native minutes with eligible account status, or to tags under tag storage. Visitors apply the demo’s local conversion. Connected writes remain subject to the native-conversion eligibility and value rules.
