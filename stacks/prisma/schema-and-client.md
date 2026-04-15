---
id: prisma/schema-and-client
title: Prisma Schema and Client
type: stack
stack: prisma
concern: data
priority: high
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - schema.prisma
  - PrismaClient
  - prisma.
related_rules:
  - security/secret-handling
---
# Prisma Schema and Client

## When to read
Use this when Prisma owns schema, migrations, and database access.

## Core rules
- Treat schema.prisma as the source of truth for the data model.
- Use migrations for model changes.
- Reuse PrismaClient across app lifetime.
- Select only needed fields and map results into domain models when necessary.

## Good example
```typescript
export const prisma = globalThis.prisma ?? new PrismaClient()

```

## Bad example
```typescript
export async function getUser(id: string) {
  const prisma = new PrismaClient()
  return prisma.user.findUnique({ where: { id } })
}

```

## Exceptions
Short-lived scripts can create and dispose a client inline.
