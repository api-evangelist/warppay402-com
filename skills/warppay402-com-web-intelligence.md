---
name: Extract web, browser, PDF and screenshot content
description: Pick the right WarpPay402 extraction tool for a URL and pay for it once — markdown scrape, headless render, PDF text, full-page screenshot or schema-shaped JSON.
api: openapi/warppay402-com-openapi.yml
operations: [scrapeWeb, browserScrape, extractPdf, renderScreenshot, extractJson]
generated: '2026-09-19'
method: generated
source: openapi/warppay402-com-openapi.yml, well-known/warppay402-com-x402-manifest.json, mcp/warppay402-com-tools-list.json
---

# Extract web, browser, PDF and screenshot content

All five are `POST` operations on `https://api.warppay402.com` with a JSON body and the x402 pay-per-call flow (see `warppay402-com-pay-per-call-x402.md`). Prices are the served manifest values on 2026-09-19.

| Need | operationId | Path | Body | Price (USDC) |
|---|---|---|---|---|
| Static page -> Markdown for an LLM context | `scrapeWeb` | `/api/v1/tools/web-scraper` | `{"url"}` | 0.001 |
| JS-rendered page (SPA, anti-bot) -> text | `browserScrape` | `/api/v1/tools/browser-scraper` | `{"url"}` | 0.005 |
| Public PDF -> plain-text preview | `extractPdf` | `/api/v1/tools/pdf-extractor` | `{"pdfUrl"}` | 0.005 |
| Full-page image for a multimodal model | `renderScreenshot` | `/api/v1/tools/render-screenshot` | `{"url"}` | 0.01 |
| Page -> JSON matching your schema | `extractJson` | `/api/v1/tools/extract-json` | `{"url", "schema"?}` | 0.01 |

## Steps

1. Start with `scrapeWeb`; it is the cheapest and answers most static pages.
2. If the result is empty or a bot wall, escalate to `browserScrape` (residential proxy + Chromium) — 5x the price, so do not default to it.
3. For a `.pdf` URL go straight to `extractPdf` with `pdfUrl`, not `url`.
4. Use `extractJson` when a downstream tool needs typed fields; pass `schema` as a JSON object describing the fields you want (the request schema marks only `url` as required).
5. `renderScreenshot` returns image data for visual evaluation; budget for it separately.

## Rules

- Only **public** URLs: the provider's privacy policy says inputs are processed in real time and target-site policies apply; do not pass authenticated or private links.
- Each call is a fresh payment. Cache results locally; there is no server-side dedupe or idempotency.
- These five are read/extract operations with no on-chain side effects — the one part of this API that is safe to retry if you accept paying again.
