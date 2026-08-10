---
name: Pay a payee with a push-to-card payout
description: Register a payee, create a push-to-card payout, let the payee claim funds to their own card through the payment widget, and cancel or reconcile the payout — using ConnexPay's Push to Card operations.
api: openapi/connexpay-push-to-card-openapi.yml
operations: [PushToCard_CreatePayee, PushToCard_GetPayee, PushToCard_UpdatePayee, PushToCard_ManagePayee, PushToCard_CreatePayout, PushToCard_GetPayoutDetails, PushToCard_CancelPayments, PushToCard_GetAuthenticationTokenAsync, PushToCard_PushFundsToCardAsync]
generated: '2026-08-09'
method: generated
source: openapi/connexpay-push-to-card-openapi.yml
---

# Pay a payee with a push-to-card payout

Push to Card is the disbursement side of ConnexPay: instead of issuing a virtual card the supplier pulls
from, you push funds to a card the payee already holds. A payout is a container; the individual payments
inside it have their own lifecycle.

## Steps

1. **Authenticate** against the Purchases host with `issuing-token`. Push to Card lives on
   `https://sandboxpurchasesapi.connexpay.com` in sandbox.

2. **Create the payee** — `PushToCard_CreatePayee` (`POST /api/v1/PushToCard/Payees`).
   Look up existing payees first with `PushToCard_GetPayee` (`GET /api/v1/PushToCard/Payees`) so you do
   not create a duplicate — there is no idempotency key to protect you.

3. **Maintain the payee** as needed:
   - `PushToCard_UpdatePayee` (`PATCH /api/v1/PushToCard/Payees/{payeeGuid}`) for detail changes.
   - `PushToCard_ManagePayee` (`PUT /api/v1/PushToCard/Payees/{payeeGuid}/{status}`) to change status.

4. **Create the payout** — `PushToCard_CreatePayout` (`POST /api/v1/PushToCard/Payouts`).
   This returns a `payoutGuid`. A payout may contain multiple individual payments.

5. **Let the payee claim the funds.** The payee-facing widget authenticates with
   `PushToCard_GetAuthenticationTokenAsync` (`GET /api/v1/PushToCard/AuthenticatePaymentWidget`), and the
   push itself is `PushToCard_PushFundsToCardAsync`
   (`PATCH /api/v1/PushToCard/Payments/{ridGuid}/{cardId}`). Do not collect the payee's card number
   yourself — routing it through the widget is what keeps the card data out of your scope.

6. **Track state** — `PushToCard_GetPayoutDetails` (`GET /api/v1/PushToCard/Payouts/{payoutGuid}`), and
   subscribe to the payout events in `asyncapi/connexpay-webhooks.yml`:
   `purchase.card.payout.approved` (payout created), `purchase.card.payment.payout` (an individual
   payment claimed), `purchase.card.payment.failed` (failed at disbursement — expired card, do not
   honor), `purchase.card.payment.expired`, `purchase.card.payment.deactivated`, and
   `purchase.card.payout.cancelled` (every payment in the payout cancelled).

7. **Cancel if needed** — `PushToCard_CancelPayments`
   (`POST /api/v1/PushToCard/Payouts/{payoutGuid}/Cancel`) deactivates the payments in a payout.

## Error handling

Failures at disbursement come back as card decline reasons, not HTTP errors — resolve them against the
PayOut decline list in `errors/connexpay-decline-codes.yml` (for example *Do not honor*, *Expired card*,
*Card is not active*, *MCC not allowed*, *Isocountry not allowed*).

## Alternative rails

If the payee should be paid by ACH, check or bank transfer rather than to a card, use the Payment Valet
Payment Instruction API instead (`CreatePaymentInstruction`, `GetFundingStatus`, `GetPaymentStatus`,
`VoidPaymentInstruction` in `openapi/connexpay-payment-instruction-openapi.yml`) — one access point
across card, check and ACH.
