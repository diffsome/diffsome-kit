---
description: Coupon management and validation
---

# Coupons

Manage discount coupons.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/coupons` | List available coupons |
| POST | `/coupons/validate` | Validate coupon code |
| POST | `/coupons/apply` | Apply coupon to cart |

## List Coupons

Returns coupons available to the current user:

```json
{
  "data": [
    {
      "id": 1,
      "code": "SAVE10",
      "description": "10% off your order",
      "discount_type": "percentage",
      "discount_value": 10,
      "min_order_amount": 50,
      "max_discount": 100,
      "valid_from": "2026-01-01",
      "valid_until": "2026-12-31",
      "usage_limit": 100,
      "usage_count": 45,
      "applicable_to": "all"
    }
  ]
}
```

## Validate Coupon

```json
{
  "code": "SAVE10",
  "cart_total": 75.00
}
```

Response (valid):
```json
{
  "valid": true,
  "coupon": {
    "code": "SAVE10",
    "discount_type": "percentage",
    "discount_value": 10
  },
  "discount_amount": 7.50,
  "message": "Coupon applied successfully"
}
```

Response (invalid):
```json
{
  "valid": false,
  "message": "Minimum order amount is $50"
}
```

## Apply Coupon

```json
{
  "code": "SAVE10"
}
```

Applies coupon to current cart session.

## Discount Types

| Type | Description |
|------|-------------|
| percentage | Percentage off (e.g., 10%) |
| fixed | Fixed amount off (e.g., $5) |
| free_shipping | Free shipping |
| buy_x_get_y | Buy X get Y free |

## Coupon Restrictions

| Field | Description |
|-------|-------------|
| min_order_amount | Minimum cart total required |
| max_discount | Maximum discount cap |
| applicable_to | all, specific_products, categories |
| first_order_only | Only for first-time customers |
| single_use | One-time use per customer |

## Validation Errors

| Error | Description |
|-------|-------------|
| invalid_code | Coupon doesn't exist |
| expired | Coupon has expired |
| not_started | Coupon not yet active |
| usage_limit_reached | Coupon fully redeemed |
| min_amount_not_met | Cart total too low |
| already_used | User already used this coupon |
| not_applicable | Products not eligible |

## Use Cases

- "Show available coupons"
- "Validate coupon SAVE10"
- "Apply coupon to my cart"
- "What coupons can I use for this order?"
