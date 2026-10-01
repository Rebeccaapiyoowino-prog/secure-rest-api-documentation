# API Endpoints

## Overview

This document describes example REST API endpoints, their expected requests, and their responses.

All protected endpoints should require valid authentication and appropriate authorization.

## User Endpoint

### GET /api/v1/users/{id}

Retrieves information about a specific user.

#### Request

```http
GET /api/v1/users/123
Authorization: Bearer <access-token>
Accept: application/json
