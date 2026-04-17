# REST API endpoints for Copilot user management

Use the REST API to manage the GitHub Copilot Business subscription for your organization.

> [!NOTE] These endpoints are in public preview and subject to change.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get Copilot seat information and settings for an organization

```
GET /orgs/{org}/copilot/billing
```

Note

This endpoint is in public preview and is subject to change.

Gets information about an organization's Copilot subscription, including seat breakdown
and feature policies. To configure these settings, go to your organization's settings on GitHub.com.
For more information, see "Managing policies for Copilot in your organization."
Only organization owners can view details about the organization's Copilot Business or Copilot Enterprise subscription.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or read:org scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - There is a problem with your account's associated payment method.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/billing
```

**Response schema (Status: 200):**

* `seat_breakdown`: required, `Copilot Seat Breakdown`:
  * `total`: integer
  * `added_this_cycle`: integer
  * `pending_cancellation`: integer
  * `pending_invitation`: integer
  * `active_this_cycle`: integer
  * `inactive_this_cycle`: integer
* `public_code_suggestions`: required, string, enum: `allow`, `block`, `unconfigured`
* `ide_chat`: string, enum: `enabled`, `disabled`, `unconfigured`
* `platform_chat`: string, enum: `enabled`, `disabled`, `unconfigured`
* `cli`: string, enum: `enabled`, `disabled`, `unconfigured`
* `seat_management_setting`: required, string, enum: `assign_all`, `assign_selected`, `disabled`, `unconfigured`
* `plan_type`: string, enum: `business`, `enterprise`





## List all Copilot seat assignments for an organization

```
GET /orgs/{org}/copilot/billing/seats
```

Note

This endpoint is in public preview and is subject to change.

Lists all Copilot seats for which an organization with a Copilot Business or Copilot Enterprise subscription is currently being billed.
Only organization owners can view assigned seats.
Each seat object contains information about the assigned user's most recent Copilot activity. Users must have telemetry enabled in their IDE for Copilot in the IDE activity to be reflected in last_activity_at.
For more information about activity data, see Metrics data properties for GitHub Copilot.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or read:org scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `50`






### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/billing/seats
```

**Response schema (Status: 200):**

* `total_seats`: integer
* `seats`: array of `Copilot Business Seat Detail`:
  * `assignee`: any of:
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
  * `organization`: any of:
    * **null**
    * **Organization Simple**
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
  * `assigning_team`: one of:
    * **Team**
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
    * **Enterprise Team**
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
  * `pending_cancellation_date`: string or null, format: date
  * `last_activity_at`: string or null, format: date-time
  * `last_activity_editor`: string or null
  * `last_authenticated_at`: string or null, format: date-time
  * `created_at`: required, string, format: date-time
  * `updated_at`: string, format: date-time, deprecated
  * `plan_type`: string, enum: `business`, `enterprise`, `unknown`





## Add teams to the Copilot subscription for an organization

```
POST /orgs/{org}/copilot/billing/selected_teams
```

Note

This endpoint is in public preview and is subject to change.

Purchases a GitHub Copilot seat for all users within each specified team.
The organization will be billed for each seat based on the organization's Copilot plan. For more information about Copilot pricing, see "About billing for GitHub Copilot in your organization."
Only organization owners can purchase Copilot seats for their organization members. The organization must have a Copilot Business or Copilot Enterprise subscription and a configured suggestion matching policy.
For more information about setting up a Copilot subscription, see "Subscribing to Copilot for your organization."
For more information about setting a suggestion matching policy, see "Managing policies for Copilot in your organization."
The response contains the total number of new seats that were created and existing seats that were refreshed.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or admin:org scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`selected_teams`** (array of strings) (required)
  List of team names within the organization to which to grant access to GitHub Copilot.





### HTTP response status codes


- **201** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Copilot Business or Enterprise is not enabled for this organization, billing has not been set up for this organization, a public code suggestions policy has not been set for this organization, or the organization's Copilot access setting is set to enable Copilot for all users or is unconfigured.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/copilot/billing/selected_teams \
  -d '{
  "selected_teams": [
    "engteam1",
    "engteam2",
    "engteam3"
  ]
}'
```

**Response schema (Status: 201):**

* `seats_created`: required, integer





## Remove teams from the Copilot subscription for an organization

```
DELETE /orgs/{org}/copilot/billing/selected_teams
```

Note

This endpoint is in public preview and is subject to change.

Sets seats for all members of each team specified to "pending cancellation".
This will cause the members of the specified team(s) to lose access to GitHub Copilot at the end of the current billing cycle unless they retain access through another team.
For more information about disabling access to Copilot, see "Revoking access to Copilot for members of your organization."
Only organization owners can cancel Copilot seats for their organization members.
The response contains the total number of seats set to "pending cancellation".
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or admin:org scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`selected_teams`** (array of strings) (required)
  The names of teams from which to revoke access to GitHub Copilot.





### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Copilot Business or Enterprise is not enabled for this organization, billing has not been set up for this organization, a public code suggestions policy has not been set for this organization, or the organization's Copilot access setting is set to enable Copilot for all users or is unconfigured.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/copilot/billing/selected_teams \
  -d '{
  "selected_teams": [
    "engteam1",
    "engteam2",
    "engteam3"
  ]
}'
```

