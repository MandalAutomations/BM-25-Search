# REST API endpoints for organization members

Use the REST API to manage memberships in your organization.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List failed organization invitations

```
GET /orgs/{org}/failed_invitations
```

The return hash contains failed_at and failed_reason fields which represent the time at which the invitation failed and the reason for the failure.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/failed_invitations
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





## List pending organization invitations

```
GET /orgs/{org}/invitations
```

The return hash contains a role field which refers to the Organization
Invitation role and will be one of the following values: direct_member, admin,
billing_manager, or hiring_manager. If the invitee is not a GitHub
member, the login field in the return hash will be null.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`role`** (string)
  Filter invitations by their member role.
  Default: `all`
  Can be one of: `all`, `admin`, `direct_member`, `billing_manager`, `hiring_manager`

- **`invitation_source`** (string)
  Filter invitations by their invitation source.
  Default: `all`
  Can be one of: `all`, `member`, `scim`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/invitations
```

**Response schema (Status: 200):**

Same response schema as [List failed organization invitations](#list-failed-organization-invitations).





## Create an organization invitation

```
POST /orgs/{org}/invitations
```

Invite people to an organization by using their GitHub user ID or their email address. In order to create invitations in an organization, the authenticated user must be an organization owner.
This endpoint triggers notifications. Creating content too quickly using this endpoint may result in secondary rate limiting. For more information, see "Rate limits for the API"
and "Best practices for using the REST API."


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`invitee_id`** (integer)
  Required unless you provide email. GitHub user ID for the person you are inviting.

- **`email`** (string)
  Required unless you provide invitee_id. Email address of the person you are inviting, which can be an existing GitHub user.

- **`role`** (string)
  The role for the new member.

admin - Organization owners with full administrative rights to the organization and complete access to all repositories and teams.
direct_member - Non-owner organization members with ability to see other members and join teams by invitation.
billing_manager - Non-owner organization members with ability to manage the billing settings of your organization.
reinstate - The previous role assigned to the invitee before they were removed from your organization. Can be one of the roles listed above. Only works if the invitee was previously part of your organization.
  Default: `direct_member`
  Can be one of: `admin`, `direct_member`, `billing_manager`, `reinstate`

- **`team_ids`** (array of integers)
  Specify IDs for the teams you want to invite new members to.





### HTTP response status codes


- **201** - Created


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/invitations \
  -d '{
  "email": "octocat@github.com",
  "role": "direct_member",
  "team_ids": [
    12,
    26
  ]
}'
```

**Response schema (Status: 201):**

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





## Cancel an organization invitation

```
DELETE /orgs/{org}/invitations/{invitation_id}
```

Cancel an organization invitation. In order to cancel an organization invitation, the authenticated user must be an organization owner.
This endpoint triggers notifications.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`invitation_id`** (integer) (required)
  The unique identifier of the invitation.






### HTTP response status codes


- **204** - No Content


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/invitations/INVITATION_ID
```

**Response schema (Status: 204):**





## List organization invitation teams

```
GET /orgs/{org}/invitations/{invitation_id}/teams
```

List all teams associated with an invitation. In order to see invitations in an organization, the authenticated user must be an organization owner.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`invitation_id`** (integer) (required)
  The unique identifier of the invitation.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/invitations/INVITATION_ID/teams
```

**Response schema (Status: 200):**

Array of `Team`:
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
  * `type`: required, string, enum: `enterprise`, `organization`
  * `organization_id`: integer
  * `enterprise_id`: integer
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





## List organization members

```
GET /orgs/{org}/members
```

List all users who are members of an organization. If the authenticated user is also a member of this organization then both concealed and public members will be returned.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`filter`** (string)
  Filter members returned in the list. 2fa_disabled means that only members without two-factor authentication enabled will be returned. 2fa_insecure means that only members with insecure 2FA methods will be returned. These options are only available for organization owners.
  Default: `all`
  Can be one of: `2fa_disabled`, `2fa_insecure`, `all`

- **`role`** (string)
  Filter members returned by their role.
  Default: `all`
  Can be one of: `all`, `admin`, `member`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/members
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





## Check organization membership for a user

```
GET /orgs/{org}/members/{username}
```

Check if a user is, publicly or privately, a member of the organization.


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


- **204** - Response if requester is an organization member and user is a member


- **302** - Response if requester is not an organization member


- **404** - Not Found if requester is an organization member and user is not a member




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/members/USERNAME
```

**Response schema (Status: 204):**





## Remove an organization member

```
DELETE /orgs/{org}/members/{username}
```

Removing a user from this list will remove them from all teams and they will no longer have any access to the organization's repositories.
Note

If a user has both direct membership in the organization as well as indirect membership via an enterprise team, only their direct membership will be removed. Their indirect membership via an enterprise team remains until the user is removed from the enterprise team.


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


- **403** - Forbidden


- **451** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/members/USERNAME
```

**Response schema (Status: 204):**





## Get organization membership for a user

```
GET /orgs/{org}/memberships/{username}
```

