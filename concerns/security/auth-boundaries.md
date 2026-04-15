---
id: security/auth-boundaries
title: Authorization Boundaries
type: concern
concern: security
priority: critical
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - session
  - role
  - permission
  - authorization
related_rules:
  - security/client-server-boundaries
  - security/input-validation
---
# Authorization Boundaries

## When to read
Use this when a feature depends on user identity, role, or resource ownership.

## Core rules
- Authorize on the server at the resource boundary, not only in the UI.
- Use explicit policy checks close to data access or command execution.
- Return least-privilege data and actions for the current actor.
- Keep role names out of presentation logic when a capability check is clearer.

## Good example
```typescript
await requireProjectAccess({ userId: session.userId, projectId })

```

## Bad example
```tsx
if (user.role === 'admin') {
  showDeleteButton = true
}

```

## Exceptions
Read-only cosmetic UI changes can still branch on client state once the server already enforced access.
