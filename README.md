# WarpPay402 Studio

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

WarpPay402 Studio operates WarpPay402, a non-custodial x402 monetization gateway and hosted MCP tool suite for autonomous AI agents. Nineteen pay-per-use tools — Markdown and headless-browser web scraping, PDF text extraction, full-page screenshots, schema-driven JSON extraction, Base and Arc network analytics, Basescan contract verification, Aerodrome yield, swap, concentrated-liquidity and veAERO routes, contract deployment factories for Base, Solana and Arc, and Circle CCTP bridging — are exposed three ways from one host: a REST API described by an OpenAPI 3.1 document at api.warppay402.com/openapi.json, a hosted MCP server at api.warppay402.com/mcp (Streamable HTTP and legacy SSE, 19 tools listed anonymously), and an agent card at /.well-known/agent.json. There are no API keys: every call answers HTTP 402 with an x402 v2 PAYMENT-REQUIRED challenge and settles in USDC on Base, Solana, Arbitrum One or Arc (prices from $0.0001 to $5.00 per call), with flat-rate access tokens offered by email. The company also publishes @warppay402/server, the x402 middleware its Self-Serve Gateway is built on, so other developers can wrap their own APIs and MCP tools in the same 402 challenge, and @warppay402/sdk plus a stdio MCP bridge for Cursor, Windsurf and Claude Desktop. The site is a Google Sites page; all documentation lives on it and in the npm READMEs.

**Areas:** x402 · Micropayments · AI Agents · MCP · A2A · Agent-Native · Web Scraping · Data Extraction · Blockchain · DeFi · Base · Solana

## WarpPay402 Studio on APIs.io

Everything profiled for WarpPay402 Studio is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/warppay402-com/](https://apis.io/providers/warppay402-com/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [WarpPay402 MCP Server](https://apis.io/apis/warppay402-com/warppay402-mcp-server/) — Hosted MCP server at https://api.warppay402.com/mcp exposing the same 19 tools as the REST API (public_data_feed, data_feeds, web_scraper, browser_scraper,…
- [WarpPay402 Studio Feeds API](https://apis.io/apis/warppay402-com/warppay402-com-feeds-api/) — The Feeds API from WarpPay402 Studio — 1 operation(s) for feeds.
- [WarpPay402 Studio Public Data Feed API](https://apis.io/apis/warppay402-com/warppay402-com-public-data-feed-api/) — The Public Data Feed API from WarpPay402 Studio — 1 operation(s) for public data feed.
- [WarpPay402 Studio Tools API](https://apis.io/apis/warppay402-com/warppay402-com-tools-api/) — The Tools API from WarpPay402 Studio — 17 operation(s) for tools.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [WarpPay402 Backend](https://apis.io/servers/warppay402-com/warppay402-backend/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Warppay402 Com Agentic Access](https://apis.io/agentic-access/warppay402-com/warppay402-com-agentic-access/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Warppay402 Com Openapi Overlay](https://apis.io/overlays/warppay402-com/warppay402-com-openapi-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Warppay402 Com Authentication](https://apis.io/security/warppay402-com/warppay402-com-authentication/)
- [Warppay402 Com Domain Security](https://apis.io/security/warppay402-com/warppay402-com-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Warppay402 Com Plans Pricing](https://apis.io/plans/warppay402-com/warppay402-com-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Warppay402 Com Rate Limits](https://apis.io/rate-limits/warppay402-com/warppay402-com-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://warppay402.com/)
- [Terms of service](https://www.warppay402.com/terms-of-service)
- [Privacy policy](https://www.warppay402.com/privacy-policy)
- [GitHub](https://github.com/Warppay402)

## API Evangelist rating

**Kin Score 40.6** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 39.8 |
| Contract governance | 18.2 |
| Operational transparency | 5.3 |
| Developer ergonomics | 45.2 |
| Access clarity | 52.6 |

**Agent readiness 32.6** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | flavored (partial credit) |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 24.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/warppay402-com/](https://apis.io/providers/warppay402-com/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for WarpPay402 Studio: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/warppay402-com/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
