---
id: web3-react/usage
title: web3-react Usage
type: stack
stack: web3-react
concern: wallet
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - useWeb3React
  - activate(
  - chainId
related_rules:
  - ethers/usage
---
# web3-react Usage

## When to read
Use this when legacy wallet connection flows still rely on web3-react.

## Core rules
- Keep connectors as shared singletons.
- Wrap connect and disconnect flows in dedicated hooks.
- Handle unsupported chain and user rejection errors explicitly.
- Never assume library is defined before connection succeeds.

## Good example
```typescript
const { account, library } = useWeb3React()
if (!account || !library) return <ConnectWalletButton />

```

## Bad example
```typescript
const { library } = useWeb3React()
const balance = await library.getBalance(address)

```

## Exceptions
Migration periods can keep web3-react and wagmi side by side if boundaries are clear.
