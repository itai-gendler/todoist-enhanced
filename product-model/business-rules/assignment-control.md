---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Assignee
references:
- kind: code
  role: implementation
  target: src/domain/assignees.ts
- kind: code
  role: implementation
  target: src/domain/sharing.ts
- kind: code
  role: implementation
  target: src/store/collab.ts
permits:
- actors:
  - user
  when:
  - entity: project
    fact: Assignment allowed
    is: true
---

# Users change assignment only when the project permits it

An explicit assignment denial closes both assigning and unassigning. Candidate selection is limited to the current person and active collaborators of the same project; pending invitations are not assignees.
