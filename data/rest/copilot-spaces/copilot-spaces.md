# REST API endpoints for Copilot Spaces

Use the REST API to manage Copilot Spaces and related resources.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List organization Copilot Spaces

```
GET /orgs/{org}/copilot-spaces
```

Lists Copilot Spaces owned by an organization. The authenticated user must have read access to the organization's Copilot Spaces.
Only Spaces that are readable by the authenticated user are returned. This includes public Spaces and internal Spaces if the user is a member of the organization.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100).
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor.

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor.






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot-spaces
```

**Response schema (Status: 200):**

* `spaces`: required, array of `Space`:
  * `id`: required, integer, format: int64
  * `number`: required, integer
  * `name`: required, string
  * `description`: string or null
  * `general_instructions`: string or null, maxLength: 4000
  * `base_role`: required, string, enum: `reader`, `writer`, `admin`, `no_access`
  * `owner`: required, any of:
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
    * **Organization Simple**
      * `login`: required, string
      * `id`: required, integer
      * `node_id`: required, string
      * `url`: required, string, format: uri
      * `repos_url`: required, string, format: uri
      * `events_url`: required, string, format: uri
      * `hooks_url`: required, string
      * `issues_url`: required, string
      * `members_url`: required, string
      * `public_members_url`: required, string
      * `avatar_url`: required, string
      * `description`: required, string or null
  * `creator`: required, `Simple User`:
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
  * `html_url`: required, string, format: uri
  * `api_url`: required, string, format: uri
  * `resources_attributes`: array of objects:
    * `id`: integer, format: int64
    * `resource_type`: string, enum: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`, `media_content`, `uploaded_text_file`
    * `copilot_chat_attachment_id`: integer or null, format: int64
    * `created_at`: string, format: date-time
    * `updated_at`: string, format: date-time
    * `metadata`: object:
      * `repository_id`: integer
      * `file_path`: string
      * `text`: string
      * `name`: string
      * `number`: integer
      * `copilot_chat_attachment_id`: integer
      * `media_type`: string
      * `url`: string
      * `height`: integer
      * `width`: integer





## Create an organization Copilot Space

```
POST /orgs/{org}/copilot-spaces
```

Creates a new Copilot Space owned by an organization. The authenticated user must have permissions to create spaces in the organization.
Organization members with appropriate permissions can create Copilot Spaces to be shared within their organization.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  The name of the Copilot Space.

- **`description`** (string)
  A description of the Copilot Space.

- **`general_instructions`** (string)
  General instructions for the Copilot Space.

- **`base_role`** (string)
  The base role that determines default permissions for organization members.

no_access: No default access (default)
reader: Organization members can read the space
writer: Organization members can read and edit the space
admin: Organization members have full admin access to the space
  Default: `no_access`
  Can be one of: `reader`, `writer`, `admin`, `no_access`

- **`resources_attributes`** (array of objects)
  Resources to attach to the space.
  - **`resource_type`** (string)
    The type of resource.
    Can be one of: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`, `media_content`, `uploaded_text_file`
  - **`metadata`** (object)
    Metadata specific to the resource type.
    - **`repository_id`** (integer)
      Repository ID for repository or file resources.
    - **`file_path`** (string)
      File path for file resources.
    - **`text`** (string)
      Text content for free text resources.
    - **`name`** (string)
      Name for the resource.
    - **`number`** (integer)
      Issue or PR number.





### HTTP response status codes


- **201** - Created


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/copilot-spaces \
  -d '{
  "name": "Team Planning Space",
  "description": "Organization space for team planning and coordination",
  "general_instructions": "Help the team with planning and coordination tasks",
  "resources_attributes": [
    {
      "resource_type": "github_file",
      "metadata": {
        "repository_id": 123456,
        "file_path": "docs/planning.md"
      }
    },
    {
      "resource_type": "free_text",
      "metadata": {
        "name": "Team Guidelines",
        "text": "Our team follows agile methodology and holds daily standups"
      }
    }
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer, format: int64
* `number`: required, integer
* `name`: required, string
* `description`: string or null
* `general_instructions`: string or null, maxLength: 4000
* `base_role`: required, string, enum: `reader`, `writer`, `admin`, `no_access`
* `owner`: required, any of:
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
  * **Organization Simple**
    * `login`: required, string
    * `id`: required, integer
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `repos_url`: required, string, format: uri
    * `events_url`: required, string, format: uri
    * `hooks_url`: required, string
    * `issues_url`: required, string
    * `members_url`: required, string
    * `public_members_url`: required, string
    * `avatar_url`: required, string
    * `description`: required, string or null
* `creator`: required, `Simple User`:
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
* `html_url`: required, string, format: uri
* `api_url`: required, string, format: uri
* `resources_attributes`: array of objects:
  * `id`: integer, format: int64
  * `resource_type`: string, enum: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`, `media_content`, `uploaded_text_file`
  * `copilot_chat_attachment_id`: integer or null, format: int64
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time
  * `metadata`: object:
    * `repository_id`: integer
    * `file_path`: string
    * `text`: string
    * `name`: string
    * `number`: integer
    * `copilot_chat_attachment_id`: integer
    * `media_type`: string
    * `url`: string
    * `height`: integer
    * `width`: integer





