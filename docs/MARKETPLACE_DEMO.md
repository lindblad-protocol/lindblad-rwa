# F5 Marketplace Demo

A static, single-page demonstration of the producer and buyer experience built on top of the Arbitrum Sepolia demonstration.

**Access:** restricted preview. The demo runs behind access control and is not publicly available; no link is published.

## Four kinds of content, always labelled

| Label | Meaning |
|---|---|
| **Executed on testnet** | Real Arbitrum Sepolia transactions (see [`EVIDENCE.md`](EVIDENCE.md)), each linked to Arbiscan |
| **Core record** | A result recorded by the RWA Core and included in the verification snapshot |
| **Simulation · this session** | Your own actions in the page. Nothing is sent anywhere; state lives only in the open browser tab and resets on reload |
| **Not executed · illustrative** | Features shown for explanation only (for example, financing) |

Simulated quantities are **never added** to on-chain balances.

## Journeys

**Producer:** Asset → Tokenize → My tokens → Sell **or** Finance → Proof.
- *Asset* shows the certified quantity (19.950 t) and the eligible Physical NAV (19.900 t).
- *Tokenize* simulates new issuance up to the eligible remainder. The only real issuance is the 1.000 tLICO mint, which is linked.
- *Sell* publishes a simulated listing with principal, test fee and buyer total shown separately. The price is **producer-defined**; no market price reference is used.
- *Finance* is an illustrative calculator (quantity × assumed valuation, haircut, LTV). There is no lender, no credit and no collateral lock.

**Buyer:** Marketplace → Offer → Proof → simulated purchase, offer or counter-offer.

**Proof · Verify** is open to both roles. It separates what Arbiscan proves (the transactions happened) from what the Lindblad verification adds (the link between the verified asset and the tokens). Authorized viewers can download the verification snapshot there.

## What the demo never does

It never connects a wallet, requests a signature, sends a transaction or calls an external service. The page loads no external script, and a strict Content Security Policy enforces that.
