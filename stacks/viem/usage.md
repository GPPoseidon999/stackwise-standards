---
id: viem/usage
title: viem Usage
type: stack
stack: viem
concern: web3
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - createPublicClient
  - readContract
  - writeContract
related_rules:
  - wagmi/usage
---
# viem Usage

## When to read
Use this when viem performs contract IO and typed EVM data handling.

## Core rules
- Create public and wallet clients at clear app boundaries.
- Keep ABI definitions typed and close to contract helpers.
- Use viem helpers for unit parsing and formatting instead of manual conversion.
- Handle RPC and simulation failures as first-class errors.

## Good example
```typescript
const publicClient = createPublicClient({ chain, transport: http() })
const balance = await publicClient.readContract(config)

```

## Bad example
```typescript
const amount = Number(input) * 1e18

```

## Exceptions
Standalone scripts can create a short-lived client inline.
