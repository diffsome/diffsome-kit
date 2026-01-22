---
description: Product reviews management
---

# Product Reviews

Manage product reviews and ratings.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/products/{slug}/reviews` | List product reviews |
| GET | `/products/{slug}/reviews/can-review` | Check if can review |
| POST | `/products/{slug}/reviews` | Create review |
| PUT | `/reviews/{id}` | Update review |
| DELETE | `/reviews/{id}` | Delete review |
| POST | `/reviews/{id}/helpful` | Mark as helpful |
| GET | `/my/reviews` | List my reviews |

## List Reviews

```
GET /api/{tenant}/products/cool-t-shirt/reviews?page=1&sort=newest
```

### Query Parameters

| Param | Type | Description |
|-------|------|-------------|
| page | int | Page number |
| per_page | int | Items per page |
| sort | string | newest, oldest, highest, lowest, helpful |
| rating | int | Filter by rating (1-5) |

## Review Response

```json
{
  "data": [
    {
      "id": 1,
      "rating": 5,
      "title": "Great product!",
      "content": "Really happy with this purchase...",
      "pros": ["Quality", "Fast shipping"],
      "cons": ["Slightly expensive"],
      "images": ["https://..."],
      "verified_purchase": true,
      "helpful_count": 12,
      "author": {
        "name": "John D.",
        "avatar": "https://..."
      },
      "created_at": "2026-01-20T10:00:00Z"
    }
  ],
  "meta": {
    "average_rating": 4.5,
    "total_reviews": 50,
    "rating_distribution": {
      "5": 30,
      "4": 15,
      "3": 3,
      "2": 1,
      "1": 1
    }
  }
}
```

## Can Review

Check if current user can write a review:

```json
{
  "can_review": true,
  "reason": null,
  "has_purchased": true,
  "existing_review_id": null
}
```

Reasons for `can_review: false`:
- `not_purchased` - Haven't bought the product
- `already_reviewed` - Already submitted review
- `not_authenticated` - Not logged in

## Create Review

```json
{
  "rating": 5,
  "title": "Excellent quality!",
  "content": "This product exceeded my expectations...",
  "pros": ["Quality materials", "True to size"],
  "cons": [],
  "images": ["media_id_1", "media_id_2"]
}
```

## Mark Helpful

```
POST /api/{tenant}/reviews/123/helpful
```

Response:
```json
{
  "helpful_count": 13,
  "user_marked_helpful": true
}
```

## Use Cases

- "Show reviews for product 'cool-t-shirt'"
- "Can I review this product?"
- "Write a 5-star review"
- "Show my reviews"
- "Mark review as helpful"
