---
description: Theme management and AI theme builder
---

# Themes

Manage site themes and use AI theme generator.

## Theme Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/themes` | List all themes |
| POST | `/themes` | Create new theme |
| GET | `/themes/{slug}` | Get theme details |
| PUT | `/themes/{slug}` | Update theme |
| DELETE | `/themes/{slug}` | Delete theme |
| POST | `/themes/{slug}/activate` | Activate theme |

## Theme Builder (Conversational)

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/theme-builder/start` | Start new session |
| POST | `/theme-builder/message` | Send message |
| GET | `/theme-builder/session/{id}` | Get session |
| GET | `/theme-builder/session/{id}/messages` | Get messages |
| POST | `/theme-builder/session/{id}/end` | End session |

## Theme Generator V2 (One-shot)

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/theme-generator/generate` | Generate theme |

## Create Theme

```json
{
  "name": "Modern Dark",
  "slug": "modern-dark",
  "description": "A sleek dark theme",
  "config": {
    "colors": {
      "primary": "#6366f1",
      "secondary": "#8b5cf6",
      "background": "#0f172a",
      "text": "#f8fafc"
    },
    "fonts": {
      "heading": "Inter",
      "body": "Inter"
    },
    "spacing": {
      "base": "1rem"
    }
  },
  "css": ":root { --primary: #6366f1; ... }"
}
```

## Theme Generator Request

```json
{
  "prompt": "Create a modern e-commerce theme with purple accents, dark mode, and minimalist design",
  "base_theme": "default",
  "options": {
    "dark_mode": true,
    "responsive": true
  }
}
```

## Theme Response

```json
{
  "id": 1,
  "name": "Modern Dark",
  "slug": "modern-dark",
  "is_active": true,
  "config": {...},
  "css": "...",
  "preview_url": "https://..."
}
```

## Start Builder Session

```json
{
  "initial_message": "I want a professional business theme with blue colors"
}
```

## Builder Conversation

```json
{
  "session_id": "sess_xxx",
  "message": "Make the header sticky and add a gradient background"
}
```

## Use Cases

- "List all themes"
- "Create a dark theme with purple accents"
- "Generate a theme for a coffee shop website"
- "Activate theme 'modern-dark'"
- "Start a theme builder conversation"
