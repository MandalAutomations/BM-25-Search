# REST API endpoints for Codespaces organizations

Use the REST API to manage your organization members codespaces.

## About Codespaces organizations

You can manage Codespaces that are billed to your
organization. For more information,
see [Codespaces documentation](/en/codespaces).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List codespaces for the organization

```
GET /orgs/{org}/codespaces
```

Lists the codespaces associated to a specified organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/codespaces
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `codespaces`: required, array of `Codespace`:
  * `id`: required, integer, format: int64
  * `name`: required, string
  * `display_name`: string or null
  * `environment_id`: required, string or null
  * `owner`: required, `Simple User`:
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
  * `billable_owner`: required, `Simple User`:
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
  * `repository`: required, `Minimal Repository`:
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `name`: required, string
    * `full_name`: required, string
    * `owner`: required, `Simple User`:
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
    * `private`: required, boolean
    * `html_url`: required, string, format: uri
    * `description`: required, string or null
    * `fork`: required, boolean
    * `url`: required, string, format: uri
    * `archive_url`: required, string
    * `assignees_url`: required, string
    * `blobs_url`: required, string
    * `branches_url`: required, string
    * `collaborators_url`: required, string
    * `comments_url`: required, string
    * `commits_url`: required, string
    * `compare_url`: required, string
    * `contents_url`: required, string
    * `contributors_url`: required, string, format: uri
    * `deployments_url`: required, string, format: uri
    * `downloads_url`: required, string, format: uri
    * `events_url`: required, string, format: uri
    * `forks_url`: required, string, format: uri
    * `git_commits_url`: required, string
    * `git_refs_url`: required, string
    * `git_tags_url`: required, string
    * `git_url`: string
    * `issue_comment_url`: required, string
    * `issue_events_url`: required, string
    * `issues_url`: required, string
    * `keys_url`: required, string
    * `labels_url`: required, string
    * `languages_url`: required, string, format: uri
    * `merges_url`: required, string, format: uri
    * `milestones_url`: required, string
    * `notifications_url`: required, string
    * `pulls_url`: required, string
    * `releases_url`: required, string
    * `ssh_url`: string
    * `stargazers_url`: required, string, format: uri
    * `statuses_url`: required, string
    * `subscribers_url`: required, string, format: uri
    * `subscription_url`: required, string, format: uri
    * `tags_url`: required, string, format: uri
    * `teams_url`: required, string, format: uri
    * `trees_url`: required, string
    * `clone_url`: string
    * `mirror_url`: string or null
    * `hooks_url`: required, string, format: uri
    * `svn_url`: string
    * `homepage`: string or null
    * `language`: string or null
    * `forks_count`: integer
    * `stargazers_count`: integer
    * `watchers_count`: integer
    * `size`: integer
    * `default_branch`: string
    * `open_issues_count`: integer
    * `is_template`: boolean
    * `topics`: array of string
    * `has_issues`: boolean
    * `has_projects`: boolean
    * `has_wiki`: boolean
    * `has_pages`: boolean
    * `has_discussions`: boolean
    * `has_pull_requests`: boolean
    * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
    * `archived`: boolean
    * `disabled`: boolean
    * `visibility`: string
    * `pushed_at`: string or null, format: date-time
    * `created_at`: string or null, format: date-time
    * `updated_at`: string or null, format: date-time
    * `permissions`: object:
      * `admin`: boolean
      * `maintain`: boolean
      * `push`: boolean
      * `triage`: boolean
      * `pull`: boolean
    * `role_name`: string
    * `temp_clone_token`: string
    * `delete_branch_on_merge`: boolean
    * `subscribers_count`: integer
    * `network_count`: integer
    * `code_of_conduct`: `Code Of Conduct`:
      * `key`: required, string
      * `name`: required, string
      * `url`: required, string, format: uri
      * `body`: string
      * `html_url`: required, string or null, format: uri
    * `license`: object or null:
      * `key`: string
      * `name`: string
      * `spdx_id`: string
      * `url`: string or null
      * `node_id`: string
    * `forks`: integer
    * `open_issues`: integer
    * `watchers`: integer
    * `allow_forking`: boolean
    * `web_commit_signoff_required`: boolean
    * `security_and_analysis`: object or null:
      * `advanced_security`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `code_security`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `dependabot_security_updates`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `secret_scanning`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `secret_scanning_push_protection`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `secret_scanning_non_provider_patterns`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `secret_scanning_ai_detection`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `secret_scanning_delegated_alert_dismissal`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `secret_scanning_delegated_bypass`: object:
        * `status`: string, enum: `enabled`, `disabled`
      * `secret_scanning_delegated_bypass_options`: object:
        * `reviewers`: array of object
    * `custom_properties`: object, additional properties allowed
  * `machine`: required, any of:
    * **null**
    * **Codespace machine**
      * `name`: required, string
      * `display_name`: required, string
      * `operating_system`: required, string
      * `storage_in_bytes`: required, integer
      * `memory_in_bytes`: required, integer
      * `cpus`: required, integer
      * `prebuild_availability`: required, string or null, enum: `none`, `ready`, `in_progress`, `null`
  * `devcontainer_path`: string or null
  * `prebuild`: required, boolean or null
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `last_used_at`: required, string, format: date-time
  * `state`: required, string, enum: `Unknown`, `Created`, `Queued`, `Provisioning`, `Available`, `Awaiting`, `Unavailable`, `Deleted`, `Moved`, `Shutdown`, `Archived`, `Starting`, `ShuttingDown`, `Failed`, `Exporting`, `Updating`, `Rebuilding`
  * `url`: required, string, format: uri
  * `git_status`: required, object:
    * `ahead`: integer
    * `behind`: integer
    * `has_unpushed_changes`: boolean
    * `has_uncommitted_changes`: boolean
    * `ref`: string
  * `location`: required, string, enum: `EastUs`, `SouthEastAsia`, `WestEurope`, `WestUs2`
  * `idle_timeout_minutes`: required, integer or null
  * `web_url`: required, string, format: uri
  * `machines_url`: required, string, format: uri
  * `start_url`: required, string, format: uri
  * `stop_url`: required, string, format: uri
  * `publish_url`: string or null, format: uri
  * `pulls_url`: required, string or null, format: uri
  * `recent_folders`: required, array of string
  * `runtime_constraints`: object:
    * `allowed_port_privacy_settings`: array of string or null
  * `pending_operation`: boolean or null
  * `pending_operation_disabled_reason`: string or null
  * `idle_timeout_notice`: string or null
  * `retention_period_minutes`: integer or null
  * `retention_expires_at`: string or null, format: date-time
  * `last_known_stop_notice`: string or null

