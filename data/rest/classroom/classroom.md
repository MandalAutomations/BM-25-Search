# REST API endpoints for {% data variables.product.prodname_classroom %}

Use the REST API to interact with GitHub Classroom.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get an assignment

```
GET /assignments/{assignment_id}
```

Gets a GitHub Classroom assignment. Assignment will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`assignment_id`** (integer) (required)
  The unique identifier of the classroom assignment.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/assignments/ASSIGNMENT_ID
```

**Response schema (Status: 200):**

* `id`: required, integer
* `public_repo`: required, boolean
* `title`: required, string
* `type`: required, string, enum: `individual`, `group`
* `invite_link`: required, string
* `invitations_enabled`: required, boolean
* `slug`: required, string
* `students_are_repo_admins`: required, boolean
* `feedback_pull_requests_enabled`: required, boolean
* `max_teams`: required, integer or null
* `max_members`: required, integer or null
* `editor`: required, string
* `accepted`: required, integer
* `submitted`: required, integer
* `passing`: required, integer
* `language`: required, string
* `deadline`: required, string or null, format: date-time
* `starter_code_repository`: required, `Simple Classroom Repository`:
  * `id`: required, integer
  * `full_name`: required, string
  * `html_url`: required, string, format: uri
  * `node_id`: required, string
  * `private`: required, boolean
  * `default_branch`: required, string
* `classroom`: required, `Classroom`:
  * `id`: required, integer
  * `name`: required, string
  * `archived`: required, boolean
  * `organization`: required, `Organization Simple for Classroom`:
    * `id`: required, integer
    * `login`: required, string
    * `node_id`: required, string
    * `html_url`: required, string, format: uri
    * `name`: required, string or null
    * `avatar_url`: required, string
  * `url`: required, string





## List accepted assignments for an assignment

```
GET /assignments/{assignment_id}/accepted_assignments
```

Lists any assignment repositories that have been created by students accepting a GitHub Classroom assignment. Accepted assignments will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`assignment_id`** (integer) (required)
  The unique identifier of the classroom assignment.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/assignments/ASSIGNMENT_ID/accepted_assignments
```

**Response schema (Status: 200):**

Array of `Classroom Accepted Assignment`:
  * `id`: required, integer
  * `submitted`: required, boolean
  * `passing`: required, boolean
  * `commit_count`: required, integer
  * `grade`: required, string
  * `students`: required, array of `Simple Classroom User`:
    * `id`: required, integer
    * `login`: required, string
    * `avatar_url`: required, string, format: uri
    * `html_url`: required, string, format: uri
  * `repository`: required, `Simple Classroom Repository`:
    * `id`: required, integer
    * `full_name`: required, string
    * `html_url`: required, string, format: uri
    * `node_id`: required, string
    * `private`: required, boolean
    * `default_branch`: required, string
  * `assignment`: required, `Simple Classroom Assignment`:
    * `id`: required, integer
    * `public_repo`: required, boolean
    * `title`: required, string
    * `type`: required, string, enum: `individual`, `group`
    * `invite_link`: required, string
    * `invitations_enabled`: required, boolean
    * `slug`: required, string
    * `students_are_repo_admins`: required, boolean
    * `feedback_pull_requests_enabled`: required, boolean
    * `max_teams`: integer or null
    * `max_members`: integer or null
    * `editor`: required, string
    * `accepted`: required, integer
    * `submitted`: required, integer
    * `passing`: required, integer
    * `language`: required, string
    * `deadline`: required, string or null, format: date-time
    * `classroom`: required, `Simple Classroom`:
      * `id`: required, integer
      * `name`: required, string
      * `archived`: required, boolean
      * `url`: required, string





## Get assignment grades

```
GET /assignments/{assignment_id}/grades
```

Gets grades for a GitHub Classroom assignment. Grades will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`assignment_id`** (integer) (required)
  The unique identifier of the classroom assignment.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/assignments/ASSIGNMENT_ID/grades
```

**Response schema (Status: 200):**

Array of `Classroom Assignment Grade`:
  * `assignment_name`: required, string
  * `assignment_url`: required, string
  * `starter_code_url`: required, string
  * `github_username`: required, string
  * `roster_identifier`: required, string
  * `student_repository_name`: required, string
  * `student_repository_url`: required, string
  * `submission_timestamp`: required, string
  * `points_awarded`: required, integer
  * `points_available`: required, integer
  * `group_name`: string





## List classrooms

```
GET /classrooms
```

Lists GitHub Classroom classrooms for the current user. Classrooms will only be returned if the current user is an administrator of one or more GitHub Classrooms.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/classrooms
```

**Response schema (Status: 200):**

Array of `Simple Classroom`:
  * `id`: required, integer
  * `name`: required, string
  * `archived`: required, boolean
  * `url`: required, string





## Get a classroom

```
GET /classrooms/{classroom_id}
```

Gets a GitHub Classroom classroom for the current user. Classroom will only be returned if the current user is an administrator of the GitHub Classroom.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`classroom_id`** (integer) (required)
  The unique identifier of the classroom.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/classrooms/CLASSROOM_ID
```

**Response schema (Status: 200):**

* `id`: required, integer
* `name`: required, string
* `archived`: required, boolean
* `organization`: required, `Organization Simple for Classroom`:
  * `id`: required, integer
  * `login`: required, string
  * `node_id`: required, string
  * `html_url`: required, string, format: uri
  * `name`: required, string or null
  * `avatar_url`: required, string
* `url`: required, string





## List assignments for a classroom

```
GET /classrooms/{classroom_id}/assignments
```

Lists GitHub Classroom assignments for a classroom. Assignments will only be returned if the current user is an administrator of the GitHub Classroom.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`classroom_id`** (integer) (required)
  The unique identifier of the classroom.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/classrooms/CLASSROOM_ID/assignments
```

**Response schema (Status: 200):**

Array of `Simple Classroom Assignment`:
  * `id`: required, integer
  * `public_repo`: required, boolean
  * `title`: required, string
  * `type`: required, string, enum: `individual`, `group`
  * `invite_link`: required, string
  * `invitations_enabled`: required, boolean
  * `slug`: required, string
  * `students_are_repo_admins`: required, boolean
  * `feedback_pull_requests_enabled`: required, boolean
  * `max_teams`: integer or null
  * `max_members`: integer or null
  * `editor`: required, string
  * `accepted`: required, integer
  * `submitted`: required, integer
  * `passing`: required, integer
  * `language`: required, string
  * `deadline`: required, string or null, format: date-time
  * `classroom`: required, `Simple Classroom`:
    * `id`: required, integer
    * `name`: required, string
    * `archived`: required, boolean
    * `url`: required, string