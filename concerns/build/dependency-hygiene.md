---
id: build/dependency-hygiene
title: Dependency Hygiene
type: concern
concern: build
priority: medium
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - package.json
  - dependency
  - import
related_rules:
  - build/import-boundaries
---
# Dependency Hygiene

## When to read
Use this before introducing a new package or expanding an existing one.

## Core rules
- Prefer mature, maintained packages with clear ownership and release activity.
- Avoid adding a package for a tiny utility already solved by the platform or current stack.
- Review bundle cost, SSR support, and TypeScript support before adoption.
- Wrap third-party packages in small local adapters when business code depends on them heavily.

## Good example
```typescript
import { z } from 'zod'
// Existing stack already covers runtime validation

```

## Bad example
```typescript
import tinyUniqueNeed from 'very-large-package'

```

## Exceptions
One-off scripts can use small utility packages when they stay outside product runtime paths.
