---
description: Bulletin boards - boards, posts, comments
---

# Boards

Manage bulletin boards and posts.

## Board Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/boards` | List all boards |
| GET | `/boards/{board}` | Get board details |

## Post Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/boards/{board}/posts` | List posts in board |
| GET | `/posts/{id}` | Get post by ID |
| POST | `/posts` | Create new post |
| PUT | `/posts/{id}` | Update post |
| DELETE | `/posts/{id}` | Delete post |

## Comment Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/posts/{id}/comments` | Get post comments |
| POST | `/posts/{id}/comments` | Add comment |
| PUT | `/comments/{id}` | Update comment |
| DELETE | `/comments/{id}` | Delete comment |
| POST | `/comments/{id}/like` | Like comment |

## Create Post

```json
{
  "board_id": 1,
  "title": "Post Title",
  "content": "Post content here...",
  "is_notice": false,
  "attachments": []
}
```

## Post Response

```json
{
  "id": 1,
  "board_id": 1,
  "title": "Post Title",
  "content": "Content...",
  "is_notice": false,
  "views": 50,
  "comments_count": 5,
  "author": {
    "id": 1,
    "name": "User"
  },
  "created_at": "2026-01-22T00:00:00Z"
}
```

## Query Parameters

| Param | Type | Description |
|-------|------|-------------|
| page | int | Page number |
| per_page | int | Items per page |
| search | string | Search in title/content |
| notice_only | bool | Only show notices |

## Use Cases

- "List all boards"
- "Show posts in 'notice' board"
- "Create a new announcement"
- "Delete post #123"
