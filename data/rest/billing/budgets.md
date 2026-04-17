# Budgets

Use the REST API to get budget information.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get all budgets for an organization

```
GET /organizations/{org}/settings/billing/budgets
```

Note

This endpoint is in public preview and is subject to change.

Gets all budgets for an organization. The authenticated user must be an organization admin or billing manager.
Each page returns up to 10 budgets.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`page`** (integer)
  The page number of the results to fetch.
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 10).
  Default: `10`

- **`scope`** (string)
  Filter budgets by scope type.
  Can be one of: `enterprise`, `organization`, `repository`, `cost_center`






### HTTP response status codes


- **200** - Response when getting all budgets


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/organizations/ORG/settings/billing/budgets
```

**Response schema (Status: 200):**

* `budgets`: required, array of objects:
  * `id`: required, string
  * `budget_type`: required, one of:
    * **string, enum: `SkuPricing`**
    * **string, enum: `ProductPricing`**
  * `budget_amount`: required, integer
  * `prevent_further_usage`: required, boolean
  * `budget_scope`: required, string
  * `budget_entity_name`: string
  * `budget_product_sku`: required, string
  * `budget_alerting`: required, object:
    * `will_alert`: required, boolean
    * `alert_recipients`: required, array of string
* `has_next_page`: boolean
* `total_count`: integer





## Get a budget by ID for an organization

```
GET /organizations/{org}/settings/billing/budgets/{budget_id}
```

Note

This endpoint is in public preview and is subject to change.

Gets a budget by ID. The authenticated user must be an organization admin or billing manager.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`budget_id`** (string) (required)
  The ID corresponding to the budget.






### HTTP response status codes


- **200** - Response when updating a budget


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
  -X GET \
  https://api.github.com/organizations/ORG/settings/billing/budgets/BUDGET_ID
```

**Response schema (Status: 200):**

* `id`: required, string
* `budget_scope`: required, string, enum: `enterprise`, `organization`, `repository`, `cost_center`
* `budget_entity_name`: required, string
* `budget_amount`: required, integer
* `prevent_further_usage`: required, boolean
* `budget_product_sku`: required, string
* `budget_type`: required, one of:
  * **string, enum: `ProductPricing`**
  * **string, enum: `SkuPricing`**
* `budget_alerting`: required, object:
  * `will_alert`: boolean
  * `alert_recipients`: array of string





## Update a budget for an organization

```
PATCH /organizations/{org}/settings/billing/budgets/{budget_id}
```

Note

This endpoint is in public preview and is subject to change.

Updates an existing budget for an organization. The authenticated user must be an organization admin or billing manager.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`budget_id`** (string) (required)
  The ID corresponding to the budget.




#### Body parameters

- **`budget_amount`** (integer)
  The budget amount in whole dollars. For license-based products, this represents the number of licenses.

- **`prevent_further_usage`** (boolean)
  Whether to prevent additional spending once the budget is exceeded

- **`budget_alerting`** (object)
  - **`will_alert`** (boolean)
    Whether alerts are enabled for this budget
  - **`alert_recipients`** (array of strings)
    Array of user login names who will receive alerts

- **`budget_scope`** (string)
  The scope of the budget
  Can be one of: `enterprise`, `organization`, `repository`, `cost_center`

- **`budget_entity_name`** (string)
  The name of the entity to apply the budget to

- **`budget_type`** (string)
  The type of pricing for the budget

- **`budget_product_sku`** (string)
  A single product or SKU that will be covered in the budget





### HTTP response status codes


- **200** - Budget updated successfully


- **400** - Bad Request


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Budget not found or feature not enabled


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal server error




### Code examples



#### Update budget example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/organizations/ORG/settings/billing/budgets/BUDGET_ID \
  -d '{
  "prevent_further_usage": false,
  "budget_amount": 10,
  "budget_alerting": {
    "will_alert": false,
    "alert_recipients": []
  }
}'
```

**Response schema (Status: 200):**

* `message`: string
* `budget`: object:
  * `id`: string
  * `budget_amount`: number, format: float
  * `prevent_further_usage`: boolean
  * `budget_alerting`: object:
    * `will_alert`: required, boolean
    * `alert_recipients`: required, array of string
  * `budget_scope`: string, enum: `enterprise`, `organization`, `repository`, `cost_center`
  * `budget_entity_name`: string, default: `""`
  * `budget_type`: one of:
    * **string, enum: `ProductPricing`**
    * **string, enum: `SkuPricing`**
  * `budget_product_sku`: string





## Delete a budget for an organization

```
DELETE /organizations/{org}/settings/billing/budgets/{budget_id}
```

Note

This endpoint is in public preview and is subject to change.

Deletes a budget by ID for an organization. The authenticated user must be an organization admin or billing manager.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`budget_id`** (string) (required)
  The ID corresponding to the budget.






### HTTP response status codes


- **200** - Response when deleting a budget


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
  https://api.github.com/organizations/ORG/settings/billing/budgets/BUDGET_ID
```

**Response schema (Status: 200):**

* `message`: required, string
* `id`: required, string