# REST API endpoints for team synchronization

Use the REST API to manage connections between GitHub teams and external identity provider (IdP) groups.

## About team synchronization

To use these endpoints, the authenticated user must be a team maintainer or an owner of the organization associated with the team. The token you use to authenticate will also need to be authorized for use with your IdP (SSO) provider. For more information, see [Authorizing a personal access token for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on).

You can manage GitHub team members through your IdP with team synchronization. Team synchronization must be enabled to use these endpoints. For more information, see [Managing team synchronization for your organization](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/managing-team-synchronization-for-your-organization).

> \[!NOTE]
> These endpoints cannot be used with Enterprise Managed Users. To learn more about managing an organization with managed users, see [REST API endpoints for external groups](/en/enterprise-cloud@latest/rest/teams/external-groups).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List IdP groups for an organization

```
GET /orgs/{org}/team-sync/groups
```

Lists IdP groups available in an organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (string)
  Page token

* **`q`** (string)
  Filters the results to return only those that begin with the value specified by this parameter. For example, a value of ab will return results that begin with "ab".

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/team-sync/groups
```

**Response schema (Status: 200):**

* `groups`: array of objects:
  * `group_id`: required, string
  * `group_name`: required, string
  * `group_description`: required, string
  * `status`: string
  * `synced_at`: string or null

## List IdP groups for a team

```
GET /orgs/{org}/teams/{team_slug}/team-sync/group-mappings
```

List IdP groups connected to a team on GitHub Enterprise Cloud.
Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
Note

You can also specify a team by org\_id and team\_id using the route GET /organizations/{org\_id}/team/{team\_id}/team-sync/group-mappings.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

### HTTP response status codes

* **200** - OK

* **422** - Unprocessable entity if you attempt to modify an enterprise team at the organization level.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/team-sync/group-mappings
```

**Response schema (Status: 200):**

Same response schema as [List IdP groups for an organization](#list-idp-groups-for-an-organization).

## Create or update IdP group connections

```
PATCH /orgs/{org}/teams/{team_slug}/team-sync/group-mappings
```

Creates, updates, or removes a connection between a team and an IdP group. When adding groups to a team, you must include all new and existing groups to avoid replacing existing groups with the new ones. Specifying an empty groups array will remove all connections for a team.
Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
Note

You can also specify a team by org\_id and team\_id using the route PATCH /organizations/{org\_id}/team/{team\_id}/team-sync/group-mappings.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

#### Body parameters

* **`groups`** (array of objects)
  The IdP groups you want to connect to a GitHub team. When updating, the new groups object will replace the original one. You must include any existing groups that you don't want to remove.
  * **`group_id`** (string) (required)
    ID of the IdP group.
  * **`group_name`** (string) (required)
    Name of the IdP group.
  * **`group_description`** (string) (required)
    Description of the IdP group.

### HTTP response status codes

* **200** - OK

* **422** - Unprocessable entity if you attempt to modify an enterprise team at the organization level.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/team-sync/group-mappings \
  -d '{
  "groups": [
    {
      "group_id": "123",
      "group_name": "Octocat admins",
      "group_description": "string"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List IdP groups for an organization](#list-idp-groups-for-an-organization).

## List IdP groups for a team (Legacy)

```
GET /teams/{team_id}/team-sync/group-mappings
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new List IdP groups for a team endpoint.

Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
List IdP groups connected to a team on GitHub Enterprise Cloud.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/teams/TEAM_ID/team-sync/group-mappings
```

**Response schema (Status: 200):**

Same response schema as [List IdP groups for an organization](#list-idp-groups-for-an-organization).

## Create or update IdP group connections (Legacy)

```
PATCH /teams/{team_id}/team-sync/group-mappings
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new Create or update IdP group connections endpoint.

Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
Creates, updates, or removes a connection between a team and an IdP group. When adding groups to a team, you must include all new and existing groups to avoid replacing existing groups with the new ones. Specifying an empty groups array will remove all connections for a team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

#### Body parameters

* **`groups`** (array of objects) (required)
  The IdP groups you want to connect to a GitHub team. When updating, the new groups object will replace the original one. You must include any existing groups that you don't want to remove.
  * **`group_id`** (string) (required)
    ID of the IdP group.
  * **`group_name`** (string) (required)
    Name of the IdP group.
  * **`group_description`** (string) (required)
    Description of the IdP group.
  * **`id`** (string)
  * **`name`** (string)
  * **`description`** (string)

* **`synced_at`** (string)

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/teams/TEAM_ID/team-sync/group-mappings \
  -d '{
  "groups": [
    {
      "group_id": "123",
      "group_name": "Octocat admins",
      "description": "The people who configure your octoworld.",
      "group_description": "string"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List IdP groups for an organization](#list-idp-groups-for-an-organization).