## Manage access control for organization codespaces

```
PUT /orgs/{org}/codespaces/access
```

Sets which users can access codespaces in an organization. This is synonymous with granting or revoking codespaces access permissions for users according to the visibility.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`visibility`** (string) (required)
  Which users can access codespaces in the organization. disabled means that no users can access codespaces in the organization.
  Can be one of: `disabled`, `selected_members`, `all_members`, `all_members_and_outside_collaborators`

* **`selected_usernames`** (array of strings)
  The usernames of the organization members who should have access to codespaces in the organization. Required when visibility is selected\_members. The provided list of usernames will replace any existing value.

### HTTP response status codes

* **204** - Response when successfully modifying permissions.

* **304** - Not modified

* **400** - Users are neither members nor collaborators of this organization.

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/codespaces/access \
  -d '{
  "visibility": "selected_members",
  "selected_usernames": [
    "johnDoe",
    "atomIO"
  ]
}'
```

**Response schema (Status: 204):**

## Add users to Codespaces access for an organization

```
POST /orgs/{org}/codespaces/access/selected_users
```

Codespaces for the specified users will be billed to the organization.
To use this endpoint, the access settings for the organization must be set to selected\_members.
For information on how to change this setting, see "Manage access control for organization codespaces."
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`selected_usernames`** (array of strings) (required)
  The usernames of the organization members and outside collaborators whose codespaces should be billed to the organization.

### HTTP response status codes

* **204** - Response when successfully modifying permissions.

* **304** - Not modified

* **400** - Users are neither members nor collaborators of this organization.

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/codespaces/access/selected_users \
  -d '{
  "selected_usernames": [
    "johnDoe",
    "atomIO"
  ]
}'
```

