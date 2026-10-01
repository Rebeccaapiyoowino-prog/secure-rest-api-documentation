# API Error Handling

## Overview

Consistent error handling helps API clients understand why a request failed and allows applications to respond appropriately.

API errors should provide useful information without exposing sensitive implementation details.

## HTTP Status Codes

The API may use standard HTTP status codes to communicate request results.

| Status Code | Meaning |
|-------------|---------|
| 200 | Request completed successfully |
| 201 | Resource created successfully |
| 204 | Request completed with no response body |
| 400 | Bad request or invalid input |
| 401 | Authentication is required or invalid |
| 403 | Authenticated user is not authorized |
| 404 | Requested resource was not found |
| 500 | Unexpected server error |

## Error Response Format

API errors should use a consistent JSON structure.

Example:

```json
{
  "error": "invalid_request",
  "message": "The request contains invalid parameters."
}
```

## 400 Bad Request

Returned when the client sends invalid or malformed input.

```json
{
  "error": "invalid_request",
  "message": "The request contains invalid parameters."
}
```

## 401 Unauthorized

Returned when authentication is missing or invalid.

```json
{
  "error": "unauthorized",
  "message": "Authentication is required."
}
```

## 403 Forbidden

Returned when an authenticated user does not have permission to perform the requested operation.

```json
{
  "error": "forbidden",
  "message": "You do not have permission to perform this operation."
}
```

## 404 Not Found

Returned when the requested resource does not exist.

```json
{
  "error": "not_found",
  "message": "The requested resource was not found."
}
```

## 500 Internal Server Error

Returned when an unexpected error occurs on the server.

```json
{
  "error": "internal_server_error",
  "message": "An unexpected error occurred."
}
```

## Security Considerations

Error responses should not expose:

- Passwords
- Authentication tokens
- API keys
- Database credentials
- Internal file paths
- Stack traces
- Sensitive system configuration

Detailed diagnostic information should be recorded securely in server-side logs when appropriate.
