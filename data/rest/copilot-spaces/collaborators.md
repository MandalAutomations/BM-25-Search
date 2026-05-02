# Copilot Spaces collaborators

Use the REST API to manage collaborators for Copilot Spaces.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List collaborators for an organization Copilot Space

```
GET /orgs/{org}/copilot-spaces/{space_number}/collaborators
```

Lists all collaborators for a specific Copilot Space owned by an organization. The authenticated user must have appropriate permissions to view collaborators.
Each collaborator entry specifies which user or team has access to the space and at what level (reader, writer, or admin). The space owner (organization) is excluded from this list.
Note: Team collaborators listed here are teams that are defined in the organization.
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
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/collaborators
```

**Response schema (Status: 200):**

* `collaborators`: required, array of object





## Add a collaborator to an organization Copilot Space

```
POST /orgs/{org}/copilot-spaces/{space_number}/collaborators
```

Adds a collaborator (user or team) to a specific Copilot Space owned by an organization. The authenticated user must have appropriate permissions to manage collaborators.
Note: When adding users as collaborators, they must already be members of the organization.
When adding teams as collaborators, they must be defined in the organization.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


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

- **`actor_type`** (string) (required)
  The type of actor (user or team).
  Can be one of: `User`, `Team`

- **`actor_identifier`** (string) (required)
  The username (for users) or team slug (for teams). The numeric ID of a user or team is also accepted.

- **`role`** (string) (required)
  The role to grant to the collaborator.
  Can be one of: `reader`, `writer`, `admin`





### HTTP response status codes


- **201** - Created


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example 1: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/collaborators \
  -d '{
  "actor_type": "User",
  "actor_identifier": "octocat",
  "role": "writer"
}'
```

**Response schema (Status: 201):**

* any of:
  * **object**
  * **object**
    * `actor_type`: required, string, enum: `Team`
    * `role`: required, string, enum: `reader`, `writer`, `admin`
    * `id`: required, integer
    * `node_id`: required, string
    * `name`: required, string
    * `slug`: required, string
    * `type`: required, string, enum: `Team`
    * `description`: string or null
    * `privacy`: string
    * `notification_setting`: string
    * `url`: string, format: uri
    * `html_url`: string, format: uri
    * `members_url`: string
    * `repositories_url`: string, format: uri
    * `organization_id`: integer
    * `parent`: null



#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/collaborators \
  -d '{
  "actor_type": "Team",
  "actor_identifier": "developers",
  "role": "reader"
}'
```

**Response schema (Status: 201):**

* any of:
  * **object**
  * **object**
    * `actor_type`: required, string, enum: `Team`
    * `role`: required, string, enum: `reader`, `writer`, `admin`
    * `id`: required, integer
    * `node_id`: required, string
    * `name`: required, string
    * `slug`: required, string
    * `type`: required, string, enum: `Team`
    * `description`: string or null
    * `privacy`: string
    * `notification_setting`: string
    * `url`: string, format: uri
    * `html_url`: string, format: uri
    * `members_url`: string
    * `repositories_url`: string, format: uri
    * `organization_id`: integer
    * `parent`: null





## Set a collaborator role for an organization Copilot Space

```
PUT /orgs/{org}/copilot-spaces/{space_number}/collaborators/{actor_type}/{actor_identifier}
```

Updates the role of a collaborator for a specific Copilot Space owned by an organization. The authenticated user must have appropriate permissions to manage collaborators.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.

- **`actor_type`** (string) (required)
  The type of actor (user or team).
  Can be one of: `User`, `Team`

- **`actor_identifier`** (string) (required)
  The username (for users) or team slug (for teams). The numeric ID of a user or team is also accepted.




#### Body parameters

- **`role`** (string) (required)
  The new role to grant to the collaborator. Use no_access to remove the collaborator.
  Can be one of: `reader`, `writer`, `admin`, `no_access`





### HTTP response status codes


- **200** - OK


- **204** - Response when role is no_access and the collaborator was removed.


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/collaborators/ACTOR_TYPE/ACTOR_IDENTIFIER \
  -d '{
  "role": "admin"
}'
```

**Response schema (Status: 200):**

