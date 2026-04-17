# REST API endpoints for security campaigns

Use the REST API to create and manage security campaigns for your organization.

> [!NOTE]
> These endpoints only interact with published campaigns. Draft campaigns cannot currently be viewed or managed through the API.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List campaigns for an organization

```
GET /orgs/{org}/campaigns
```

Lists campaigns in an organization.
The authenticated user must be an owner or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the security_events scope to use this endpoint.


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
  Default: `30`

- **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`state`** (string)
  If specified, only campaigns with this state will be returned.
  Can be one of: `open`, `closed`

- **`sort`** (string)
  The property by which to sort the results.
  Default: `created`
  Can be one of: `created`, `updated`, `ends_at`, `published`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/campaigns
```

**Response schema (Status: 200):**

Array of `Campaign summary`:
  * `number`: required, integer
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `name`: string
  * `description`: required, string
  * `managers`: required, array of `Simple User`:
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
  * `team_managers`: array of `Team`:
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
  * `published_at`: string, format: date-time
  * `ends_at`: required, string, format: date-time
  * `closed_at`: string or null, format: date-time
  * `state`: required, string, enum: `open`, `closed`
  * `contact_link`: required, string or null, format: uri
  * `alert_stats`: object:
    * `open_count`: required, integer
    * `closed_count`: required, integer
    * `in_progress_count`: required, integer





## Create a campaign for an organization

```
POST /orgs/{org}/campaigns
```

Create a campaign for an organization.
The authenticated user must be an owner or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the security_events scope to use this endpoint.
Fine-grained tokens must have the "Code scanning alerts" repository permissions (read) on all repositories included
in the campaign.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **400** - Bad Request


- **404** - Resource not found


- **422** - Unprocessable Entity


- **429** - Too Many Requests


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/campaigns \
  -d '{
  "name": "Critical CodeQL alerts",
  "description": "Address critical alerts before they are exploited to prevent breaches, protect sensitive data, and mitigate financial and reputational damage.",
  "managers": [
    "octocat"
  ],
  "ends_at": "2024-03-14T00:00:00Z",
  "code_scanning_alerts": [
    {
      "repository_id": 1296269,
      "alert_numbers": [
        1,
        2
      ]
    }
  ]
}'
```

**Response schema (Status: 200):**

* `number`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `name`: string
* `description`: required, string
* `managers`: required, array of `Simple User`:
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
* `team_managers`: array of `Team`:
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
* `published_at`: string, format: date-time
* `ends_at`: required, string, format: date-time
* `closed_at`: string or null, format: date-time
* `state`: required, string, enum: `open`, `closed`
* `contact_link`: required, string or null, format: uri
* `alert_stats`: object:
  * `open_count`: required, integer
  * `closed_count`: required, integer
  * `in_progress_count`: required, integer





## Get a campaign for an organization

```
GET /orgs/{org}/campaigns/{campaign_number}
```

Gets a campaign for an organization.
The authenticated user must be an owner or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`campaign_number`** (integer) (required)
  The campaign number.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **422** - Unprocessable Entity


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/campaigns/CAMPAIGN_NUMBER
```

**Response schema (Status: 200):**

Same response schema as [Create a campaign for an organization](#create-a-campaign-for-an-organization).





## Update a campaign

```
PATCH /orgs/{org}/campaigns/{campaign_number}
```

Updates a campaign in an organization.
The authenticated user must be an owner or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`campaign_number`** (integer) (required)
  The campaign number.




#### Body parameters

- **`name`** (string)
  The name of the campaign

- **`description`** (string)
  A description for the campaign

- **`managers`** (array of strings)
  The logins of the users to set as the campaign managers. At this time, only a single manager can be supplied.

- **`team_managers`** (array of strings)
  The slugs of the teams to set as the campaign managers.

- **`ends_at`** (string)
  The end date and time of the campaign, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.

- **`contact_link`** (string or null)
  The contact link of the campaign. Must be a URI.

- **`state`** (string)
  Indicates whether a campaign is open or closed
  Can be one of: `open`, `closed`





### HTTP response status codes


- **200** - OK


- **400** - Bad Request


- **404** - Resource not found


- **422** - Unprocessable Entity


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/campaigns/CAMPAIGN_NUMBER \
  -d '{
  "name": "Critical CodeQL alerts"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a campaign for an organization](#create-a-campaign-for-an-organization).





## Delete a campaign for an organization

```
DELETE /orgs/{org}/campaigns/{campaign_number}
```

Deletes a campaign in an organization.
The authenticated user must be an owner or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`campaign_number`** (integer) (required)
  The campaign number.






### HTTP response status codes


- **204** - Deletion successful


- **404** - Resource not found


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/campaigns/CAMPAIGN_NUMBER
```

**Response schema (Status: 204):**