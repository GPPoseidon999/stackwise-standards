---
id: vitest/testing-patterns
title: Vitest Testing Patterns
type: stack
stack: vitest
concern: testing
priority: high
always_apply: false
applies_to:
  - testing
  - review
signals:
  - vi.
  - vitest
  - describe(
related_rules:
  - testing/test-case-design
  - testing/mock-boundaries
---
# Vitest Testing Patterns

## When to read
Use this when Vitest is the unit and component test runner.

## Core rules
- Clear mocks before each test.
- Await async expectations and user events.
- Use snapshots sparingly and only for stable structure.
- Keep test setup deterministic and local when possible.

## Good example
```typescript
beforeEach(() => {
  vi.clearAllMocks()
})

```

## Bad example
```typescript
test('snapshot', () => {
  expect(result).toMatchSnapshot()
})

```

## Exceptions
A small snapshot can still help for a stable presentation-only component.
