# REST API endpoints for {% data variables.product.prodname_project_v1_caps %} columns

Use the REST API to create and manage columns on a project (classic).


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.


## Get a project column

```
GET /projects/columns/{column_id}
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`column_id`** (integer) (required)
  The unique identifier of the column.






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/projects/columns/COLUMN_ID
```

**Response schema (Status: 200):**

* `url`: required, string, format: uri
* `project_url`: required, string, format: uri
* `cards_url`: required, string, format: uri
* `id`: required, integer
* `node_id`: required, string
* `name`: required, string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time





## Update an existing project column

```
PATCH /projects/columns/{column_id}
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`column_id`** (integer) (required)
  The unique identifier of the column.




#### Body parameters

- **`name`** (string) (required)
  Name of the project column





### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Rename the project column

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/projects/columns/COLUMN_ID \
  -d '{
  "name": "To Do"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a project column](#get-a-project-column).





## Delete a project column

```
DELETE /projects/columns/{column_id}
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`column_id`** (integer) (required)
  The unique identifier of the column.






### HTTP response status codes


- **204** - No Content


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/projects/columns/COLUMN_ID
```

**Response schema (Status: 204):**





## Move a project column

```
POST /projects/columns/{column_id}/moves
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`column_id`** (integer) (required)
  The unique identifier of the column.




#### Body parameters

- **`position`** (string) (required)
  The position of the column in a project. Can be one of: first, last, or after:<column_id> to place after the specified column.





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Move the column to the end of the board

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/projects/columns/COLUMN_ID/moves \
  -d '{
  "position": "last"
}'
```

**Response schema (Status: 201):**







## List project columns

```
GET /projects/{project_id}/columns
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_id`** (integer) (required)
  The unique identifier of the project.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID/columns
```

**Response schema (Status: 200):**

Array of `Project Column`:
  * `url`: required, string, format: uri
  * `project_url`: required, string, format: uri
  * `cards_url`: required, string, format: uri
  * `id`: required, integer
  * `node_id`: required, string
  * `name`: required, string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time





## Create a project column

```
POST /projects/{project_id}/columns
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_id`** (integer) (required)
  The unique identifier of the project.




#### Body parameters

- **`name`** (string) (required)
  Name of the project column





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID/columns \
  -d '{
  "name": "Remaining tasks"
}'
```

**Response schema (Status: 201):**

Same response schema as [Get a project column](#get-a-project-column).