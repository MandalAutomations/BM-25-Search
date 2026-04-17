# REST API endpoints for issue fields

Use the REST API to create and manage issue fields for an organization.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List issue fields for an organization

```
GET /orgs/{org}/issue-fields
```

Lists all issue fields for an organization. OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/issue-fields
```

**Response schema (Status: 200):**

Array of `Issue Field`:
  * `id`: required, integer
  * `node_id`: required, string
  * `name`: required, string
  * `description`: string or null
  * `data_type`: required, string, enum: `text`, `date`, `single_select`, `number`
  * `visibility`: string, enum: `organization_members_only`, `all`
  * `options`: array of objects or null:
    * `id`: required, integer
    * `name`: required, string
    * `description`: string or null
    * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
    * `priority`: integer or null
    * `created_at`: string, format: date-time
    * `updated_at`: string, format: date-time
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time





## Create issue field for an organization

```
POST /orgs/{org}/issue-fields
```

Creates a new issue field for an organization.
You can find out more about issue fields in Managing issue fields in an organization.
To use this endpoint, the authenticated user must be an administrator for the organization. OAuth app tokens and
personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  Name of the issue field.

- **`description`** (string or null)
  Description of the issue field.

- **`data_type`** (string) (required)
  The data type of the issue field.
  Can be one of: `text`, `date`, `single_select`, `number`

- **`visibility`** (string)
  The visibility of the issue field. Can be organization_members_only (visible only within the organization) or all (visible to all users who can see issues). Only used when the visibility settings feature is enabled. Defaults to organization_members_only.
  Can be one of: `organization_members_only`, `all`

- **`options`** (array of objects or null)
  Options for single select fields. Required when data_type is 'single_select'.
  - **`name`** (string) (required)
    Name of the option.
  - **`description`** (string or null)
    Description of the option.
  - **`color`** (string) (required)
    Color for the option.
    Can be one of: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`
  - **`priority`** (integer) (required)
    Priority of the option for ordering.





### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/issue-fields \
  -d '{
  "name": "Priority",
  "description": "Level of importance for the issue",
  "data_type": "single_select",
  "options": [
    {
      "name": "High",
      "description": "High priority",
      "color": "red"
    },
    {
      "name": "Medium",
      "description": "Medium priority",
      "color": "yellow"
    },
    {
      "name": "Low",
      "description": "Low priority",
      "color": "green"
    }
  ]
}'
```

**Response schema (Status: 200):**

* `id`: required, integer
* `node_id`: required, string
* `name`: required, string
* `description`: string or null
* `data_type`: required, string, enum: `text`, `date`, `single_select`, `number`
* `visibility`: string, enum: `organization_members_only`, `all`
* `options`: array of objects or null:
  * `id`: required, integer
  * `name`: required, string
  * `description`: string or null
  * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
  * `priority`: integer or null
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time





## Update issue field for an organization

```
PATCH /orgs/{org}/issue-fields/{issue_field_id}
```

Updates an issue field for an organization.
You can find out more about issue fields in Managing issue fields in an organization.
To use this endpoint, the authenticated user must be an administrator for the organization. OAuth app tokens and
personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`issue_field_id`** (integer) (required)
  The unique identifier of the issue field.




#### Body parameters

- **`name`** (string)
  Name of the issue field.

- **`description`** (string or null)
  Description of the issue field.

- **`visibility`** (string)
  The visibility of the issue field. Can be organization_members_only (visible only within the organization) or all (visible to all users who can see issues). Only used when the visibility settings feature is enabled.
  Can be one of: `organization_members_only`, `all`

- **`options`** (array of objects)
  Options for single select fields. Only applicable when updating single_select fields. When provided, this array replaces the entire existing set of options rather than adding to or updating individual options. To retain or update an existing option, include it in the array with its id. Options sent without an id are treated as new options and may cause existing options to be deleted and recreated.
  - **`id`** (integer)
    The id of an existing option to retain or update. Omit this when creating a new option.
  - **`name`** (string) (required)
    Name of the option.
  - **`description`** (string or null)
    Description of the option.
  - **`color`** (string) (required)
    Color for the option.
    Can be one of: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`
  - **`priority`** (integer) (required)
    Priority of the option for ordering.





### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Update name and description

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/issue-fields/ISSUE_FIELD_ID \
  -d '{
  "name": "Priority",
  "description": "Level of importance for the issue"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create issue field for an organization](#create-issue-field-for-an-organization).





## Delete issue field for an organization

```
DELETE /orgs/{org}/issue-fields/{issue_field_id}
```

Deletes an issue field for an organization.
You can find out more about issue fields in Managing issue fields in an organization.
To use this endpoint, the authenticated user must be an administrator for the organization. OAuth app tokens and
personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`issue_field_id`** (integer) (required)
  The unique identifier of the issue field.






### HTTP response status codes


- **204** - A header with no content is returned.


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/issue-fields/ISSUE_FIELD_ID
```

**Response schema (Status: 204):**