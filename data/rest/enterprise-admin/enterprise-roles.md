# REST API endpoints for enterprise roles

Use the REST API to manage the enterprise roles available in this enterprise


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get all enterprise roles for an enterprise

```
GET /enterprises/{enterprise}/enterprise-roles
```

Lists the enterprise roles available in this enterprise.
To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission read_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) require the read:enterprise scope to access this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **200** - Response - list of enterprise roles


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles
```

**Response schema (Status: 200):**

* `total_count`: integer
* `roles`: array of `Enterprise Role`:
  * `id`: required, integer, format: int64
  * `name`: required, string
  * `description`: string or null
  * `source`: string or null, enum: `Enterprise`, `Predefined`, `null`
  * `permissions`: required, array of string
  * `enterprise`: required, any of:
    * **null**
    * **Enterprise**
      * `description`: string or null
      * `html_url`: required, string, format: uri
      * `website_url`: string or null, format: uri
      * `id`: required, integer
      * `node_id`: required, string
      * `name`: required, string
      * `slug`: required, string
      * `created_at`: required, string or null, format: date-time
      * `updated_at`: required, string or null, format: date-time
      * `avatar_url`: required, string, format: uri
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time





## Remove all enterprise roles from a team

```
DELETE /enterprises/{enterprise}/enterprise-roles/teams/{team_slug}
```

Removes all assigned enterprise roles from a team in an enterprise.
Warning

This API is not available for Copilot Business for non-GHE.

To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission write_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`team_slug`** (string) (required)
  The slug of the enterprise team name.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found


- **422** - Response if the enterprise roles feature is not enabled for the enterprise, or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/teams/TEAM_SLUG
```

**Response schema (Status: 204):**





## Assign an enterprise role to a team

```
PUT /enterprises/{enterprise}/enterprise-roles/teams/{team_slug}/{role_id}
```

Assigns an enterprise role to a team in an enterprise.
Warning

This API is not available for Copilot Business for non-GHE.

To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission write_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`team_slug`** (string) (required)
  The slug of the enterprise team name.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found


- **422** - Response if the enterprise roles feature is not enabled for the enterprise, or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/teams/TEAM_SLUG/ROLE_ID
```

**Response schema (Status: 204):**





## Remove an enterprise role from a team

```
DELETE /enterprises/{enterprise}/enterprise-roles/teams/{team_slug}/{role_id}
```

Removes an enterprise role from a team in an enterprise.
Warning

This API is not available for Copilot Business for non-GHE.

To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission write_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`team_slug`** (string) (required)
  The slug of the enterprise team name.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found


- **422** - Response if the enterprise roles feature is not enabled for the enterprise, or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/teams/TEAM_SLUG/ROLE_ID
```

**Response schema (Status: 204):**





## Remove all enterprise roles from a user

```
DELETE /enterprises/{enterprise}/enterprise-roles/users/{username}
```

Removes all enterprise roles from an enterprise user in an enterprise.
To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission write_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`username`** (string) (required)
  The handle for the GitHub user account.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found


- **422** - Response if the enterprise roles feature is not enabled for the enterprise, or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/users/USERNAME
```

**Response schema (Status: 204):**





## Assign an enterprise role to an enterprise user

```
PUT /enterprises/{enterprise}/enterprise-roles/users/{username}/{role_id}
```

Assigns an enterprise role to a user in an enterprise.
To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission write_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found


- **422** - Response if the enterprise roles feature is not enabled for the enterprise, or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/users/USERNAME/ROLE_ID
```

**Response schema (Status: 204):**





## Remove enterprise user role assignment

```
DELETE /enterprises/{enterprise}/enterprise-roles/users/{username}/{role_id}
```

Removes an enterprise role from an enterprise user.
To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission write_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found


- **422** - Response if the enterprise roles feature is not enabled for the enterprise, or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/users/USERNAME/ROLE_ID
```

**Response schema (Status: 204):**





## Get an enterprise role

```
GET /enterprises/{enterprise}/enterprise-roles/{role_id}
```

Gets a custom enterprise role that is available within the enterprise.
To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission read_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) require the read:enterprise scope to access this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






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
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/ROLE_ID
```

**Response schema (Status: 200):**

* `id`: required, integer, format: int64
* `name`: required, string
* `description`: string or null
* `source`: string or null, enum: `Enterprise`, `Predefined`, `null`
* `permissions`: required, array of string
* `enterprise`: required, any of:
  * **null**
  * **Enterprise**
    * `description`: string or null
    * `html_url`: required, string, format: uri
    * `website_url`: string or null, format: uri
    * `id`: required, integer
    * `node_id`: required, string
    * `name`: required, string
    * `slug`: required, string
    * `created_at`: required, string or null, format: date-time
    * `updated_at`: required, string or null, format: date-time
    * `avatar_url`: required, string, format: uri
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time





## List teams that are assigned to an enterprise role

```
GET /enterprises/{enterprise}/enterprise-roles/{role_id}/teams
```

Lists the teams that are assigned to an enterprise role.
Warning

This API is not available for Copilot Business for non-GHE.

To use this endpoint, the authenticated user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission read_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) require the read:enterprise scope to access this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`role_id`** (integer) (required)
  The unique identifier of the role.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






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
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/ROLE_ID/teams
```

**Response schema (Status: 200):**

Array of `Enterprise Team`:
  * `id`: required, integer, format: int64
  * `name`: required, string
  * `description`: string
  * `slug`: required, string
  * `url`: required, string, format: uri
  * `sync_to_organizations`: string
  * `organization_selection_type`: string
  * `group_id`: required, string or null
  * `group_name`: string or null
  * `html_url`: required, string, format: uri
  * `members_url`: required, string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time





## List users that are assigned to an enterprise role

```
GET /enterprises/{enterprise}/enterprise-roles/{role_id}/users
```

Lists enterprise members that are assigned to an enterprise role.
To use this endpoint, a user must be one of:

An administrator for the enterprise.
A user, or a user on a team, with the fine-grained permission read_enterprise_custom_enterprise_role in the enterprise.

OAuth app tokens and personal access tokens (classic) require the enterprise:admin scope to access this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`role_id`** (integer) (required)
  The unique identifier of the role.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - Response - List of assigned users


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/enterprise-roles/ROLE_ID/users
```

**Response schema (Status: 200):**

Array of `An Enterprise Role Assignment for a User` objects: all of:
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
  * **object**
    * `assignment`: string, enum: `direct`, `indirect`, `mixed`
    * `inherited_from`: array of `Enterprise Team`:
      * `id`: required, integer, format: int64
      * `name`: required, string
      * `description`: string
      * `slug`: required, string
      * `url`: required, string, format: uri
      * `sync_to_organizations`: string
      * `organization_selection_type`: string
      * `group_id`: required, string or null
      * `group_name`: string or null
      * `html_url`: required, string, format: uri
      * `members_url`: required, string
      * `created_at`: required, string, format: date-time
      * `updated_at`: required, string, format: date-time