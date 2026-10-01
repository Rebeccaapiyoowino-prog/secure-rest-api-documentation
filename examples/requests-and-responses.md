# API Requests and Responses

## Overview

This document provides examples of common REST API requests and their corresponding responses.

The examples demonstrate authenticated requests, successful responses, validation errors, authentication errors, and authorization errors.

## Get User

### Request

```http
GET /api/v1/users/123
Authorization: Bearer <access-token>
Accept: application/json
```

### Successful Response

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

```json
{
  "id": 123,
  "name": "Example User",
  "email": "user@example.com"
}
```

## Create User

### POST /api/v1/users

Creates a new user.

### Request

```http
POST /api/v1/users
Authorization: Bearer <access-token>
Content-Type: application/json
```

```json
{
  "name": "Example User",
  "email": "user@example.com"
}
```

### Successful Response

```http
HTTP/1.1 201 Created
Content-Type: application/json
```

```json
{
  "id": 124,
  "name": "Example User",
  "email": "user@example.com"
}
```

## Update User

### PUT /api/v1/users/{id}

Updates an existing user's information.

### Request

```http
PUT /api/v1/users/123
Authorization: Bearer <access-token>
Content-Type: application/json
```

```json
{
  "name": "Updated User"
}
```

### Successful Response

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

```json
{
  "id": 123,
  "name": "Updated User"
}
```

## Delete User

### DELETE /api/v1/users/{id}

Deletes a specific user.

### Request

```http
DELETE /api/v1/users/123
Authorization: Bearer <access-token>
```

### Successful Response

```http
HTTP/1.1 204 No Content
```

## Error Responses

### 400 Bad Request

Returned when the request contains invalid or malformed data.

```json
{
  "error": "invalid_request",
  "message": "The request contains invalid parameters."
}
```

### 401 Unauthorized

Returned when authentication is missing or invalid.

```json
{
  "error": "unauthorized",
  "message": "Authentication is required."
}
```

### 403 Forbidden

Returned when an authenticated user does not have permission to perform an operation.

```json
{
  "error": "forbidden",
  "message": "You do not have permission to perform this operation."
}
```

### 404 Not Found

Returned when the requested resource does not exist.

```json
{
  "error": "not_found",
  "message": "The requested resource was not found."
}
```

## Security Requirements

- Protected endpoints must require authentication.
- Authorization must be enforced according to user roles or permissions.
- Request data should be validated before processing.
- Sensitive information should not be unnecessarily exposed in responses.
- API credentials and access tokens should be protected.
- HTTPS should be used when transmitting API requests and responses.
- Error messages should avoid exposing sensitive implementation details.
