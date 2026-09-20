# @warppay402/warppay402-mcp-tools

Pay-per-use AI tools monetized via x402 USDC micropayments on Base Mainnet (EIP-155:8453) and Solana Mainnet-Beta[cite: 1]. Includes web scraping, headless browsing, blockchain analytics, PDF parsing, full-page screenshots, structured JSON extraction, smart contract verification, and signed attestation data feeds[cite: 1].

---

## Overview

This skill provides autonomous AI agents with instant access to monetized developer endpoints powered by `@warppay402/server`[cite: 1]. Agents can trigger these tools using micropayments without needing API keys or subscriptions[cite: 1].

- **Base URL:** `https://api.warppay402.com`
- **Protocol:** x402 Micropayments[cite: 1]
- **Accepted Assets:** USDC on Base (`0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`) & USDC on Solana (`EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`)[cite: 1]

---

## Available Tools & Pricing

### 1. Public Attestation Data Feed
- **Price:** $0.001 USDC[cite: 1]
- **Endpoint:** `GET https://api.warppay402.com/public_data_feed/{filename}`[cite: 1]
- **Description:** Retrieves signed attestation JSON payloads and data feeds from the public oracle network[cite: 1].

### 2. Pre-Scraped Intelligence Feeds (`data_feeds`)
- **Price:** $0.05 USDC[cite: 1]
- **Endpoint:** `GET https://api.warppay402.com/api/v1/feeds/{feedId}`[cite: 1]
- **Description:** Fetches live, cached market intelligence and anti-bot data reports (e.g., Base APY yield pools, trending pairs)[cite: 1].

### 3. Web Scraper & Markdown Extractor (`web_scraper`)
- **Price:** $0.01 USDC[cite: 1]
- **Endpoint:** `POST https://api.warppay402.com/api/v1/tools/web-scraper`[cite: 1]
- **Payload:** `{"url": "https://example.com"}`[cite: 1]
- **Description:** Scrapes public webpage URLs and strips HTML scripts/navbars to yield clean Markdown for AI context ingestion[cite: 1].

### 4. JavaScript Headless Browser Scraper (`browser_scraper`)
- **Price:** $0.05 USDC[cite: 1]
- **Endpoint:** `POST https://api.warppay402.com/api/v1/tools/browser-scraper`[cite: 1]
- **Payload:** `{"url": "https://example.com"}`[cite: 1]
- **Description:** Executes dynamic client-side JS rendering using distributed proxy worker nodes[cite: 1].

### 5. Base Wallet & Token Analytics (`base_analytics`)
- **Price:** $0.02 USDC[cite: 1]
- **Endpoint:** `POST https://api.warppay402.com/api/v1/tools/base-analytics`[cite: 1]
- **Payload:** `{"address": "0x556c77792642e8ff95ec930ffb8d46a76579126e"}`[cite: 1]
- **Description:** Queries Base Mainnet for current ETH balance, nonce, and account transaction metrics[cite: 1].

### 6. PDF Document Extractor (`pdf_extractor`)
- **Price:** $0.05 USDC[cite: 1]
- **Endpoint:** `POST https://api.warppay402.com/api/v1/tools/pdf-extractor`[cite: 1]
- **Payload:** `{"pdfUrl": "https://example.com/document.pdf"}`[cite: 1]
- **Description:** Downloads and parses text content directly from hosted PDF files[cite: 1].

### 7. Full-Page Render & Screenshot (`render_screenshot`)
- **Price:** $0.10 USDC[cite: 1]
- **Endpoint:** `POST https://api.warppay402.com/api/v1/tools/render-screenshot`[cite: 1]
- **Payload:** `{"url": "https://example.com"}`[cite: 1]
- **Description:** Generates rendered full-page web screenshot image data[cite: 1].

### 8. Structured JSON Schema Extractor (`extract_json`)
- **Price:** $0.15 USDC[cite: 1]
- **Endpoint:** `POST https://api.warppay402.com/api/v1/tools/extract-json`[cite: 1]
- **Payload:** `{"url": "https://example.com", "schema": {}}`[cite: 1]
- **Description:** Extracts structured data matching specified target schemas from web pages[cite: 1].

### 9. Base Smart Contract Verifier (`smart_contract_verifier`)
- **Price:** $0.35 USDC[cite: 1]
- **Endpoint:** `POST https://api.warppay402.com/api/v1/tools/smart-contract-verifier`[cite: 1]
- **Payload:** `{"address": "0x456CdEC6ccf1FE853563a0fBa2BA72DE9266aD0E"}`[cite: 1]
- **Description:** Evaluates Basescan verification status, compiler options, ABI definitions, and proxy implementations[cite: 1].

---

## Discovery & Manifest Routes

- **A2A Agent Manifest:** `GET https://api.warppay402.com/.well-known/agent.json`[cite: 1]
- **MCP Manifest:** `GET https://api.warppay402.com/.well-known/mcp.json`[cite: 1]
- **OpenAPI Specification:** `GET https://api.warppay402.com/openapi.json`[cite: 1]
- **LLMs Text Interface:** `GET https://api.warppay402.com/llms.txt`[cite: 1]