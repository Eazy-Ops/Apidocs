## Get Available Connectors by Cloud Name

**Endpoint:**

`GET https://rest.eazyops.cloud/api/connector/list?cloud_name={cloud_name}`

**Description:**

This endpoint retrieves a list of available connectors for a specific cloud provider. You can identify the cloud provider by its name, which can be obtained from the [Get Connected Clouds](connected_clouds.md) API.

**Request Headers:**

| Header          | Value                               |
|-----------------|-------------------------------------|
| `accept`        | `application/json, text/plain, */*` |
| `Authorization` | `Bearer <authentication_token>`     |

**Path Parameters:**

| Parameter    | Description                                   | Example       |
|--------------|-----------------------------------------------|---------------|
| `cloud_name` | The name of the cloud (e.g., `gcp`, `azure`). | `gcp`         |

**Example cURL:**

```bash
curl 'https://rest.eazyops.cloud/api/connector/list?cloud_name=gcp' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'authorization: Bearer <authentication_token>' \
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
[
    {
        "id": "a737a699-4653-4b12-a8cd-eb678d7a4d15",
        "name": "gcp",
        "status": "Active",
        "type": "file",
        "no_of_projects": 1,
        "organisation_id": [
            "c847339a-8201-4d05-a817-ec2e35f8c95d"
        ],
        "project_id": [
            "3fac14fa-2c3f-4208-b917-c516cc938e95"
        ],
        "discovery_id": "066a6312-1ddc-4370-858b-347724d3fcc0",
        "last_synced_at": "2025-08-21T06:04:18.445146",
        "project_name": [
            "dev-ezo"
        ],
        "resources_count": {
            "instance": 1,
            "disk": 6,
            "database": 0,
            "log": 1,
            "cluster": 0,
            "bq_table": 0,
            "bq_job": 0
        },
        "token_scope": {
            "disk": true,
            "instance": true,
            "database": true,
            "log": true,
            "cluster": true,
            "bucket": false,
            "project": false,
            "bq_table": true,
            "bq_job": true
        },
        "stages_info": {
            "disk": "completed",
            "instance": "completed",
            "database": "completed",
            "log": "completed",
            "cluster": "completed",
            "bq_table": "completed",
            "bq_job": "completed",
            "deployment": "completed"
        },
        "discovery_stage_by_status": {
            "completed": [
                "bq_job",
                "bq_table",
                "cluster",
                "database",
                "deployment",
                "disk",
                "instance",
                "log"
            ]
        },
        "discovery_stage": "completed",
        "discovery_status": true,
        "expires_in": "No Expiration",
        "created_at": "2025-08-21T06:02:06.285111",
        "updated_at": "2025-08-21T06:02:15.415474"
    }
]
```

**Notes:**

*   The `id` in the response is the `connector_id` that you can use in the [Overview API](overview_api.md).
*   The `organisation_id` is the ID of the organization that you can use in the [Overview API](overview_api.md).
