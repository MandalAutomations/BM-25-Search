# REST API endpoints for custom repository roles

Use the REST API to interact with custom repository roles.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Closing down - List custom repository roles in an organization

```
GET /organizations/{organization_id}/custom_roles
```

Warning

Closing down notice: This operation is closing down and will be removed in the future. Use the "List custom repository roles" endpoint instead.

List the custom repository roles available in this organization. For more information on custom repository roles, see "About custom repository roles."
The authenticated user must be administrator of the organization or of a repository of the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`organization_id`** (string) (required)
  The unique identifier of the organization.






### HTTP response status codes


- **404** - Resource not found





## List custom repository roles in an organization

```
GET /orgs/{org}/custom-repository-roles
```

List the custom repository roles available in this organization. For more information on custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator of the organization or of a repository of the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - Response - list of custom role names




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/custom-repository-roles
```

**Response schema (Status: 200):**

* `total_count`: integer
* `custom_roles`: array of `Organization Custom Repository Role`:
  * `id`: required, integer
  * `name`: required, string
  * `description`: string or null
  * `base_role`: required, string, enum: `read`, `triage`, `write`, `maintain`
  * `permissions`: required, array of string
  * `organization`: required, `Simple User`:
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





## Create a custom repository role

```
POST /orgs/{org}/custom-repository-roles
```

Creates a custom repository role that can be used by all repositories owned by the organization. For more information on custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  The name of the custom role.

- **`description`** (string or null)
  A short description about who this role is for or what permissions it grants.

- **`base_role`** (string) (required)
  The system role from which this role inherits permissions.
  Can be one of: `read`, `triage`, `write`, `maintain`

- **`permissions`** (array of strings) (required)
  A list of additional permissions included in this role.





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
  https://api.github.com/orgs/ORG/custom-repository-roles \
  -d '{
  "name": "Labeler",
  "description": "A role for issue and pull request labelers",
  "base_role": "read",
  "permissions": [
    "add_label"
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `name`: required, string
* `description`: string or null
* `base_role`: required, string, enum: `read`, `triage`, `write`, `maintain`
* `permissions`: required, array of string
* `organization`: required, `Simple User`:
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





## Get a custom repository role

```
GET /orgs/{org}/custom-repository-roles/{role_id}
```

Gets a custom repository role that is available to all repositories owned by the organization. For more information on custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator of the organization or of a repository of the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/custom-repository-roles/ROLE_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a custom repository role](#create-a-custom-repository-role).





## Update a custom repository role

```
PATCH /orgs/{org}/custom-repository-roles/{role_id}
```

Updates a custom repository role that can be used by all repositories owned by the organization. For more information about custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`role_id`** (integer) (required)
  The unique identifier of the role.




#### Body parameters

- **`name`** (string)
  The name of the custom role.

- **`description`** (string or null)
  A short description about who this role is for or what permissions it grants.

- **`base_role`** (string)
  The system role from which this role inherits permissions.
  Can be one of: `read`, `triage`, `write`, `maintain`

- **`permissions`** (array of strings)
  A list of additional permissions included in this role.





### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/custom-repository-roles/ROLE_ID \
  -d '{
  "name": "Labeler",
  "description": "A role for issue and PR labelers",
  "base_role": "read",
  "permissions": [
    "add_label",
    "remove_label"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a custom repository role](#create-a-custom-repository-role).





## Delete a custom repository role

```
DELETE /orgs/{org}/custom-repository-roles/{role_id}
```

Deletes a custom role from an organization. Once the custom role has been deleted, any
user, team, or invitation with the deleted custom role will be reassigned the inherited role. For more information about custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/custom-repository-roles/ROLE_ID
```

**Response schema (Status: 204):**





## Closing down - Create a custom role

```
POST /orgs/{org}/custom_roles
```

Warning

Closing down notice: This operation is closing down and will be removed after September 6, 2023. Use the "Create a custom repository role" endpoint instead.

Creates a custom repository role that can be used by all repositories owned by the organization. For more information on custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  The name of the custom role.

- **`description`** (string or null)
  A short description about who this role is for or what permissions it grants.

- **`base_role`** (string) (required)
  The system role from which this role inherits permissions.
  Can be one of: `read`, `triage`, `write`, `maintain`

- **`permissions`** (array of strings) (required)
  A list of additional permissions included in this role.





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
  https://api.github.com/orgs/ORG/custom_roles \
  -d '{
  "name": "Labeler",
  "description": "A role for issue and pull request labelers",
  "base_role": "read",
  "permissions": [
    "add_label"
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a custom repository role](#create-a-custom-repository-role).





## Closing down - Get a custom role

```
GET /orgs/{org}/custom_roles/{role_id}
```

Warning

Closing down notice: This operation is closing down and will be removed after September 6, 2023. Use the "Get a custom repository role" endpoint instead.

Gets a custom repository role that is available to all repositories owned by the organization. For more information on custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator of the organization or of a repository of the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/custom_roles/ROLE_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a custom repository role](#create-a-custom-repository-role).





## Closing down - Update a custom role

```
PATCH /orgs/{org}/custom_roles/{role_id}
```

Warning

Closing down notice: This operation is closing down and will be removed after September 6, 2023. Use the "Update a custom repository role" endpoint instead.

Updates a custom repository role that can be used by all repositories owned by the organization. For more information about custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`role_id`** (integer) (required)
  The unique identifier of the role.




#### Body parameters

- **`name`** (string)
  The name of the custom role.

- **`description`** (string or null)
  A short description about who this role is for or what permissions it grants.

- **`base_role`** (string)
  The system role from which this role inherits permissions.
  Can be one of: `read`, `triage`, `write`, `maintain`

- **`permissions`** (array of strings)
  A list of additional permissions included in this role.





### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/custom_roles/ROLE_ID \
  -d '{
  "name": "Labeler",
  "description": "A role for issue and PR labelers",
  "base_role": "read",
  "permissions": [
    "add_label",
    "remove_label"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a custom repository role](#create-a-custom-repository-role).





## Closing down - Delete a custom role

```
DELETE /orgs/{org}/custom_roles/{role_id}
```

Warning

Closing down notice: This operation is closing down and will be removed after September 6, 2023. Use the "Delete a custom repository role" endpoint instead.

Deletes a custom role from an organization. Once the custom role has been deleted, any
user, team, or invitation with the deleted custom role will be reassigned the inherited role. For more information about custom repository roles, see "About custom repository roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/custom_roles/ROLE_ID
```

**Response schema (Status: 204):**





## Closing down - List fine-grained permissions for an organization

```
GET /orgs/{org}/fine_grained_permissions
```

Warning

Closing down notice: This operation is closing down and will be removed after September 6, 2023. Use the "List fine-grained repository permissions" endpoint instead.

Lists the fine-grained permissions that can be used in custom repository roles for an organization. For more information, see "About custom repository roles."
To use this endpoint the authenticated user must be an administrator of the organization or of a repository of the organization.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/fine_grained_permissions
```

**Response schema (Status: 200):**

Array of `Repository Fine-Grained Permission`:
  * `name`: required, string
  * `description`: required, string





## List repository fine-grained permissions for an organization

```
GET /orgs/{org}/repository-fine-grained-permissions
```

Lists the fine-grained permissions that can be used in custom repository roles for an organization. For more information, see "About custom repository roles."
The authenticated user must be an administrator of the organization or of a repository of the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/repository-fine-grained-permissions
```

**Response schema (Status: 200):**

Same response schema as [Closing down - List fine-grained permissions for an organization](#closing-down---list-fine-grained-permissions-for-an-organization).