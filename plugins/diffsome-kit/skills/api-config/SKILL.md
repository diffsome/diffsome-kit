---
description: Diffsome API configuration and authentication
---

# Diffsome API Configuration

Base configuration for all Diffsome API calls.

## Base URL

```
https://www.diffsome.com/api/{DIFFSOME_TENANT}/
```

## Authentication

All requests require `X-API-Key` header:

```
X-API-Key: {DIFFSOME_API_KEY}
```

For member-authenticated endpoints, also include:

```
Authorization: Bearer {member_token}
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `DIFFSOME_TENANT` | Tenant ID (subdomain) |
| `DIFFSOME_API_KEY` | API Key from dashboard |

## Making Requests

When the user asks to interact with Diffsome:

1. Check environment variables are set
2. Construct the full URL: `https://www.diffsome.com/api/{tenant}/{endpoint}`
3. Include required headers
4. Make the HTTP request
5. Parse and present the response

## Response Format

All responses follow this structure:

```json
{
  "success": true,
  "data": { ... },
  "message": "Optional message"
}
```

Error responses:

```json
{
  "success": false,
  "message": "Error description",
  "errors": { "field": ["error"] }
}
```

## Rate Limits

| Endpoint | Limit |
|----------|-------|
| Login/Register | 5/min |
| Upload | 10/min |
| General | 60/min |
