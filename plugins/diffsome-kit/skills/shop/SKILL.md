---
description: E-commerce - products, categories, variants
---

# Shop - Products

Manage e-commerce products and categories.

## Category Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/categories` | List all categories |
| GET | `/categories/{slug}` | Get category details |

## Product Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/products` | List products |
| GET | `/products/{slug}` | Get product details |
| GET | `/products/{slug}/related` | Get related products |
| GET | `/products/{slug}/bundle-items` | Get bundle items |

## List Products

```
GET /api/{tenant}/products?page=1&category=shoes&min_price=10&max_price=100
```

### Query Parameters

| Param | Type | Description |
|-------|------|-------------|
| page | int | Page number |
| per_page | int | Items per page |
| category | string | Category slug |
| min_price | number | Minimum price |
| max_price | number | Maximum price |
| search | string | Search term |
| sort | string | Sort field |
| order | string | asc or desc |
| in_stock | bool | Only in-stock items |

## Product Response

```json
{
  "id": 1,
  "name": "Cool T-Shirt",
  "slug": "cool-t-shirt",
  "description": "Product description...",
  "price": 29.99,
  "compare_price": 39.99,
  "sku": "TSH-001",
  "stock": 100,
  "is_active": true,
  "images": [
    {"url": "https://...", "alt": "Front view"}
  ],
  "category": {
    "id": 1,
    "name": "T-Shirts",
    "slug": "t-shirts"
  },
  "variants": [
    {
      "id": 1,
      "name": "Small / White",
      "sku": "TSH-001-S-W",
      "price": 29.99,
      "stock": 25,
      "options": {"size": "S", "color": "White"}
    }
  ],
  "options": [
    {"name": "Size", "values": ["S", "M", "L", "XL"]},
    {"name": "Color", "values": ["White", "Black", "Blue"]}
  ]
}
```

## Product Types

| Type | Description |
|------|-------------|
| simple | Single product |
| variable | Product with variants |
| bundle | Product bundle |
| digital | Digital download |
| subscription | Recurring subscription |

## Use Cases

- "List all products"
- "Find products under $50"
- "Show 'cool-t-shirt' product"
- "List products in 'shoes' category"
