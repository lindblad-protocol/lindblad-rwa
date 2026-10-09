# Status matrix

| Capability | Implemented | Demonstrated on testnet (verifiable) | Simulated in the demo | In development | Future objective |
|---|---|---|---|---|---|
| Third-party evidence intake (3 independent, authorized issuers) | ✓ | ✓ (issuer activation via Safe 2-of-3) | — | | |
| LAS verdict + certified quantity | ✓ | ✓ (result in the verification snapshot) | — | | |
| Physical NAV capped by the certified quantity; single allocation | ✓ | ✓ | — | | |
| Allocation-bound issuance (Safe 2-of-3) | ✓ | ✓ (1.000 tLICO) | additional quantities | | |
| Market access profile (USDC only, minimum quantity, fee) | ✓ | ✓ | listings, offers, counter-offers | | |
| TRADE_LOCK + atomic DvP in USDC | ✓ | ✓ (one trade, 0.010 tLICO) | purchases | | |
| Replay protection (issuance and trade) | ✓ | ✓ | — | | |
| Verification snapshot (two providers, fixed block height; on request) | ✓ | ✓ | — | | |
| Contract source verification on Arbiscan | | | | pending | |
| Collateral / financing | — | — | illustrative calculator | — | ✓ |
| Redemption / physical release | — | — | — | ✓ | |
| Real lots, real issuers, real counterparties | — | — | — | — | ✓ |
| Legal structure, custody, regulated use | — | — | — | — | ✓ |
| Mainnet deployment of this flow | — | — | — | — | ✓ |

## Limits of the demonstration

- **Synthetic** lot and issuers; **testnet** only; one trade of 0.010 tLICO.
- Producer-defined prices and a test fee. No market price reference.
- No lender, no financing, no institutional participant.
- No statement in this repository implies regulatory approval, licensing or adoption by any institution.
