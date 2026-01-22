# diffsome-kit

Claude Code plugin for [Diffsome](https://diffsome.com) - Multi-tenant Headless CMS & E-commerce Platform.

## Installation

```bash
# Add marketplace
/plugin marketplace add diffsome/diffsome-kit

# Install plugin
/plugin install diffsome-kit
```

## Features

### Authentication
| Skill | Description |
|-------|-------------|
| `/diffsome-kit:auth` | Login, register, logout, profile, social auth |

### Content Management
| Skill | Description |
|-------|-------------|
| `/diffsome-kit:blog` | Blog posts, categories, tags, comments |
| `/diffsome-kit:boards` | Bulletin boards, posts, comments |
| `/diffsome-kit:media` | Upload, list, delete media files |
| `/diffsome-kit:forms` | Form definitions and submissions |

### E-commerce
| Skill | Description |
|-------|-------------|
| `/diffsome-kit:shop` | Products, categories, variants |
| `/diffsome-kit:cart` | Shopping cart management |
| `/diffsome-kit:orders` | Order creation and management |
| `/diffsome-kit:payments` | Toss Payments & Stripe |
| `/diffsome-kit:wishlist` | Product wishlists |
| `/diffsome-kit:reviews` | Product reviews and ratings |
| `/diffsome-kit:coupons` | Discount coupons |
| `/diffsome-kit:subscriptions` | Recurring subscriptions |
| `/diffsome-kit:downloads` | Digital product downloads |

### Advanced Features
| Skill | Description |
|-------|-------------|
| `/diffsome-kit:reservations` | Booking and reservation system |
| `/diffsome-kit:entities` | Custom dynamic data structures |
| `/diffsome-kit:agents` | AI-powered automation agents |

## Authentication

### API Key (Required)

```bash
export DIFFSOME_API_KEY=pky_your_api_key
export DIFFSOME_TENANT=your-tenant-id
```

Or in `.claude/settings.json`:

```json
{
  "env": {
    "DIFFSOME_API_KEY": "pky_your_api_key",
    "DIFFSOME_TENANT": "your-tenant-id"
  }
}
```

### Member Login (Optional)

For member-level operations (orders, cart, profile):

```typescript
await client.auth.login({
  email: 'user@example.com',
  password: 'password'
});
```

## Usage Examples

```bash
# Blog
/diffsome-kit:blog
> Show latest 10 blog posts

# Products
/diffsome-kit:shop
> Find products under $50 in 'shoes' category

# Cart
/diffsome-kit:cart
> Add 2 of product 'cool-t-shirt' size M to cart

# Orders
/diffsome-kit:orders
> Show my pending orders

# Reservations
/diffsome-kit:reservations
> Book haircut with Jane tomorrow at 2pm

# Custom Entities
/diffsome-kit:entities
> Create a 'leads' entity with name, email, source fields

# AI Agents
/diffsome-kit:agents
> Run content-writer agent with topic "AI trends 2026"
```

## How It Works

This plugin provides **skills** (prompt templates) that instruct Claude to call the Diffsome REST API directly.

```
User → Claude + Skill → HTTP Request → Diffsome API → Response → Claude → User
```

No MCP server required. Claude makes direct HTTP calls to the API.

## API Reference

Base URL: `https://www.diffsome.com/api/{tenant}/`

Authentication: `X-API-Key: pky_xxx` header

Full API documentation: [diffsome.com/docs](https://diffsome.com/docs)

## Diffsome Platform

Diffsome is a multi-tenant SaaS platform offering:

- **Headless CMS** - Blog, boards, custom entities
- **E-commerce** - Products, orders, payments (Toss/Stripe)
- **Member Management** - Authentication, profiles
- **AI Content** - Claude/Gemini powered content generation
- **Notifications** - Email, SMS, Kakao, Push
- **Reservations** - Booking system
- **Subscriptions** - Recurring payments with Stripe

Learn more at [diffsome.com](https://diffsome.com)

## License

MIT
