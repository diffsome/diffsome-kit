---
description: Payment processing - Toss Payments, Stripe
---

# Payments

Process payments via Toss Payments and Stripe.

## Toss Payments (Korea)

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/payments/toss/ready` | Prepare payment |
| POST | `/payments/toss/confirm` | Confirm payment |
| POST | `/payments/toss/cancel` | Cancel/refund |
| POST | `/payments/toss/virtual-account` | Create virtual account |
| GET | `/payments/toss/success` | Success callback |
| GET | `/payments/toss/fail` | Failure callback |

## Stripe (Global)

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/payments/stripe/checkout` | Create Checkout Session |
| POST | `/payments/stripe/intent` | Create Payment Intent |
| POST | `/payments/stripe/confirm` | Confirm payment |
| POST | `/payments/stripe/verify` | Verify payment |
| POST | `/payments/stripe/refund` | Process refund |

## Common

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/payments/status` | Check payment status |

## Toss Ready Request

```json
{
  "order_number": "ORD-20260122-001",
  "amount": 58990,
  "order_name": "Cool T-Shirt 외 1건",
  "method": "CARD",
  "success_url": "https://site.com/success",
  "fail_url": "https://site.com/fail"
}
```

## Toss Methods

| Method | Description |
|--------|-------------|
| CARD | Credit/Debit Card |
| VIRTUAL_ACCOUNT | Virtual Account |
| TRANSFER | Bank Transfer |
| MOBILE | Mobile Payment |
| EASY_PAY | Easy Pay (Kakao, Naver) |

## Stripe Checkout

```json
{
  "order_number": "ORD-20260122-001",
  "success_url": "https://site.com/success?session_id={CHECKOUT_SESSION_ID}",
  "cancel_url": "https://site.com/cancel"
}
```

## Stripe Payment Intent

```json
{
  "order_number": "ORD-20260122-001",
  "payment_method_id": "pm_xxx"
}
```

## Refund

```json
{
  "order_number": "ORD-20260122-001",
  "amount": 58990,
  "reason": "Customer request"
}
```

## Use Cases

- "Initiate Toss payment for order X"
- "Create Stripe checkout session"
- "Refund order X"
- "Check payment status"
