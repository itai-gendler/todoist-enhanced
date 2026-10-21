---
references:
- kind: code
  role: implementation
  target: src/domain/sharing.ts
---

# Project member

A person’s participation in one project, read from Todoist.

## Information kept

- **Name** — The collaborator’s reported name.
- **Email** — The address used for invitations and removal.
- **Role** — The role reported for this person in this project.
- **Participation** — Invited or active; declined and removed people are left out of the current member list.
