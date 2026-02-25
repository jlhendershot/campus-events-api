# API Endpoints

## GET /events

Retrieves a list of all campus events.

### Request
```http
GET /events HTTP/1.1
Host: api.campusevents.example.com
Authorization: Bearer YOUR_API_KEY
```

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `category` | string | No | Filter by event category (academic, social, athletic, cultural) |
| `start_date` | date | No | Filter events starting after this date (YYYY-MM-DD) |
| `end_date` | date | No | Filter events ending before this date (YYYY-MM-DD) |
| `limit` | integer | No | Maximum number of results (default: 50, max: 100) |

### Response

**Status Code:** 200 OK
```json
{
  "events": [
    {
      "id": "evt_123456",
      "title": "Spring Career Fair",
      "description": "Annual career fair featuring 50+ employers",
      "category": "academic",
      "location": "Student Union Ballroom",
      "start_time": "2026-03-15T09:00:00Z",
      "end_time": "2026-03-15T16:00:00Z",
      "capacity": 500,
      "registered_count": 342,
      "organizer": {
        "name": "Career Services",
        "email": "careers@university.edu"
      }
    }
  ],
  "total": 1,
  "page": 1
}
```

---

## GET /events/{id}

Retrieves details for a specific event.

### Request
```http
GET /events/evt_123456 HTTP/1.1
Host: api.campusevents.example.com
Authorization: Bearer YOUR_API_KEY
```

### Response

**Status Code:** 200 OK
```json
{
  "id": "evt_123456",
  "title": "Spring Career Fair",
  "description": "Annual career fair featuring 50+ employers",
  "category": "academic",
  "location": "Student Union Ballroom",
  "start_time": "2025-03-15T09:00:00Z",
  "end_time": "2025-03-15T16:00:00Z",
  "capacity": 500,
  "registered_count": 342,
  "organizer": {
    "name": "Career Services",
    "email": "careers@university.edu"
  }
}
```

### Error Responses

**Status Code:** 404 Not Found
```json
{
  "error": "Event not found",
  "message": "No event exists with ID evt_123456"
}
```

---

## POST /events

Creates a new campus event.

### Request
```http
POST /events HTTP/1.1
Host: api.campusevents.example.com
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```
```json
{
  "title": "Guest Lecture: AI in Education",
  "description": "Dr. Jane Smith discusses the impact of AI on learning",
  "category": "academic",
  "location": "Science Building Room 201",
  "start_time": "2026-04-10T14:00:00Z",
  "end_time": "2026-04-10T15:30:00Z",
  "capacity": 100
}
```

### Response

**Status Code:** 201 Created
```json
{
  "id": "evt_789012",
  "title": "Guest Lecture: AI in Education",
  "description": "Dr. Jane Smith discusses the impact of AI on learning",
  "category": "academic",
  "location": "Science Building Room 201",
  "start_time": "2026-04-10T14:00:00Z",
  "end_time": "2026-04-10T15:30:00Z",
  "capacity": 100,
  "registered_count": 0,
  "created_at": "2026-01-15T10:30:00Z"
}
```

---

## PUT /events/{id}

Updates an existing event.

### Request
```http
PUT /events/evt_789012 HTTP/1.1
Host: api.campusevents.example.com
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```
```json
{
  "capacity": 150,
  "location": "Science Building Auditorium"
}
```

### Response

**Status Code:** 200 OK

Returns the updated event object.

---

## DELETE /events/{id}

Deletes an event.

### Request
```http
DELETE /events/evt_789012 HTTP/1.1
Host: api.campusevents.example.com
Authorization: Bearer YOUR_API_KEY
```

### Response

**Status Code:** 204 No Content

No response body. Event successfully deleted.
