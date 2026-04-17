# Usage reports

Use the REST API to create and retrieve usage report exports for an enterprise.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List usage report exports

```
GET /enterprises/{enterprise}/settings/billing/reports
```

Note

This endpoint is in public preview and is subject to change.

Lists all usage report exports for an enterprise. The authenticated user must be an enterprise admin or billing manager.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **200** - List of usage report exports


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/reports
```

**Response schema (Status: 200):**

* `usage_report_exports`: required, array of objects:
  * `id`: required, string, format: uuid
  * `report_type`: required, string, enum: `detailed`, `summarized`, `premium_request`
  * `start_date`: required, string, format: date
  * `end_date`: required, string, format: date
  * `status`: required, string, enum: `processing`, `completed`, `failed`
  * `download_urls`: array of string
  * `created_at`: string, format: date-time
  * `actor`: string





## Create a usage report export

```
POST /enterprises/{enterprise}/settings/billing/reports
```

Note

This endpoint is in public preview and is subject to change.

Initiates the generation of a usage report export for an enterprise. The report will be processed asynchronously
and can be downloaded once completed. The authenticated user must be an enterprise admin or billing manager.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`report_type`** (string) (required)
  The type of usage report to generate
  Can be one of: `detailed`, `summarized`, `premium_request`

- **`start_date`** (string) (required)
  The start date for the report in YYYY-MM-DD format

- **`end_date`** (string)
  The end date for the report in YYYY-MM-DD format. Defaults to today (UTC) if not provided.

- **`send_email`** (boolean)
  Whether to send an email notification to the requester when the report is ready. Defaults to false.
  Default: `false`





### HTTP response status codes


- **202** - Report export request accepted


- **400** - Bad Request


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/reports \
  -d '{
  "report_type": "detailed",
  "start_date": "2024-01-01",
  "end_date": "2024-01-31"
}'
```

**Response schema (Status: 202):**

* `id`: required, string, format: uuid
* `report_type`: required, string, enum: `detailed`, `summarized`, `premium_request`
* `start_date`: required, string, format: date
* `end_date`: required, string, format: date
* `status`: required, string, enum: `processing`, `completed`, `failed`
* `download_urls`: array of string
* `created_at`: string, format: date-time
* `actor`: string





## Get a usage report export

```
GET /enterprises/{enterprise}/settings/billing/reports/{report_id}
```

Note

This endpoint is in public preview and is subject to change.

Gets the status and details of a usage report export by ID. The authenticated user must be an enterprise admin or billing manager.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`report_id`** (string) (required)
  The unique identifier (UUID) for the usage report export.






### HTTP response status codes


- **200** - Usage report export details


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/reports/REPORT_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a usage report export](#create-a-usage-report-export).