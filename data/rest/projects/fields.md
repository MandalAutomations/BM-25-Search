# REST API endpoints for Project fields

Use the REST API to manage Project fields


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List project fields for organization

```
GET /orgs/{org}/projectsV2/{project_number}/fields
```

List all fields for a specific organization-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."






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
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/fields
```

**Response schema (Status: 200):**

Array of `Projects v2 Field`:
  * `id`: required, integer
  * `issue_field_id`: integer
  * `node_id`: string
  * `project_url`: required, string
  * `name`: required, string
  * `data_type`: required, string, enum: `assignees`, `linked_pull_requests`, `reviewers`, `labels`, `milestone`, `repository`, `title`, `text`, `single_select`, `number`, `date`, `iteration`, `issue_type`, `parent_issue`, `sub_issues_progress`
  * `options`: array of `Projects v2 Single Select Option`:
    * `id`: required, string
    * `name`: required, object:
      * `raw`: required, string
      * `html`: required, string
    * `description`: required, object:
      * `raw`: required, string
      * `html`: required, string
    * `color`: required, string
  * `configuration`: object:
    * `start_day`: integer
    * `duration`: integer
    * `iterations`: array of `Projects v2 Iteration Setting`:
      * `id`: required, string
      * `start_date`: required, string, format: date
      * `duration`: required, integer
      * `title`: required, object:
        * `raw`: required, string
        * `html`: required, string
      * `completed`: required, boolean
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time





## Add a field to an organization-owned project.

```
POST /orgs/{org}/projectsV2/{project_number}/fields
```

Add a field to an organization-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`issue_field_id`** (integer) (required)
  The ID of the IssueField to create the field for.

- **`name`** (string) (required)
  The name of the field.

- **`data_type`** (string) (required)
  The field's data type.
  Can be one of: `iteration`

- **`single_select_options`** (array of objects)
  The options available for single select fields. At least one option must be provided when creating a single select field.
  - **`name`** (string)
    The display name of the option.
  - **`color`** (string)
    The color associated with the option.
    Can be one of: `BLUE`, `GRAY`, `GREEN`, `ORANGE`, `PINK`, `PURPLE`, `RED`, `YELLOW`
  - **`description`** (string)
    The description of the option.

- **`iteration_configuration`** (object) (required)
  The configuration for iteration fields.
  - **`start_date`** (string)
    The start date of the first iteration.
  - **`duration`** (integer)
    The default duration for iterations in days. Individual iterations can override this value.
  - **`iterations`** (array of objects)
    Zero or more iterations for the field.
    - **`title`** (string)
      The title of the iteration.
    - **`start_date`** (string)
      The start date of the iteration.
    - **`duration`** (integer)
      The duration of the iteration in days.





### HTTP response status codes


- **201** - Response for adding a field to an organization-owned project.


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Create a text field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Team notes",
  "data_type": "text"
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `issue_field_id`: integer
* `node_id`: string
* `project_url`: required, string
* `name`: required, string
* `data_type`: required, string, enum: `assignees`, `linked_pull_requests`, `reviewers`, `labels`, `milestone`, `repository`, `title`, `text`, `single_select`, `number`, `date`, `iteration`, `issue_type`, `parent_issue`, `sub_issues_progress`
* `options`: array of `Projects v2 Single Select Option`:
  * `id`: required, string
  * `name`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `description`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `color`: required, string
* `configuration`: object:
  * `start_day`: integer
  * `duration`: integer
  * `iterations`: array of `Projects v2 Iteration Setting`:
    * `id`: required, string
    * `start_date`: required, string, format: date
    * `duration`: required, integer
    * `title`: required, object:
      * `raw`: required, string
      * `html`: required, string
    * `completed`: required, boolean
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time



#### Create a number field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Story points",
  "data_type": "number"
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `issue_field_id`: integer
* `node_id`: string
* `project_url`: required, string
* `name`: required, string
* `data_type`: required, string, enum: `assignees`, `linked_pull_requests`, `reviewers`, `labels`, `milestone`, `repository`, `title`, `text`, `single_select`, `number`, `date`, `iteration`, `issue_type`, `parent_issue`, `sub_issues_progress`
* `options`: array of `Projects v2 Single Select Option`:
  * `id`: required, string
  * `name`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `description`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `color`: required, string
* `configuration`: object:
  * `start_day`: integer
  * `duration`: integer
  * `iterations`: array of `Projects v2 Iteration Setting`:
    * `id`: required, string
    * `start_date`: required, string, format: date
    * `duration`: required, integer
    * `title`: required, object:
      * `raw`: required, string
      * `html`: required, string
    * `completed`: required, boolean
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time



#### Create a date field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Due date",
  "data_type": "date"
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `issue_field_id`: integer
* `node_id`: string
* `project_url`: required, string
* `name`: required, string
* `data_type`: required, string, enum: `assignees`, `linked_pull_requests`, `reviewers`, `labels`, `milestone`, `repository`, `title`, `text`, `single_select`, `number`, `date`, `iteration`, `issue_type`, `parent_issue`, `sub_issues_progress`
* `options`: array of `Projects v2 Single Select Option`:
  * `id`: required, string
  * `name`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `description`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `color`: required, string
* `configuration`: object:
  * `start_day`: integer
  * `duration`: integer
  * `iterations`: array of `Projects v2 Iteration Setting`:
    * `id`: required, string
    * `start_date`: required, string, format: date
    * `duration`: required, integer
    * `title`: required, object:
      * `raw`: required, string
      * `html`: required, string
    * `completed`: required, boolean
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time



#### Create a single select field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Priority",
  "data_type": "single_select",
  "single_select_options": [
    {
      "name": {
        "raw": "Low",
        "html": "Low"
      },
      "color": "GREEN",
      "description": {
        "raw": "Low priority items",
        "html": "Low priority items"
      }
    },
    {
      "name": {
        "raw": "Medium",
        "html": "Medium"
      },
      "color": "YELLOW",
      "description": {
        "raw": "Medium priority items",
        "html": "Medium priority items"
      }
    },
    {
      "name": {
        "raw": "High",
        "html": "High"
      },
      "color": "RED",
      "description": {
        "raw": "High priority items",
        "html": "High priority items"
      }
    }
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `issue_field_id`: integer
* `node_id`: string
* `project_url`: required, string
* `name`: required, string
* `data_type`: required, string, enum: `assignees`, `linked_pull_requests`, `reviewers`, `labels`, `milestone`, `repository`, `title`, `text`, `single_select`, `number`, `date`, `iteration`, `issue_type`, `parent_issue`, `sub_issues_progress`
* `options`: array of `Projects v2 Single Select Option`:
  * `id`: required, string
  * `name`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `description`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `color`: required, string
* `configuration`: object:
  * `start_day`: integer
  * `duration`: integer
  * `iterations`: array of `Projects v2 Iteration Setting`:
    * `id`: required, string
    * `start_date`: required, string, format: date
    * `duration`: required, integer
    * `title`: required, object:
      * `raw`: required, string
      * `html`: required, string
    * `completed`: required, boolean
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time



#### Create an iteration field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Sprint",
  "data_type": "iteration",
  "iteration_configuration": {
    "start_day": 1,
    "duration": 14,
    "iterations": [
      {
        "title": {
          "raw": "Sprint 1",
          "html": "Sprint 1"
        },
        "start_date": "2022-07-01",
        "duration": 14
      },
      {
        "title": {
          "raw": "Sprint 2",
          "html": "Sprint 2"
        },
        "start_date": "2022-07-15",
        "duration": 14
      }
    ]
  }
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `issue_field_id`: integer
* `node_id`: string
* `project_url`: required, string
* `name`: required, string
* `data_type`: required, string, enum: `assignees`, `linked_pull_requests`, `reviewers`, `labels`, `milestone`, `repository`, `title`, `text`, `single_select`, `number`, `date`, `iteration`, `issue_type`, `parent_issue`, `sub_issues_progress`
* `options`: array of `Projects v2 Single Select Option`:
  * `id`: required, string
  * `name`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `description`: required, object:
    * `raw`: required, string
    * `html`: required, string
  * `color`: required, string
* `configuration`: object:
  * `start_day`: integer
  * `duration`: integer
  * `iterations`: array of `Projects v2 Iteration Setting`:
    * `id`: required, string
    * `start_date`: required, string, format: date
    * `duration`: required, integer
    * `title`: required, object:
      * `raw`: required, string
      * `html`: required, string
    * `completed`: required, boolean
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time





## Get project field for organization

```
GET /orgs/{org}/projectsV2/{project_number}/fields/{field_id}
```

Get a specific field for an organization-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`field_id`** (integer) (required)
  The unique identifier of the field.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






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
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/fields/FIELD_ID
```

