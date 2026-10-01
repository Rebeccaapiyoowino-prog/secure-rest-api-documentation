# API Error Handling

## Overview

Consistent error handling helps API clients understand why a request failed and allows developers to troubleshoot problems safely.

A secure REST API should return appropriate HTTP status codes and useful error messages without exposing sensitive implementation details.

## HTTP Status Codes

The API should use standard HTTP status codes to communicate the result of a request.

Common status codes include:

- `200 OK` — The request was successfully processed.
- `201 Created` — A new resource was successfully created.
- `204 No Content` — The request succeeded without returning a response body.
- `400 Bad Request` — The request contains invalid or malformed data.
- `401 Unauthorized` — Authentication is required or the supplied credentials are invalid.
- `403 Forbidden` — The client is authenticated but does not have permission to perform the requested operation.
- `404 Not Found` — The requested resource could not be found.
- `409 Conflict` — The request conflicts with the current state of the resource.
- `422 Unprocessable Entity` — The request is syntactically valid but contains validation errors.
- `500 Internal Server Error` — An unexpected server-side error occurred.

## Error Response Format

Error responses should use a consistent structure.

Example:

```json
{
  "error": "validation_error",
  "message": "The request contains invalid data.",
  "details": {
    "email": "A valid email address is required."
  }
}
