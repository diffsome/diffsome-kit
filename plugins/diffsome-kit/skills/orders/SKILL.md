---
description: Order management - create, view, cancel orders
---

# Orders

Manage customer orders.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/orders/preview` | Preview order before placing |
| POST | `/orders` | Create new order |
| GET | `/orders` | List my orders |
| GET | `/orders/{order_number}` | Get order details |
| POST | `/orders/{order_number}/cancel` | Cancel order |

## Preview Order

Before creating an order, preview to see final totals:

```json
{
  "shipping_address": {
    "name": "John Doe",
    "phone": "010-1234-5678",
    "address": "123 Main St",
    "city": "Seoul",
    "postal_code": "12345"
  },
  "coupon_code": "SAVE10"
}
```

## Create Order

```json
{
  "shipping_address": {
    "name": "John Doe",
    "phone": "010-1234-5678",
    "address": "123 Main St",
    "address_detail": "Apt 101",
    "city": "Seoul",
    "postal_code": "12345"
  },
  "billing_address": null,
  "coupon_code": "SAVE10",
  "note": "Please leave at door",
  "payment_method": "toss"
}
```

## Order Response

```json
{
  "order_number": "ORD-20260122-001",
  "status": "pending",
  "items": [...],
  "subtotal": 59.98,
  "shipping": 5.00,
  "discount": 5.99,
  "total": 58.99,
  "shipping_address": {...},
  "payment": {
    "method": "toss",
    "status": "pending"
  },
  "created_at": "2026-01-22T10:00:00Z"
}
```

## Order Statuses

| Status | Description |
|--------|-------------|
| pending | Awaiting payment |
| paid | Payment confirmed |
| processing | Being prepared |
| shipped | In transit |
| delivered | Completed |
| cancelled | Cancelled |
| refunded | Refunded |

## List Orders

```
GET /api/{tenant}/orders?status=paid&page=1
```

## Use Cases

- "Show my orders"
- "Get order ORD-20260122-001"
- "Cancel my pending order"
- "List all paid orders"
