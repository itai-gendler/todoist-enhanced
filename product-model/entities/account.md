---
references:
- kind: code
  role: implementation
  target: src/store/sync.ts
relations:
- entity: project
  verb: holds
  cardinality: one-to-many
- entity: settings
  verb: keeps
  cardinality: one-to-one
- entity: display-preferences
  verb: remembers
  cardinality: one-to-many
---

# Account

The Todoist account whose profile and work are available in this browser. Demo exploration supplies a fictional profile.

## Information kept

- **Name** — The name returned for the person.
- **Email** — The account email.
- **Week start** — The start day reported by Todoist.
- **Plan** — The plan information reported by Todoist.
- **Duration storage allowed** — False for an explicitly free account unless the reported premium or team status permits duration use; an unknown plan is tried and checked after writing.
- **Connection method** — Todoist sign-in, a personal token, or demo exploration.
- **Sync status** — Whether the current copy is synchronizing, current, offline, or has a reported error.
- **Pending changes** — How many queued writes remain on the device.
