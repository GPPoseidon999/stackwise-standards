---
id: ethers/usage
title: Ethers Usage
type: stack
stack: ethers
concern: web3
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - ethers
  - parseUnits
  - formatUnits
related_rules:
  - bignumber/usage
  - wagmi/usage
---
# Ethers Usage

## When to read
Use this when ethers drives contract reads, writes, or amount conversion.

## Core rules
- Use BigNumber utilities for on-chain amounts.
- Create providers and signers once at app boundaries.
- Wrap contracts in hooks or helpers instead of ad hoc construction in components.
- Handle user rejection and chain errors explicitly.

## Good example
```typescript
const amount = parseUnits(inputValue, decimals)
const display = formatUnits(balance, 18)

```

## Bad example
```typescript
const amount = parseFloat(inputValue) * 1e18

```

## Exceptions
Small scripts can construct a contract inline when there is no UI layer.
