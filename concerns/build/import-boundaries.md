---
id: build/import-boundaries
title: Import Boundaries
type: concern
concern: build
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - import
  - export *
  - dynamic import
related_rules:
  - build/code-splitting
  - build/dependency-hygiene
---
# Import Boundaries

## When to read
Use this when adding imports, exports, shared modules, or large dependencies.

## Core rules
- Prefer direct imports over barrel imports on hot paths.
- Keep server-only modules out of client bundles.
- Do not hide expensive imports behind broad helper files.
- Review import boundaries when bundle size or startup cost grows.

## Good example
```typescript
import { format } from 'date-fns'
const ChartPanel = lazy(() => import('./ChartPanel'))

```

## Bad example
```typescript
import * as dateFns from 'date-fns'
import { Button, Modal } from '../components'

```

## Exceptions
Tiny internal modules with no bundling cost can still use a small index file.
