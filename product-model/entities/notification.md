---
references:
- kind: code
  role: implementation
  target: src/domain/notifications.ts
---

# Notification

A Todoist notice received through synchronization, including actionable project invitations when the required invitation details are present.

## Information kept

- **Message** — The returned message or a description of the recognized event.
- **Sender** — The sender when supplied.
- **Subject** — The named work or person.
- **Received on** — The reported event time.
- **Read** — Whether the notice has been marked read.
- **Invitation answer** — Unanswered, accepted or declined where this notice carries an invitation.
- **Answer available** — Whether a project invitation has the details needed to answer it.
