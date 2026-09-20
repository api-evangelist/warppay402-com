---
name: Read on-chain state before any DeFi or deployment write
description: Use WarpPay402's cheap read tools (yields, analytics, contract verifier, Arc telemetry) to check state and cost before paying for an irreversible swap, liquidity, lock, bridge or deployment call.
api: openapi/warppay402-com-openapi.yml
operations: [getAerodromeYields, getBaseAnalytics, getArcAnalytics, queryArcNetworkOracle, verifySmartContract, executeAerodromeSwap, manageAerodromeClamm, manageAerodromeVeaero, bridgeArcCctp, deployBaseContract, deploySolanaContract, deployArcContract]
generated: '2026-09-19'
method: generated
source: openapi/warppay402-com-openapi.yml, mcp/warppay402-com-tools-list.json (enum values), conventions/warppay402-com-conventions.yml (reversibility)
---

# Read on-chain state before any DeFi or deployment write

Seven WarpPay402 operations act on public mainnets and **cannot be reversed** (`conventions/warppay402-com-conventions.yml` -> `reversibility: none`). Five cheap reads exist to de-risk them. Base URL `https://api.warppay402.com`; every call is x402-paid.

## Reads (safe, repeatable, $0.001–$0.10)

- `getAerodromeYields` — `GET /api/v1/tools/aerodrome-yields` (no body): top Aerodrome pools with APY and TVL on Base. $0.003.
- `getBaseAnalytics` — `POST /api/v1/tools/base-analytics` `{"address"}`: ETH balance and nonce of a Base address. $0.002.
- `getArcAnalytics` — `POST /api/v1/tools/arc-analytics` (empty body): Arc block height, gas, node metrics. $0.001.
- `queryArcNetworkOracle` — `POST /api/v1/tools/arc-network-query` `{"includeGasTrends"?, "checkMerchantAccount"?}`: Arc RPC latency, gas in Gwei, native USDC balance, nonce. $0.10.
- `verifySmartContract` — `POST /api/v1/tools/smart-contract-verifier` `{"address"}`: Basescan verification status, ABI, proxy implementation. $0.02.

## Writes (irreversible — confirm with a human unless explicitly delegated)

- `executeAerodromeSwap` — `POST /api/v1/tools/aerodrome-swap` `{"tokenIn","tokenOut","amountIn","decimalsIn","isStable"}` (all required). $0.01 fee plus the swap itself.
- `manageAerodromeClamm` — `POST /api/v1/tools/aerodrome-clamm` `{"action": mint|increaseLiquidity|decreaseLiquidity|collect, ...}`. $0.01.
- `manageAerodromeVeaero` — `POST /api/v1/tools/aerodrome-veaero` `{"action": createLock|increaseAmount|increaseUnlockTime|vote|claimBribes, ...}`. $0.01.
- `bridgeArcCctp` — `POST /api/v1/tools/arc-cctp-bridge` `{"amountUsdc","destinationChain": ethereum|avalanche|optimism|arbitrum|solana|base,"recipientAddress"}`. $0.25.
- `deployBaseContract` / `deployArcContract` — `{"contractType": escrow|bounty|subscription(|pendle on Base)}`. $5.00 each.
- `deploySolanaContract` — `{"contractType": spl_escrow|cnft_badge|raydium_vault, "params"?}`. $5.00.

## Steps

1. `verifySmartContract` on any token or contract address you are about to swap into, LP against or bridge to; refuse unverified or proxy-masked targets unless the user accepts.
2. `getAerodromeYields` before `manageAerodromeClamm` / `manageAerodromeVeaero` to choose a pool with real TVL.
3. `getBaseAnalytics` / `queryArcNetworkOracle` to confirm the executing wallet has balance and the network is healthy (gas, latency) — a failed on-chain action still costs the WarpPay402 fee.
4. Present amount, network, recipient and the WarpPay402 fee to the user; only then sign the 402 challenge for the write.
5. Never retry a write on timeout without checking chain state first — there is no idempotency key, and a retry is a second transaction.
