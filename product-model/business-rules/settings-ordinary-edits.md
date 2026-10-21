---
appliesTo:
- type: entity
  id: settings
  effect: changes
  facts:
  - Language
  - General
  - Appearance
  - Sidebar
  - Lists
  - Week label
  - Quick group
  - Dust group
  - Dust delay
  - Quiet delay
  - Daily capacity
  - Weekly override
  - Conflict checks
  - Matrix rules
  - Dashboard arrangement
  - Setup completion
  - Release notices
  - Estimate storage
references:
- kind: code
  role: implementation
  target: src/store/preferences.ts
permits:
- actors:
  - user
  - visitor
- unattended: true
---

# Users and demo visitors change ordinary settings fields

The product offers these ordinary edits in connected work and the disposable demo. Connected writes remain subject to Todoist’s responses.
