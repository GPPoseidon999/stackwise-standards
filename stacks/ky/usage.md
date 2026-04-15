---
id: ky/usage
title: Ky Usage
type: stack
stack: ky
concern: data-fetching
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - ky.
  - beforeRequest
  - beforeRetry
related_rules:
  - security/input-validation
---
# Ky Usage

## When to read
Use this when Ky wraps browser-friendly HTTP requests.

## Core rules
- Create one shared instance with extend.
- Centralize auth headers and retry hooks.
- Use retries only for safe or idempotent requests.
- Translate low-level errors before they reach UI code.

## Good example
```typescript
export const api = ky.extend({ timeout: 10_000 })

```

## Bad example
```typescript
await ky('/api/projects', { headers: { Authorization: token } })

```

## Exceptions
Standalone scripts can use a direct ky call outside app runtime.
