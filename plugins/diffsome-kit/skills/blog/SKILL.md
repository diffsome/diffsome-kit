---
description: Blog management - posts, categories, tags, comments
---

# Blog

Manage blog posts and content.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/blog` | List blog posts |
| GET | `/blog/categories` | List categories |
| GET | `/blog/tags` | List tags |
| GET | `/blog/{slug}` | Get post by slug |
| GET | `/blog/{slug}/comments` | Get post comments |
| POST | `/blog/{slug}/comments` | Add comment |

## List Posts

```
GET /api/{tenant}/blog?page=1&per_page=10&category=tech&tag=ai
```

### Query Parameters

| Param | Type | Description |
|-------|------|-------------|
| page | int | Page number |
| per_page | int | Items per page (default: 10) |
| category | string | Filter by category slug |
| tag | string | Filter by tag |
| status | string | Filter by status (published, draft) |
| search | string | Search in title/content |

## Post Response

```json
{
  "id": 1,
  "title": "Hello World",
  "slug": "hello-world",
  "content": "<p>Post content...</p>",
  "excerpt": "Short summary",
  "featured_image": "https://...",
  "category": {
    "id": 1,
    "name": "Tech",
    "slug": "tech"
  },
  "tags": ["ai", "tech"],
  "author": {
    "id": 1,
    "name": "Admin"
  },
  "published_at": "2026-01-22T00:00:00Z",
  "views": 100
}
```

## Add Comment

```json
{
  "content": "Great post!",
  "author_name": "Guest User",
  "author_email": "guest@example.com"
}
```

## Use Cases

- "Show latest blog posts"
- "Find posts about AI"
- "List all categories"
- "Get post by slug 'hello-world'"
