# Authentication

This document provides an overview of the authentication methods supported by the API. All requests to protected endpoints must include a valid authentication token.

## Table of Contents

1. [Overview](#overview)
2. [Authentication Methods](#authentication-methods)
   - [API Key Authentication](#api-key-authentication)
   - [Bearer Token Authentication](#bearer-token-authentication)
3. [Obtaining Tokens](#obtaining-tokens)
4. [Refreshing Tokens](#refreshing-tokens)
5. [Token Revocation](#token-revocation)
6. [Common Errors](#common-errors)
7. [Best Practices](#best-practices)

## Overview

The API uses token-based authentication to protect endpoints and ensure secure access. You can authenticate using an API key or Bearer token depending on the endpoint requirements.

## Authentication Methods

### API Key Authentication

- **Description**: API Key authentication involves including a unique key in the request headers or query parameters.
- **Usage**: Typically used for server-to-server communication or for requests that require less security.
- **Header Format**:
```http
GET /endpoint
Host: api.example.com
X-API-Key: YOUR_API_KEY
```
- **Query Parameter Format**:
```http
GET /endpoint?api_key=YOUR_API_KEY
```
### Bearer Token

- **Description**: Bearer Token authentication is more secure and involves passing a JWT (JSON Web Token) in the `Authorization` header of each request.
- **Usage**: Required for accessing most protected endpoints and is typically used after logging in or obtaining a token via OAuth2.
- **Header Format**:
```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Obtaining Token

To obtain a token, you must authenticate with your credentials (username and password) using the `/auth/login` endpoint. Upon successful authentication, an access token and a refresh token are returned.

### Example Request
```http
POST /auth/login
Host: api.example.com
Content-Type: application/json

{
  "username": "user@example.com",
  "password": "your-password"
}
```

### Example Response
```json
{
  "access_token": "your-access-token",
  "refresh_token": "your-refresh-token",
  "expires_in": 3600
}
```

## Refreshing Tokens

Access tokens are short-lived, and a new token must be obtained using a refresh token. The refresh token does not expire quickly and can be used to request a new access token.

### Example Request
```http
POST /auth/refresh
Host: api.example.com
Content-Type: application/json
Authorization: Bearer YOUR_REFRESH_TOKEN

{
  "refresh_token": "your-refresh-token"
}
```

### Example Response
```json
{
  "access_token": "new-access-token",
  "expires_in": 3600
}
```

## Token Revocation

To revoke an active access or refresh token, use the `/auth/logout` endpoint. This action prevents further use of the token for authentication.

### Example Request
```http
POST /auth/logout
Host: api.example.com
Authorization: Bearer YOUR_ACCESS_TOKEN
```

### Example Response
```json
{
  "message": "Successfully logged out."
}
```

## Common Errors

- **401 Unauthorized**: The token is missing, expired, or invalid.
- **403 Forbidden**: The token is valid, but the user does not have permission to access the requested resource.
- **400 Bad Request**: The request format is incorrect, or required parameters are missing.

### Example Error Response
```json
{
  "error": {
    "code": "INVALID_TOKEN",
    "message": "The provided token is invalid or expired."
  }
}
```

## Best Practices

- Always use HTTPS to encrypt requests and responses.
- Store access tokens securely (e.g., HTTP-only cookies, secure storage).
- Use short-lived access tokens and refresh them when needed.
- Log out and revoke tokens after a user session ends or during suspicious activity.
- Regularly rotate API keys and secrets.