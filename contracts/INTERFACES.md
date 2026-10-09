# Interface documentation (observable functions; no source code)

> Read-only functions below were **called on Arbitrum Sepolia** and their selectors were found in the deployed bytecode (check of 2026-10-09). State-changing calls are listed by the **selector actually used** in the demonstration transactions. Exact parameter lists of state-changing functions are not published here. This document grants no license.

## tLICO token: `0xb2dce511b798b5975efb2691dce610742e089bc2`

| Function | Selector | Observed |
|---|---|---|
| `totalSupply()` | `0x18160ddd` | 1.000 tLICO after the single issuance (18 decimals) |
| `controls()` | `0x8c878e52` | `63`: set through the governance Safe (tx 6) |
| `settlementContract()` | `0xea42418b` | the DvP contract: set through the governance Safe (tx 7) |
| `setSettlementContract(address)` | `0x3719fd05` | state-changing; called via the governance Safe 2-of-3 (tx 7) |
| `issuanceNonceUsed(uint256)` | `0xfdebff19` | `true` for nonce 1 (replay protection for issuance) |
| control-flags setter | — | state-changing; called via the governance Safe 2-of-3 (tx 6) |
| issuance (mint under a Safe-approved authorization) | `0x488c038b` | 1.000 tLICO minted to the producer (tx 8) |
| TRADE_LOCK commit | `0x6d3ec581` | trade terms fixed with the authority Safe's 2-of-3 approval (tx 9) |

## DvP settlement: `0x9e35e8ce0ab155a48847c354f184e52f3fd9ba8b`

| Function | Selector | Observed |
|---|---|---|
| `tradeAuthority()` | `0x58ec99a8` | the issuance and trade authority Safe `0xa4c2…b8b4` |
| `feeRecipient()` | `0x46904840` | the governance Safe `0x8591…216e` (immutable) |
| `tradeNonceUsed(uint256)` | `0xe575acbd` | `true` for trade 1 (replay protection for settlement) |
| `settleTradeLock` (atomic delivery-versus-payment) | `0x65c67e40` | token to the buyer, 10.000000 USDC to the producer, 0.050000 USDC fee to the governance Safe (tx 11) |

## Not included

Source code, internal libraries, deployment tooling, tests and every off-chain component.
