# Architecture (conceptual)

This document describes **what each stage guarantees and who controls it**. It does not describe internal algorithms, rule parameters or implementation details. Those are proprietary.

```
 ┌──────────────────────────┐   ┌──────────────────────┐   ┌───────────────────────┐   ┌──────────────────┐
 │ 1 PHYSICAL ASSET          │   │ 2 TOKENIZATION        │   │ 3 MARKET ACCESS        │   │ 4 CAPITAL         │
 │   ASSURANCE               │──▶│                       │──▶│                        │──▶│                  │
 │ evidence → LAS →          │   │ allocation-bound      │   │ authorized trade lock  │   │ collateral and    │
 │ Physical NAV              │   │ issuance (Safe 2/3)   │   │ → atomic DvP (USDC)    │   │ financing         │
 └──────────────────────────┘   └──────────────────────┘   └───────────────────────┘   └──────────────────┘
        off-chain, authoritative          on-chain                  on-chain                not executed
```

## 1 · Physical Asset Assurance

- **Inputs:** signed evidence from independent, authorized third parties. In the demonstration these are a warehouse receipt, a weight ticket and a laboratory certificate. Each issuer signs with its own key (EIP-712). An issuer is accepted only after a 2-of-3 Safe approval (EIP-1271).
- **LAS (Lindblad Assurance Standard):** a deterministic evaluation of that evidence. It returns a verdict (for example, VERIFIED) and a certified quantity. See [`ASSURANCE.md`](ASSURANCE.md).
- **Physical NAV:** the quantity that is eligible to back tokens. It can never exceed the certified quantity.
- **RWA Core** is the authoritative off-chain record of lots, evidence, assurance results, NAV and allocations. Every record is content-addressed (hashed).

## 2 · Tokenization

- Issuance is possible only against an **active allocation** of eligible Physical NAV.
- Each issuance needs an **authorization signed by a 2-of-3 Safe** (issuance authority) that is bound to that allocation. The token contract checks the authorization and refuses a replay (`issuanceNonceUsed`).
- Token settings (control flags, settlement contract) are set through a separate **governance Safe** (2-of-3).

## 3 · Market Access

- A market access profile defines what may trade: the settlement asset (USDC only in the demonstration), the minimum quantity and the fee.
- A trade is first fixed as a **TRADE_LOCK**, committed with the trade authority's 2-of-3 approval.
- The buyer approves the **exact** payment amount.
- Settlement is a single **atomic DvP** transaction. The token goes to the buyer, the principal goes to the producer and the fee goes to the governance Safe, which is the DvP contract's immutable fee recipient. Either everything happens or nothing does. A settled trade cannot be settled again (`tradeNonceUsed`).

## 4 · Capital

Collateral and financing flows are **designed but not executed** in this demonstration. The Marketplace Demo shows them only as an illustrative calculator. No lender, no credit and no collateral lock exist.

## Verification

A **verification snapshot** of the instance can be regenerated from chain data at a fixed L1-finalized block height and compared byte for byte. Two independent RPC providers must agree at that height. The snapshot file is available to authorized evaluators on request; its SHA-256 is given in [`EVIDENCE.md`](EVIDENCE.md).

## Trust boundaries

| Component | Controlled by | Public? |
|---|---|---|
| Evidence signatures (issuers) | each third-party issuer | the hashes only |
| LAS, Physical NAV, RWA Core | Lindblad | results only; rules and code are proprietary |
| Issuance / trade authority | 2-of-3 Safe | yes (on-chain) |
| Governance | 2-of-3 Safe | yes (on-chain) |
| Token, DvP contracts | immutable deployment | addresses and transactions yes; source publication pending |
