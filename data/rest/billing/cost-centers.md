# Cost centers

Use the REST API to get cost center information.

## Required roles

The following roles can access cost center API endpoints:

* **Enterprise owners**
* **Billing managers**
* **Organization owners**

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get all cost centers for an enterprise

```
GET /enterprises/{enterprise}/settings/billing/cost-centers
```

Gets a list of all the cost centers for an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`state`** (string)
  Set to active or deleted to only list cost centers in a specific state.
  Can be one of: `active`, `deleted`






### HTTP response status codes


- **200** - Response when getting cost centers


- **400** - Bad Request


- **403** - Forbidden


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/cost-centers
```

**Response schema (Status: 200):**

* `costCenters`: array of objects:
  * `id`: required, string
  * `name`: required, string
  * `state`: string, enum: `active`, `deleted`
  * `azure_subscription`: string or null
  * `resources`: required, array of objects:
    * `type`: required, string
    * `name`: required, string





## Create a new cost center

```
POST /enterprises/{enterprise}/settings/billing/cost-centers
```

Creates a new cost center for an enterprise. The authenticated user must be an enterprise admin.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`name`** (string) (required)
  The name of the cost center (max length 255 characters)





### HTTP response status codes


- **200** - Cost center created successfully


- **400** - Bad request


- **409** - Conflict


- **500** - Internal server error




### Code examples



#### Example request to create a cost center

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/cost-centers \
  -d '{
  "name": "Engineering Team"
}'
```

**Response schema (Status: 200):**

* `id`: string
* `name`: string
* `azure_subscription`: string or null
* `state`: string, enum: `active`, `deleted`
* `resources`: array of objects:
  * `type`: string
  * `name`: string





## Get a cost center by ID

```
GET /enterprises/{enterprise}/settings/billing/cost-centers/{cost_center_id}
```

Gets a cost center by ID. The authenticated user must be an enterprise admin.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`cost_center_id`** (string) (required)
  The ID corresponding to the cost center.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






### HTTP response status codes


- **200** - Response when getting a cost center


- **400** - Bad Request


- **403** - Forbidden


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/cost-centers/COST_CENTER_ID
```

**Response schema (Status: 200):**

* `id`: required, string
* `name`: required, string
* `azure_subscription`: string or null
* `state`: string, enum: `active`, `deleted`
* `resources`: required, array of objects:
  * `type`: required, string
  * `name`: required, string
* `has_next_page`: boolean





## Update a cost center name

```
PATCH /enterprises/{enterprise}/settings/billing/cost-centers/{cost_center_id}
```

Updates an existing cost center name.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name

- **`cost_center_id`** (string) (required)
  The unique identifier of the cost center




#### Body parameters

- **`name`** (string) (required)
  The new name for the cost center





### HTTP response status codes


- **200** - Response when updating a cost center


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Update cost center name example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/cost-centers/COST_CENTER_ID \
  -d '{
  "name": "New Cost Center Name"
}'
```

**Response schema (Status: 200):**

* `id`: required, string
* `name`: required, string
* `azure_subscription`: string or null
* `state`: string, enum: `active`, `deleted`
* `resources`: required, array of objects:
  * `type`: required, string
  * `name`: required, string





## Delete a cost center

```
DELETE /enterprises/{enterprise}/settings/billing/cost-centers/{cost_center_id}
```

Archieves a cost center by ID. The authenticated user must be an enterprise admin.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`cost_center_id`** (string) (required)
  The ID corresponding to the cost center.






### HTTP response status codes


- **200** - Response when deleting a cost center


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/cost-centers/COST_CENTER_ID
```

**Response schema (Status: 200):**

* `message`: required, string
* `id`: required, string
* `name`: required, string
* `costCenterState`: required, string, enum: `CostCenterArchived`





## Add resources to a cost center

```
POST /enterprises/{enterprise}/settings/billing/cost-centers/{cost_center_id}/resource
```

Adds resources to a cost center.
The usage for the resources will be charged to the cost center's budget. The authenticated user must be an enterprise admin in order to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`cost_center_id`** (string) (required)
  The ID corresponding to the cost center.




#### Body parameters

- **`users`** (array of strings)
  The usernames of the users to add to the cost center.

- **`organizations`** (array of strings)
  The organizations to add to the cost center.

- **`repositories`** (array of strings)
  The repositories to add to the cost center.





### HTTP response status codes


- **200** - Response when adding resources to a cost center


- **400** - Bad Request


- **403** - Forbidden


- **409** - Conflict


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/cost-centers/COST_CENTER_ID/resource \
  -d '{
  "users": [
    "monalisa"
  ]
}'
```

**Response schema (Status: 200):**

* `message`: string
* `reassigned_resources`: array of objects or null:
  * `resource_type`: string
  * `name`: string
  * `previous_cost_center`: string





## Remove resources from a cost center

```
DELETE /enterprises/{enterprise}/settings/billing/cost-centers/{cost_center_id}/resource
```

Remove resources from a cost center.
The usage for the resources will no longer be charged to the cost center's budget. The authenticated user must be an enterprise admin in order to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`cost_center_id`** (string) (required)
  The ID corresponding to the cost center.




#### Body parameters

- **`users`** (array of strings)
  The usernames of the users to remove from the cost center.

- **`organizations`** (array of strings)
  The organizations to remove from the cost center.

- **`repositories`** (array of strings)
  The repositories to remove from the cost center.





### HTTP response status codes


- **200** - Response when removing resources from a cost center


- **400** - Bad Request


- **403** - Forbidden


- **500** - Internal Error


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/cost-centers/COST_CENTER_ID/resource \
  -d '{
  "users": [
    "monalisa"
  ]
}'
```

**Response schema (Status: 200):**

* `message`: string