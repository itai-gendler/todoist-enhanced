---
entities:
- entity: account
  shows:
  - Name
  - Email
  - Week start
  - Connection method
  - Sync status
  - Pending changes
references:
- kind: code
  role: implementation
  target: src/views/SettingsView.tsx
entryPoints:
- web: '#/settings'
---

# Account

Read the connected profile and connection status.
