# API Authorization

## Overview

Authorization determines what an authenticated user or client is allowed to access within an API.

Authentication verifies identity, while authorization verifies whether that authenticated identity has permission to perform a requested action.

A secure REST API should enforce authorization checks for protected resources and operations.

## Role Based Access Control

Role based access control can be used to assign permissions according to a user's role.

Typical roles may include:

- Administrator
- Standard user
- Read only user

Each role should have only the permissions required to perform its intended functions.

## Authorization Checks

Authorization should be checked before allowing access to protected resources.

A typical authorization process follows these steps:

1. The client authenticates successfully.
2. The server identifies the user's assigned role or permissions.
3. The server checks whether the requested operation is permitted.
4. The server allows the operation when sufficient permissions exist.
5. The server rejects the request when the required permission is missing.

## Resource Level Authorization

Authorization checks should also be applied to individual resources.

A user should not be able to access or modify another user's resources simply by changing an identifier in the request.

For example:

```http
GET /api/v1/users/123
Authorization: Bearer <access-token>
