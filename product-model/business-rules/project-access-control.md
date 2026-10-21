---
appliesTo:
- type: entity
  id: project
  effect: changes
  facts:
  - Access
references:
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
permits:
- actors:
  - user
  when:
  - fact: Access editing available
    is: true
---

# Project creators and admins change visibility

The sharing view offers existing-project access editing when Todoist reports the current person as creator or admin. The product requests the chosen level and handles any external refusal.
