# REST API endpoints for external groups

Use the REST API to view the external identity provider groups that are available to your organization and manage the connection between external groups and teams in your organization.

## About external groups

To use these endpoints, the authenticated user must be a team maintainer or an owner of the organization associated with the team.

> \[!NOTE]
>
> * These endpoints are only available for organizations that are part of an enterprise using Enterprise Managed Users. For more information, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/about-enterprise-managed-users).
> * If your organization uses team synchronization, you can use the API to manage team synchronization. For more information, see [REST API endpoints for team synchronization](/en/enterprise-cloud@latest/rest/teams/team-sync).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get an external group

```
GET /orgs/{org}/external-group/{group_id}
```

Displays information about the specific group's usage.  Provides a list of the group's external members as well as a list of teams that this group is connected to.
You can manage team membership with your identity provider using Enterprise Managed Users for GitHub Enterprise Cloud. For more information, see "GitHub's products" in the GitHub Help documentation.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`group_id`** (integer) (required)
  The unique identifier of the group.

* **`per_page`** (integer)
  The number of results per page for the "members" array (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the "members" array results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/external-group/GROUP_ID
```

**Response schema (Status: 200):**

* `group_id`: required, integer
* `group_name`: required, string
* `updated_at`: string
* `teams`: required, array of objects:
  * `team_id`: required, integer
  * `team_name`: required, string
* `members`: required, array of objects:
  * `member_id`: required, integer
  * `member_login`: required, string
  * `member_name`: required, string
  * `member_email`: required, string

## List external groups available to an organization

```
GET /orgs/{org}/external-groups
```

Lists external groups provisioned on the enterprise that are available to an organization. You can query the groups using the display\_name parameter, only groups with a group\_name containing the text provided in the display\_name parameter will be returned.  You can also limit your page results using the per\_page parameter. GitHub Enterprise Cloud generates a url-encoded page token using a cursor value for where the next page begins. For more information on cursor pagination, see "Offset and Cursor Pagination explained."
You can manage team membership with your identity provider using Enterprise Managed Users for GitHub Enterprise Cloud. For more information, see "GitHub's products" in the GitHub Help documentation.

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

* **`page`** (integer)
  Page token

* **`display_name`** (string)
  Limits the list to groups containing the text in the group name

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/external-groups
```

**Response schema (Status: 200):**

* `groups`: array of objects:
  * `group_id`: required, integer
  * `group_name`: required, string
  * `updated_at`: required, string

## List a connection between an external group and a team

```
GET /orgs/{org}/teams/{team_slug}/external-groups
```

Lists a connection between a team and an external group.
You can manage team membership with your identity provider using Enterprise Managed Users for GitHub Enterprise Cloud. For more information, see "GitHub's products" in the GitHub Help documentation.

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
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/external-groups
```

**Response schema (Status: 200):**

Same response schema as [List external groups available to an organization](#list-external-groups-available-to-an-organization).

## Update the connection between an external group and a team

```
PATCH /orgs/{org}/teams/{team_slug}/external-groups
```

Creates a connection between a team and an external group.  Only one external group can be linked to a team.
You can manage team membership with your identity provider using Enterprise Managed Users for GitHub Enterprise Cloud. For more information, see "GitHub's products" in the GitHub Help documentation.

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

* **`group_id`** (integer) (required)
  External Group Id

### HTTP response status codes

* **200** - OK

* **422** - Unprocessable entity if you attempt to modify an enterprise team at the organization level.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/external-groups \
  -d '{
  "group_id": 123
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an external group](#get-an-external-group).

## Remove the connection between an external group and a team

```
DELETE /orgs/{org}/teams/{team_slug}/external-groups
```

Deletes a connection between a team and an external group.
You can manage team membership with your IdP using Enterprise Managed Users for GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.

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

* **204** - No Content

* **422** - Unprocessable entity if you attempt to modify an enterprise team at the organization level.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/external-groups
```

**Response schema (Status: 204):**