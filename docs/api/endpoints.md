# Endpoints

## User API

### Get User

Retrieve information about a specific user.

- **URL**: `/api/v1/users/{user_id}`
- **Method**: `GET`
- **URL Params**: `{user_id}`: The ID of the user to retrieve.
- **Success Response**:

    ```json
    {
      "id": "user_id",
      "name": "User Name",
      "email": "user@example.com"
    }
    ```

### Create User

Create a new user.

- **URL**: `/api/v1/users`
- **Method**: `POST`
- **Body**:

    ```json
    {
      "name": "User Name",
      "email": "user@example.com",
      "password": "password"
    }
    ```

- **Success Response**:

    ```json
    {
      "id": "new_user_id",
      "name": "User Name",
      "email": "user@example.com"
    }
    ```

## Product API

### List Products

Retrieve a list of products.

- **URL**: `/api/v1/products`
- **Method**: `GET`
- **Success Response**:

    ```json
    [
      {
        "id": "product_id",
        "name": "Product Name",
        "price": 100
      }
    ]
    ```

### Create Product

Create a new product.

- **URL**: `/api/v1/products`
- **Method**: `POST`
- **Body**:

    ```json
    {
      "name": "Product Name",
      "price": 100
    }
    ```

- **Success Response**:

    ```json
    {
      "id": "new_product_id",
      "name": "Product Name",
      "price": 100
    }
    ```