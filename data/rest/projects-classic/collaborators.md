# REST API endpoints for {% data variables.product.prodname_project_v1_caps %} collaborators

Use the REST API to manage collaborators on a project (classic).


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.


## List project collaborators

```
GET /projects/{project_id}/collaborators
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

- **`affiliation`** (string)
  Filters the collaborators by their affiliation. outside means outside collaborators of a project that are not a member of the project's organization. direct means collaborators with permissions to a project, regardless of organization membership status. all means all collaborators the authenticated user can see.
  Default: `all`
  Can be one of: `outside`, `direct`, `all`

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


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID/collaborators
```

**Response schema (Status: 200):**

Array of `Simple User`:
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





## Add project collaborator

```
PUT /projects/{project_id}/collaborators/{username}
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

- **`username`** (string) (required)
  The handle for the GitHub user account.




#### Body parameters

- **`permission`** (string)
  The permission to grant the collaborator.
  Default: `write`
  Can be one of: `read`, `write`, `admin`





### HTTP response status codes


- **204** - No Content


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Applying write permissions for the new collaborator

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID/collaborators/USERNAME \
  -d '{
  "permission": "write"
}'
```

**Response schema (Status: 204):**





## Remove user as a collaborator

```
DELETE /projects/{project_id}/collaborators/{username}
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

- **`username`** (string) (required)
  The handle for the GitHub user account.






### HTTP response status codes


- **204** - No Content


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID/collaborators/USERNAME
```

**Response schema (Status: 204):**





## Get project permission for a user

```
GET /projects/{project_id}/collaborators/{username}/permission
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

- **`username`** (string) (required)
  The handle for the GitHub user account.






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/projects/PROJECT_ID/collaborators/USERNAME/permission
```

**Response schema (Status: 200):**

* `permission`: required, string
* `user`: required, any of:
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