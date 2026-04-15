---
id: bignumber/usage
title: BigNumber Usage
type: stack
stack: bignumber
concern: precision
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - BigNumber
  - .gt(
  - .lt(
related_rules:
  - ethers/usage
---
# BigNumber Usage

## When to read
Use this when precision matters for money, balances, prices, or rates.

## Core rules
- Keep values as BigNumber-like types until final display.
- Compare values with library comparison helpers, not JS operators.
- Centralize formatting helpers for display.
- Do not mix number, BigInt, and BigNumber casually.

## Good example
```typescript
if (balance.lt(requiredAmount)) throw new Error('Insufficient balance')

```

## Bad example
```typescript
const price = Number(amountOut) / Number(amountIn)

```

## Exceptions
Small integer identifiers such as chain IDs can stay as number.
