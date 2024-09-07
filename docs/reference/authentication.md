# Authentication

Our API uses OAuth 2.0 for authentication. Below are the details for obtaining and using access tokens.

## Getting an Access Token

To obtain an access token, send a POST request to `/oauth2/token` with the following parameters:

- `grant_type`: The type of grant being used. For example, `authorization_code` or `client_credentials`.
- `client_id`: Your client ID.
- `client_secret`: Your client secret.
- `redirect_uri`: The URI to which the authorization server will redirect the user after granting access.

### Example Request

```http
POST /oauth2/token HTTP/1.1
Host: api.example.com
Content-Type: application/x-www-form-urlencoded

grant_type=authorization_code&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET&code=AUTH_CODE&redirect_uri=YOUR_REDIRECT_URI
```

## Using the Access Token

Include the access token in the Authorization header for all API requests.

### Example Request

```http
GET /api/v1/resource HTTP/1.1
Host: api.example.com
Authorization: Bearer ACCESS_TOKEN
```

### Example Response

```json
{
  "data": "Your data here"
}
```