Same response schema as [Add a collaborator to an organization Copilot Space](#add-a-collaborator-to-an-organization-copilot-space).



#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/collaborators/ACTOR_TYPE/ACTOR_IDENTIFIER \
  -d '{
  "role": "admin"
}'
```

**Response schema (Status: 200):**

Same response schema as [Add a collaborator to an organization Copilot Space](#add-a-collaborator-to-an-organization-copilot-space).





## Remove a collaborator from an organization Copilot Space

```
DELETE /orgs/{org}/copilot-spaces/{space_number}/collaborators/{actor_type}/{actor_identifier}
```

Removes a collaborator from a specific Copilot Space owned by an organization. The authenticated user must have appropriate permissions to manage collaborators.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.

- **`actor_type`** (string) (required)
  The type of actor (user or team).
  Can be one of: `User`, `Team`

- **`actor_identifier`** (string) (required)
  The username (for users) or team slug (for teams). The numeric ID of a user or team is also accepted.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/collaborators/ACTOR_TYPE/ACTOR_IDENTIFIER
```

**Response schema (Status: 204):**





## List collaborators for a Copilot Space for a user

```
GET /users/{username}/copilot-spaces/{space_number}/collaborators
```

Lists all collaborators for a specific Copilot Space owned by a user. The authenticated user must be the owner of the space or have admin access to the space.
Each collaborator entry specifies which user has access to the space and at what level (reader, writer, or admin). The space owner is excluded from this list.
Team collaborators are not supported for user-owned Copilot Spaces.
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


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER/collaborators
```

**Response schema (Status: 200):**

Same response schema as [List collaborators for an organization Copilot Space](#list-collaborators-for-an-organization-copilot-space).





## Add a collaborator to a Copilot Space for a user

```
POST /users/{username}/copilot-spaces/{space_number}/collaborators
```

Adds a collaborator to a specific Copilot Space owned by a user. The authenticated user must be the owner of the space or have admin access to the space.
Team collaborators are not supported for user-owned Copilot Spaces.
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




#### Body parameters

- **`actor_type`** (string) (required)
  The type of actor (must be User for user-owned spaces; Team will be rejected).
  Can be one of: `User`, `Team`

- **`actor_identifier`** (string) (required)
  The username of the collaborator. The numeric user ID is also accepted.

- **`role`** (string) (required)
  The role to grant to the collaborator.
  Can be one of: `reader`, `writer`, `admin`





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
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER/collaborators \
  -d '{
  "actor_type": "User",
  "actor_identifier": "octocat",
  "role": "writer"
}'
```

**Response schema (Status: 201):**

Same response schema as [Add a collaborator to an organization Copilot Space](#add-a-collaborator-to-an-organization-copilot-space).





## Set a collaborator role for a Copilot Space for a user

```
PUT /users/{username}/copilot-spaces/{space_number}/collaborators/{actor_type}/{actor_identifier}
```

Updates the role of a collaborator for a specific Copilot Space owned by a user. The authenticated user must be the owner of the space or have admin access to the space.
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

- **`actor_type`** (string) (required)
  The type of actor (must be User for user-owned spaces; Team will be rejected).
  Can be one of: `User`, `Team`

- **`actor_identifier`** (string) (required)
  The username of the collaborator. The numeric user ID is also accepted.




#### Body parameters

- **`role`** (string) (required)
  The new role to grant to the collaborator. Use no_access to remove the collaborator.
  Can be one of: `reader`, `writer`, `admin`, `no_access`





### HTTP response status codes


- **200** - OK


- **204** - Response when role is no_access and the collaborator was removed.


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER/collaborators/ACTOR_TYPE/ACTOR_IDENTIFIER \
  -d '{
  "role": "admin"
}'
```

**Response schema (Status: 200):**

Same response schema as [Add a collaborator to an organization Copilot Space](#add-a-collaborator-to-an-organization-copilot-space).





## Remove a collaborator from a Copilot Space for a user

```
DELETE /users/{username}/copilot-spaces/{space_number}/collaborators/{actor_type}/{actor_identifier}
```

Removes a collaborator from a specific Copilot Space owned by a user. The authenticated user must be the owner of the space or have admin access to the space.
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

- **`actor_type`** (string) (required)
  The type of actor (must be User for user-owned spaces; Team will be rejected).
  Can be one of: `User`, `Team`

- **`actor_identifier`** (string) (required)
  The username of the collaborator. The numeric user ID is also accepted.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER/collaborators/ACTOR_TYPE/ACTOR_IDENTIFIER
```

**Response schema (Status: 204):**