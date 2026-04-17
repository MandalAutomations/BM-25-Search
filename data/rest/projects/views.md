# REST API endpoints for Project views

Use the REST API to manage Project views


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Create a view for an organization-owned project

```
POST /orgs/{org}/projectsV2/{project_number}/views
```

Create a new view in an organization-owned project. Views allow you to customize how items in a project are displayed and filtered.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`project_number`** (integer) (required)
  The project's number.




#### Body parameters

- **`name`** (string) (required)
  The name of the view.

- **`layout`** (string) (required)
  The layout of the view.
  Can be one of: `table`, `board`, `roadmap`

- **`filter`** (string)
  The filter query for the view. See Filtering projects for more information.

- **`visible_fields`** (array of integers)
  visible_fields is not applicable to roadmap layout views.
For table and board layouts, this represents the field IDs that should be visible in the view. If not provided, the default visible fields will be used.





### HTTP response status codes


- **201** - Response for creating a view in an organization-owned project.


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **503** - Service unavailable




### Code examples



#### Create a table view

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/views \
  -d '{
  "name": "All Issues",
  "layout": "table",
  "filter": "is:issue",
  "visible_fields": [
    123,
    456,
    789
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `number`: required, integer
* `name`: required, string
* `layout`: required, string, enum: `table`, `board`, `roadmap`
* `node_id`: required, string
* `project_url`: required, string
* `html_url`: required, string, format: uri
* `creator`: required, all of:
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
* `filter`: string or null
* `visible_fields`: required, array of integer
* `sort_by`: required, array of array, minItems: 2, maxItems: 2
* `group_by`: required, array of integer
* `vertical_group_by`: required, array of integer



#### Create a board view with filter

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/views \
  -d '{
  "name": "Sprint Board",
  "layout": "board",
  "filter": "is:issue is:open label:sprint",
  "visible_fields": [
    123,
    456,
    789
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `number`: required, integer
* `name`: required, string
* `layout`: required, string, enum: `table`, `board`, `roadmap`
* `node_id`: required, string
* `project_url`: required, string
* `html_url`: required, string, format: uri
* `creator`: required, all of:
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
* `filter`: string or null
* `visible_fields`: required, array of integer
* `sort_by`: required, array of array, minItems: 2, maxItems: 2
* `group_by`: required, array of integer
* `vertical_group_by`: required, array of integer



#### Create a roadmap view

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/views \
  -d '{
  "name": "Product Roadmap",
  "layout": "roadmap"
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `number`: required, integer
* `name`: required, string
* `layout`: required, string, enum: `table`, `board`, `roadmap`
* `node_id`: required, string
* `project_url`: required, string
* `html_url`: required, string, format: uri
* `creator`: required, all of:
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
* `filter`: string or null
* `visible_fields`: required, array of integer
* `sort_by`: required, array of array, minItems: 2, maxItems: 2
* `group_by`: required, array of integer
* `vertical_group_by`: required, array of integer





## Create a view for a user-owned project

```
POST /users/{user_id}/projectsV2/{project_number}/views
```

Create a new view in a user-owned project. Views allow you to customize how items in a project are displayed and filtered.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`user_id`** (string) (required)
  The unique identifier of the user.

- **`project_number`** (integer) (required)
  The project's number.




#### Body parameters

- **`name`** (string) (required)
  The name of the view.

- **`layout`** (string) (required)
  The layout of the view.
  Can be one of: `table`, `board`, `roadmap`

- **`filter`** (string)
  The filter query for the view. See Filtering projects for more information.

- **`visible_fields`** (array of integers)
  visible_fields is not applicable to roadmap layout views.
For table and board layouts, this represents the field IDs that should be visible in the view. If not provided, the default visible fields will be used.





### HTTP response status codes


- **201** - Response for creating a view in a user-owned project.


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **503** - Service unavailable




### Code examples



#### Create a table view

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USER_ID/projectsV2/PROJECT_NUMBER/views \
  -d '{
  "name": "All Issues",
  "layout": "table",
  "filter": "is:issue",
  "visible_fields": [
    123,
    456,
    789
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a view for an organization-owned project](#create-a-view-for-an-organization-owned-project).



#### Create a board view with filter

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USER_ID/projectsV2/PROJECT_NUMBER/views \
  -d '{
  "name": "Sprint Board",
  "layout": "board",
  "filter": "is:issue is:open label:sprint",
  "visible_fields": [
    123,
    456,
    789
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a view for an organization-owned project](#create-a-view-for-an-organization-owned-project).



#### Create a roadmap view

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USER_ID/projectsV2/PROJECT_NUMBER/views \
  -d '{
  "name": "Product Roadmap",
  "layout": "roadmap"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a view for an organization-owned project](#create-a-view-for-an-organization-owned-project).