---
description: Forms - submissions, validation
---

# Forms

Manage form submissions and data collection.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/forms` | List all forms |
| GET | `/forms/{slug}` | Get form definition |
| GET | `/forms/{slug}/submissions` | List submissions (admin) |
| GET | `/forms/{slug}/check-ip` | Check IP submission limit |
| POST | `/forms/{slug}/submit` | Submit form |
| GET | `/my/submissions` | My submissions |
| GET | `/my/submissions/{id}` | Get my submission |

## Form Definition

```json
{
  "id": 1,
  "name": "Contact Form",
  "slug": "contact",
  "description": "Get in touch with us",
  "fields": [
    {
      "name": "name",
      "type": "text",
      "label": "Your Name",
      "required": true
    },
    {
      "name": "email",
      "type": "email",
      "label": "Email Address",
      "required": true
    },
    {
      "name": "message",
      "type": "textarea",
      "label": "Message",
      "required": true
    },
    {
      "name": "category",
      "type": "select",
      "label": "Category",
      "options": ["General", "Support", "Sales"]
    }
  ],
  "settings": {
    "submit_limit_per_ip": 5,
    "require_auth": false,
    "notification_email": "admin@example.com"
  }
}
```

## Submit Form

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "message": "Hello, I have a question...",
  "category": "General"
}
```

## Field Types

| Type | Description |
|------|-------------|
| text | Single line text |
| textarea | Multi-line text |
| email | Email address |
| phone | Phone number |
| number | Numeric input |
| select | Dropdown selection |
| checkbox | Boolean checkbox |
| radio | Radio buttons |
| date | Date picker |
| file | File upload |

## Submission Response

```json
{
  "id": 123,
  "form_id": 1,
  "data": {
    "name": "John Doe",
    "email": "john@example.com",
    "message": "Hello..."
  },
  "ip_address": "1.2.3.4",
  "created_at": "2026-01-22T10:00:00Z"
}
```

## Use Cases

- "List all forms"
- "Show contact form fields"
- "Submit contact form"
- "View my submissions"
