---
description: AI Agents - automated tasks and workflows
---

# AI Agents

Configure and run AI-powered automation agents.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/agents` | List available agents |
| GET | `/agents/{slug}` | Get agent details |
| POST | `/agents/{slug}/configure` | Configure agent |
| POST | `/agents/{slug}/run` | Run agent manually |
| GET | `/agents/{slug}/executions` | List executions |
| GET | `/agents/{slug}/stats` | Get agent stats |
| POST | `/agents/{slug}/webhook` | Webhook trigger |
| GET | `/executions/{id}` | Get execution details |

## Available Agents

| Agent | Description |
|-------|-------------|
| content-writer | AI content generation |
| seo-optimizer | SEO analysis and optimization |
| review-responder | Respond to product reviews |
| social-poster | Social media posting |
| email-campaign | Email marketing automation |
| inventory-alert | Stock level alerts |

## Configure Agent

```json
{
  "enabled": true,
  "settings": {
    "tone": "professional",
    "language": "ko",
    "auto_publish": false
  },
  "schedule": {
    "type": "daily",
    "time": "09:00",
    "timezone": "Asia/Seoul"
  },
  "triggers": {
    "on_new_review": true,
    "on_low_stock": true
  }
}
```

## Run Agent

```json
{
  "input": {
    "topic": "AI trends in 2026",
    "keywords": ["AI", "machine learning", "automation"]
  },
  "options": {
    "dry_run": false
  }
}
```

## Execution Response

```json
{
  "execution_id": "exec_xxx",
  "agent": "content-writer",
  "status": "completed",
  "input": {...},
  "output": {
    "title": "AI Trends in 2026",
    "content": "...",
    "post_id": 123
  },
  "started_at": "2026-01-22T10:00:00Z",
  "completed_at": "2026-01-22T10:01:30Z",
  "tokens_used": 1500
}
```

## Execution Statuses

| Status | Description |
|--------|-------------|
| pending | Queued |
| running | In progress |
| completed | Successfully done |
| failed | Error occurred |
| cancelled | Manually cancelled |

## Agent Stats

```json
{
  "total_executions": 150,
  "successful": 145,
  "failed": 5,
  "avg_duration": 45.5,
  "tokens_used_total": 250000,
  "last_run": "2026-01-22T09:00:00Z"
}
```

## Use Cases

- "List available agents"
- "Configure content-writer agent"
- "Run content-writer with topic 'AI trends'"
- "Show recent agent executions"
- "Get stats for review-responder agent"
