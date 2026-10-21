---
appliesTo:
- type: entity
  id: settings
- type: entity
  id: display-preferences
- type: entity
  id: task
  facts:
  - Kept on
references:
- kind: code
  role: implementation
  target: src/store/prefs.ts
- kind: code
  role: implementation
  target: src/store/preferences.ts
- kind: code
  role: implementation
  target: src/store/dust.ts
---

# Account settings and project display choices follow the account

The app stores Settings and a project page’s mode, grouping, sorting, calendar choices, and subtask/completion inclusion in an Inbox comment. Other page display choices, task filters, sidebar collapse and the Gathering dust Keep ledger stay on the device. Changing the week label is a reading preference, not a rename of existing task labels.
