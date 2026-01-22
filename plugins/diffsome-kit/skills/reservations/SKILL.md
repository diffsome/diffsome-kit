---
description: Reservation system - services, staffs, booking
---

# Reservations

Manage booking and reservation system.

## Settings & Availability

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/reservation/settings` | Get reservation settings |
| GET | `/reservation/services` | List available services |
| GET | `/reservation/staffs` | List staff members |
| GET | `/reservation/available-dates` | Get available dates |
| GET | `/reservation/available-slots` | Get time slots for date |

## Reservations

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/reservations` | Create reservation |
| GET | `/reservations` | List my reservations |
| GET | `/reservations/{number}` | Get reservation details |
| POST | `/reservations/{number}/cancel` | Cancel reservation |

## Payment

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/reservation-payments/toss/ready` | Prepare payment |
| POST | `/reservation-payments/toss/confirm` | Confirm payment |
| GET | `/reservation-payments/{order_id}/status` | Check status |

## Get Available Dates

```
GET /api/{tenant}/reservation/available-dates?service_id=1&staff_id=2&month=2026-01
```

Response:
```json
{
  "dates": [
    "2026-01-22",
    "2026-01-23",
    "2026-01-24"
  ]
}
```

## Get Available Slots

```
GET /api/{tenant}/reservation/available-slots?service_id=1&staff_id=2&date=2026-01-22
```

Response:
```json
{
  "slots": [
    {"time": "09:00", "available": true},
    {"time": "10:00", "available": true},
    {"time": "11:00", "available": false},
    {"time": "14:00", "available": true}
  ]
}
```

## Create Reservation

```json
{
  "service_id": 1,
  "staff_id": 2,
  "date": "2026-01-22",
  "time": "10:00",
  "customer_name": "John Doe",
  "customer_phone": "010-1234-5678",
  "customer_email": "john@example.com",
  "note": "First time visit"
}
```

## Reservation Response

```json
{
  "reservation_number": "RSV-20260122-001",
  "service": {
    "id": 1,
    "name": "Haircut",
    "duration": 60,
    "price": 30000
  },
  "staff": {
    "id": 2,
    "name": "Jane"
  },
  "datetime": "2026-01-22T10:00:00",
  "status": "confirmed",
  "payment_status": "pending"
}
```

## Statuses

| Status | Description |
|--------|-------------|
| pending | Awaiting confirmation |
| confirmed | Confirmed |
| completed | Service done |
| cancelled | Cancelled |
| no_show | Customer didn't show |

## Use Cases

- "Show available services"
- "Check available times on Jan 22"
- "Book haircut with Jane at 10am"
- "Cancel reservation RSV-001"
