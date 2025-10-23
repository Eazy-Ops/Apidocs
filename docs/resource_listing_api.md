## Resource Listing API

### List Resources by Project and Type

**Endpoint:**

GET https://rest.eazyops.cloud/api/resource/{project_id}/list?type={type}&page=1&size=50&platform={platform}&sort_by_savings=desc

**Description:**
Retrieves a paginated list of resources for a given project and resource type. The `project_id` can be obtained from the Overview API response.

**Request Headers:**

| Header        | Value             |
|---------------|-----------------|
| accept        | application/json, text/plain, */* |
| Authorization	| Bearer <final_token> |

**Path Parameters:**

| Parameter    | Description                                   | Example |
|--------------|-----------------------------------------------|---------|
| `project_id` | The UUID of the project.                      | `595258a8-0514-45f9-a549-dad3407d78e4` |

**Query Parameters:**

| Parameter        | Description                                   | Example |
|------------------|-----------------------------------------------|---------|
| `type`           | The type of resource to list.                 | `database` |
| `page`           | The page number for pagination.               | `1`     |
| `size`           | The number of items per page.                 | `50`    |
| `platform`       | The cloud platform (e.g., `gcp`, `aws`, `azure`). | `gcp`   |
| `sort_by_savings`| Sort order for savings.                       | `desc`  |

**Available Resource Types:**

- `log`
- `disk`
- `instance`
- `database`
- `cluster`
- `bucket`

**Example cURL:**

```bash
curl 'https://rest.eazyops.cloud/api/resource/595258a8-0514-45f9-a549-dad3407d78e4/list?type=database&page=1&size=50&platform=gcp&sort_by_savings=desc' \
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
    "items": [
        {
            "id": "c44a8dfa-6e48-4576-a0de-3b6f48c6becd",
            "object": "{}",
            "version": "latest",
            "discovery_id": "fd7f8441-f5a8-49b3-9394-c7114fc8ffa8",
            "name": "prod-postgres",
            "type": "sql#instance",
            "is_deleted": false,
            "project_id": "595258a8-0514-45f9-a549-dad3407d78e4",
            "created_at": "2025-10-03T07:01:20.504792",
            "discovery": null,
            "project": {
                "id": "595258a8-0514-45f9-a549-dad3407d78e4",
                "name": "stg-ezo",
                "connectors": []
            },
            "logs": [],
            "savings": {
                "scaling": {
                    "high": {
                        "detail": {
                            "action": "scaling",
                            "after_current_disk": "PD_SSD",
                            "after_current_disk_size": 10.0,
                            "cost_after": 48.11,
                            "cost_before": 70.36999999999999,
                            "count": 1,
                            "current_disk": "PD_SSD",
                            "current_disk_size": 20.0,
                            "saving_percentage": 31.63279806735824,
                            "type_after": "db-custom-1-2556",
                            "type_before": "db-custom-1-6656",
                            "id": "c44a8dfa-6e48-4576-a0de-3b6f48c6becd",
                            "policy_name": "high"
                        },
                        "schedule": null,
                        "projection_id": "ba935fd1-fb0d-4d13-8c3b-d8bb789b9741",
                        "action_essentials": {
                            "state": true,
                            "non_disruptive": false,
                            "reversible": true
                        },
                        "cli": {
                            "command": "gcloud sql instances patch None --tier=db-custom-1-2556 \n "
                        },
                        "teraform": {
                            "command": "\n        resource \"google_sql_database_instance\" \"instance\" {\n        name             = \"None\"\n        database_version = \"MYSQL_8_0\" # Or your desired database version\n        region           = \"us-central1\"\n\n        settings {\n            tier = \"db-custom-1-6656\" # Or your existing tier\n\n            data_disk_type = \"db-custom-1-2556\" # Change the disk type here\n            data_disk_size_gb = 10 # Or your desired disk size\n        }\n        }\n     \n "
                        },
                        "yaml": {
                            "command": "\n        resources:\n        - name: prod-postgres\n        type: gcp-types/sqladmin-v1beta4:instances\n        properties:\n            region: us-central1\n            settings:\n            tier: db-custom-1-6656\n            dataDiskType: db-custom-1-2556\n            dataDiskSizeGb: 10\n    gcloud deployment-manager deployments update  --config sql-instance-update.yaml \n "
                        }
                    }
                }
            },
            "max_savings": 31.63279806735824,
            "health": "healthy",
            "risk": "low"
        }
    ],
    "total": 1,
    "page": 1,
    "size": 50,
    "pages": 1,
    "projections": {
        "actual_cost": 70.36999999999999,
        "potential_cost": 48.11,
        "actual_cost_annually": 844.4399999999998,
        "saving": 22.25999999999999,
        "saving_annually": 267.1199999999999,
        "forecast_actual_cost": 73.8885,
        "forecast_actual_cost_annually": 886.6619999999999,
        "savings_percentage": 31.63
    }
}
```

**Notes:**

- The `id` within each item in the `items` array is the `resource_id`.
- This `resource_id` can be used in the Reports API for type `resource`.
- The currency for all amounts related data in reponse section is USD $.