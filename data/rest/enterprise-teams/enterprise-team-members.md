# REST API endpoints for enterprise team memberships

Use the REST API to create and manage membership of enterprise teams in your GitHub enterprise.

## About enterprise team members

> \[!NOTE]
> These endpoints are currently in public preview and subject to change.
>
> This API documentation is for enterprises on GitHub Enterprise Cloud.
>
> If your enterprise is Copilot Business for non-GHE, please refer to the early access documentation link that was previously shared to you.

These endpoints are only available to authenticated members of the enterprise team's enterprise with classic personal access tokens with the `read:enterprise` [scope](/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps) for `GET` APIs and `admin:enterprise` for other APIs.

These endpoints are not compatible with fine-grained personal access tokens or GitHub App access tokens.

GitHub generates the enterprise team's `slug` from the team `name` and adds the `ent:` prefix.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List members in an enterprise team

```
GET /enterprises/{enterprise}/teams/{enterprise-team}/memberships
```

Lists all team members in an enterprise team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/memberships
```

**Response schema (Status: 200):**

Array of `Simple User`:

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

## Bulk add team members

```
POST /enterprises/{enterprise}/teams/{enterprise-team}/memberships/add
```

Add multiple team members to an enterprise team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

#### Body parameters

* **`usernames`** (array of strings) (required)
  The GitHub user handles to add to the team.

### HTTP response status codes

* **200** - Successfully added team members.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/memberships/add \
  -d '{
  "usernames": [
    "monalisa",
    "octocat"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List members in an enterprise team](#list-members-in-an-enterprise-team).

## Bulk remove team members

```
POST /enterprises/{enterprise}/teams/{enterprise-team}/memberships/remove
```

Remove multiple team members from an enterprise team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

#### Body parameters

* **`usernames`** (array of strings) (required)
  The GitHub user handles to be removed from the team.

### HTTP response status codes

* **200** - Successfully removed team members.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/memberships/remove \
  -d '{
  "usernames": [
    "monalisa",
    "octocat"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List members in an enterprise team](#list-members-in-an-enterprise-team).

## Get enterprise team membership

```
GET /enterprises/{enterprise}/teams/{enterprise-team}/memberships/{username}
```

Returns whether the user is a member of the enterprise team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **200** - User is a member of the enterprise team.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/memberships/USERNAME
```

**Response schema (Status: 200):**

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

## Add team member

```
PUT /enterprises/{enterprise}/teams/{enterprise-team}/memberships/{username}
```

Add a team member to an enterprise team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **201** - Successfully added team member

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/memberships/USERNAME
```

**Response schema (Status: 201):**

Same response schema as [Get enterprise team membership](#get-enterprise-team-membership).

## Remove team membership

```
DELETE /enterprises/{enterprise}/teams/{enterprise-team}/memberships/{username}
```

Remove membership of a specific user from a particular team in an enterprise.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/memberships/USERNAME
```

**Response schema (Status: 204):**