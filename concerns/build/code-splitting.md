---
id: build/code-splitting
title: Code Splitting
type: concern
concern: build
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - import(
  - React.lazy
  - dynamic import
related_rules:
  - build/import-boundaries
---
# Code Splitting

## When to read
Use this when loading heavy routes, editors, charts, or low-frequency features.

## Core rules
- Split route-level and modal-level code by default when modules are large.
- Choose split points around user journeys, not random files.
- Add loading and error states for async chunks.
- Do not split critical above-the-fold content without strong reason.

## Good example
```tsx
const Editor = React.lazy(() => import('./Editor'))

```

## Bad example
```tsx
import { Editor } from './Editor'
import { ChartPanel } from './ChartPanel'

```

## Exceptions
Keep a module synchronous when first-paint speed would get worse after splitting.
