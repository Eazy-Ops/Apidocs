## Overview API

### Get Organization Overview

**Endpoint:**

GET https://rest.eazyops.cloud/overview/organisation/{organisation_id}/{connector_id}?page=1&size=10

**Description:**
Retrieves an overview of an organization, including resource counts, potential cost savings, and project-specific details.

**Request Headers:**

| Header        | Value             |
|---------------|-----------------|
| accept        | application/json, text/plain, */* |
| Authorization	| Bearer <final_token> |

**Path Parameters:**

| Parameter        | Description                                   | Example |
|------------------|-----------------------------------------------|---------|
| `organisation_id`| The UUID of the organization.                 | `7bbc83cd-ba37-4f8a-9e34-3d1e24701678` |
| `connector_id`   | The UUID of the connector.                    | `a68028aa-7e48-4eb3-a5b5-7d1d74479610` |

**Query Parameters:**

| Parameter | Description                                   | Example |
|-----------|-----------------------------------------------|---------|
| `page`    | The page number for pagination.               | `1`     |
| `size`    | The number of items per page.                 | `10`    |

**Example cURL:**

```bash
curl 'https://rest.eazyops.cloud/overview/organisation/7bbc83cd-ba37-4f8a-9e34-3d1e24701678/a68028aa-7e48-4eb3-a5b5-7d1d74479610?page=1&size=10' \
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
    "id": "7bbc83cd-ba37-4f8a-9e34-3d1e24701678",
    "name": "eazy_547574100405",
    "instances": 0,
    "disks": 6,
    "databases": 1,
    "logs": 2,
    "clusters": 0,
    "potential_cost": 48.11,
    "actual_cost": 92.22999999999999,
    "savings_percentage": 47.84,
    "action": {
        "scaling": 3,
        "delete": 6
    },
    "projects": [
        {
            "id": "595258a8-0514-45f9-a549-dad3407d78e4",
            "name": "stg-ezo",
            "workload": 2,
            "instances": 0,
            "databases": 1,
            "disks": 0,
            "bq_tables": 0,
            "bq_jobs": 0,
            "logs": 1,
            "clusters": 0,
            "disk_action": {},
            "bq_table_action": {},
            "bq_job_action": {},
            "instance_action": {},
            "database_action": {
                "delete": 0,
                "scaling": 1
            },
            "log_action": {
                "delete": 0,
                "scaling": 1
            },
            "disk_resource": {},
            "cluster_resource": {},
            "instance_resource": {},
            "database_resource": {
                "delete": 0,
                "scaling": 1
            },
            "cluster_resource": {},
            "bq_table_resource": {},
            "bq_job_resource": {},
            "log_resource": {
                "delete": 0,
                "scaling": 1
            },
            "token_scopes": {
                "log": true,
                "disk": true,
                "bq_job": false,
                "bucket": false,
                "cluster": true,
                "project": false,
                "bq_table": false,
                "database": true,
                "instance": true
            },
            "potential_cost": 48.11,
            "actual_cost": 70.36999999999999,
            "savings_percentage": 31.63,
            "action": {
                "scaling": 2,
                "delete": 0,
                "cost": 0
            },
            "cross_cloud_pricing": {
                "aws": 178.85,
                "azure": 266.68
            },
            "cuds": {
                "instance": {
                    "Commit1Yr": 0.0,
                    "Commit3Yr": 0.0,
                    "underutilization_waste_usd": 0.0,
                    "spend_based_cud_utilization_percent": 0.0,
                    "expected_utilization_percent": 0.0
                },
                "database": {
                    "Commit1Yr": 0.0,
                    "Commit3Yr": 0.0,
                    "underutilization_waste_usd": 0.0,
                    "spend_based_cud_utilization_percent": 0.0,
                    "expected_utilization_percent": 0.0
                },
                "cluster": {
                    "Commit1Yr": 0.0,
                    "Commit3Yr": 0.0,
                    "underutilization_waste_usd": 0.0,
                    "spend_based_cud_utilization_percent": 0.0,
                    "expected_utilization_percent": 0.0
                }
            },
            "spot_prices": {
                "instance": {
                    "spot_price_monthly": 0.0
                },
                "database": {
                    "spot_price_monthly": 0.0
                },
                "cluster": {
                    "spot_price_monthly": 0.0
                }
            },
            "total_spot_prices": 0.0,
            "potential_cost_spot_prices": 70.37,
            "savings_percentage_spot_prices": -0.0,
            "total_1yr_cuds": 0.0,
            "potential_cost_1yr_cuds": 0.0,
            "savings_percentage_1yr_cuds": 0.0,
            "total_3yr_cuds": 0.0,
            "potential_cost_3yr_cuds": 0.0,
            "savings_percentage_3yr_cuds": 0.0,
            "discovery_id": "fd7f8441-f5a8-49b3-9394-c7114fc8ffa8",
            "last_synced_at": "2025-10-03T07:04:34.258490",
            "artifact_image_data": [],
            "actual_cost_annually": 844.4399999999998,
            "saving": 22.25999999999999,
            "saving_annually": 267.1199999999999,
            "forecast_actual_cost": 77.40699999999998,
            "forecast_actual_cost_annually": 928.8839999999998,
            "resource_wise_costing": {
                "disk": 0,
                "instance": 0,
                "database": 70.36999999999999,
                "log": 0,
                "cluster": 0,
                "static_ip": 0.0,
                "disk_snapshot": 0,
                "database_snapshot": 0,
                "artifact_image": 0
            },
            "action_wise_savings": {
                "scaling": {
                    "count": 2,
                    "saving": 22.25999999999999
                },
                "delete": {
                    "count": 0,
                    "saving": 0
                },
                "cuds": {
                    "count": 0,
                    "saving": 0
                }
            },
            "ip": 0,
            "snapshot": 0,
            "billing": {},
            "discovery_status": "completed",
            "is_unattended": false
        }
    ],
    "bq_jobs": 0,
    "bq_tables": 0,
    "buckets": 0,
    "total": 3,
    "page": 1,
    "size": 10,
    "pages": 1
}
```
**Notes:**

- The `id` in the top-level response is the `organisation_id`.
- Each object in the `projects` array contains an `id` which is the `project_id`.
- These IDs can be used in the Reports API for type `organisation` or `project` respectively.
- The currency for all amounts related data in reponse section is USD $.
