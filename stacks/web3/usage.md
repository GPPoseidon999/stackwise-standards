---
id: web3/usage
title: web3.js Usage
type: stack
stack: web3
concern: web3
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - new Web3
  - web3.eth
  - Contract(
related_rules:
  - bignumber/usage
  - security/input-validation
---
# web3.js Usage

## When to read
Use this when legacy EVM integrations still rely on web3.js.

## Core rules
- Create providers and contracts in shared helpers, not inline across components.
- Treat on-chain values as precise numeric types, not JS numbers.
- Handle user rejection, RPC failure, and chain mismatch explicitly.
- Keep web3.js usage isolated if the codebase is migrating to viem or ethers.

## Good example
```typescript
const web3 = new Web3(provider)
const contract = new web3.eth.Contract(abi, address)
```

## Bad example
```typescript
const amount = Number(inputValue) * 1e18
const contract = new Web3(window.ethereum).eth.Contract(abi, address)
```

## Exceptions
Short migration shims can stay thin while newer web3 layers take over.
