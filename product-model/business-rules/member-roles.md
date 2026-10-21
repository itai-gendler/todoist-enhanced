---
appliesTo:
- type: entity
  id: project-member
  effect: changes
  facts:
  - Role
references:
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
permits:
- actors:
  - user
  when:
  - entity: project
    fact: People management available
    is: true
  - fact: Role
    is-not: Creator
---

# Project creators and admins change other members’ roles

Role editing is offered in team projects to the person reported as creator or admin. The creator’s role cannot be changed through this control; new choices are Collaborator and Admin.
