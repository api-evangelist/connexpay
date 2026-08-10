---
name: Take a payment and issue a supplier virtual card
description: Charge a consumer with the ConnexPay Sales API, then issue a virtual card funded by that exact sale to pay the supplier. This matched pair is ConnexPay's core model — money in funds money out, with no float in between.
api: openapi/connexpay-sales-openapi.yml, openapi/connexpay-purchases-openapi.yml
operations: [sales-token, issuing-token, getting-started-with-your-api, issuecard, get-issuecard-detail, terminatecard]
generated: '2026-08-09'
method: generated
source: openapi/connexpay-sales-openapi.yml, openapi/connexpay-purchases-openapi.yml, https://docs.connexpay.com/docs/platform-overview
---

# Take a payment and issue a supplier virtual card

ConnexPay pairs an inbound sale (PayIn) with the outbound payment it funds (PayOut). A sale returns an
**Incoming Transaction Code (ITC)**; every virtual card you issue against that ITC is capped by the
sale's `Amount` and `ExpectedPayments`. That coupling is the product — do not treat the two APIs as
independent.

## Before you start

- The Sales API and the Purchases API have **separate hosts and separate tokens**. You need both.
- Sandbox: `https://sandboxsalesapi.connexpay.com` and `https://sandboxpurchasesapi.connexpay.com`.
- One credential set per MID. Sandbox credentials never work in production.
- There is **no idempotency key on any ConnexPay operation.** See `conventions/connexpay-conventions.yml`.
  Never blind-retry a sale or an issue call — check first, or you will get decline `D0001` /
  `D0008` (duplicate request) or, worse, a second real charge.

## Steps

1. **Get a Sales token** — `sales-token` (`POST /api/v1/token`).
   Form-encoded `grant_type=password` with the CXP-provided username and password. The token is valid
   for **24 hours**; cache it, do not mint one per request.

2. **Get a Purchases token** — `issuing-token` (`POST /api/v1/token` on the purchases host).
   Also 24 hours. These are different credentials from the Sales ones.

3. **Create the sale** — `getting-started-with-your-api` (`POST /api/v1/sales`).
   Set `Amount`, `Currency`, `DeviceGuid`, and `ExpectedPayments` to the number of supplier payments this
   booking will need. `ExpectedPayments` is a hard cap — you cannot issue more cards than that number.
   A credit sale authorizes immediately and settles that night; an ACH sale received before 3:00 PM EST
   processes overnight.
   To postpone the charge, pass a future `ActivationDate` and later call `activate-delayed-sale` or
   adjust with `update-delayed-sale`.

4. **Read the response, do not assume success.** An HTTP 200/201 does **not** mean approved. Check the
   processor status code and response message. A declined authorization is a business outcome, not an
   HTTP error — resolve it against `errors/connexpay-decline-codes.yml` (523 US, 39 EU/UK and 113 CA
   codes). Capture the returned **IncomingTransactionCode**.

5. **Issue the virtual card** — `issuecard` (`POST /api/v1/IssueCard`).
   Pass the ITC from step 4 plus the amount and the supplier's booking details. Constrain the card as
   tightly as the flow allows: a restrictive `PurchaseType`, a usage limit, an activation date, and
   country restrictions. ConnexPay's own guidance is to always assign the most restrictive purchase type
   the payment permits.
   - Issuing beyond `ExpectedPayments` fails with *"This incoming transaction code is not registered in
     the Issue Card database or it's already closed or voided"*.
   - Issuing for more than the sale amount fails with *"Amount requested ($xx.xx) is greater than
     authorized amount ($xx.xx)"*.

6. **Retrieve card detail when you need the PAN** — `get-issuecard-detail`
   (`GET /api/v1/Cards/{CardGuid}/{ShowFullPan}`). Treat the full PAN as cardholder data: it is in PCI
   scope the moment you store it. Prefer `resendtransmission` to deliver card details to the supplier
   instead of handling the PAN yourself.

7. **Terminate on cancellation** — `terminatecard` (`POST /api/v1/TerminateCard/<guid>`) stops the
   supplier authorizing a card you no longer owe. If the whole booking cancels — sale *and* purchase —
   use the Sales `cancel` operation instead, which refunds the consumer and terminates the card in one
   move.

## Reconciliation

Do not poll. Subscribe to CXP Eventing (`asyncapi/connexpay-webhooks.yml`) and drive state from
`purchase.card.issued`, `purchase.card.auth.approved`, `purchase.card.auth.declined`,
`purchase.card.auth.settled` and `purchase.card.terminated`. Delivery is **at-least-once** and duplicates
are documented as possible, so key your handler on the event `id` GUID. If you suspect a gap, replay with
`purchase-event-history` by GUID or date range rather than re-issuing anything.

## Testing

Use the published sandbox cards and magic values in `sandbox/connexpay-sandbox.yml` — including
`decline@connexpay.com` in the `Email` field to force a risk decline, and the AVS-simulation zip codes.
Never invent test values.
