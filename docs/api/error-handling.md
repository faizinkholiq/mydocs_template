# Error Handling

Our API uses standard HTTP status codes to indicate the success or failure of an API request. Here are some common error responses:

## Common Errors

- **400 Bad Request**: The request was invalid. This can occur due to missing parameters or incorrect request format.
- **401 Unauthorized**: Authentication failed or user does not have permission for the requested operation.
- **403 Forbidden**: The user does not have the necessary permissions to access the resource.
- **404 Not Found**: The requested resource was not found.
- **500 Internal Server Error**: An error occurred on the server.

### Example Error Response

```json
{
  "error": "invalid_request",
  "error_description": "The request is missing required parameters."
}