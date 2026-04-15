---
id: testing/mock-boundaries
title: Mock Boundaries
type: concern
concern: testing
priority: high
always_apply: true
applies_to:
  - testing
  - review
signals:
  - mock
  - spyOn
  - vi.mock
  - jest.mock
related_rules:
  - testing/test-case-design
---
# Mock Boundaries

## When to read
Use this when tests touch network, storage, time, randomness, or browser APIs.

## Core rules
- Mock external boundaries, not the business logic under test.
- Reset mocks between tests.
- Prefer one consistent mocking strategy per module.
- Use integration tests when mocking would hide the real risk.

## Good example
```typescript
vi.mock('@/services/http', () => ({ http: { get: vi.fn() } }))

```

## Bad example
```typescript
vi.mock('@/features/createProject', () => ({ createProject: vi.fn() }))

```

## Exceptions
A wrapper around a hard-to-control SDK can be mocked if the wrapper itself is tested elsewhere.
