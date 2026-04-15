---
id: testing/test-case-design
title: Test Case Design
type: concern
concern: testing
priority: high
always_apply: true
applies_to:
  - implementation
  - review
  - testing
signals:
  - test(
  - describe(
  - .spec.
  - .test.
related_rules:
  - testing/mock-boundaries
  - testing/e2e-scope
---
# Test Case Design

## When to read
Use this when adding or reviewing automated tests.

## Core rules
- Cover the happy path, boundary cases, and expected failure modes.
- Name tests after behavior, not implementation details.
- Assert user-visible results, outputs, and side effects before internal structure.
- Keep each test focused on one main intent.

## Good example
```typescript
test('returns placeholder for missing value', () => {
  expect(formatPrice(null)).toBe('--')
})

```

## Bad example
```typescript
test('works', () => {
  expect(result).toBeTruthy()
})

```

## Exceptions
Early spikes may start with happy-path coverage, but merge-ready work must cover critical edges.
