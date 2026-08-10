---
name: Embed a ConnexPay checkout form without touching card data
description: Create a server-side checkout session and render ConnexPay's browser SDK payment form, so credit, ACH, Apple Pay and Google Pay all flow through ConnexPay's iframe and card data never reaches your server.
api: openapi/connexpay-checkout-session-openapi.yml, openapi/connexpay-sales-openapi.yml
operations: [sales-token, createCheckoutSession, hpp-token-request]
generated: '2026-08-09'
method: generated
source: openapi/connexpay-checkout-session-openapi.yml, https://docs.connexpay.com/docs/quick-start-guide
---

# Embed a ConnexPay checkout form without touching card data

The point of this flow is PCI scope. The session is created on your backend with your API token; the
card is collected inside ConnexPay's own hosted form. Your server never sees a PAN.

## Steps

1. **Get a Sales token** — `sales-token` (`POST /api/v1/token`). 24-hour lifetime. Server-side only:
   this credential must never reach the browser.

2. **Create the checkout session server-side** — `createCheckoutSession`
   (`POST /api/v2/Checkout/checkout-session`). Note this is the **v2** path on the sales host —
   sandbox `https://sandboxsalesapi.connexpay.com`, production `https://salesapi.connexpay.com`.
   Send `ClientId`, `TenderTypeOptions` (any of `Credit`, `ACH`, `GooglePay`, `ApplePay`) and a `Sale`
   block carrying `DeviceGuid`, `Amount` and `Currency`. Return only the `checkoutSessionId` to your
   frontend.

3. **Mind the 60-minute expiry.** Sessions expire after 60 minutes by design. Create the session when
   the customer reaches checkout, not when they start browsing, and re-create rather than reuse a stale
   one.

4. **Load the SDK from the CDN** — `<script src="https://js.connexpay.com/sdk/v2/connexpay.min.js">`.
   ConnexPay explicitly instructs integrators not to vendor this file: loading from the CDN is what keeps
   the PCI posture and the version current.

5. **Initialize and mount.** `ConnexPay(clientId)`, then wait for readiness (`isSDKReady()` or the
   `ready` event), then `createPaymentForm({ element, checkoutSessionID })`. Optionally call
   `setAppearance({theme, layout})` and `setCustomer({...})` *before* creating the form.

6. **Confirm.** `confirmPayment()` returns the result. Handle failure against the SDK error-code
   reference (https://docs.connexpay.com/docs/error-codes) — these are SDK/client errors and are a
   different vocabulary from the processor decline codes in `errors/connexpay-decline-codes.yml`.

7. **Do not treat the browser result as settlement.** Confirm server-side from the sale record or from
   the `sale.card.auth.approved` / `sale.card.auth.declined` webhook before you fulfil anything.

## If you cannot embed

Use the Hosted Payment Page instead: request a token with `hpp-token-request`
(`POST /api/v1/HostedPaymentPageRequests`) and redirect. Same PCI benefit, no client-side integration.
Bridge Payment Links cover the case where you want a shareable link rather than a checkout at all.

## Testing

Sandbox test cards, CVVs and AVS zip codes are in `sandbox/connexpay-sandbox.yml`. Note the documented
caveat that test card `2223000048400011` currently errors on SDK test sale attempts — use the Visa or
Amex test card when exercising the SDK path.
