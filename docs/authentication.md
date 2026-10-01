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
