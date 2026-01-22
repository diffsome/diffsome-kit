---
description: Digital downloads management
---

# Digital Downloads

Manage digital product downloads.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/my/downloads` | List my downloads |
| GET | `/orders/{orderNumber}/downloads` | Order downloads |
| GET | `/downloads/{token}` | Download file |
| GET | `/downloads/{token}/info` | Get download info |

## My Downloads

List all digital products the user has access to:

```json
{
  "data": [
    {
      "id": 1,
      "product": {
        "id": 10,
        "name": "E-Book: Learn AI",
        "slug": "ebook-learn-ai"
      },
      "files": [
        {
          "id": 1,
          "name": "learn-ai.pdf",
          "size": 5242880,
          "download_url": "/downloads/token_xxx",
          "download_count": 2,
          "download_limit": 5,
          "expires_at": "2026-02-22T00:00:00Z"
        }
      ],
      "order_number": "ORD-20260122-001",
      "purchased_at": "2026-01-22T10:00:00Z"
    }
  ]
}
```

## Order Downloads

Get downloads for a specific order:

```
GET /api/{tenant}/orders/ORD-20260122-001/downloads
```

## Download Info

Before downloading, get file info:

```
GET /api/{tenant}/downloads/token_xxx/info
```

Response:
```json
{
  "file_name": "learn-ai.pdf",
  "file_size": 5242880,
  "mime_type": "application/pdf",
  "download_count": 2,
  "download_limit": 5,
  "remaining_downloads": 3,
  "expires_at": "2026-02-22T00:00:00Z",
  "is_expired": false
}
```

## Download File

```
GET /api/{tenant}/downloads/token_xxx
```

Returns the file stream with appropriate headers.

## Download Restrictions

| Restriction | Description |
|-------------|-------------|
| download_limit | Max number of downloads |
| expires_at | Expiration date |
| ip_restriction | Limit to certain IPs |
| device_limit | Max devices |

## Error Cases

| Error | Description |
|-------|-------------|
| invalid_token | Token doesn't exist |
| expired | Download link expired |
| limit_reached | Download limit exceeded |
| not_found | File not found |

## Use Cases

- "Show my digital downloads"
- "Get downloads for order ORD-001"
- "Download my e-book"
- "Check remaining downloads for file"
