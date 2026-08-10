---
name: Subscribe to CXP Eventing and reconcile safely
description: Stand up a ConnexPay webhook endpoint — pass the ownership handshake, verify deliveries, survive at-least-once duplicates, and recover missed events with the purchase event history replay endpoint.
api: openapi/connexpay-purchases-openapi.yml
operations: [issuing-token, purchase-event-history]
generated: '2026-08-09'
method: generated
source: https://docs.connexpay.com/docs/getting-started-with-webhooks, https://docs.connexpay.com/docs/webhook-events
---

# Subscribe to CXP Eventing and reconcile safely

ConnexPay pushes 51 documented event types across purchase cards, purchase ACH, sale cards, sale ACH and
funding. Webhooks — not polling — are the intended way to track payment state. The full catalogue is in
`asyncapi/connexpay-webhooks.yml`.

## Steps

1. **Expose an HTTPS endpoint.** HTTP is not accepted. It must return **HTTP 200** to acknowledge; any
   other status puts the event into the retry queue.

2. **Configure the subscription in Bridge.** Endpoint URL and optional security values are self-service
   through the Bridge UI. Sandbox and production endpoints are configured separately (you may point both
   at the same URL, but that is your call).

3. **Pass the ownership handshake.** ConnexPay will not deliver events until you prove you own the
   endpoint:
   - *Synchronous* — echo the `validationCode` from the validation event's `data` back in your response.
   - *Asynchronous* — GET the `validationUrl` from `data`. ConnexPay recommends this one.

4. **Parse the envelope.** Every notification carries `id`, `subject` (your merchant or parent org GUID),
   `data`, `eventType`, `eventTime` and `dataVersion`. Purchase card events also carry
   `incomingTransactionCode`, which joins the event back to the funding sale.

5. **Verify the sender.** There is **no HMAC signature** on ConnexPay webhooks. Your only verification
   levers are (a) the shared secret you configured as a header or query parameter, and (b) checking
   `subject` matches your merchant GUID. Treat the payload as untrusted input and re-read authoritative
   state from the API before acting on anything financial.

6. **Be idempotent on your side.** Delivery is at-least-once and ConnexPay documents that duplicates can
   arrive. Deduplicate on the event `id` GUID and make your handler safe to run twice. This matters more
   here than with most providers because the ConnexPay API itself has no idempotency key to fall back on.

7. **Recover gaps with replay, not with re-issuing.** `purchase-event-history`
   (`POST /api/v1/PurchaseEventHistory/Resend`) returns VCC, Lodged Card, Physical Card and ACH purchase
   events by GUID or across a date range. This is the documented recovery path when you suspect you
   missed deliveries. Never re-issue a card or re-run a sale to "resync".

## Events worth wiring first

| Purpose | Events |
|---|---|
| Card lifecycle | `purchase.card.issued`, `purchase.card.adjusted`, `purchase.card.terminated`, `purchase.card.expired` |
| Supplier authorization | `purchase.card.auth.approved`, `purchase.card.auth.declined`, `purchase.card.auth.settled` |
| Consumer payment | `sale.card.auth.approved`, `sale.card.auth.declined`, `sale.card.auth.voided` |
| ACH state machine | `sale.ach.pending` → `sale.ach.processing` → `sale.ach.processed`, plus `sale.ach.return.*` and `purchase.ach.noc` |
| Disputes | `purchase.card.chargeback.initiated.success`, `purchase.card.chargeback.accepted`, `purchase.card.chargeback.declined` |
| Balance | `sale.cash.balance.funding` |

Handle `purchase.ach.noc` deliberately: a Notification of Change means previously valid bank details are
now stale and must be updated before the next request, or subsequent ACH payouts will fail.

## Retry behaviour

Retries follow a published schedule, but steps may be **skipped** when your endpoint is consistently
unhealthy, down for a long period, or appears overwhelmed. A slow endpoint therefore loses events —
acknowledge with 200 immediately and process asynchronously.
