---
description: Custom entities - dynamic data structures
---

# Custom Entities

Create and manage dynamic data structures.

## Entity Definition Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/entities` | List all entities |
| POST | `/entities` | Create new entity |
| GET | `/entities/{slug}` | Get entity definition |
| PUT | `/entities/{slug}` | Update entity |
| DELETE | `/entities/{slug}` | Delete entity |

## Record Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/entities/{slug}/records` | List records |
| POST | `/entities/{slug}/records` | Create record |
| GET | `/entities/{slug}/records/{id}` | Get record |
| PUT | `/entities/{slug}/records/{id}` | Update record |
| DELETE | `/entities/{slug}/records/{id}` | Delete record |

## Create Entity

```json
{
  "name": "Customers",
  "slug": "customers",
  "description": "Customer management",
  "schema": {
    "fields": [
      {
        "name": "company",
        "type": "text",
        "label": "Company Name",
        "required": true
      },
      {
        "name": "email",
        "type": "email",
        "label": "Email",
        "required": true
      },
      {
        "name": "status",
        "type": "select",
        "label": "Status",
        "options": [
          {"value": "active", "label": "Active"},
          {"value": "inactive", "label": "Inactive"}
        ]
      },
      {
        "name": "revenue",
        "type": "number",
        "label": "Annual Revenue"
      }
    ]
  }
}
```

## Field Types

| Type | Description |
|------|-------------|
| text | Single line text |
| textarea | Multi-line text |
| number | Numeric value |
| email | Email address |
| url | URL |
| date | Date |
| datetime | Date and time |
| boolean | True/false |
| select | Single selection |
| multiselect | Multiple selection |
| relation | Reference to another entity |
| json | JSON object |

## Create Record

```
POST /api/{tenant}/entities/customers/records
```

```json
{
  "company": "ACME Inc",
  "email": "contact@acme.com",
  "status": "active",
  "revenue": 1000000
}
```

## Query Records

```
GET /api/{tenant}/entities/customers/records?status=active&sort=revenue&order=desc
```

## Record Response

```json
{
  "id": 1,
  "entity_slug": "customers",
  "data": {
    "company": "ACME Inc",
    "email": "contact@acme.com",
    "status": "active",
    "revenue": 1000000
  },
  "created_at": "2026-01-22T10:00:00Z",
  "updated_at": "2026-01-22T10:00:00Z"
}
```

## Use Cases

- "Create a 'leads' entity with name, email, source fields"
- "Add a new customer record"
- "List all active customers"
- "Update customer #5 status to inactive"
- "Show entity schema for 'customers'"