**Response schema (Status: 204):**

## Remove users from Codespaces access for an organization

```
DELETE /orgs/{org}/codespaces/access/selected_users
```

Codespaces for the specified users will no longer be billed to the organization.
To use this endpoint, the access settings for the organization must be set to selected\_members.
For information on how to change this setting, see "Manage access control for organization codespaces."
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`selected_usernames`** (array of strings) (required)
  The usernames of the organization members and outside collaborators whose codespaces should not be billed to the organization.

### HTTP response status codes

* **204** - Response when successfully modifying permissions.

* **304** - Not modified

* **400** - Users are neither members nor collaborators of this organization.

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/codespaces/access/selected_users \
  -d '{
  "selected_usernames": [
    "johnDoe",
    "atomIO"
  ]
}'
```

**Response schema (Status: 204):**

## List codespaces for a user in organization

```
GET /orgs/{org}/members/{username}/codespaces
```

Lists the codespaces that a member of an organization has for repositories in that organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/members/USERNAME/codespaces
```

**Response schema (Status: 200):**

Same response schema as [List codespaces for the organization](#list-codespaces-for-the-organization).

## Delete a codespace from the organization

```
DELETE /orgs/{org}/members/{username}/codespaces/{codespace_name}
```

Deletes a user's codespace.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`codespace_name`** (string) (required)
  The name of the codespace.

### HTTP response status codes

* **202** - Accepted

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/members/USERNAME/codespaces/CODESPACE_NAME
```

**Response schema (Status: 202):**

object

## Stop a codespace for an organization user

```
POST /orgs/{org}/members/{username}/codespaces/{codespace_name}/stop
```

Stops a user's codespace.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`codespace_name`** (string) (required)
  The name of the codespace.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/members/USERNAME/codespaces/CODESPACE_NAME/stop
```

**Response schema (Status: 200):**

* `id`: required, integer, format: int64
* `name`: required, string
* `display_name`: string or null
* `environment_id`: required, string or null
* `owner`: required, `Simple User`:
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
* `billable_owner`: required, `Simple User`:
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
* `repository`: required, `Minimal Repository`:
  * `id`: required, integer, format: int64
  * `node_id`: required, string
  * `name`: required, string
  * `full_name`: required, string
  * `owner`: required, `Simple User`:
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
  * `private`: required, boolean
  * `html_url`: required, string, format: uri
  * `description`: required, string or null
  * `fork`: required, boolean
  * `url`: required, string, format: uri
  * `archive_url`: required, string
  * `assignees_url`: required, string
  * `blobs_url`: required, string
  * `branches_url`: required, string
  * `collaborators_url`: required, string
  * `comments_url`: required, string
  * `commits_url`: required, string
  * `compare_url`: required, string
  * `contents_url`: required, string
  * `contributors_url`: required, string, format: uri
  * `deployments_url`: required, string, format: uri
  * `downloads_url`: required, string, format: uri
  * `events_url`: required, string, format: uri
  * `forks_url`: required, string, format: uri
  * `git_commits_url`: required, string
  * `git_refs_url`: required, string
  * `git_tags_url`: required, string
  * `git_url`: string
  * `issue_comment_url`: required, string
  * `issue_events_url`: required, string
  * `issues_url`: required, string
  * `keys_url`: required, string
  * `labels_url`: required, string
  * `languages_url`: required, string, format: uri
  * `merges_url`: required, string, format: uri
  * `milestones_url`: required, string
  * `notifications_url`: required, string
  * `pulls_url`: required, string
  * `releases_url`: required, string
  * `ssh_url`: string
  * `stargazers_url`: required, string, format: uri
  * `statuses_url`: required, string
  * `subscribers_url`: required, string, format: uri
  * `subscription_url`: required, string, format: uri
  * `tags_url`: required, string, format: uri
  * `teams_url`: required, string, format: uri
  * `trees_url`: required, string
  * `clone_url`: string
  * `mirror_url`: string or null
  * `hooks_url`: required, string, format: uri
  * `svn_url`: string
  * `homepage`: string or null
  * `language`: string or null
  * `forks_count`: integer
  * `stargazers_count`: integer
  * `watchers_count`: integer
  * `size`: integer
  * `default_branch`: string
  * `open_issues_count`: integer
  * `is_template`: boolean
  * `topics`: array of string
  * `has_issues`: boolean
  * `has_projects`: boolean
  * `has_wiki`: boolean
  * `has_pages`: boolean
  * `has_discussions`: boolean
  * `has_pull_requests`: boolean
  * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
  * `archived`: boolean
  * `disabled`: boolean
  * `visibility`: string
  * `pushed_at`: string or null, format: date-time
  * `created_at`: string or null, format: date-time
  * `updated_at`: string or null, format: date-time
  * `permissions`: object:
    * `admin`: boolean
    * `maintain`: boolean
    * `push`: boolean
    * `triage`: boolean
    * `pull`: boolean
  * `role_name`: string
  * `temp_clone_token`: string
  * `delete_branch_on_merge`: boolean
  * `subscribers_count`: integer
  * `network_count`: integer
  * `code_of_conduct`: `Code Of Conduct`:
    * `key`: required, string
    * `name`: required, string
    * `url`: required, string, format: uri
    * `body`: string
    * `html_url`: required, string or null, format: uri
  * `license`: object or null:
    * `key`: string
    * `name`: string
    * `spdx_id`: string
    * `url`: string or null
    * `node_id`: string
  * `forks`: integer
  * `open_issues`: integer
  * `watchers`: integer
  * `allow_forking`: boolean
  * `web_commit_signoff_required`: boolean
  * `security_and_analysis`: object or null:
    * `advanced_security`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `code_security`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `dependabot_security_updates`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `secret_scanning`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `secret_scanning_push_protection`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `secret_scanning_non_provider_patterns`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `secret_scanning_ai_detection`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `secret_scanning_delegated_alert_dismissal`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `secret_scanning_delegated_bypass`: object:
      * `status`: string, enum: `enabled`, `disabled`
    * `secret_scanning_delegated_bypass_options`: object:
      * `reviewers`: array of objects:
        * `reviewer_id`: required, integer
        * `reviewer_type`: required, string, enum: `TEAM`, `ROLE`
        * `mode`: string, enum: `ALWAYS`, `EXEMPT`, default: `"ALWAYS"`
  * `custom_properties`: object, additional properties allowed
* `machine`: required, any of:
  * **null**
  * **Codespace machine**
    * `name`: required, string
    * `display_name`: required, string
    * `operating_system`: required, string
    * `storage_in_bytes`: required, integer
    * `memory_in_bytes`: required, integer
    * `cpus`: required, integer
    * `prebuild_availability`: required, string or null, enum: `none`, `ready`, `in_progress`, `null`
* `devcontainer_path`: string or null
* `prebuild`: required, boolean or null
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `last_used_at`: required, string, format: date-time
* `state`: required, string, enum: `Unknown`, `Created`, `Queued`, `Provisioning`, `Available`, `Awaiting`, `Unavailable`, `Deleted`, `Moved`, `Shutdown`, `Archived`, `Starting`, `ShuttingDown`, `Failed`, `Exporting`, `Updating`, `Rebuilding`
* `url`: required, string, format: uri
* `git_status`: required, object:
  * `ahead`: integer
  * `behind`: integer
  * `has_unpushed_changes`: boolean
  * `has_uncommitted_changes`: boolean
  * `ref`: string
* `location`: required, string, enum: `EastUs`, `SouthEastAsia`, `WestEurope`, `WestUs2`
* `idle_timeout_minutes`: required, integer or null
* `web_url`: required, string, format: uri
* `machines_url`: required, string, format: uri
* `start_url`: required, string, format: uri
* `stop_url`: required, string, format: uri
* `publish_url`: string or null, format: uri
* `pulls_url`: required, string or null, format: uri
* `recent_folders`: required, array of string
* `runtime_constraints`: object:
  * `allowed_port_privacy_settings`: array of string or null
* `pending_operation`: boolean or null
* `pending_operation_disabled_reason`: string or null
* `idle_timeout_notice`: string or null
* `retention_period_minutes`: integer or null
* `retention_expires_at`: string or null, format: date-time
* `last_known_stop_notice`: string or null