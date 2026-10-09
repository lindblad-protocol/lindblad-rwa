# Evidence: Arbitrum Sepolia (chain ID 421614)

All items below are **public chain data**. They can be checked on [sepolia.arbiscan.io](https://sepolia.arbiscan.io) or with any Arbitrum Sepolia RPC endpoint. Every transaction has status 1 (success). At execution time each one was verified on two independent RPC providers.

## Contracts

| Role | Address |
|---|---|
| Governance Safe (2-of-3), fee recipient | [`0x8591605a68974beb1be5e4963e7451aa01c3216e`](https://sepolia.arbiscan.io/address/0x8591605a68974beb1be5e4963e7451aa01c3216e) |
| Issuance and trade authority Safe (2-of-3) | [`0xa4c249dd35a8649182a40e79d12b630a8be9b8b4`](https://sepolia.arbiscan.io/address/0xa4c249dd35a8649182a40e79d12b630a8be9b8b4) |
| tLICO token (testnet) | [`0xb2dce511b798b5975efb2691dce610742e089bc2`](https://sepolia.arbiscan.io/address/0xb2dce511b798b5975efb2691dce610742e089bc2) |
| DvP settlement | [`0x9e35e8ce0ab155a48847c354f184e52f3fd9ba8b`](https://sepolia.arbiscan.io/address/0x9e35e8ce0ab155a48847c354f184e52f3fd9ba8b) |
| TEST regression asset (unused in USDC mode) | [`0xfc7a0bd4adb0f69e1dfdbe45a6a45fda5d8a4761`](https://sepolia.arbiscan.io/address/0xfc7a0bd4adb0f69e1dfdbe45a6a45fda5d8a4761) |
| Circle USDC (Arbitrum Sepolia; third party) | [`0x75faf114eafb1bdbe2f0316df893fd58ce46aa4d`](https://sepolia.arbiscan.io/address/0x75faf114eafb1bdbe2f0316df893fd58ce46aa4d) |

> **Source verification on Arbiscan** of the Lindblad contracts is **pending**. Until then, Arbiscan shows the bytecode only.

## Transactions (11)

| # | Stage | Step | Tx | Block | Gas used |
|---|---|---|---|---|---|
| 1 | Deployment | create governance Safe (2-of-3) | [`0x9def97b5…6a370`](https://sepolia.arbiscan.io/tx/0x9def97b517416320616bc06b5b55f691843f15e0033c6e33c545af57f796a370) | 316,924,411 | 305,871 |
| 2 | Deployment | create authority Safe (2-of-3) | [`0x765eb3d7…7ec3`](https://sepolia.arbiscan.io/tx/0x765eb3d7cb6ea2d63dbe04d35553ac476701ce1a8d28d6411648b7cc07497ec3) | 316,930,449 | 305,871 |
| 3 | Deployment | deploy tLICO token | [`0x20b332be…4d520a`](https://sepolia.arbiscan.io/tx/0x20b332be67779afec2f75aa4320f13728948025c8c7aaca8243a0fd57f4d520a) | 316,934,102 | 2,511,438 |
| 4 | Deployment | deploy DvP settlement | [`0x88c986d6…f348e3`](https://sepolia.arbiscan.io/tx/0x88c986d6ec47a310356be5ecc17767077462f21890c2744c1e03820267f348e3) | 316,938,776 | 1,229,928 |
| 5 | Deployment | deploy TEST regression asset | [`0xfdb41634…b8ae2`](https://sepolia.arbiscan.io/tx/0xfdb416340a3b65092fea7a5cfa4e16d648ce6a50ebb4769249c6208d4b9b8ae2) | 316,946,992 | 484,710 |
| 6 | Governance | `setControls(63)` via governance Safe 2-of-3 | [`0x0a887b85…77940f`](https://sepolia.arbiscan.io/tx/0x0a887b85b5774127848e67c1f4ba2132b80d00e6055c054f3374baf3bd77940f) | 316,964,192 | 123,088 |
| 7 | Governance | `setSettlementContract(DvP)` via governance Safe 2-of-3 | [`0xa4f787c0…f0fd23`](https://sepolia.arbiscan.io/tx/0xa4f787c0d6be069c21dd58a3447be2dcfbcff7356b41d89b64b54c5a08f0fd23) | 316,970,671 | 86,109 |
| 8 | Tokenization | mint 1.000 tLICO to the producer (authority Safe, EIP-1271) | [`0x4c03c441…b378ef`](https://sepolia.arbiscan.io/tx/0x4c03c44162902c6374b920a1e4b2874a486c81e8629c6ae7a3563bd91cb378ef) | 317,062,197 | 139,411 |
| 9 | Sale | TRADE_LOCK commit (authority Safe 2-of-3) | [`0xfec6882c…ced3f2`](https://sepolia.arbiscan.io/tx/0xfec6882ccc13702f5c93743df02c71ab2d072320e946e647e7a7a15158ced3f2) | 317,076,675 | 186,541 |
| 10 | Sale | exact USDC approve (10.050000) to the DvP | [`0x213343bf…cf7617`](https://sepolia.arbiscan.io/tx/0x213343bf03024bc9b46857d4ad334e88d58d655d8f95569de89fde59cccf7617) | 317,083,883 | 55,437 |
| 11 | Sale | **atomic DvP settlement** (authority Safe 2-of-3) | [`0x56835abc…460f7b`](https://sepolia.arbiscan.io/tx/0x56835abc29a0614d54720e83cd1779deae18c02fe5f1f1baf8466f2438460f7b) | 317,084,903 | 227,626 |

Total gas: 5,656,030.

## Results you can check

- **Token:** `totalSupply()` = 1.000 tLICO; `controls()` = 63; `settlementContract()` = the DvP address.
- **Settlement (tx 11):** 0.010 tLICO to the buyer; 10.000000 USDC to the producer; 0.050000 USDC (50 bps test fee) to the governance Safe; the buyer's remaining USDC allowance to the DvP is 0.
- **Replay protection:** token `issuanceNonceUsed(1)` and DvP `tradeNonceUsed(1)` both return `true`; a second settlement of the same trade is refused.

## Check it from the command line (Foundry `cast`, read-only)

```bash
RPC=https://sepolia-rollup.arbitrum.io/rpc
TOKEN=0xb2dce511b798b5975efb2691dce610742e089bc2
DVP=0x9e35e8ce0ab155a48847c354f184e52f3fd9ba8b
cast call $TOKEN "controls()(uint256)"           --rpc-url $RPC   # 63
cast call $TOKEN "settlementContract()(address)" --rpc-url $RPC   # the DvP address
cast call $TOKEN "totalSupply()(uint256)"        --rpc-url $RPC   # 1.000 tLICO in base units
cast call $DVP   "tradeAuthority()(address)"     --rpc-url $RPC   # authority Safe 0xa4c2…b8b4
cast call $DVP   "feeRecipient()(address)"       --rpc-url $RPC   # governance Safe 0x8591…216e
cast call $TOKEN "issuanceNonceUsed(uint256)(bool)" 1 --rpc-url $RPC   # true (issuance replay protection)
cast call $DVP   "tradeNonceUsed(uint256)(bool)" 1    --rpc-url $RPC   # true (settlement replay protection)
cast receipt 0x56835abc29a0614d54720e83cd1779deae18c02fe5f1f1baf8466f2438460f7b status --rpc-url $RPC   # 1 (success)
```

## Machine-readable evidence and verification snapshot

- [`evidence/proof-manifest.lico-demo-001.public.json`](../evidence/proof-manifest.lico-demo-001.public.json): the contracts and the 11 transactions in machine-readable form.
- **Verification snapshot** of the instance at block height 317,129,498: **not included in this repository**. It is available to authorized evaluators on request. Its SHA-256 (file bytes) is:

```
a7efd73622037492467bae9b9f622d6c18e21a82780e24bce17f918f460fb0f2
```

An evaluator who receives the file can check it with `shasum -a 256 <file>`.

## Scope

- **Testnet only**, synthetic lot and issuers. No real value is represented.
- The USDC used is Circle's testnet USDC and has no value. The 50 bps fee is a **test** parameter, not a commercial fee policy.
