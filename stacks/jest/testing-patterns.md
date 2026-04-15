---
id: jest/testing-patterns
title: Jest Testing Patterns
type: stack
stack: jest
concern: testing
priority: medium
always_apply: false
applies_to:
  - testing
  - review
signals:
  - jest.
  - describe(
  - it(
related_rules:
  - testing/mock-boundaries
---
# Jest Testing Patterns

## When to read
Use this when Jest remains the project test runner.

## Core rules
- Clear mocks and timers between tests.
- Use snapshots sparingly.
- Keep CI runs deterministic and avoid watch-only assumptions.
- Prefer Vitest in new Vite-native projects unless Jest compatibility is required.

## Good example
```typescript
beforeEach(() => {
  jest.clearAllMocks()
})

```

## Bad example
```typescript
it('matches snapshot', () => {
  expect(result).toMatchSnapshot()
})

```

## Exceptions
Existing Jest-heavy repos can keep Jest as long as patterns stay disciplined.
