---
id: react/component-structure
title: React Component Structure
type: stack
stack: react
concern: structure
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - .tsx
  - component
  - props
related_rules:
  - react/hooks
  - react/performance
---
# React Component Structure

## When to read
Use this when creating or refactoring React components.

## Core rules
- One file should export one main component.
- Keep component flow predictable: hooks, derived state, handlers, JSX.
- Name props types clearly and keep files reasonably small.
- Avoid barrel imports for component usage on hot paths.

## Good example
```tsx
interface UserCardProps {
  userId: string
  onSelect: (id: string) => void
}

export function UserCard({ userId, onSelect }: UserCardProps) {
  function handleClick() {
    onSelect(userId)
  }

  return <button onClick={handleClick}>Open</button>
}

```

## Bad example
```tsx
export function UserCard(props) {
  return <button onClick={() => props.onSelect(props.userId)}>Open</button>
}

```

## Exceptions
Error boundaries still need class components.
