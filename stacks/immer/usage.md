---
id: immer/usage
title: Immer Usage
type: stack
stack: immer
concern: state
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - produce(
  - immer
related_rules:
  - zustand/store-structure
  - redux-toolkit/store-structure
---
# Immer Usage

## When to read
Use this when immutable updates are deep enough to become noisy.

## Core rules
- Use Immer for complex updates, not every shallow object write.
- Keep produce callbacks synchronous and side-effect free.
- Name draft values clearly.
- Revisit state shape if Immer usage becomes excessive.

## Good example
```typescript
const nextState = produce(state, (draft) => {
  draft.filters.keyword = keyword
})

```

## Bad example
```typescript
const nextState = produce(state, async (draft) => {
  await saveDraft(draft)
})

```

## Exceptions
Simple shallow updates should stay as plain object spreads.
