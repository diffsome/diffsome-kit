---
description: Media file management - upload, list, delete
---

# Media

Manage media files (images, documents, etc.).

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/media` | Upload file |
| GET | `/media` | List media files |
| DELETE | `/media/{id}` | Delete file |

## Upload File

```
POST /api/{tenant}/media
Content-Type: multipart/form-data

file: (binary)
folder: "products"
alt: "Product image"
```

## Upload Response

```json
{
  "id": 123,
  "filename": "image-abc123.jpg",
  "original_name": "my-photo.jpg",
  "mime_type": "image/jpeg",
  "size": 102400,
  "url": "https://storage.diffsome.com/tenant/products/image-abc123.jpg",
  "thumbnail_url": "https://storage.diffsome.com/tenant/products/thumb-image-abc123.jpg",
  "folder": "products",
  "alt": "Product image",
  "width": 1920,
  "height": 1080,
  "created_at": "2026-01-22T10:00:00Z"
}
```

## List Media

```
GET /api/{tenant}/media?folder=products&mime_type=image&page=1
```

### Query Parameters

| Param | Type | Description |
|-------|------|-------------|
| folder | string | Filter by folder |
| mime_type | string | Filter by type (image, video, document) |
| search | string | Search filename |
| page | int | Page number |
| per_page | int | Items per page |

## Media Response

```json
{
  "data": [
    {
      "id": 123,
      "filename": "image-abc123.jpg",
      "url": "https://...",
      "thumbnail_url": "https://...",
      "size": 102400,
      "mime_type": "image/jpeg"
    }
  ],
  "meta": {
    "current_page": 1,
    "total": 50
  }
}
```

## Supported Types

| Type | Extensions |
|------|------------|
| Images | jpg, jpeg, png, gif, webp, svg |
| Videos | mp4, webm, mov |
| Documents | pdf, doc, docx, xls, xlsx |
| Archives | zip, rar |

## Upload Limits

- Max file size: 10MB (images), 100MB (videos)
- Rate limit: 10 uploads per minute

## Use Cases

- "Upload product image"
- "List all images in 'products' folder"
- "Delete media file #123"
- "Find images matching 'banner'"
