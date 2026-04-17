# REST API endpoints for enterprise teams

Use the REST API to create and manage enterprise teams in your GitHub enterprise.

## About enterprise teams

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

## List enterprise teams

```
GET /enterprises/{enterprise}/teams
```

List all teams in the enterprise for the authenticated user

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/teams
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

## Create an enterprise team

```
POST /enterprises/{enterprise}/teams
```

To create an enterprise team, the authenticated user must be an owner of the enterprise.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`name`** (string) (required)
  The name of the team.

* **`description`** (string or null)
  A description of the team.

* **`sync_to_organizations`** (string)
  Retired: this field is no longer supported.
  Whether the enterprise team should be reflected in each organization.
  This value cannot be set.
  Default: `disabled`
  Can be one of: `all`, `disabled`

* **`organization_selection_type`** (string)
  Specifies which organizations in the enterprise should have access to this team. Can be one of disabled, selected, or all.
  disabled: The team is not assigned to any organizations. This is the default when you create a new team.
  selected: The team is assigned to specific organizations. You can then use the add organization assignments API endpoint.
  all: The team is assigned to all current and future organizations in the enterprise.
  Default: `disabled`
  Can be one of: `disabled`, `selected`, `all`

* **`group_id`** (string or null)
  The ID of the IdP group to assign team membership with. You can get this value from the REST API endpoints for SCIM.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/teams \
  -d '{
  "name": "Justice League",
  "description": "A great team.",
  "group_id": "62ab9291-fae2-468e-974b-7e45096d5021"
}'
```

**Response schema (Status: 201):**

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

## Get an enterprise team

```
GET /enterprises/{enterprise}/teams/{team_slug}
```

Gets a team using the team's slug. To create the slug, GitHub replaces special characters in the name string, changes all words to lowercase, and replaces spaces with a - separator and adds the "ent:" prefix. For example, "My TEam Näme" would become ent:my-team-name.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`team_slug`** (string) (required)
  The slug of the team name.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/teams/TEAM_SLUG
```

**Response schema (Status: 200):**

Same response schema as [Create an enterprise team](#create-an-enterprise-team).

## Update an enterprise team

```
PATCH /enterprises/{enterprise}/teams/{team_slug}
```

To edit a team, the authenticated user must be an enterprise owner.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`team_slug`** (string) (required)
  The slug of the team name.

#### Body parameters

* **`name`** (string or null)
  A new name for the team.

* **`description`** (string or null)
  A new description for the team.

* **`sync_to_organizations`** (string)
  Retired: this field is no longer supported.
  Whether the enterprise team should be reflected in each organization.
  This value cannot be changed.
  Default: `disabled`
  Can be one of: `all`, `disabled`

* **`organization_selection_type`** (string)
  Specifies which organizations in the enterprise should have access to this team. Can be one of disabled, selected, or all.
  disabled: The team is not assigned to any organizations. This is the default when you create a new team.
  selected: The team is assigned to specific organizations. You can then use the add organization assignments API.
  all: The team is assigned to all current and future organizations in the enterprise.
  Default: `disabled`
  Can be one of: `disabled`, `selected`, `all`

* **`group_id`** (string or null)
  The ID of the IdP group to assign team membership with. The new IdP group will replace the existing one, or replace existing direct members if the team isn't currently linked to an IdP group.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/teams/TEAM_SLUG \
  -d '{
  "name": "Justice League",
  "description": "A great team.",
  "group_id": "62ab9291-fae2-468e-974b-7e45096d5021"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an enterprise team](#create-an-enterprise-team).

## Delete an enterprise team

```
DELETE /enterprises/{enterprise}/teams/{team_slug}
```

To delete an enterprise team, the authenticated user must be an enterprise owner.
If you are an enterprise owner, deleting an enterprise team will delete all of its IdP mappings as well.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`team_slug`** (string) (required)
  The slug of the team name.

### HTTP response status codes

* **204** - No Content

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/teams/TEAM_SLUG
```

**Response schema (Status: 204):**