**Response schema (Status: 200):**

Same response schema as [Add a field to an organization-owned project.](#add-a-field-to-an-organization-owned-project).





## List project fields for user

```
GET /users/{username}/projectsV2/{project_number}/fields
```

List all fields for a specific user-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."






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
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/fields
```

**Response schema (Status: 200):**

Same response schema as [List project fields for organization](#list-project-fields-for-organization).





## Add field to user owned project

```
POST /users/{username}/projectsV2/{project_number}/fields
```

Add a field to a specified user owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`project_number`** (integer) (required)
  The project's number.




#### Body parameters

- **`name`** (string) (required)
  The name of the field.

- **`data_type`** (string) (required)
  The field's data type.
  Can be one of: `iteration`

- **`single_select_options`** (array of objects)
  The options available for single select fields. At least one option must be provided when creating a single select field.
  - **`name`** (string)
    The display name of the option.
  - **`color`** (string)
    The color associated with the option.
    Can be one of: `BLUE`, `GRAY`, `GREEN`, `ORANGE`, `PINK`, `PURPLE`, `RED`, `YELLOW`
  - **`description`** (string)
    The description of the option.

- **`iteration_configuration`** (object) (required)
  The configuration for iteration fields.
  - **`start_date`** (string)
    The start date of the first iteration.
  - **`duration`** (integer)
    The default duration for iterations in days. Individual iterations can override this value.
  - **`iterations`** (array of objects)
    Zero or more iterations for the field.
    - **`title`** (string)
      The title of the iteration.
    - **`start_date`** (string)
      The start date of the iteration.
    - **`duration`** (integer)
      The duration of the iteration in days.





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Create a text field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Team notes",
  "data_type": "text"
}'
```

**Response schema (Status: 201):**

Same response schema as [Add a field to an organization-owned project.](#add-a-field-to-an-organization-owned-project).



#### Create a number field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Story points",
  "data_type": "number"
}'
```

**Response schema (Status: 201):**

Same response schema as [Add a field to an organization-owned project.](#add-a-field-to-an-organization-owned-project).



#### Create a date field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Due date",
  "data_type": "date"
}'
```

**Response schema (Status: 201):**

Same response schema as [Add a field to an organization-owned project.](#add-a-field-to-an-organization-owned-project).



#### Create a single select field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Priority",
  "data_type": "single_select",
  "single_select_options": [
    {
      "name": {
        "raw": "Low",
        "html": "Low"
      },
      "color": "GREEN",
      "description": {
        "raw": "Low priority items",
        "html": "Low priority items"
      }
    },
    {
      "name": {
        "raw": "Medium",
        "html": "Medium"
      },
      "color": "YELLOW",
      "description": {
        "raw": "Medium priority items",
        "html": "Medium priority items"
      }
    },
    {
      "name": {
        "raw": "High",
        "html": "High"
      },
      "color": "RED",
      "description": {
        "raw": "High priority items",
        "html": "High priority items"
      }
    }
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Add a field to an organization-owned project.](#add-a-field-to-an-organization-owned-project).



#### Create an iteration field

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/fields \
  -d '{
  "name": "Sprint",
  "data_type": "iteration",
  "iteration_configuration": {
    "start_day": 1,
    "duration": 14,
    "iterations": [
      {
        "title": {
          "raw": "Sprint 1",
          "html": "Sprint 1"
        },
        "start_date": "2022-07-01",
        "duration": 14
      },
      {
        "title": {
          "raw": "Sprint 2",
          "html": "Sprint 2"
        },
        "start_date": "2022-07-15",
        "duration": 14
      }
    ]
  }
}'
```

**Response schema (Status: 201):**

Same response schema as [Add a field to an organization-owned project.](#add-a-field-to-an-organization-owned-project).





## Get project field for user

```
GET /users/{username}/projectsV2/{project_number}/fields/{field_id}
```

Get a specific field for a user-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`field_id`** (integer) (required)
  The unique identifier of the field.

- **`username`** (string) (required)
  The handle for the GitHub user account.






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
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/fields/FIELD_ID
```

**Response schema (Status: 200):**

Same response schema as [Add a field to an organization-owned project.](#add-a-field-to-an-organization-owned-project).