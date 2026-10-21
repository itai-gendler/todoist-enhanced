---
availability:
- place: web::connected
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/SettingsView.tsx
- kind: code
  role: implementation
  target: src/store/preferences.ts
- kind: code
  role: implementation
  target: src/store/prefs.ts
domain: features
---

# Change Features and planning settings

Choose how planning works: the Quick group and the week label, Gathering dust and its delay, the quiet-project delay, where new estimates are stored, and the daily and weekly capacity. Choosing another estimate storage converts nothing already saved.
