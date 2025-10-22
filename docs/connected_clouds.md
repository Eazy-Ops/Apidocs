## Connected Clouds API

### Get Connected Clouds

**Endpoint:**

GET https://rest.eazyops.cloud/api/clouds/connected-clouds

**Description:**
Retrieves a list of clouds that the user has integrated or against which discoveries have been performed.

**Request Headers:**

| Header        | Value             |
|---------------|-----------------|
| accept        | application/json, text/plain, */* |
| Authorization	| Bearer <final_token> |

**Example cURL:**

```bash
curl 'https://rest.eazyops.cloud/api/clouds/connected-clouds' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'authorization: Bearer <final_token>' \
  -H 'origin: https://eazyops.cloud' \
  -H 'priority: u=1, i' \
  -H 'referer: https://eazyops.cloud/' \
  -H 'sec-ch-ua: "Google Chrome";v="141", "Not?A_Brand";v="8", "Chromium";v="141"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Linux"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-site' \
  -H 'user-agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/141.0.0.0 Safari/537.36'
```

**Response Example:**

```json
{
    "connected_clouds": [
        {
            "name": "azure",
            "created_at": "2025-07-17T15:29:31.911387",
            "projects": 1
        },
        {
            "name": "gcp",
            "created_at": "2025-08-03T18:10:47.128850",
            "projects": 2
        }
    ]
}
```
**Notes:**

- The `name` in the top-level response is the name param for connector listing API.

