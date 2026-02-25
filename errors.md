# Errors

## HTTP Status Codes

The Campus Events API uses standard HTTP status codes:

| Code | Status | Description |
|------|--------|-------------|
| 200 | OK | Request succeeded |
| 201 | Created | Resource successfully created |
| 204 | No Content | Request succeeded, no content returned |
| 400 | Bad Request | Invalid request format or parameters |
| 401 | Unauthorized | Missing or invalid API key |
| 403 | Forbidden | API key lacks required permissions |
| 404 | Not Found | Resource doesn't exist |
| 429 | Too Many Requests | Rate limit exceeded |
| 500 | Internal Server Error | Server error occurred |

## Error Response Format

All error responses follow this structure:
```json
{
  "error": "Error type",
  "message": "Detailed error description",
  "request ID": "req_abc123"
}
```

### Example: Invalid Parameters
```json
{
  "error": "Validation Error",
  "message": "start_time must be in ISO 8601 format (YYYY-MM-DDTHH:MM:SSZ)",
  "request_id": "req_xyz789"
}
```

### Example: Rate Limit Exceeded
```json
{
  "error": "Rate Limit Exceeded",
  "message": "You have exceeded 1000 requests per hour. Resets at 2025-01-15T15:00:00Z",
  "request_id": "req_def456"
