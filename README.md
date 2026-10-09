# Lindblad Protocol — Verifiable Physical Assets for On-Chain Markets

Physical asset verification, tokenization, and market access infrastructure. Architecture, verifiable deployments, demonstrations, and development milestones.

**Lindblad is RWA infrastructure.** It lets a token exist **only** for a physical quantity that independent parties have verified, and lets that token trade **only** through authorized, atomic delivery-versus-payment.

> **Current verifiable deployment: Arbitrum Sepolia (testnet, chain 421614).** The architecture is not tied to a single chain; this is the current deployment of the full flow, built on a **synthetic** lithium-carbonate lot and **synthetic** issuers. Nothing here represents a real asset or counterparty, and nothing is an offer of any financial product.

---

## The idea in 30 seconds

A token on-chain proves that it was minted, not that the asset behind it was checked first. Lindblad puts the check **before** the token:

```
1 PHYSICAL ASSURANCE         2 TOKENIZATION              3 MARKET ACCESS               4 CAPITAL
independent evidence    →    mint only against an   →    authorized trade lock    →    collateral / financing
→ assurance verdict          allocation of verified      → atomic DvP in USDC          (designed; not executed)
→ eligible quantity          quantity (Safe 2-of-3)      (Safe 2-of-3)
   off-chain, hashed            on-chain                    on-chain
```

## Verify it yourself (2 minutes, Arbiscan)

| What | Proof |
|---|---|
| **1.000 tLICO minted** under a 2-of-3 Safe authorization | [tx `0x4c03c441…b378ef`](https://sepolia.arbiscan.io/tx/0x4c03c44162902c6374b920a1e4b2874a486c81e8629c6ae7a3563bd91cb378ef) |
| **Trade terms locked** by the trade-authority Safe | [tx `0xfec6882c…ced3f2`](https://sepolia.arbiscan.io/tx/0xfec6882ccc13702f5c93743df02c71ab2d072320e946e647e7a7a15158ced3f2) |
| **Atomic DvP:** 0.010 tLICO ↔ 10.050000 USDC (10.000000 to the producer, 0.050000 fee to the governance Safe) | [tx `0x56835abc…460f7b`](https://sepolia.arbiscan.io/tx/0x56835abc29a0614d54720e83cd1779deae18c02fe5f1f1baf8466f2438460f7b) |
| Token / DvP contracts | [tLICO `0xb2dc…9bc2`](https://sepolia.arbiscan.io/address/0xb2dce511b798b5975efb2691dce610742e089bc2) · [DvP `0x9e35…ba8b`](https://sepolia.arbiscan.io/address/0x9e35e8ce0ab155a48847c354f184e52f3fd9ba8b) |

All **11 transactions**, the 6 contracts and copy-paste `cast` checks are in [**docs/EVIDENCE.md**](docs/EVIDENCE.md).

## What is real, and what is not

| | Where | Status |
|---|---|---|
| Deployment, governance wiring, mint, trade lock, USDC approve, atomic DvP | Arbitrum Sepolia | **Executed on testnet**: 11 transactions, all successful |
| Evidence from 3 independent issuers → verified result, **19.950 t certified**, **19.900 t eligible** | Lindblad RWA Core (off-chain) | **Recorded**: hash-anchored; covered by a verification snapshot, available on request |
| Listings, offers, counter-offers, extra issuance in the **F5 Marketplace Demo** | the user's browser | **Simulated**: nothing is sent; see [docs/MARKETPLACE_DEMO.md](docs/MARKETPLACE_DEMO.md) |
| Financing / collateral | — | **Not executed**: illustrative only |
| Real lots, real issuers, legal structure, mainnet | — | **Future** (see [docs/STATUS.md](docs/STATUS.md)) |

## Current deployment: why Arbitrum

- **Low cost:** all 11 transactions, including deploying every contract, used about 5.66 M gas at about 0.1 gwei.
- **Safe** multisig for governance and for issuance / trade authority (EIP-1271 approvals).
- **Native USDC** (Circle) for settlement.
- **Verifiable:** every result was cross-checked on two independent RPC providers.

## Repository map

| | |
|---|---|
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | the four stages, who controls what, trust boundaries |
| [docs/ASSURANCE.md](docs/ASSURANCE.md) | what the assurance layer (LAS) and Physical NAV guarantee: observable results only |
| [docs/EVIDENCE.md](docs/EVIDENCE.md) | contracts, 11 transactions, on-chain results, `cast` commands |
| [docs/MARKETPLACE_DEMO.md](docs/MARKETPLACE_DEMO.md) | the F5 producer / buyer demo (restricted preview) and how it labels testnet versus simulation |
| [docs/STATUS.md](docs/STATUS.md) | implemented · demonstrated · simulated · in development · future |
| [contracts/INTERFACES.md](contracts/INTERFACES.md) | observable functions of the token and DvP contracts, selectors checked on-chain (no source code) |
| [evidence/](evidence/) | machine-readable proof manifest |

## Not claimed

No real inventory, no institutional adoption, no regulatory approval, no audit, no production deployment. The internal rules of LAS, Physical NAV and the RWA Core are proprietary and are not published here.

---

**Contact:** Lindblad Protocol Inc. · founder@lindblad.io
**License:** © 2026 Lindblad Protocol Inc. All rights reserved. No license is granted; see [NOTICE](NOTICE).
