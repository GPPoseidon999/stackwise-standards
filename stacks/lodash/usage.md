---
id: lodash/usage
title: Lodash Usage
type: stack
stack: lodash
concern: utilities
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - lodash
  - debounce
  - throttle
  - merge
related_rules:
  - build/import-boundaries
---
# Lodash Usage

## When to read
Use this when lodash solves real complexity, not when native JS is enough.

## Core rules
- Import narrowly and explicitly.
- Prefer native array and object methods for simple transforms.
- Use lodash for proven hard edges such as debounce, throttle, or deep path helpers when justified.
- Avoid deep merge in business logic unless object semantics are well understood.

## Good example
```typescript
import debounce from 'lodash/debounce'

```

## Bad example
```typescript
import _ from 'lodash'

```

## Exceptions
A legacy codebase may still use broader imports temporarily during incremental cleanup.
