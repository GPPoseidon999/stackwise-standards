---
id: security/secret-handling
title: Secret Handling
type: concern
concern: security
priority: critical
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - process.env
  - import.meta.env
  - SECRET
  - API_KEY
related_rules:
  - security/client-server-boundaries
---
# Secret Handling

## When to read
Use this when introducing env vars, API keys, or server credentials.

## Core rules
- Keep secrets on the server only.
- Read runtime config through one module, not scattered env access.
- Use explicit public prefixes for client-exposed values.
- Never log or snapshot real secrets.

## Good example
```typescript
export const env = {
  apiBaseUrl: process.env.API_BASE_URL ?? fail('Missing API_BASE_URL'),
}

```

## Bad example
```typescript
export const stripeSecret = import.meta.env.STRIPE_SECRET_KEY
console.log(process.env.DATABASE_URL)

```

## Exceptions
Public browser keys are allowed when the provider documents them as public-safe.
