# REST API endpoints for enterprise team organizations

Use the REST API to create and manage organization assignments for enterprise teams in your GitHub enterprise.

## About enterprise team organizations

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

## Get organization assignments

```
GET /enterprises/{enterprise}/teams/{enterprise-team}/organizations
```

Get all organizations assigned to an enterprise team

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

* **200** - An array of organizations the team is assigned to

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/organizations
```

**Response schema (Status: 200):**

Array of `Organization Simple`:

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

## Add organization assignments

```
POST /enterprises/{enterprise}/teams/{enterprise-team}/organizations/add
```

Assign an enterprise team to multiple organizations.

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

* **`organization_slugs`** (array of strings) (required)
  Organization slug to assign the team to.

### HTTP response status codes

* **200** - Successfully assigned the enterprise team to organizations.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/organizations/add \
  -d '{
  "organization_slugs": [
    "github"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get organization assignments](#get-organization-assignments).

## Remove organization assignments

```
POST /enterprises/{enterprise}/teams/{enterprise-team}/organizations/remove
```

Unassign an enterprise team from multiple organizations.

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

* **`organization_slugs`** (array of strings) (required)
  Organization slug to unassign the team from.

### HTTP response status codes

* **204** - Successfully unassigned the enterprise team from organizations.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/organizations/remove \
  -d '{
  "organization_slugs": [
    "github"
  ]
}'
```

**Response schema (Status: 204):**

## Get organization assignment

```
GET /enterprises/{enterprise}/teams/{enterprise-team}/organizations/{org}
```

Check if an enterprise team is assigned to an organization

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - The team is assigned to the organization

* **404** - The team is not assigned to the organization

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/organizations/ORG
```

**Response schema (Status: 200):**

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

## Add an organization assignment

```
PUT /enterprises/{enterprise}/teams/{enterprise-team}/organizations/{org}
```

Assign an enterprise team to an organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **201** - Successfully assigned the enterprise team to the organization.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/organizations/ORG
```

**Response schema (Status: 201):**

Same response schema as [Get organization assignment](#get-organization-assignment).

## Delete an organization assignment

```
DELETE /enterprises/{enterprise}/teams/{enterprise-team}/organizations/{org}
```

Unassign an enterprise team from an organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`enterprise-team`** (string) (required)
  The slug version of the enterprise team name. You can also substitute this value with the enterprise team id.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **204** - Successfully unassigned the enterprise team from the organization.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/teams/ENTERPRISE-TEAM/organizations/ORG
```

**Response schema (Status: 204):**