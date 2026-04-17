# REST API endpoints for organization roles

Use the REST API to interact with organization roles.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get all organization roles for an organization

```
GET /orgs/{org}/organization-roles
```

Lists the organization roles available in this organization. For more information on organization roles, see "Using organization roles."
To use this endpoint, the authenticated user must be one of:

An administrator for the organization.
An organization member (or a member of a team) assigned a custom organization role that includes the View organization roles (read_organization_custom_org_role) permission. For more information, see "Permissions for organization access."

OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - Response - list of organization roles


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/organization-roles
```

**Response schema (Status: 200):**

* `total_count`: integer
* `roles`: array of `Organization Role`:
  * `id`: required, integer, format: int64
  * `name`: required, string
  * `description`: string or null
  * `base_role`: string or null, enum: `read`, `triage`, `write`, `maintain`, `admin`, `null`
  * `source`: string or null, enum: `Organization`, `Enterprise`, `Predefined`, `null`
  * `permissions`: required, array of string
  * `organization`: required, any of:
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





## Remove all organization roles for a team

```
DELETE /orgs/{org}/organization-roles/teams/{team_slug}
```

Removes all assigned organization roles from a team. For more information on organization roles, see "Using organization roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`team_slug`** (string) (required)
  The slug of the team name.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/organization-roles/teams/TEAM_SLUG
```

**Response schema (Status: 204):**





## Assign an organization role to a team

```
PUT /orgs/{org}/organization-roles/teams/{team_slug}/{role_id}
```

Assigns an organization role to a team in an organization. For more information on organization roles, see "Using organization roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`team_slug`** (string) (required)
  The slug of the team name.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **204** - No Content


- **404** - Response if the organization, team or role does not exist.


- **422** - Response if the organization roles feature is not enabled for the organization, or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/organization-roles/teams/TEAM_SLUG/ROLE_ID
```

**Response schema (Status: 204):**





## Remove an organization role from a team

```
DELETE /orgs/{org}/organization-roles/teams/{team_slug}/{role_id}
```

Removes an organization role from a team. For more information on organization roles, see "Using organization roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`team_slug`** (string) (required)
  The slug of the team name.

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
  https://api.github.com/orgs/ORG/organization-roles/teams/TEAM_SLUG/ROLE_ID
```

**Response schema (Status: 204):**





## Remove all organization roles for a user

```
DELETE /orgs/{org}/organization-roles/users/{username}
```

Revokes all assigned organization roles from a user. For more information on organization roles, see "Using organization roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`username`** (string) (required)
  The handle for the GitHub user account.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/organization-roles/users/USERNAME
```

**Response schema (Status: 204):**





## Assign an organization role to a user

```
PUT /orgs/{org}/organization-roles/users/{username}/{role_id}
```

Assigns an organization role to a member of an organization. For more information on organization roles, see "Using organization roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`role_id`** (integer) (required)
  The unique identifier of the role.






### HTTP response status codes


- **204** - No Content


- **404** - Response if the organization, user or role does not exist.


- **422** - Response if the organization roles feature is not enabled enabled for the organization, the validation failed, or the user is not an organization member.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/organization-roles/users/USERNAME/ROLE_ID
```

**Response schema (Status: 204):**





## Remove an organization role from a user

```
DELETE /orgs/{org}/organization-roles/users/{username}/{role_id}
```

Remove an organization role from a user. For more information on organization roles, see "Using organization roles."
The authenticated user must be an administrator for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`username`** (string) (required)
  The handle for the GitHub user account.

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
  https://api.github.com/orgs/ORG/organization-roles/users/USERNAME/ROLE_ID
```

**Response schema (Status: 204):**





## Get an organization role

```
GET /orgs/{org}/organization-roles/{role_id}
```

Gets an organization role that is available to this organization. For more information on organization roles, see "Using organization roles."
To use this endpoint, the authenticated user must be one of:

An administrator for the organization.
An organization member (or a member of a team) assigned a custom organization role that includes the View organization roles (read_organization_custom_org_role) permission. For more information, see "Permissions for organization access."

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


- **200** - OK


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/organization-roles/ROLE_ID
```

**Response schema (Status: 200):**

* `id`: required, integer, format: int64
* `name`: required, string
* `description`: string or null
* `base_role`: string or null, enum: `read`, `triage`, `write`, `maintain`, `admin`, `null`
* `source`: string or null, enum: `Organization`, `Enterprise`, `Predefined`, `null`
* `permissions`: required, array of string
* `organization`: required, any of:
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





## List teams that are assigned to an organization role

```
GET /orgs/{org}/organization-roles/{role_id}/teams
```

Lists the teams that are assigned to an organization role. For more information on organization roles, see "Using organization roles."
To use this endpoint, you must be an administrator for the organization.
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

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - Response - List of assigned teams


- **404** - Response if the organization or role does not exist.


- **422** - Response if the organization roles feature is not enabled or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/organization-roles/ROLE_ID/teams
```

**Response schema (Status: 200):**

Array of `A Role Assignment for a Team`:
  * `assignment`: string, enum: `direct`, `indirect`, `mixed`
  * `id`: required, integer
  * `node_id`: required, string
  * `name`: required, string
  * `slug`: required, string
  * `description`: required, string or null
  * `privacy`: string
  * `notification_setting`: string
  * `permission`: required, string
  * `permissions`: object:
    * `pull`: required, boolean
    * `triage`: required, boolean
    * `push`: required, boolean
    * `maintain`: required, boolean
    * `admin`: required, boolean
  * `url`: required, string, format: uri
  * `html_url`: required, string, format: uri
  * `members_url`: required, string
  * `repositories_url`: required, string, format: uri
  * `parent`: required, any of:
    * **null**
    * **Team Simple**
      * `id`: required, integer
      * `node_id`: required, string
      * `url`: required, string, format: uri
      * `members_url`: required, string
      * `name`: required, string
      * `description`: required, string or null
      * `permission`: required, string
      * `privacy`: string
      * `notification_setting`: string
      * `html_url`: required, string, format: uri
      * `repositories_url`: required, string, format: uri
      * `slug`: required, string
      * `ldap_dn`: string
      * `type`: required, string, enum: `enterprise`, `organization`
      * `organization_id`: integer
      * `enterprise_id`: integer
  * `type`: required, string, enum: `enterprise`, `organization`
  * `organization_id`: integer
  * `enterprise_id`: integer





## List users that are assigned to an organization role

```
GET /orgs/{org}/organization-roles/{role_id}/users
```

Lists organization members that are assigned to an organization role. For more information on organization roles, see "Using organization roles."
To use this endpoint, you must be an administrator for the organization.
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

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - Response - List of assigned users


- **404** - Response if the organization or role does not exist.


- **422** - Response if the organization roles feature is not enabled or validation failed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/organization-roles/ROLE_ID/users
```

**Response schema (Status: 200):**

Array of `A Role Assignment for a User`:
  * `assignment`: string, enum: `direct`, `indirect`, `mixed`
  * `inherited_from`: array of `Team Simple`:
    * `id`: required, integer
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `members_url`: required, string
    * `name`: required, string
    * `description`: required, string or null
    * `permission`: required, string
    * `privacy`: string
    * `notification_setting`: string
    * `html_url`: required, string, format: uri
    * `repositories_url`: required, string, format: uri
    * `slug`: required, string
    * `ldap_dn`: string
    * `type`: required, string, enum: `enterprise`, `organization`
    * `organization_id`: integer
    * `enterprise_id`: integer
  * `name`: string or null
  * `email`: string or null
  * `login`: required, string
  * `id`: required, integer
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