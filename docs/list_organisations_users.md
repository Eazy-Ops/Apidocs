# List available organisations and users

This endpoint retrieves a list of organisations and their associated users that have been onboarded to EazyOps.

## API Endpoint

`GET /api/v1/users/main/organisations`

### Query Parameters

| Name     | Type    | Description                |
|----------|---------|----------------------------|
| `offset` | integer | The starting offset for pagination. |
| `limit`  | integer | The maximum number of results to return. |

### cURL Example

```bash
curl -X 'GET' \
  'https://rest.eazyops.cloud/api/v1/users/main/organisations?offset=0&limit=10' \
  -H 'accept: application/json'
```

### Sample Response

```json
{
  "total": 17,
  "offset": 10,
  "limit": 10,
  "next_offset": null,
  "has_more": false,
  "results": [
    {
      "id": "2c751e58-c78e-4e80-bb50-18bb86200da8",
      "name": "dbaplatform",
      "users": [
        {
          "email": "lior@dbaplatform.com"
        }
      ]
    },
    {
      "id": "50faa978-78d2-492b-95c0-2232a89bf2a7",
      "name": "pawapay",
      "users": [
        {
          "email": "ali.kahoot@pawapay.co.uk"
        }
      ]
    },
    {
      "id": "1ad56dc5-61ae-4f44-b83a-f49d49797595",
      "name": "mecocloud",
      "users": [
        {
          "email": "jessie@mecocloud.com"
        }
      ]
    },
    {
      "id": "300456a2-d2a7-4d1e-8e82-81a7783bcc2b",
      "name": "bazaartech",
      "users": [
        {
          "email": "adnan.khan@bazaartech.com"
        }
      ]
    },
    {
      "id": "db8788d0-415f-4eb1-8e2b-7097c10f2acf",
      "name": "akqa",
      "users": [
        {
          "email": "owais.amjed@akqa.com"
        }
      ]
    },
    {
      "id": "c9949dfb-f635-4522-a330-fa7b902293d8",
      "name": "streem",
      "users": [
        {
          "email": "accounts@streem.com.au"
        },
        {
          "email": "jack.bartlett@streem.com.au"
        }
      ]
    },
    {
      "id": "a4bf9b7c-4b14-413a-8a1c-7e10ebef99d3",
      "name": "esmglobalconsulting",
      "users": [
        {
          "email": "ab@esmglobalconsulting.com"
        }
      ]
    }
  ]
}
```

### Usage Notes

The `users` array in the response contains the email addresses of users who have been onboarded to EazyOps. You can use these email addresses with the [User Authentication API](authentication.md) to obtain an authentication token for a specific user. This token can then be used to call other APIs, such as the [Reports API](reports.md), to get data for that user's organisation report.

