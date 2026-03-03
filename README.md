# Lendf.Me ERC777 Reentrancy via imBTC — PoC

> **Educational Purpose Only** — This PoC is created for security research and education
> purposes only. It runs against a fork, not mainnet.

## Quick Start

```bash
git clone https://github.com/NomosLabs-Security/poc-lendf-me-2020
cd poc-lendf-me-2020
forge install foundry-rs/forge-std --no-git
forge test -vvvv
```

## Details

- **Exploit Date:** 2020-04-19
- **Fork Block:** #9899738
- **Expected Output:** ERC777 tokensReceived callback reentrancy inflating collateral balance
- **Full Analysis:** [NomosLabs Security Intelligence Archive](https://nomoslabs.io/archive/lendf-me-2020)

## Description

Lendf.Me (dForce) accepted imBTC as collateral, an ERC777-compatible token.
During withdrawal, the ERC777 `tokensReceived` callback allowed the attacker
to re-enter the supply function before the withdraw balance was updated,
inflating their recorded collateral. This drained ~$25M from the protocol.

## License

MIT — For educational use only.
