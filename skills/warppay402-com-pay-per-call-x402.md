---
name: Call a WarpPay402 tool with an x402 micropayment
description: The one flow every WarpPay402 operation shares — send the request, receive the 402 challenge, sign a USDC transfer, retry with PAYMENT-SIGNATURE. Grounded in the web scraper; identical for all 19 operations.
api: openapi/warppay402-com-openapi.yml
operations: [scrapeWeb, getDataFeed, getPublicDataFeed]
generated: '2026-09-19'
method: generated
source: openapi/warppay402-com-openapi.yml, conventions/warppay402-com-conventions.yml, errors/warppay402-com-problem-types.yml, live 402 observed 2026-09-19
---

# Call a WarpPay402 tool with an x402 micropayment

WarpPay402 has no API keys. Every operation in `openapi/warppay402-com-openapi.yml` answers `402 Payment Required` until the request carries a signed USDC payment. Base URL: `https://api.warppay402.com`.

## Steps

1. **Send the request unpaid.** `POST /api/v1/tools/web-scraper` (`scrapeWeb`) with body `{"url": "<public URL>"}`. Expect **402**.
2. **Read the challenge.** The body (and the base64 `PAYMENT-REQUIRED` header) is an x402 v2 object: `accepts[]` lists one option per network — `network` (CAIP-2: `eip155:8453` Base, `solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp`, `eip155:42161` Arbitrum One, `eip155:5042` Arc), `asset` (USDC contract or mint), `amount` in 6-decimal base units (`"1000"` = $0.001), `payTo`, `maxTimeoutSeconds: 300`. `extensions.bazaar.schema` is the JSON Schema of the expected input.
3. **Choose a network you hold USDC on and sign.** Base/Arbitrum: EIP-712 `TransferWithAuthorization` (gasless). Solana: SPL transfer. Arc: native USDC value transfer. The `@warppay402/sdk` `WarpPayClient({ privateKey, solanaPrivateKey })` does this automatically; so does the `@warppay402/mcp-client` bridge for MCP.
4. **Retry the identical request within 300 seconds** with the signed payload in `PAYMENT-SIGNATURE`. A settled call returns **200** with a `PAYMENT-RESPONSE` header; the 200 body is undocumented in the spec beyond "Success" (the SDK README shows `{ title, markdown }` for the scraper).
5. **Feeds are GETs with the same dance.** `GET /api/v1/feeds/{feedId}` (`getDataFeed`) and `GET /public_data_feed/{filename}` (`getPublicDataFeed`) 402 first, then 200 or 404 (`"404 Not Found"`, text/plain) for an unknown id.

## Rules an agent must respect

- **No idempotency.** A retried request after a timeout is a second paid call; the nonce store only rejects the *same* payment signature. See `conventions/warppay402-com-conventions.yml`.
- **No refunds and no reversal.** The micropayment is final on settlement (Terms of Service, section 1). Check `amount` against your budget before signing — prices range from 100 base units ($0.0001) to 5,000,000 ($5.00), and the homepage quotes some prices ~10x higher than the served manifest; trust the challenge.
- **Never send a wallet key anywhere but the local signer.** The SDK and bridge read `CUSTOMER_PRIVATE_KEY` from the environment; the API never asks for it.
- **Rate limits are undocumented** (Cloudflare edge + x402-guard); back off on any 429 or Cloudflare challenge page.
