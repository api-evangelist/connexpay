# ConnexPay

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

ConnexPay is a Milwaukee-founded B2B payments platform that combines merchant acquiring and card issuing in one integration, so a company's incoming customer payments directly fund its outgoing supplier payments with no float in between. An inbound Sale (PayIn) returns an Incoming Transaction Code that funds the virtual cards, ACH credits, push-to-card payouts, checks and international bank-to-bank transfers issued against it (PayOuts). The platform is used heavily in leisure and business travel, advertising and media buying, insurance claims, and embedded-payments software, and is delivered through ten REST APIs — Sales, Purchases, Push to Card, Payment Valet payment instructions, Checkout Session, Merchant Payor, Stop Payment, Chargebacks (CMS), and two Reporting surfaces — plus a browser payments SDK, a Hosted Payment Page, the Bridge operator console, and a 51-event webhook surface called CXP Eventing. ConnexPay is a registered ISO/MSP of The Central Trust Bank and MVB Bank.

**Areas:** Payments · Virtual Cards · Card Issuing · Merchant Acquiring · Payouts · ACH · Travel · B2B Payments · Embedded Payments · Chargebacks · Fintech · Disbursements

## ConnexPay on APIs.io

Everything profiled for ConnexPay is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/connexpay/](https://apis.io/providers/connexpay/)** — or go straight to one of the APIs or properties below.

### APIs (39)

- [ConnexPay Accounting API](https://apis.io/apis/connexpay/connexpay-accounting-api/) — The Accounting API from ConnexPay — 2 operation(s) for accounting.
- [ConnexPay Addendum API](https://apis.io/apis/connexpay/connexpay-addendum-api/) — The Addendum API from ConnexPay — 3 operation(s) for addendum.
- [ConnexPay Authenticate API](https://apis.io/apis/connexpay/connexpay-authenticate-api/) — The Authenticate API from ConnexPay — 1 operation(s) for authenticate.
- [ConnexPay Authonlys API](https://apis.io/apis/connexpay/connexpay-authonlys-api/) — The Authonlys API from ConnexPay — 1 operation(s) for authonlys.
- [ConnexPay Cancel API](https://apis.io/apis/connexpay/connexpay-cancel-api/) — The Cancel API from ConnexPay — 1 operation(s) for cancel.
- [ConnexPay Captures API](https://apis.io/apis/connexpay/connexpay-captures-api/) — The Captures API from ConnexPay — 1 operation(s) for captures.
- [ConnexPay Card Booking API](https://apis.io/apis/connexpay/connexpay-cardbooking-api/) — The CardBooking API from ConnexPay — 1 operation(s) for cardbooking.
- [ConnexPay Cards API](https://apis.io/apis/connexpay/connexpay-cards-api/) — The Cards API from ConnexPay — 2 operation(s) for cards.
- [ConnexPay Chargeback API](https://apis.io/apis/connexpay/connexpay-chargeback-api/) — The Chargeback API from ConnexPay — 2 operation(s) for chargeback.
- [ConnexPay Checkout Sessions API](https://apis.io/apis/connexpay/connexpay-checkout-sessions-api/) — Operations for creating and managing checkout sessions. Checkout sessions are secure server-side objects that contain all payment details for a transaction.…
- [ConnexPay Credit API](https://apis.io/apis/connexpay/connexpay-credit-api/) — The Credit API from ConnexPay — 1 operation(s) for credit.
- [ConnexPay Extended Data API](https://apis.io/apis/connexpay/connexpay-extendeddata-api/) — The ExtendedData API from ConnexPay — 1 operation(s) for extendeddata.
- [ConnexPay Hosted Payment Page Requests API](https://apis.io/apis/connexpay/connexpay-hostedpaymentpagerequests-api/) — The HostedPaymentPageRequests API from ConnexPay — 1 operation(s) for hostedpaymentpagerequests.
- [ConnexPay Issue ACH API](https://apis.io/apis/connexpay/connexpay-issueach-api/) — The IssueACH API from ConnexPay — 2 operation(s) for issueach.
- [ConnexPay Issue Card API](https://apis.io/apis/connexpay/connexpay-issuecard-api/) — The IssueCard API from ConnexPay — 15 operation(s) for issuecard.
- [ConnexPay IssueCard (COPY) API](https://apis.io/apis/connexpay/connexpay-issuecard-copy-api/) — The IssueCard (COPY) API from ConnexPay — 1 operation(s) for issuecard (copy).
- [ConnexPay Merchant Flex Funding API](https://apis.io/apis/connexpay/connexpay-merchantflexfunding-api/) — The MerchantFlexFunding API from ConnexPay — 1 operation(s) for merchantflexfunding.
- [ConnexPay Merchant Payor API](https://apis.io/apis/connexpay/connexpay-merchantpayor-api/) — The MerchantPayor API from ConnexPay — 2 operation(s) for merchantpayor.
- [ConnexPay Merchants API](https://apis.io/apis/connexpay/connexpay-merchants-api/) — The Merchants API from ConnexPay — 2 operation(s) for merchants.
- [ConnexPay Merchant Self Service Funding API](https://apis.io/apis/connexpay/connexpay-merchantselfservicefunding-api/) — The MerchantSelfServiceFunding API from ConnexPay — 1 operation(s) for merchantselfservicefunding.
- [ConnexPay Merchantsupplier API](https://apis.io/apis/connexpay/connexpay-merchantsupplier-api/) — The Merchantsupplier API from ConnexPay — 1 operation(s) for merchantsupplier.
- [ConnexPay Payment Instruction API](https://apis.io/apis/connexpay/connexpay-paymentinstruction-api/) — Controller for handling Payment Instructions.
- [ConnexPay Physical Card API](https://apis.io/apis/connexpay/connexpay-physicalcard-api/) — The PhysicalCard API from ConnexPay — 1 operation(s) for physicalcard.
- [ConnexPay Purchase Event History API](https://apis.io/apis/connexpay/connexpay-purchaseeventhistory-api/) — The PurchaseEventHistory API from ConnexPay — 1 operation(s) for purchaseeventhistory.
- [ConnexPay Returns API](https://apis.io/apis/connexpay/connexpay-returns-api/) — The Returns API from ConnexPay — 2 operation(s) for returns.
- [ConnexPay Sale Event History API](https://apis.io/apis/connexpay/connexpay-saleeventhistory-api/) — The SaleEventHistory API from ConnexPay — 1 operation(s) for saleeventhistory.
- [ConnexPay Sales Api](https://apis.io/apis/connexpay/connexpay-sales-api-api/) — The Sales Api API from ConnexPay — 1 operation(s) for sales api.
- [ConnexPay Sales API](https://apis.io/apis/connexpay/connexpay-sales-api/) — The Sales API from ConnexPay — 6 operation(s) for sales.
- [ConnexPay Search API](https://apis.io/apis/connexpay/connexpay-search-api/) — The Search API from ConnexPay — 7 operation(s) for search.
- [ConnexPay Stop Payment Service API](https://apis.io/apis/connexpay/connexpay-stoppaymentservice-api/) — The StopPaymentService API from ConnexPay — 1 operation(s) for stoppaymentservice.
- [ConnexPay Terminate Card API](https://apis.io/apis/connexpay/connexpay-terminatecard-api/) — The TerminateCard API from ConnexPay — 1 operation(s) for terminatecard.
- [ConnexPay Token API](https://apis.io/apis/connexpay/connexpay-token-api/) — The Token API from ConnexPay — 1 operation(s) for token.
- [ConnexPay UATP API](https://apis.io/apis/connexpay/connexpay-uatp-api/) — The UATP API from ConnexPay — 1 operation(s) for uatp.
- [ConnexPay Verify API](https://apis.io/apis/connexpay/connexpay-verify-api/) — The Verify API from ConnexPay — 1 operation(s) for verify.
- [ConnexPay Verify1 API](https://apis.io/apis/connexpay/connexpay-verify1-api/) — The Verify1 API from ConnexPay — 1 operation(s) for verify1.
- [ConnexPay Void API](https://apis.io/apis/connexpay/connexpay-void-api/) — The Void API from ConnexPay — 1 operation(s) for void.
- [ConnexPay 3 DS API](https://apis.io/apis/connexpay/connexpay-3-ds-api/) — The 3 DS API from ConnexPay — 2 operation(s) for 3 ds.
- [ConnexPay 3D Secure API](https://apis.io/apis/connexpay/connexpay-3d-secure-api/) — The 3D Secure API from ConnexPay — 1 operation(s) for 3d secure.
- [ConnexPay push to card API](https://apis.io/apis/connexpay/connexpay-push-to-card-api/) — The push to card API from ConnexPay — 8 operation(s) for push to card.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Connexpay Webhooks](https://apis.io/asyncapis/connexpay/connexpay-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [connexpay-mcp.yml](https://apis.io/servers/connexpay/connexpay-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Connexpay Agentic Access](https://apis.io/agentic-access/connexpay/connexpay-agentic-access/)

#### Collections (39)

Postman and Open Collection request collections.

- [sales-api 3ds API](https://apis.io/collections/connexpay/open-connexpay-3ds-api/)
- [sales-api 3 D Secure API](https://apis.io/collections/connexpay/open-connexpay-3dsecure-api/)
- [ConnexPay Reporting Accounting API](https://apis.io/collections/connexpay/open-connexpay-accounting-api/)
- [purchases-api Addendum API](https://apis.io/collections/connexpay/open-connexpay-addendum-api/)
- [reporting-authentication Authenticate API](https://apis.io/collections/connexpay/open-connexpay-authenticate-api/)
- [sales-api Authonlys API](https://apis.io/collections/connexpay/open-connexpay-authonlys-api/)
- [sales-api Cancel API](https://apis.io/collections/connexpay/open-connexpay-cancel-api/)
- [sales-api Captures API](https://apis.io/collections/connexpay/open-connexpay-captures-api/)
- [purchases-api Card Booking API](https://apis.io/collections/connexpay/open-connexpay-cardbooking-api/)
- [purchases-api Cards API](https://apis.io/collections/connexpay/open-connexpay-cards-api/)
- [Connexpay Chargeback API](https://apis.io/collections/connexpay/open-connexpay-chargeback-api/)
- [ConnexPay Checkout Session Checkout Sessions API](https://apis.io/collections/connexpay/open-connexpay-checkout-sessions-api/)
- [ConnexPay Reporting Credit API](https://apis.io/collections/connexpay/open-connexpay-credit-api/)
- [ConnexPay Reporting Extended Data API](https://apis.io/collections/connexpay/open-connexpay-extendeddata-api/)
- [sales-api Hosted Payment Page Requests API](https://apis.io/collections/connexpay/open-connexpay-hostedpaymentpagerequests-api/)
- [purchases-api Issue ACH API](https://apis.io/collections/connexpay/open-connexpay-issueach-api/)
- [purchases-api Issue Card API](https://apis.io/collections/connexpay/open-connexpay-issuecard-api/)
- [purchases-api IssueCard (COPY) IssueCard (COPY) API](https://apis.io/collections/connexpay/open-connexpay-issuecard-copy-api/)
- [sales-api Merchant Flex Funding API](https://apis.io/collections/connexpay/open-connexpay-merchantflexfunding-api/)
- [Purchases Merchant Payor API](https://apis.io/collections/connexpay/open-connexpay-merchantpayor-api/)
- [purchases-api Merchants API](https://apis.io/collections/connexpay/open-connexpay-merchants-api/)
- [sales-api Merchant Self Service Funding API](https://apis.io/collections/connexpay/open-connexpay-merchantselfservicefunding-api/)
- [purchases-api Merchantsupplier API](https://apis.io/collections/connexpay/open-connexpay-merchantsupplier-api/)
- [v1 Payment Instruction API](https://apis.io/collections/connexpay/open-connexpay-paymentinstruction-api/)
- [purchases-api Physical Card API](https://apis.io/collections/connexpay/open-connexpay-physicalcard-api/)
- …and 14 more published on APIs.io

#### Overlays (10)

OpenAPI overlays, including conversational phrasing for each operation.

- [Connexpay Chargebacks Overlay](https://apis.io/overlays/connexpay/connexpay-chargebacks-overlay/)
- [Connexpay Checkout Session Overlay](https://apis.io/overlays/connexpay/connexpay-checkout-session-overlay/)
- [Connexpay Merchant Payor Overlay](https://apis.io/overlays/connexpay/connexpay-merchant-payor-overlay/)
- [Connexpay Payment Instruction Overlay](https://apis.io/overlays/connexpay/connexpay-payment-instruction-overlay/)
- [Connexpay Purchases Overlay](https://apis.io/overlays/connexpay/connexpay-purchases-overlay/)
- [Connexpay Push To Card Overlay](https://apis.io/overlays/connexpay/connexpay-push-to-card-overlay/)
- [Connexpay Reporting Authentication Overlay](https://apis.io/overlays/connexpay/connexpay-reporting-authentication-overlay/)
- [Connexpay Reporting Overlay](https://apis.io/overlays/connexpay/connexpay-reporting-overlay/)
- [Connexpay Sales Overlay](https://apis.io/overlays/connexpay/connexpay-sales-overlay/)
- [Connexpay Stop Payment Service Overlay](https://apis.io/overlays/connexpay/connexpay-stop-payment-service-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Connexpay Authentication](https://apis.io/security/connexpay/connexpay-authentication/)
- [Connexpay Domain Security](https://apis.io/security/connexpay/connexpay-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Connexpay Plans Pricing](https://apis.io/plans/connexpay/connexpay-plans-pricing/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.connexpay.com/)
- [Documentation](https://docs.connexpay.com/docs/platform-overview)
- [Getting started](https://docs.connexpay.com/docs/getting-started)
- [API reference](https://docs.connexpay.com/reference/introduction)
- [Pricing](https://www.connexpay.com/pricing)
- [Support](https://www.connexpay.com/contact-us)
- [Changelog](https://docs.connexpay.com/changelog)
- [Blog](https://www.connexpay.com/resources/blog)
- [Compliance](https://www.connexpay.com/security-and-compliance)
- [Terms of service](https://www.connexpay.com/legal/terms-of-use)
- [Privacy policy](https://www.connexpay.com/legal/privacy-policy)

## API Evangelist rating

**Kin Score 52.0** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 58.5 |
| Contract governance | 4.5 |
| Operational transparency | 15.8 |
| Developer ergonomics | 58.9 |
| Access clarity | 67.1 |

**Agent readiness 40.0** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | verified |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | mostly |

**Regulatory alignment 35.7** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/connexpay/](https://apis.io/providers/connexpay/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for ConnexPay: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/connexpay/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
