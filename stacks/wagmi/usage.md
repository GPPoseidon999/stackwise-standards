---
id: wagmi/usage
title: wagmi Usage
type: stack
stack: wagmi
concern: wallet
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - useAccount
  - useConnect
  - WagmiProvider
related_rules:
  - viem/usage
  - react-query/data-fetching
---
# wagmi Usage

## When to read
Use this when wagmi manages wallet state and EVM app hooks.

## Core rules
- Create wagmi config once and provide it at the app root.
- Prefer wagmi hooks over ad hoc window.ethereum access.
- Handle disconnected, wrong-chain, and pending-transaction states explicitly.
- Keep wallet actions in dedicated hooks or service layers, not random UI handlers.

## Good example
```tsx
const { address, chainId } = useAccount()
if (!address) return <ConnectWalletButton />

```

## Bad example
```tsx
const address = window.ethereum.selectedAddress

```

## Exceptions
A quick migration shim may read window.ethereum in one isolated adapter while moving toward wagmi.