**Response schema (Status: 200):**

* `seats_cancelled`: required, integer





## Add users to the Copilot subscription for an organization

```
POST /orgs/{org}/copilot/billing/selected_users
```

Note

This endpoint is in public preview and is subject to change.

Purchases a GitHub Copilot seat for each user specified.
The organization will be billed for each seat based on the organization's Copilot plan. For more information about Copilot pricing, see "About billing for GitHub Copilot in your organization."
Only organization owners can purchase Copilot seats for their organization members. The organization must have a Copilot Business or Copilot Enterprise subscription and a configured suggestion matching policy.
For more information about setting up a Copilot subscription, see "Subscribing to Copilot for your organization."
For more information about setting a suggestion matching policy, see "Managing policies for Copilot in your organization."
The response contains the total number of new seats that were created and existing seats that were refreshed.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or admin:org scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`selected_usernames`** (array of strings) (required)
  The usernames of the organization members to be granted access to GitHub Copilot.





### HTTP response status codes


- **201** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Copilot Business or Enterprise is not enabled for this organization, billing has not been set up for this organization, a public code suggestions policy has not been set for this organization, or the organization's Copilot access setting is set to enable Copilot for all users or is unconfigured.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/copilot/billing/selected_users \
  -d '{
  "selected_usernames": [
    "cooluser1",
    "hacker2",
    "octocat"
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Add teams to the Copilot subscription for an organization](#add-teams-to-the-copilot-subscription-for-an-organization).





## Remove users from the Copilot subscription for an organization

```
DELETE /orgs/{org}/copilot/billing/selected_users
```

Note

This endpoint is in public preview and is subject to change.

Sets seats for all users specified to "pending cancellation".
This will cause the specified users to lose access to GitHub Copilot at the end of the current billing cycle unless they retain access through team membership.
For more information about disabling access to Copilot, see "Revoking access to Copilot for members of your organization."
Only organization owners can cancel Copilot seats for their organization members.
The response contains the total number of seats set to "pending cancellation".
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or admin:org scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`selected_usernames`** (array of strings) (required)
  The usernames of the organization members for which to revoke access to GitHub Copilot.





### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Copilot Business or Enterprise is not enabled for this organization, billing has not been set up for this organization, a public code suggestions policy has not been set for this organization, the seat management setting is set to enable Copilot for all users or is unconfigured, or a user's seat cannot be cancelled because it was assigned to them via a team.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/copilot/billing/selected_users \
  -d '{
  "selected_usernames": [
    "cooluser1",
    "hacker2",
    "octocat"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Remove teams from the Copilot subscription for an organization](#remove-teams-from-the-copilot-subscription-for-an-organization).





## Get Copilot seat assignment details for a user

```
GET /orgs/{org}/members/{username}/copilot
```

Note

This endpoint is in public preview and is subject to change.

Gets the GitHub Copilot seat details for a member of an organization who currently has access to GitHub Copilot.
The seat object contains information about the user's most recent Copilot activity. Users must have telemetry enabled in their IDE for Copilot in the IDE activity to be reflected in last_activity_at.
For more information about activity data, see Metrics data properties for GitHub Copilot.
Only organization owners can view Copilot seat assignment details for members of their organization.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or read:org scopes to use this endpoint.


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


- **200** - The user's GitHub Copilot seat details, including usage.


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Copilot Business or Enterprise is not enabled for this organization or the user has a pending organization invitation.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/members/USERNAME/copilot
```

**Response schema (Status: 200):**

* `assignee`: any of:
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
* `organization`: any of:
  * **null**
  * **Organization Simple**
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
* `assigning_team`: one of:
  * **Team**
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
  * **Enterprise Team**
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
* `pending_cancellation_date`: string or null, format: date
* `last_activity_at`: string or null, format: date-time
* `last_activity_editor`: string or null
* `last_authenticated_at`: string or null, format: date-time
* `created_at`: required, string, format: date-time
* `updated_at`: string, format: date-time, deprecated
* `plan_type`: string, enum: `business`, `enterprise`, `unknown`