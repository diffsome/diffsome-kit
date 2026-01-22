---
description: Shopping cart management
---

# Cart

Manage shopping cart items.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/cart` | Get cart contents |
| POST | `/cart/items` | Add item to cart |
| PUT | `/cart/items/{id}` | Update item quantity |
| DELETE | `/cart/items/{id}` | Remove item |
| DELETE | `/cart` | Clear entire cart |
| POST | `/cart/validate` | Validate cart items |
| POST | `/cart/merge` | Merge guest cart after login |

## Get Cart

```json
{
  "items": [
    {
      "id": 1,
      "product_id": 10,
      "variant_id": 5,
      "product": {
        "name": "Cool T-Shirt",
        "slug": "cool-t-shirt",
        "image": "https://..."
      },
      "variant": {
        "name": "Medium / Blue",
        "sku": "TSH-001-M-B"
      },
      "quantity": 2,
      "unit_price": 29.99,
      "subtotal": 59.98
    }
  ],
  "subtotal": 59.98,
  "shipping": 5.00,
  "discount": 0,
  "total": 64.98,
  "item_count": 2
}
```

## Add Item

```json
{
  "product_id": 10,
  "variant_id": 5,
  "quantity": 2
}
```

## Update Item

```json
{
  "quantity": 3
}
```

## Validate Cart

Checks all items for:
- Stock availability
- Price changes
- Product status

Returns validation errors if any issues found.

## Use Cases

- "Show my cart"
- "Add 2 of product 'cool-t-shirt' size M"
- "Remove item #1 from cart"
- "Clear my cart"
- "Check if cart items are still available"