In order to get a user's membership with an organization, the authenticated user must be an organization member. The state parameter in the response can be used to identify the user's membership status.


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


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/memberships/USERNAME
```

**Response schema (Status: 200):**

* `url`: required, string, format: uri
* `state`: required, string, enum: `active`, `pending`
* `role`: required, string, enum: `admin`, `member`, `billing_manager`
* `direct_membership`: boolean
* `enterprise_teams_providing_indirect_membership`: array of string
* `organization_url`: required, string, format: uri
* `organization`: required, `Organization Simple`:
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
* `user`: required, any of:
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
* `permissions`: object:
  * `can_create_repository`: required, boolean





## Set organization membership for a user

```
PUT /orgs/{org}/memberships/{username}
```

Only authenticated organization owners can add a member to the organization or update the member's role.

If the authenticated user is adding a member to the organization, the invited user will receive an email inviting them to the organization. The user's membership status will be pending until they accept the invitation.

Authenticated users can update a user's membership by passing the role parameter. If the authenticated user changes a member's role to admin, the affected user will receive an email notifying them that they've been made an organization owner. If the authenticated user changes an owner's role to member, no email will be sent.

Rate limits
To prevent abuse, organization owners are limited to creating 50 organization invitations for an organization within a 24 hour period. If the organization is more than one month old or on a paid plan, the limit is 500 invitations per 24 hour period.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`username`** (string) (required)
  The handle for the GitHub user account.




#### Body parameters

- **`role`** (string)
  The role to give the user in the organization. Can be one of:

admin - The user will become an owner of the organization.
member - The user will become a non-owner member of the organization.
  Default: `member`
  Can be one of: `admin`, `member`





### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.


- **451** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Set an organization membership role for a user

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/memberships/USERNAME \
  -d '{
  "role": "member"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get organization membership for a user](#get-organization-membership-for-a-user).





## Remove organization membership for a user

```
DELETE /orgs/{org}/memberships/{username}
```

In order to remove a user's membership with an organization, the authenticated user must be an organization owner.
If the specified user is an active member of the organization, this will remove them from the organization. If the specified user has been invited to the organization, this will cancel their invitation. The specified user will receive an email notification in both cases.
Note

If a user has both direct membership in the organization as well as indirect membership via an enterprise team, only their direct membership will be removed. Their indirect membership via an enterprise team remains until the user is removed from the enterprise team.


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


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/memberships/USERNAME
```

**Response schema (Status: 204):**





## List public organization members

```
GET /orgs/{org}/public_members
```

Members of an organization can choose to have their membership publicized or not.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/public_members
```

**Response schema (Status: 200):**

Same response schema as [List organization members](#list-organization-members).





## Check public organization membership for a user

```
GET /orgs/{org}/public_members/{username}
```

Check if the provided user is a public member of the organization.


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


- **204** - Response if user is a public member


- **404** - Not Found if user is not a public member




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/public_members/USERNAME
```

**Response schema (Status: 204):**





## Set public organization membership for the authenticated user

```
PUT /orgs/{org}/public_members/{username}
```

The user can publicize their own membership. (A user cannot publicize the membership for another user.)
Note that you'll need to set Content-Length to zero when calling out to this endpoint. For more information, see "HTTP method."


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


- **403** - Forbidden




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/public_members/USERNAME
```

**Response schema (Status: 204):**





## Remove public organization membership for the authenticated user

```
DELETE /orgs/{org}/public_members/{username}
```

Removes the public membership for the authenticated user from the specified organization, unless public visibility is enforced by default.


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
  https://api.github.com/orgs/ORG/public_members/USERNAME
```

**Response schema (Status: 204):**





## List organization memberships for the authenticated user

```
GET /user/memberships/orgs
```

Lists all of the authenticated user's organization memberships.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`state`** (string)
  Indicates the state of the memberships to return. If not specified, the API returns both active and pending memberships.
  Can be one of: `active`, `pending`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/memberships/orgs
```

**Response schema (Status: 200):**

Array of `Org Membership`:
  * `url`: required, string, format: uri
  * `state`: required, string, enum: `active`, `pending`
  * `role`: required, string, enum: `admin`, `member`, `billing_manager`
  * `direct_membership`: boolean
  * `enterprise_teams_providing_indirect_membership`: array of string
  * `organization_url`: required, string, format: uri
  * `organization`: required, `Organization Simple`:
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
  * `user`: required, any of:
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
  * `permissions`: object:
    * `can_create_repository`: required, boolean





## Get an organization membership for the authenticated user

```
GET /user/memberships/orgs/{org}
```

If the authenticated user is an active or pending member of the organization, this endpoint will return the user's membership. If the authenticated user is not affiliated with the organization, a 404 is returned. This endpoint will return a 403 if the request is made by a GitHub App that is blocked by the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






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
  https://api.github.com/user/memberships/orgs/ORG
```

**Response schema (Status: 200):**

Same response schema as [Get organization membership for a user](#get-organization-membership-for-a-user).





## Update an organization membership for the authenticated user

```
PATCH /user/memberships/orgs/{org}
```

Converts the authenticated user to an active member of the organization, if that user has a pending invitation from the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`state`** (string) (required)
  The state that the membership should be in. Only "active" will be accepted.
  Can be one of: `active`





### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/user/memberships/orgs/ORG \
  -d '{
  "state": "active"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get organization membership for a user](#get-organization-membership-for-a-user).