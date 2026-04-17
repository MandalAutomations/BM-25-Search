# REST API endpoints for {% data variables.product.prodname_projects_v1_caps %}

Use the REST API to create and manage projects (classic) in a repository.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.


## List organization projects

```
GET /orgs/{org}/projects
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`state`** (string)
  Indicates the state of the projects to return.
  Default: `open`
  Can be one of: `open`, `closed`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/orgs/ORG/projects
```

**Response schema (Status: 200):**

Array of `Project`:
  * `owner_url`: required, string, format: uri
  * `url`: required, string, format: uri
  * `html_url`: required, string, format: uri
  * `columns_url`: required, string, format: uri
  * `id`: required, integer
  * `node_id`: required, string
  * `name`: required, string
  * `body`: required, string or null
  * `number`: required, integer
  * `state`: required, string
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
  * `organization_permission`: string, enum: `read`, `write`, `admin`, `none`
  * `private`: boolean





## Create an organization project

```
POST /orgs/{org}/projects
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  The name of the project.

- **`body`** (string)
  The description of the project.





### HTTP response status codes


- **201** - Created


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **410** - Gone


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/orgs/ORG/projects \
  -d '{
  "name": "Organization Roadmap",
  "body": "High-level roadmap for the upcoming year."
}'
```

**Response schema (Status: 201):**

* `owner_url`: required, string, format: uri
* `url`: required, string, format: uri
* `html_url`: required, string, format: uri
* `columns_url`: required, string, format: uri
* `id`: required, integer
* `node_id`: required, string
* `name`: required, string
* `body`: required, string or null
* `number`: required, integer
* `state`: required, string
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
* `organization_permission`: string, enum: `read`, `write`, `admin`, `none`
* `private`: boolean





## Get a project

```
GET /projects/{project_id}
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
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an organization project](#create-an-organization-project).





## Update a project

```
PATCH /projects/{project_id}
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

- **`name`** (string)
  Name of the project

- **`body`** (string or null)
  Body of the project

- **`state`** (string)
  State of the project; either 'open' or 'closed'

- **`organization_permission`** (string)
  The baseline permission that all organization members have on this project
  Can be one of: `read`, `write`, `admin`, `none`

- **`private`** (boolean)
  Whether or not this project can be seen by everyone.





### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Not Found if the authenticated user does not have access to the project


- **410** - Gone


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Change the name, state, and permissions for a project

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID \
  -d '{
  "name": "Week One Sprint",
  "state": "open",
  "organization_permission": "write"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an organization project](#create-an-organization-project).





## Delete a project

```
DELETE /projects/{project_id}
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






### HTTP response status codes


- **204** - Delete Success


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **410** - Gone




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID
```

**Response schema (Status: 204):**





## List repository projects

```
GET /repos/{owner}/{repo}/projects
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`state`** (string)
  Indicates the state of the projects to return.
  Default: `open`
  Can be one of: `open`, `closed`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **410** - Gone


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/projects
```

**Response schema (Status: 200):**

Same response schema as [List organization projects](#list-organization-projects).





## Create a repository project

```
POST /repos/{owner}/{repo}/projects
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  The name of the project.

- **`body`** (string)
  The description of the project.





### HTTP response status codes


- **201** - Created


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **410** - Gone


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/projects \
  -d '{
  "name": "Projects Documentation",
  "body": "Developer documentation project for the developer site."
}'
```

**Response schema (Status: 201):**

Same response schema as [Create an organization project](#create-an-organization-project).





## Create a user project

```
POST /user/projects
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.





#### Body parameters

- **`name`** (string) (required)
  Name of the project

- **`body`** (string or null)
  Body of the project





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Create a new project

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/user/projects \
  -d '{
  "name": "My Projects",
  "body": "A board to manage my personal projects."
}'
```

**Response schema (Status: 201):**

Same response schema as [Create an organization project](#create-an-organization-project).





## List user projects

```
GET /users/{username}/projects
```

Warning

Closing down notice: Projects (classic) is being deprecated in favor of the new Projects experience.
See the changelog for more information.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`state`** (string)
  Indicates the state of the projects to return.
  Default: `open`
  Can be one of: `open`, `closed`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/users/USERNAME/projects
```

**Response schema (Status: 200):**

Same response schema as [List organization projects](#list-organization-projects).