---
id: vite/usage
title: Vite Usage
type: stack
stack: vite
concern: build
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - vite.config
  - import.meta.env
  - defineConfig
related_rules:
  - build/code-splitting
  - security/secret-handling
---
# Vite Usage

## When to read
Use this when Vite is the dev server and bundler.

## Core rules
- Keep build behavior inside vite.config.ts.
- Use import.meta.env for client-exposed config.
- Be conservative with low-level optimizeDeps tuning.
- Review plugin cost and maintenance before adoption.

## Good example
```typescript
export default defineConfig({ plugins: [react()] })

```

## Bad example
```typescript
const apiKey = process.env.VITE_API_KEY

```

## Exceptions
Node-only scripts may still use process.env directly.
