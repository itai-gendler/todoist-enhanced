---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/ConnectView.tsx
- kind: code
  role: implementation
  target: src/api/oauth.ts
- kind: code
  role: implementation
  target: src/api/auth.ts
- kind: code
  role: implementation
  target: src/store/sync.ts
---

# Connect account

Connect an existing Todoist account through Todoist sign-in or a personal API token. The product reads the returned workspace; acceptance of credentials belongs to Todoist.
