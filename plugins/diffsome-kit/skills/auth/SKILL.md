---
description: Authentication - login, register, logout, profile, social auth
---

# Authentication

Manage user authentication for Diffsome tenant.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/auth/login` | Email/password login |
| POST | `/auth/register` | New member registration |
| POST | `/auth/logout` | Logout (invalidate token) |
| GET | `/auth/me` | Get current user |
| GET | `/profile` | Get profile |
| PUT | `/profile` | Update profile |
| POST | `/auth/forgot-password` | Request password reset |
| POST | `/auth/reset-password` | Reset with token |
| POST | `/auth/find-email` | Find email by name/phone |

## Social Auth

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/auth/social/providers` | List available providers |
| GET | `/auth/social/{provider}` | Get OAuth URL |
| POST | `/auth/social/{provider}/callback` | Handle OAuth callback |
| POST | `/auth/social/{provider}/token` | Exchange token |
| POST | `/auth/social/{provider}/connect` | Connect social account |
| POST | `/auth/social/disconnect` | Disconnect social account |

## Login Request

```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

## Login Response

```json
{
  "success": true,
  "data": {
    "token": "1|abc123...",
    "user": {
      "id": 1,
      "name": "John Doe",
      "email": "user@example.com"
    }
  }
}
```

## Register Request

```json
{
  "name": "John Doe",
  "email": "user@example.com",
  "password": "password123",
  "password_confirmation": "password123"
}
```

## Supported Social Providers

- `google` - Google OAuth
- `kakao` - Kakao Login
- `naver` - Naver Login
- `facebook` - Facebook Login
- `instagram` - Instagram Login
