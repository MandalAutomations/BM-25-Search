# REST API endpoints for {% data variables.product.prodname_project_v1_caps %} cards

Use the REST API to create and manage cards on a project (classic).


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.


## Get a project card

```
GET /projects/columns/cards/{card_id}
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`card_id`** (integer) (required)
  The unique identifier of the card.






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
  http(s)://HOSTNAME/api/v3/projects/columns/cards/CARD_ID
```

**Response schema (Status: 200):**

* `url`: required, string, format: uri
* `id`: required, integer, format: int64
* `node_id`: required, string
* `note`: required, string or null
* `creator`: required, any of:
  * **null**
  * **Simple User**
    * `name`: string or null
    * `email`: string or null
    * `login`: required, string
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `avatar_url`: required, string, format: uri
    * `gravatar_id`: required, string or null
    * `url`: required, string, format: uri
    * `html_url`: required, string, format: uri
    * `followers_url`: required, string, format: uri
    * `following_url`: required, string
    * `gists_url`: required, string
    * `starred_url`: required, string
    * `subscriptions_url`: required, string, format: uri
    * `organizations_url`: required, string, format: uri
    * `repos_url`: required, string, format: uri
    * `events_url`: required, string
    * `received_events_url`: required, string, format: uri
    * `type`: required, string
    * `site_admin`: required, boolean
    * `starred_at`: string
    * `user_view_type`: string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `archived`: boolean
* `column_name`: string
* `project_id`: string
* `column_url`: required, string, format: uri
* `content_url`: string, format: uri
* `project_url`: required, string, format: uri





## Update an existing project card

```
PATCH /projects/columns/cards/{card_id}
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`card_id`** (integer) (required)
  The unique identifier of the card.




#### Body parameters

- **`note`** (string or null)
  The project card's note

- **`archived`** (boolean)
  Whether or not the card is archived





### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Change the note on the card

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/projects/columns/cards/CARD_ID \
  -d '{
  "note": "Add payload for delete Project column"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a project card](#get-a-project-card).





## Delete a project card

```
DELETE /projects/columns/cards/{card_id}
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`card_id`** (integer) (required)
  The unique identifier of the card.






### HTTP response status codes


- **204** - No Content


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/projects/columns/cards/CARD_ID
```

**Response schema (Status: 204):**





## Move a project card

```
POST /projects/columns/cards/{card_id}/moves
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`card_id`** (integer) (required)
  The unique identifier of the card.




#### Body parameters

- **`position`** (string) (required)
  The position of the card in a column. Can be one of: top, bottom, or after:<card_id> to place after the specified card.

- **`column_id`** (integer)
  The unique identifier of the column the card should be moved to





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.


- **503** - Service Unavailable




### Code examples



#### Move the card to the bottom of the column

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/projects/columns/cards/CARD_ID/moves \
  -d '{
  "column_id": 42,
  "position": "bottom"
}'
```

**Response schema (Status: 201):**







## List project cards

```
GET /projects/columns/{column_id}/cards
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

- **`archived_state`** (string)
  Filters the project cards that are returned by the card's state.
  Default: `not_archived`
  Can be one of: `all`, `archived`, `not_archived`

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
  http(s)://HOSTNAME/api/v3/projects/columns/COLUMN_ID/cards
```

**Response schema (Status: 200):**

Array of `Project Card`:
  * `url`: required, string, format: uri
  * `id`: required, integer, format: int64
  * `node_id`: required, string
  * `note`: required, string or null
  * `creator`: required, any of:
    * **null**
    * **Simple User**
      * `name`: string or null
      * `email`: string or null
      * `login`: required, string
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `avatar_url`: required, string, format: uri
      * `gravatar_id`: required, string or null
      * `url`: required, string, format: uri
      * `html_url`: required, string, format: uri
      * `followers_url`: required, string, format: uri
      * `following_url`: required, string
      * `gists_url`: required, string
      * `starred_url`: required, string
      * `subscriptions_url`: required, string, format: uri
      * `organizations_url`: required, string, format: uri
      * `repos_url`: required, string, format: uri
      * `events_url`: required, string
      * `received_events_url`: required, string, format: uri
      * `type`: required, string
      * `site_admin`: required, boolean
      * `starred_at`: string
      * `user_view_type`: string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `archived`: boolean
  * `column_name`: string
  * `project_id`: string
  * `column_url`: required, string, format: uri
  * `content_url`: string, format: uri
  * `project_url`: required, string, format: uri





## Create a project card

```
POST /projects/columns/{column_id}/cards
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

- **`note`** (string or null) (required)
  The project card's note

- **`content_id`** (integer) (required)
  The unique identifier of the content associated with the card

- **`content_type`** (string) (required)
  The piece of content associated with the card





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed


- **503** - Service Unavailable




### Code examples



#### Create a new card

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/projects/columns/COLUMN_ID/cards \
  -d '{
  "note": "Add payload for delete Project column"
}'
```

**Response schema (Status: 201):**

Same response schema as [Get a project card](#get-a-project-card).