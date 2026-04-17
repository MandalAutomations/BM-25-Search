# REST API endpoints for LDAP

Use the REST API to update account relationships between a GitHub Enterprise Server user or team and its linked LDAP entry or queue a new synchronization.

## About LDAP

You can use these endpoints to update the Distinguished Name (DN) that a user or team maps to. Note that in most cases, you must have [LDAP Sync enabled](/en/enterprise-server@3.20/admin/identity-and-access-management/using-ldap-for-enterprise-iam/using-ldap) for your GitHub Enterprise Server appliance. The [Update LDAP mapping for a user](#update-ldap-mapping-for-a-user) endpoint can be used when LDAP is enabled, even if LDAP Sync is disabled.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## Update LDAP mapping for a team

```
PATCH /admin/ldap/teams/{team_id}/mapping
```

Updates the distinguished name (DN) of the LDAP entry to map to a team. LDAP synchronization must be enabled to map LDAP entries to a team. Use the Create a team endpoint to create a team with LDAP mapping.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

#### Body parameters

* **`ldap_dn`** (string) (required)
  The distinguished name (DN) of the LDAP entry to map to a team.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/admin/ldap/teams/TEAM_ID/mapping \
  -d '{
  "ldap_dn": "cn=Enterprise Ops,ou=teams,dc=github,dc=com"
}'
```

**Response schema (Status: 200):**

* `ldap_dn`: string
* `id`: integer
* `node_id`: string
* `url`: string
* `html_url`: string
* `name`: string
* `slug`: string
* `description`: string or null
* `privacy`: string
* `notification_setting`: string
* `permission`: string
* `members_url`: string
* `repositories_url`: string
* `parent`: null
* `type`: string
* `organization_id`: integer
* `enterprise_id`: integer

## Sync LDAP mapping for a team

```
POST /admin/ldap/teams/{team_id}/sync
```

Note that this API call does not automatically initiate an LDAP sync. Rather, if a 201 is returned, the sync job is queued successfully, and is performed when the instance is ready.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/ldap/teams/TEAM_ID/sync
```

**Response schema (Status: 201):**

* `status`: string

## Update LDAP mapping for a user

```
PATCH /admin/ldap/users/{username}/mapping
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

#### Body parameters

* **`ldap_dn`** (string) (required)
  The distinguished name (DN) of the LDAP entry to map to a team.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/admin/ldap/users/USERNAME/mapping \
  -d '{
  "ldap_dn": "uid=asdf,ou=users,dc=github,dc=com"
}'
```

**Response schema (Status: 200):**

* `ldap_dn`: string
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
* `name`: required, string or null
* `company`: required, string or null
* `blog`: required, string or null
* `location`: required, string or null
* `email`: required, string or null, format: email
* `hireable`: required, boolean or null
* `bio`: required, string or null
* `twitter_username`: string or null
* `public_repos`: required, integer
* `public_gists`: required, integer
* `followers`: required, integer
* `following`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `private_gists`: required, integer
* `total_private_repos`: required, integer
* `owned_private_repos`: required, integer
* `disk_usage`: required, integer
* `collaborators`: required, integer
* `two_factor_authentication`: required, boolean
* `plan`: object:
  * `collaborators`: required, integer
  * `name`: required, string
  * `space`: required, integer
  * `private_repos`: required, integer
* `suspended_at`: string, format: date-time
* `business_plus`: boolean
* `user_view_type`: string

## Sync LDAP mapping for a user

```
POST /admin/ldap/users/{username}/sync
```

Note that this API call does not automatically initiate an LDAP sync. Rather, if a 201 is returned, the sync job is queued successfully, and is performed when the instance is ready.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/ldap/users/USERNAME/sync
```

**Response schema (Status: 201):**

Same response schema as [Sync LDAP mapping for a team](#sync-ldap-mapping-for-a-team).