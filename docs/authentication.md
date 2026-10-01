# API Authentication

## Overview

Authentication verifies the identity of a client before allowing access to protected API resources.

A secure REST API should require authentication for endpoints that handle protected or sensitive information.

## Authentication Flow

A typical authentication process follows these steps:

1. The client submits valid authentication credentials.
2. The server verifies the credentials.
3. The server issues an access token when authentication succeeds.
4. The client includes the access token with subsequent protected requests.
5. The server validates the token before processing the request.

## Bearer Token Example

Protected requests can use a bearer token in the HTTP Authorization header.

```http
GET /api/v1/users/123
Authorization: Bearer <access-token>
Accept: application/json
```

## Authentication Requirements

Protected API endpoints should require valid authentication before allowing access to protected resources.

Authentication credentials should be protected and should not be unnecessarily exposed in API responses or logs.

## Access Tokens

Access tokens are used to authenticate subsequent requests after the client has successfully authenticated.

Clients should include the access token in the Authorization header when accessing protected endpoints.

Example:

```http
Authorization: Bearer <access-token>
```

## Authentication Failure

When authentication is missing or invalid, the API should reject the request.

Example response:

```http
HTTP/1.1 401 Unauthorized
Content-Type: application/json
```

```json
{
  "error": "unauthorized",
  "message": "Authentication is required."
}
```

## Security Considerations

- Protect authentication credentials from unauthorized access.
- Use HTTPS when transmitting authentication credentials and access tokens.
- Do not expose access tokens unnecessarily.
- Do not include sensitive authentication information in error messages.
- Avoid storing sensitive authentication information in application logs.
- Validate authentication credentials or access tokens before processing protected requests.
