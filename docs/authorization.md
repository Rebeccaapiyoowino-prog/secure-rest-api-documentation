# API Authorization

## Overview

Authorization determines what an authenticated user is permitted to access or perform.

Authentication verifies the identity of a client, while authorization determines whether that client has permission to access a requested resource.

## Authorization Requirements

Protected API resources should enforce authorization checks before allowing access.

Authorization decisions should be based on the authenticated user's assigned roles or permissions.

## Role Based Access

A REST API may use roles to control access to resources.

Example roles include:

- `admin`
- `manager`
- `user`

Administrators may have access to administrative resources, while regular users should only access resources permitted by their assigned role.

## Example Authorization Flow

A typical authorization process follows these steps:

1. The client authenticates successfully.
2. The server identifies the authenticated user.
3. The server determines the user's assigned roles or permissions.
4. The server checks whether the requested operation is allowed.
5. The server processes the request only when authorization succeeds.

## Forbidden Requests

If an authenticated user does not have permission to perform an operation, the API should return an HTTP `403 Forbidden` response.

Example:

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json
```

```json
{
  "error": "forbidden",
  "message": "You do not have permission to perform this operation."
}
```

## Security Considerations

- Authorization checks should be performed on protected resources.
- Permissions should be enforced on the server side.
- Clients should not be trusted to enforce authorization.
- Users should only receive access to resources permitted by their roles or permissions.
- Administrative endpoints should require appropriate privileges.
- Authorization failures should not expose sensitive implementation details.
