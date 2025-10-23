## 1. User Authentication

To ensure the security of your data, the EazyOps API uses a two-step authentication process. First, you generate a temporary token, which you then exchange for a final authentication token. This final token must be included in the `Authorization` header of all subsequent API requests.

### 1.1 Generate a Temporary Token

**Endpoint:**

`POST https://rest.eazyops.cloud/api/v1/users`

**Description:**

This endpoint generates a temporary token for a user based on their email address. This token is required for the next step of the authentication process.

**Request Headers:**

| Header         | Value              |
|----------------|--------------------|
| `accept`       | `application/json` |
| `Content-Type` | `application/json` |

**Request Payload:**

```json
{
  "email": "muhammad.hussain@zazmic.com",
  "name": "",
  "receive_token": true,
  "send_email": false
}
```

⚠️ **Important:** Never set `"send_email": true` for existing customers. Doing so may trigger unintended email notifications.

**Response Example:**

```json
{
  "email": "muhammad.hussain@zazmic.com",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

**Notes:**

*   The returned token is a temporary token that must be used in the next step to obtain a final authentication token.
*   This temporary token has a short expiration time and should be used immediately.

### 1.2 Exchange the Temporary Token for an Authentication Token

**Endpoint:**

`GET https://rest.eazyops.cloud/api/v1/users/login`

**Description:**

This endpoint exchanges the temporary token from the previous step for a final authentication token (Bearer token). This token is used to authenticate all subsequent API requests.

**Request Headers:**

| Header          | Value                                       |
|-----------------|---------------------------------------------|
| `accept`        | `application/json`                          |
| `Authorization` | `Bearer <token_from_previous_step>`         |

**Example cURL:**

```bash
curl -X 'GET' \
  'https://rest.eazyops.cloud/api/v1/users/login' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...'
```

**Response Example:**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

This token is the final authentication token that you will use for all subsequent API requests. Make sure to store it securely.