## Get an organization Copilot Space

```
GET /orgs/{org}/copilot-spaces/{space_number}
```

Gets details about a specific Copilot Space owned by an organization. The authenticated user must have read access to the Space.
Internal Spaces require the authenticated user to be a member of the organization or have been granted read permissions.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER
```

**Response schema (Status: 200):**

Same response schema as [Create an organization Copilot Space](#create-an-organization-copilot-space).





## Set an organization Copilot Space

```
PUT /orgs/{org}/copilot-spaces/{space_number}
```

Updates a Copilot Space owned by an organization. The authenticated user must have permissions to update spaces in the organization.
Organization members with appropriate permissions can update Copilot Spaces owned by their organization.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.




#### Body parameters

- **`name`** (string)
  The name of the Copilot Space.

- **`description`** (string)
  A description of the Copilot Space.

- **`general_instructions`** (string)
  General instructions for the Copilot Space.

- **`base_role`** (string)
  The base role that determines default permissions for organization members. Changing this field requires admin permissions.

no_access: No default access (default)
reader: Organization members can read the space
writer: Organization members can read and edit the space
admin: Organization members have full admin access to the space
  Can be one of: `reader`, `writer`, `admin`, `no_access`

- **`resources_attributes`** (array of objects)
  Resources to attach to the space.
  - **`resource_type`** (string)
    The type of resource.
    Can be one of: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`, `media_content`, `uploaded_text_file`
  - **`metadata`** (object)
    Metadata specific to the resource type.
    - **`repository_id`** (integer)
      Repository ID for repository or file resources.
    - **`file_path`** (string)
      File path for file resources.
    - **`text`** (string)
      Text content for free text resources.
    - **`name`** (string)
      Name for the resource.
    - **`number`** (integer)
      Issue or PR number.





### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER \
  -d '{
  "name": "Updated Team Planning Space",
  "description": "Updated organization space for team planning and coordination",
  "general_instructions": "Updated instructions to help the team with planning and coordination tasks",
  "resources_attributes": [
    {
      "resource_type": "github_file",
      "metadata": {
        "repository_id": 123456,
        "file_path": "docs/updated-planning.md"
      }
    },
    {
      "id": 789,
      "_destroy": true
    },
    {
      "id": 456,
      "resource_type": "free_text",
      "metadata": {
        "name": "Updated Team Guidelines",
        "text": "Our updated team follows agile methodology and holds daily standups"
      }
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an organization Copilot Space](#create-an-organization-copilot-space).





## Delete an organization Copilot Space

```
DELETE /orgs/{org}/copilot-spaces/{space_number}
```

Deletes a Copilot Space owned by an organization. The authenticated user must have permissions to delete spaces in the organization.
Warning: This action is permanent and cannot be undone. Deleting a Copilot Space will remove all associated resources and configurations.
Organization members with appropriate permissions can delete Copilot Spaces owned by their organization.
OAuth app tokens and personal access tokens (classic) need both the read:org and repo scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.






### HTTP response status codes


- **204** - The Copilot Space has been successfully deleted.


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER
```

**Response schema (Status: 204):**





## List Copilot Spaces for a user

```
GET /users/{username}/copilot-spaces
```

Lists Copilot Spaces owned by a user. The authenticated user must have read access to the user's Copilot Spaces.
Only Spaces that are readable by the authenticated user are returned. This includes the user's own spaces, and public user spaces when accessing another user's spaces.
OAuth app tokens and personal access tokens (classic) need the read:user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`per_page`** (integer)
  The number of results per page (max 100).
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor.

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor.






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/copilot-spaces
```

**Response schema (Status: 200):**

Same response schema as [List organization Copilot Spaces](#list-organization-copilot-spaces).





## Create a Copilot Space for a user

```
POST /users/{username}/copilot-spaces
```

Creates a new Copilot Space owned by a user. Only the authenticated user can create spaces for their own account.
Users can create personal Copilot Spaces for their individual use.
OAuth app tokens and personal access tokens (classic) need the read:user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.




#### Body parameters

- **`name`** (string) (required)
  The name of the Copilot Space.

- **`description`** (string)
  A description of the Copilot Space.

- **`general_instructions`** (string)
  General instructions for the Copilot Space.

- **`base_role`** (string)
  The base role that determines default permissions for the space.

no_access: No default access (default)
reader: Makes the space publicly readable
Note: User spaces do not support writer or admin base roles.
  Default: `no_access`
  Can be one of: `reader`, `no_access`

- **`resources_attributes`** (array of objects)
  Resources to attach to the space.
  - **`resource_type`** (string)
    The type of resource.
    Can be one of: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`, `media_content`, `uploaded_text_file`
  - **`metadata`** (object)
    Metadata specific to the resource type.
    - **`repository_id`** (integer)
      Repository ID for repository or file resources.
    - **`file_path`** (string)
      File path for file resources.
    - **`text`** (string)
      Text content for free text resources.
    - **`name`** (string)
      Name for the resource.
    - **`number`** (integer)
      Issue or PR number.





### HTTP response status codes


- **201** - Created


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/copilot-spaces \
  -d '{
  "name": "My Development Space",
  "description": "Personal space for development assistance",
  "general_instructions": "Help me with React development patterns and best practices",
  "resources_attributes": [
    {
      "resource_type": "github_file",
      "metadata": {
        "repository_id": 789012,
        "file_path": "src/components/App.js"
      }
    },
    {
      "resource_type": "free_text",
      "metadata": {
        "name": "Development Notes",
        "text": "Focus on clean code principles and modern React patterns"
      }
    }
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Create an organization Copilot Space](#create-an-organization-copilot-space).





## Get a Copilot Space for a user

```
GET /users/{username}/copilot-spaces/{space_number}
```

Gets details about a specific Copilot Space owned by a user. The authenticated user must have read access to the Space.
Private user spaces require the authenticated user to be the owner of the space.
Public user spaces are accessible to any authenticated user.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER
```

**Response schema (Status: 200):**

Same response schema as [Create an organization Copilot Space](#create-an-organization-copilot-space).





## Set a Copilot Space for a user

```
PUT /users/{username}/copilot-spaces/{space_number}
```

Updates a Copilot Space owned by a user. Only the authenticated user can update spaces for their own account.
Users can update their personal Copilot Spaces.
OAuth app tokens and personal access tokens (classic) need the read:user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.




#### Body parameters

- **`name`** (string)
  The name of the Copilot Space.

- **`description`** (string)
  A description of the Copilot Space.

- **`general_instructions`** (string)
  General instructions for the Copilot Space.

- **`base_role`** (string)
  The base role that determines default permissions for the space. Changing this field requires admin permissions.

no_access: No default access (default)
reader: Makes the space publicly readable
Note: User spaces do not support writer or admin base roles.
  Can be one of: `reader`, `no_access`

- **`resources_attributes`** (array of objects)
  Resources to attach to the space.
  - **`resource_type`** (string)
    The type of resource.
    Can be one of: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`, `media_content`, `uploaded_text_file`
  - **`metadata`** (object)
    Metadata specific to the resource type.
    - **`repository_id`** (integer)
      Repository ID for repository or file resources.
    - **`file_path`** (string)
      File path for file resources.
    - **`text`** (string)
      Text content for free text resources.
    - **`name`** (string)
      Name for the resource.
    - **`number`** (integer)
      Issue or PR number.





### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER \
  -d '{
  "name": "Updated Development Space",
  "description": "Updated personal space for development assistance",
  "general_instructions": "Updated instructions to help me with React development patterns and best practices",
  "resources_attributes": [
    {
      "resource_type": "github_file",
      "metadata": {
        "repository_id": 789012,
        "file_path": "src/components/UpdatedApp.js"
      }
    },
    {
      "id": 123,
      "_destroy": true
    },
    {
      "id": 456,
      "resource_type": "free_text",
      "metadata": {
        "name": "Updated Development Notes",
        "text": "Updated focus on clean code principles and modern React patterns"
      }
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an organization Copilot Space](#create-an-organization-copilot-space).





## Delete a Copilot Space for a user

```
DELETE /users/{username}/copilot-spaces/{space_number}
```

Deletes a Copilot Space owned by a user. The authenticated user must be the owner of the space.
Warning: This action is permanent and cannot be undone. Deleting a space will remove all associated resources and configurations.
OAuth app tokens and personal access tokens (classic) need the user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.






### HTTP response status codes


- **204** - The Copilot Space has been successfully deleted.


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER
```

**Response schema (Status: 204):**