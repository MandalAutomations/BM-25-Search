# REST API endpoints for security managers

Use the REST API to manage security managers in an organization.

## About security managers


The security manager role is an organization-level role that organization owners can assign to any member or team in the organization. When applied, it gives permission to view security alerts and manage settings for security features across your organization, as well as read permission for all repositories in the organization.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List security manager teams

```
GET /orgs/{org}/security-managers
```

Warning

Closing down notice: This operation is closing down and will be removed starting January 1, 2026. Please use the "Organization Roles" endpoints instead.


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
  https://api.github.com/orgs/ORG/security-managers
```

**Response schema (Status: 200):**

Array of `Team Simple`:
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





## Add a security manager team

```
PUT /orgs/{org}/security-managers/teams/{team_slug}
```

Warning

Closing down notice: This operation is closing down and will be removed starting January 1, 2026. Please use the "Organization Roles" endpoints instead.


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
  -X PUT \
  https://api.github.com/orgs/ORG/security-managers/teams/TEAM_SLUG
```

**Response schema (Status: 204):**





## Remove a security manager team

```
DELETE /orgs/{org}/security-managers/teams/{team_slug}
```

Warning

Closing down notice: This operation is closing down and will be removed starting January 1, 2026. Please use the "Organization Roles" endpoints instead.


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
  https://api.github.com/orgs/ORG/security-managers/teams/TEAM_SLUG
```

**Response schema (Status: 204):**