---
description: Subscription management - recurring payments
---

# Subscriptions

Manage recurring subscription payments.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/subscriptions` | List my subscriptions |
| GET | `/subscriptions/{id}` | Get subscription details |
| POST | `/subscriptions` | Create subscription |
| POST | `/subscriptions/checkout` | Stripe checkout |
| POST | `/subscriptions/verify` | Verify subscription |
| POST | `/subscriptions/{id}/cancel` | Cancel subscription |
| POST | `/subscriptions/{id}/pause` | Pause subscription |
| POST | `/subscriptions/{id}/resume` | Resume subscription |
| POST | `/subscriptions/setup-intent` | Create setup intent |

## Create Subscription

```json
{
  "plan_id": "plan_monthly",
  "payment_method_id": "pm_xxx"
}
```

## Stripe Checkout

```json
{
  "plan_id": "plan_monthly",
  "success_url": "https://site.com/success",
  "cancel_url": "https://site.com/cancel"
}
```

## Subscription Response

```json
{
  "id": 1,
  "plan": {
    "id": "plan_monthly",
    "name": "Pro Monthly",
    "price": 29.99,
    "interval": "month",
    "features": [
      "Unlimited products",
      "Priority support",
      "Advanced analytics"
    ]
  },
  "status": "active",
  "current_period_start": "2026-01-01",
  "current_period_end": "2026-02-01",
  "cancel_at_period_end": false,
  "payment_method": {
    "type": "card",
    "last4": "4242",
    "brand": "visa"
  }
}
```

## Subscription Statuses

| Status | Description |
|--------|-------------|
| active | Currently active |
| paused | Temporarily paused |
| canceled | Cancelled |
| past_due | Payment failed |
| trialing | In trial period |

## Cancel Subscription

```json
{
  "cancel_at_period_end": true,
  "reason": "Too expensive"
}
```

Set `cancel_at_period_end: true` to cancel at end of billing period, or `false` for immediate cancellation.

## Pause Subscription

```json
{
  "resume_at": "2026-03-01"
}
```

## Setup Intent

For adding/updating payment method:

```json
{
  "usage": "off_session"
}
```

Returns client secret for Stripe Elements.

## Use Cases

- "Show my subscriptions"
- "Subscribe to Pro plan"
- "Cancel my subscription at period end"
- "Pause subscription until March"
- "Update payment method"
