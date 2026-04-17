# REST API endpoints for milestones

Use the REST API to manage milestones.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List milestones

```
GET /repos/{owner}/{repo}/milestones
```

Lists milestones for a repository.


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
  The state of the milestone. Either open, closed, or all.
  Default: `open`
  Can be one of: `open`, `closed`, `all`

- **`sort`** (string)
  What to sort results by. Either due_on or completeness.
  Default: `due_on`
  Can be one of: `due_on`, `completeness`

- **`direction`** (string)
  The direction of the sort. Either asc or desc.
  Default: `asc`
  Can be one of: `asc`, `desc`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/milestones
```

**Response schema (Status: 200):**

Array of `Milestone`:
  * `url`: required, string, format: uri
  * `html_url`: required, string, format: uri
  * `labels_url`: required, string, format: uri
  * `id`: required, integer
  * `node_id`: required, string
  * `number`: required, integer
  * `state`: required, string, enum: `open`, `closed`, default: `"open"`
  * `title`: required, string
  * `description`: required, string or null
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
  * `open_issues`: required, integer
  * `closed_issues`: required, integer
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `closed_at`: required, string or null, format: date-time
  * `due_on`: required, string or null, format: date-time





## Create a milestone

```
POST /repos/{owner}/{repo}/milestones
```

Creates a milestone.


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

- **`title`** (string) (required)
  The title of the milestone.

- **`state`** (string)
  The state of the milestone. Either open or closed.
  Default: `open`
  Can be one of: `open`, `closed`

- **`description`** (string)
  A description of the milestone.

- **`due_on`** (string)
  The milestone due date. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.





### HTTP response status codes


- **201** - Created


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/milestones \
  -d '{
  "title": "v1.0",
  "state": "open",
  "description": "Tracking milestone for version 1.0",
  "due_on": "2012-10-09T23:39:01Z"
}'
```

**Response schema (Status: 201):**

* `url`: required, string, format: uri
* `html_url`: required, string, format: uri
* `labels_url`: required, string, format: uri
* `id`: required, integer
* `node_id`: required, string
* `number`: required, integer
* `state`: required, string, enum: `open`, `closed`, default: `"open"`
* `title`: required, string
* `description`: required, string or null
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
* `open_issues`: required, integer
* `closed_issues`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `closed_at`: required, string or null, format: date-time
* `due_on`: required, string or null, format: date-time





## Get a milestone

```
GET /repos/{owner}/{repo}/milestones/{milestone_number}
```

Gets a milestone using the given milestone number.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`milestone_number`** (integer) (required)
  The number that identifies the milestone.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/milestones/MILESTONE_NUMBER
```

**Response schema (Status: 200):**

Same response schema as [Create a milestone](#create-a-milestone).





## Update a milestone

```
PATCH /repos/{owner}/{repo}/milestones/{milestone_number}
```



### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`milestone_number`** (integer) (required)
  The number that identifies the milestone.




#### Body parameters

- **`title`** (string)
  The title of the milestone.

- **`state`** (string)
  The state of the milestone. Either open or closed.
  Default: `open`
  Can be one of: `open`, `closed`

- **`description`** (string)
  A description of the milestone.

- **`due_on`** (string)
  The milestone due date. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.





### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/milestones/MILESTONE_NUMBER \
  -d '{
  "title": "v1.0",
  "state": "open",
  "description": "Tracking milestone for version 1.0",
  "due_on": "2012-10-09T23:39:01Z"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a milestone](#create-a-milestone).





## Delete a milestone

```
DELETE /repos/{owner}/{repo}/milestones/{milestone_number}
```

Deletes a milestone using the given milestone number.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`milestone_number`** (integer) (required)
  The number that identifies the milestone.






### HTTP response status codes


- **204** - No Content


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/milestones/MILESTONE_NUMBER
```

**Response schema (Status: 204):**