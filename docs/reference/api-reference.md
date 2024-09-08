# API Reference

This document provides a detailed reference for all API endpoints, including request and response formats, error handling, and authentication requirements.

## Table of Contents

1. [Overview](#overview)
2. [Authentication](#authentication)
3. [Error Handling](#error-handling)
4. [Endpoints](#endpoints)
   - [User Endpoints](#user-endpoints)
     - [Get User](#get-user)
     - [Create User](#create-user)
     - [Update User](#update-user)
     - [Delete User](#delete-user)
   - [Order Endpoints](#order-endpoints)
     - [Get Orders](#get-orders)
     - [Create Order](#create-order)
     - [Update Order](#update-order)
     - [Delete Order](#delete-order)

## Overview

This API provides access to user and order data for managing accounts and orders within the system. All endpoints are RESTful and use standard HTTP methods and status codes.

- **Base URL**: `https://api.example.com/v1/`
- **Content-Type**: `application/json`
- **Rate Limiting**: 100 requests per minute

## Authentication

All endpoints require authentication via an API token. Tokens should be included in the `Authorization` header as follows:

```http
Authorization: Bearer YOUR_API_TOKEN
```

Tokens can be obtained by logging in through the /auth/login endpoint. See the [Authentication](authentication.md) section for more details.

## Error Handling

The API uses standard HTTP status codes to indicate the success or failure of an API request. Error responses include a JSON body with an error code and message.

- 200 OK: The request was successful.
- 400 Bad Request: The request was invalid.
- 401 Unauthorized: The request requires user authentication.
- 404 Not Found: The requested resource was not found.
- 500 Internal Server Error: An unexpected error occurred on the server.

Example of an error response:

```json
{
  "error": {
    "code": "INVALID_REQUEST",
    "message": "The request payload is missing a required field."
  }
}
```

## Endpoints

### User Endpoints

#### Get User

- **Description**: Retrieve a user by ID.
- **Method**: `GET`
- **Endpoint**: `/users/{id}`
- **Authentication**: Required
- **Request Parameters**:
  - `id` (path): The ID of the user to retrieve.
- **Response**:
    ```json
    {
    "id": "12345",
    "name": "John Doe",
    "email": "john.doe@example.com",
    "created_at": "2024-01-01T12:00:00Z"
    }
    ```
- **Errors**:
  - `404 Not Found`: User not found.
  - `401 Unauthorized`: Authentication failed.

#### Create User

- **Description**: Create a new user.
- **Method**: `POST`
- **Endpoint**: `/users`
- **Authentication**: Required
- **Request Body**:
    ```json
    {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "password": "your-secure-password"
    }
    ```
- **Response**:
    ```json
    {
        "id": "12345",
        "name": "John Doe",
        "email": "john.doe@example.com",
        "created_at": "2024-01-01T12:00:00Z"
    }
    ```
- **Errors**:
  - `400 Bad Request`: Invalid input data.
  - `401 Unauthorized`: Authentication failed.

### Order Endpoints

#### Get Orders
- **Description**: Retrieve a list of orders.
- **Method**: `GET`
- **Endpoint**: `/orders`
- **Authentication**: Required
- **Request Parameters**:
  - `user_id` (query): Optional. Filter orders by user ID.
- **Response**:
    ```json
    [
        {
            "id": "67890",
            "product": "Product A",
            "quantity": 2,
            "price": 19.99,
            "status": "Shipped",
            "created_at": "2024-01-01T12:00:00Z"
        }
    ]
    ```
- Errors:
    - `401 Unauthorized`: Authentication failed.