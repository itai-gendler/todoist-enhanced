---
appliesTo:
- type: entity
  id: project-member
  effect: removes
references:
- kind: code
  role: implementation
  target: src/components/overlays/ShareSheet.tsx
permits:
- actors:
  - user
  when:
  - fact: Participation
    is: Invited
- actors:
  - user
  when:
  - entity: project
    fact: Workspace
    absent: true
- actors:
  - user
  when:
  - entity: project
    fact: People management available
    is: true
  - fact: Role
    is-not: Creator
---

# Users remove project members through the available sharing controls

Pending invitations can be removed. Personal-project member removal is offered directly. In team projects, removal of an active member shares the creator/admin control and leaves the creator unchanged.
