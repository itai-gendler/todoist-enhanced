---
appliesTo:
- type: entity
  id: notification
  effect: changes
  facts:
  - Invitation answer
references:
- kind: code
  role: implementation
  target: src/domain/notifications.ts
- kind: code
  role: implementation
  target: src/store/collab.ts
permits:
- actors:
  - user
  when:
  - fact: Answer available
    is: true
---

# Users answer only actionable invitations

The app offers Accept and Decline for unanswered project invitations that include the necessary invitation details. The request is sent to Todoist, and a refusal restores the previous answer.
