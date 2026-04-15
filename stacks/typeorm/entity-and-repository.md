---
id: typeorm/entity-and-repository
title: TypeORM Entity and Repository
type: stack
stack: typeorm
concern: data
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - Entity(
  - Repository
  - DataSource
related_rules:
  - security/secret-handling
---
# TypeORM Entity and Repository

## When to read
Use this when TypeORM manages entities, relations, and persistence.

## Core rules
- Keep entities focused on persistence shape, not broad business orchestration.
- Configure relations deliberately; do not lean on eager loading by default.
- Keep repository and service boundaries clear.
- Manage migrations as part of normal schema change workflow.

## Good example
```typescript
@Entity()
export class ProjectEntity {
  @PrimaryColumn()
  id!: string

  @Column()
  name!: string
}
```

## Bad example
```typescript
@Entity()
export class AppStateEntity {
  @Column('json')
  everything!: unknown
}
```

## Exceptions
Legacy schemas can force less ideal entities during an incremental migration.
