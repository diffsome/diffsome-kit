---
description: Wishlist management
---

# Wishlist

Manage product wishlists.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/wishlist` | Get my wishlist |
| POST | `/wishlist` | Add to wishlist |
| PUT | `/wishlist/{id}` | Update wishlist item |
| DELETE | `/wishlist/{id}` | Remove from wishlist |
| POST | `/wishlist/toggle` | Toggle wishlist item |
| GET | `/wishlist/check` | Check if product in wishlist |
| POST | `/wishlist/check-bulk` | Check multiple products |
| GET | `/wishlist/count` | Get wishlist count |
| POST | `/wishlist/move-to-cart` | Move items to cart |
| GET | `/products/{slug}/wishlist-count` | Product wishlist count |

## Get Wishlist

```json
{
  "items": [
    {
      "id": 1,
      "product_id": 10,
      "product": {
        "name": "Cool T-Shirt",
        "slug": "cool-t-shirt",
        "price": 29.99,
        "image": "https://..."
      },
      "added_at": "2026-01-22T10:00:00Z"
    }
  ],
  "total": 1
}
```

## Add to Wishlist

```json
{
  "product_id": 10
}
```

## Toggle Wishlist

Adds if not in wishlist, removes if already in:

```json
{
  "product_id": 10
}
```

Response:
```json
{
  "in_wishlist": true,
  "action": "added"
}
```

## Check Product

```
GET /api/{tenant}/wishlist/check?product_id=10
```

Response:
```json
{
  "in_wishlist": true
}
```

## Check Bulk

```json
{
  "product_ids": [10, 20, 30]
}
```

Response:
```json
{
  "10": true,
  "20": false,
  "30": true
}
```

## Move to Cart

```json
{
  "wishlist_ids": [1, 2, 3],
  "remove_after": true
}
```

## Use Cases

- "Show my wishlist"
- "Add product 'cool-t-shirt' to wishlist"
- "Remove item from wishlist"
- "Move all wishlist items to cart"
- "How many items in my wishlist?"
