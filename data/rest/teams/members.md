# REST API endpoints for team members

Use the REST API to create and manage membership of teams in your GitHub organization.

## About team members

These endpoints are only available to authenticated members of the team's [organization](/en/rest/orgs). OAuth access tokens require the `read:org` [scope](/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps). GitHub generates the team's `slug` from the team `name`.

Where `pull` and `push` permissions are accepted, these will map to the **Read** and **Write** roles for an organization repository. For more information about repository roles, see [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

> \[!NOTE]
> When you have team synchronization set up for a team with your organization's identity provider (IdP), you will see an error if you attempt to use the API to make changes to the team's membership. If you have access to manage group membership in your IdP, you can manage GitHub team membership through your identity provider, which automatically adds and removes team members in an organization. For more information, see [Managing team synchronization for your organization](/en/organizations/managing-saml-single-sign-on-for-your-organization/managing-team-synchronization-for-your-organization).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List pending team invitations

```
GET /orgs/{org}/teams/{team_slug}/invitations
```

The return hash contains a role field which refers to the Organization Invitation role and will be one of the following values: direct\_member, admin, billing\_manager, hiring\_manager, or reinstate. If the invitee is not a GitHub member, the login field in the return hash will be null.
Note

You can also specify a team by org\_id and team\_id using the route GET /organizations/{org\_id}/team/{team\_id}/invitations.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **422** - Unprocessable entity if you attempt to modify an enterprise team at the organization level.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/invitations
```

**Response schema (Status: 200):**

Array of `Organization Invitation`:

* `id`: required, integer, format: int64
* `login`: required, string or null
* `email`: required, string or null
* `role`: required, string
* `created_at`: required, string
* `failed_at`: string or null
* `failed_reason`: string or null
* `inviter`: required, `Simple User`:
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
* `team_count`: required, integer
* `node_id`: required, string
* `invitation_teams_url`: required, string
* `invitation_source`: string

## List team members

```
GET /orgs/{org}/teams/{team_slug}/members
```

Team members will include the members of child teams.
To list members in a team, the team must be visible to the authenticated user.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

* **`role`** (string)
  Filters members returned by their role in the team.
  Default: `all`
  Can be one of: `member`, `maintainer`, `all`

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
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/members
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

## Get team membership for a user

```
GET /orgs/{org}/teams/{team_slug}/memberships/{username}
```

Team members will include the members of child teams.
To get a user's membership with a team, the team must be visible to the authenticated user.
Note

You can also specify a team by org\_id and team\_id using the route GET /organizations/{org\_id}/team/{team\_id}/memberships/{username}.

Note

The response contains the state of the membership and the member's role.

The role for organization owners is set to maintainer. For more information about maintainer roles, see Create a team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **200** - OK

* **404** - if user has no team membership

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/memberships/USERNAME
```

**Response schema (Status: 200):**

* `url`: required, string, format: uri
* `role`: required, string, enum: `member`, `maintainer`, default: `"member"`
* `state`: required, string, enum: `active`, `pending`

## Add or update team membership for a user

```
PUT /orgs/{org}/teams/{team_slug}/memberships/{username}
```

Adds an organization member to a team. An authenticated organization owner or team maintainer can add organization members to a team.
Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
Note

When you have team synchronization set up for a team with your organization's identity provider (IdP), you will see an error if you attempt to use the API for making changes to the team's membership. If you have access to manage group membership in your IdP, you can manage GitHub team membership through your identity provider, which automatically adds and removes team members in an organization. For more information, see "Synchronizing teams between your identity provider and GitHub."

An organization owner can add someone who is not part of the team's organization to a team. When an organization owner adds someone to a team who is not an organization member, this endpoint will send an invitation to the person via email. This newly-created membership will be in the "pending" state until the person accepts the invitation, at which point the membership will transition to the "active" state and the user will be added as a member of the team.
If the user is already a member of the team, this endpoint will update the role of the team member's role. To update the membership of a team member, the authenticated user must be an organization owner or a team maintainer.
Note

You can also specify a team by org\_id and team\_id using the route PUT /organizations/{org\_id}/team/{team\_id}/memberships/{username}.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

* **`username`** (string) (required)
  The handle for the GitHub user account.

#### Body parameters

* **`role`** (string)
  The role that this user should have in the team.
  Default: `member`
  Can be one of: `member`, `maintainer`

### HTTP response status codes

* **200** - OK

* **403** - Forbidden if team synchronization is set up

* **422** - Unprocessable Entity if you attempt to add an organization to a team

### Code examples

#### Add or update team membership for an organization member

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/memberships/USERNAME \
  -d '{
  "role": "maintainer"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get team membership for a user](#get-team-membership-for-a-user).

## Remove team membership for a user

```
DELETE /orgs/{org}/teams/{team_slug}/memberships/{username}
```

To remove a membership between a user and a team, the authenticated user must have 'admin' permissions to the team or be an owner of the organization that the team is associated with. Removing team membership does not delete the user, it just removes their membership from the team.
Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
Note

When you have team synchronization set up for a team with your organization's identity provider (IdP), you will see an error if you attempt to use the API for making changes to the team's membership. If you have access to manage group membership in your IdP, you can manage GitHub team membership through your identity provider, which automatically adds and removes team members in an organization. For more information, see "Synchronizing teams between your identity provider and GitHub."

Note

You can also specify a team by org\_id and team\_id using the route DELETE /organizations/{org\_id}/team/{team\_id}/memberships/{username}.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

* **403** - Forbidden if team synchronization is set up

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/memberships/USERNAME
```

**Response schema (Status: 204):**

## List pending team invitations (Legacy)

```
GET /teams/{team_id}/invitations
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new List pending team invitations endpoint.

The return hash contains a role field which refers to the Organization Invitation role and will be one of the following values: direct\_member, admin, billing\_manager, hiring\_manager, or reinstate. If the invitee is not a GitHub member, the login field in the return hash will be null.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

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
  https://api.github.com/teams/TEAM_ID/invitations
```

**Response schema (Status: 200):**

Same response schema as [List pending team invitations](#list-pending-team-invitations).

## List team members (Legacy)

```
GET /teams/{team_id}/members
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new List team members endpoint.

Team members will include the members of child teams.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`role`** (string)
  Filters members returned by their role in the team.
  Default: `all`
  Can be one of: `member`, `maintainer`, `all`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/teams/TEAM_ID/members
```

**Response schema (Status: 200):**

Same response schema as [List team members](#list-team-members).

## Get team member (Legacy)

```
GET /teams/{team_id}/members/{username}
```

The "Get team member" endpoint (described below) is closing down.
We recommend using the Get team membership for a user endpoint instead. It allows you to get both active and pending memberships.
To list members in a team, the team must be visible to the authenticated user.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - if user is a member

* **404** - if user is not a member

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/teams/TEAM_ID/members/USERNAME
```

**Response schema (Status: 204):**

## Add team member (Legacy)

```
PUT /teams/{team_id}/members/{username}
```

The "Add team member" endpoint (described below) is closing down.
We recommend using the Add or update team membership for a user endpoint instead. It allows you to invite new organization members to your teams.
Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
To add someone to a team, the authenticated user must be an organization owner or a team maintainer in the team they're changing. The person being added to the team must be a member of the team's organization.
Note

When you have team synchronization set up for a team with your organization's identity provider (IdP), you will see an error if you attempt to use the API for making changes to the team's membership. If you have access to manage group membership in your IdP, you can manage GitHub team membership through your identity provider, which automatically adds and removes team members in an organization. For more information, see "Synchronizing teams between your identity provider and GitHub."

Note that you'll need to set Content-Length to zero when calling out to this endpoint. For more information, see "HTTP method."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

* **403** - Forbidden

* **404** - Not Found if team synchronization is set up

* **422** - Unprocessable Entity if you attempt to add an organization to a team or you attempt to add a user to a team when they are not a member of at least one other team in the same organization

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/teams/TEAM_ID/members/USERNAME
```

**Response schema (Status: 204):**

## Remove team member (Legacy)

```
DELETE /teams/{team_id}/members/{username}
```

The "Remove team member" endpoint (described below) is closing down.
We recommend using the Remove team membership for a user endpoint instead. It allows you to remove both active and pending memberships.
Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
To remove a team member, the authenticated user must have 'admin' permissions to the team or be an owner of the org that the team is associated with. Removing a team member does not delete the user, it just removes them from the team.
Note

When you have team synchronization set up for a team with your organization's identity provider (IdP), you will see an error if you attempt to use the API for making changes to the team's membership. If you have access to manage group membership in your IdP, you can manage GitHub team membership through your identity provider, which automatically adds and removes team members in an organization. For more information, see "Synchronizing teams between your identity provider and GitHub."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

* **404** - Not Found if team synchronization is setup

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/teams/TEAM_ID/members/USERNAME
```

**Response schema (Status: 204):**

## Get team membership for a user (Legacy)

```
GET /teams/{team_id}/memberships/{username}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new Get team membership for a user endpoint.

Team members will include the members of child teams.
To get a user's membership with a team, the team must be visible to the authenticated user.
Note:
The response contains the state of the membership and the member's role.
The role for organization owners is set to maintainer. For more information about maintainer roles, see Create a team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/teams/TEAM_ID/memberships/USERNAME
```

**Response schema (Status: 200):**

Same response schema as [Get team membership for a user](#get-team-membership-for-a-user).

## Add or update team membership for a user (Legacy)

```
PUT /teams/{team_id}/memberships/{username}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new Add or update team membership for a user endpoint.

Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
If the user is already a member of the team's organization, this endpoint will add the user to the team. To add a membership between an organization member and a team, the authenticated user must be an organization owner or a team maintainer.
Note

When you have team synchronization set up for a team with your organization's identity provider (IdP), you will see an error if you attempt to use the API for making changes to the team's membership. If you have access to manage group membership in your IdP, you can manage GitHub team membership through your identity provider, which automatically adds and removes team members in an organization. For more information, see "Synchronizing teams between your identity provider and GitHub."

If the user is unaffiliated with the team's organization, this endpoint will send an invitation to the user via email. This newly-created membership will be in the "pending" state until the user accepts the invitation, at which point the membership will transition to the "active" state and the user will be added as a member of the team. To add a membership between an unaffiliated user and a team, the authenticated user must be an organization owner.
If the user is already a member of the team, this endpoint will update the role of the team member's role. To update the membership of a team member, the authenticated user must be an organization owner or a team maintainer.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`username`** (string) (required)
  The handle for the GitHub user account.

#### Body parameters

* **`role`** (string)
  The role that this user should have in the team.
  Default: `member`
  Can be one of: `member`, `maintainer`

### HTTP response status codes

* **200** - OK

* **403** - Forbidden if team synchronization is set up

* **404** - Resource not found

* **422** - Unprocessable Entity if you attempt to add an organization to a team

### Code examples

#### Assign the member role for a user in a team

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/teams/TEAM_ID/memberships/USERNAME \
  -d '{
  "role": "member"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get team membership for a user](#get-team-membership-for-a-user).

## Remove team membership for a user (Legacy)

```
DELETE /teams/{team_id}/memberships/{username}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new Remove team membership for a user endpoint.

Team synchronization is available for organizations using GitHub Enterprise Cloud. For more information, see GitHub's products in the GitHub Help documentation.
To remove a membership between a user and a team, the authenticated user must have 'admin' permissions to the team or be an owner of the organization that the team is associated with. Removing team membership does not delete the user, it just removes their membership from the team.
Note

When you have team synchronization set up for a team with your organization's identity provider (IdP), you will see an error if you attempt to use the API for making changes to the team's membership. If you have access to manage group membership in your IdP, you can manage GitHub team membership through your identity provider, which automatically adds and removes team members in an organization. For more information, see "Synchronizing teams between your identity provider and GitHub."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

* **403** - if team synchronization is set up

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/teams/TEAM_ID/memberships/USERNAME
```

**Response schema (Status: 204):**