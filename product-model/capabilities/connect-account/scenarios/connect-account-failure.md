---
kind: edge
routes:
  web: Connect
steps:
- text: Attempt sign-in
  kind: actor
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::connect
- text: The external sign-in or initial data read does not succeed
  kind: condition
  entities: []
  contexts:
    web:
      place: web::public::connect
- text: Show the failed connection and available alternatives
  kind: product
  entities: []
  actor: visitor
  contexts:
    web:
      place: web::public::connect
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

# Remain at Connect after sign-in fails

## Trigger

Consent is denied, the exchange fails, the credential is rejected, or a workspace read fails.

## Outcome

Connect explains the failure and permits another attempt; the app does not claim a connected account.

## Edge cases

- A malformed personal token is rejected before making a request.
- A hosted copy built for a different address explains the mismatch and offers the token route.
- When session storage cannot preserve the sign-in round trip, the visitor stays at Connect and can use the token route.
