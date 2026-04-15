---
id: drizzle/schema-and-queries
title: Drizzle Schema and Queries
type: stack
stack: drizzle
concern: data
priority: high
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - drizzle-orm
  - pgTable
  - db.select
related_rules:
  - security/secret-handling
---
# Drizzle Schema and Queries

## When to read
Use this when Drizzle ORM owns schema and SQL queries.

## Core rules
- Treat schema definitions as the source of truth for table shape.
- Keep query modules close to the domain that owns them.
- Select only needed columns and joins; do not overfetch by default.
- Use migrations and generated SQL workflows instead of manual drift.

## Good example
```typescript
export const projects = pgTable('projects', {
  id: text('id').primaryKey(),
  name: text('name').notNull(),
})

const rows = await db
  .select({ id: projects.id, name: projects.name })
  .from(projects)
```

## Bad example
```typescript
const rows = await db.select().from(projects)
// later map out dozens of unused fields
```

## Exceptions
One-off maintenance scripts can be broader if they are not part of normal app runtime.
