# REST API endpoints for Codespaces

Use the REST API to manage GitHub Codespaces.

## About GitHub Codespaces

You can manage Codespaces using the REST API. These endpoints are available for authenticated users, OAuth apps, and GitHub Apps. For more information, see [Codespaces documentation](/en/codespaces).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List codespaces in a repository for the authenticated user

```
GET /repos/{owner}/{repo}/codespaces
```

Lists the codespaces associated to a specified repository and the authenticated user.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

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

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

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
  https://api.github.com/repos/OWNER/REPO/codespaces
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

## Create a codespace in a repository

```
POST /repos/{owner}/{repo}/codespaces
```

Creates a codespace owned by the authenticated user in the specified repository.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`ref`** (string)
  Git ref (typically a branch name) for this codespace

* **`location`** (string)
  The requested location for a new codespace. Best efforts are made to respect this upon creation. Assigned by IP if not provided.

* **`geo`** (string)
  The geographic area for this codespace. If not specified, the value is assigned by IP. This property replaces location, which is closing down.
  Can be one of: `EuropeWest`, `SoutheastAsia`, `UsEast`, `UsWest`

* **`client_ip`** (string)
  IP for location auto-detection when proxying a request

* **`machine`** (string)
  Machine type to use for this codespace

* **`devcontainer_path`** (string)
  Path to devcontainer.json config to use for this codespace

* **`multi_repo_permissions_opt_out`** (boolean)
  Whether to authorize requested permissions from devcontainer.json

* **`working_directory`** (string)
  Working directory for this codespace

* **`idle_timeout_minutes`** (integer)
  Time in minutes before codespace stops from inactivity

* **`display_name`** (string)
  Display name for this codespace

* **`retention_period_minutes`** (integer)
  Duration in minutes after codespace has gone idle in which it will be deleted. Must be integer minutes between 0 and 43200 (30 days).

### HTTP response status codes

* **201** - Response when the codespace was successfully created

* **202** - Response when the codespace creation partially failed but is being retried in the background

* **400** - Bad Request

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example 1: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/codespaces \
  -d '{
  "ref": "main",
  "machine": "standardLinux32gb"
}'
```

**Response schema (Status: 201):**

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

#### Example 2: Status Code 202

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/codespaces \
  -d '{
  "ref": "main",
  "machine": "standardLinux32gb"
}'
```

**Response schema (Status: 202):**

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

## List devcontainer configurations in a repository for the authenticated user

```
GET /repos/{owner}/{repo}/codespaces/devcontainers
```

Lists the devcontainer.json files associated with a specified repository and the authenticated user. These files
specify launchpoint configurations for codespaces created within the repository.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

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

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **400** - Bad Request

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
  https://api.github.com/repos/OWNER/REPO/codespaces/devcontainers
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `devcontainers`: required, array of objects:
  * `path`: required, string
  * `name`: string
  * `display_name`: string

## Get default attributes for a codespace

```
GET /repos/{owner}/{repo}/codespaces/new
```

Gets the default attributes for codespaces created by the user with the repository.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`ref`** (string)
  The branch or commit to check for a default devcontainer path. If not specified, the default branch will be checked.

* **`client_ip`** (string)
  An alternative IP for default location auto-detection, such as when proxying a request.

### HTTP response status codes

* **200** - Response when a user is able to create codespaces from the repository.

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/codespaces/new
```

**Response schema (Status: 200):**

* `billable_owner`: `Simple User`:
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
* `defaults`: object:
  * `location`: required, string
  * `devcontainer_path`: required, string or null

## Check if permissions defined by a devcontainer have been accepted by the authenticated user

```
GET /repos/{owner}/{repo}/codespaces/permissions_check
```

Checks whether the permissions defined by a given devcontainer configuration have been accepted by the authenticated user.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`ref`** (string) (required)
  The git reference that points to the location of the devcontainer configuration to use for the permission check. The value of ref will typically be a branch name (heads/BRANCH\_NAME). For more information, see "Git References" in the Git documentation.

* **`devcontainer_path`** (string) (required)
  Path to the devcontainer.json configuration to use for the permission check.

### HTTP response status codes

* **200** - Response when the permission check is successful

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/codespaces/permissions_check
```

**Response schema (Status: 200):**

* `accepted`: required, boolean

## Create a codespace from a pull request

```
POST /repos/{owner}/{repo}/pulls/{pull_number}/codespaces
```

Creates a codespace owned by the authenticated user for the specified pull request.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`pull_number`** (integer) (required)
  The number that identifies the pull request.

#### Body parameters

* **`location`** (string)
  The requested location for a new codespace. Best efforts are made to respect this upon creation. Assigned by IP if not provided.

* **`geo`** (string)
  The geographic area for this codespace. If not specified, the value is assigned by IP. This property replaces location, which is closing down.
  Can be one of: `EuropeWest`, `SoutheastAsia`, `UsEast`, `UsWest`

* **`client_ip`** (string)
  IP for location auto-detection when proxying a request

* **`machine`** (string)
  Machine type to use for this codespace

* **`devcontainer_path`** (string)
  Path to devcontainer.json config to use for this codespace

* **`multi_repo_permissions_opt_out`** (boolean)
  Whether to authorize requested permissions from devcontainer.json

* **`working_directory`** (string)
  Working directory for this codespace

* **`idle_timeout_minutes`** (integer)
  Time in minutes before codespace stops from inactivity

* **`display_name`** (string)
  Display name for this codespace

* **`retention_period_minutes`** (integer)
  Duration in minutes after codespace has gone idle in which it will be deleted. Must be integer minutes between 0 and 43200 (30 days).

### HTTP response status codes

* **201** - Response when the codespace was successfully created

* **202** - Response when the codespace creation partially failed but is being retried in the background

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example 1: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pulls/PULL_NUMBER/codespaces \
  -d '{
  "repository_id": 1,
  "ref": "main"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a codespace in a repository](#create-a-codespace-in-a-repository).

#### Example 2: Status Code 202

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pulls/PULL_NUMBER/codespaces \
  -d '{
  "repository_id": 1,
  "ref": "main"
}'
```

**Response schema (Status: 202):**

Same response schema as [Create a codespace in a repository](#create-a-codespace-in-a-repository).

## List codespaces for the authenticated user

```
GET /user/codespaces
```

Lists the authenticated user's codespaces.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

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

* **`repository_id`** (integer)
  ID of the Repository to filter on

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
  https://api.github.com/user/codespaces
```

**Response schema (Status: 200):**

Same response schema as [List codespaces in a repository for the authenticated user](#list-codespaces-in-a-repository-for-the-authenticated-user).

## Create a codespace for the authenticated user

```
POST /user/codespaces
```

Creates a new codespace, owned by the authenticated user.
This endpoint requires either a repository\_id OR a pull\_request but not both.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`repository_id`** (integer) (required)
  Repository id for this codespace

* **`ref`** (string)
  Git ref (typically a branch name) for this codespace

* **`location`** (string)
  The requested location for a new codespace. Best efforts are made to respect this upon creation. Assigned by IP if not provided.

* **`geo`** (string)
  The geographic area for this codespace. If not specified, the value is assigned by IP. This property replaces location, which is closing down.
  Can be one of: `EuropeWest`, `SoutheastAsia`, `UsEast`, `UsWest`

* **`client_ip`** (string)
  IP for location auto-detection when proxying a request

* **`machine`** (string)
  Machine type to use for this codespace

* **`devcontainer_path`** (string)
  Path to devcontainer.json config to use for this codespace

* **`multi_repo_permissions_opt_out`** (boolean)
  Whether to authorize requested permissions from devcontainer.json

* **`working_directory`** (string)
  Working directory for this codespace

* **`idle_timeout_minutes`** (integer)
  Time in minutes before codespace stops from inactivity

* **`display_name`** (string)
  Display name for this codespace

* **`retention_period_minutes`** (integer)
  Duration in minutes after codespace has gone idle in which it will be deleted. Must be integer minutes between 0 and 43200 (30 days).

* **`pull_request`** (object) (required)
  Pull request number for this codespace
  * **`pull_request_number`** (integer) (required)
    Pull request number
  * **`repository_id`** (integer) (required)
    Repository id for this codespace

### HTTP response status codes

* **201** - Response when the codespace was successfully created

* **202** - Response when the codespace creation partially failed but is being retried in the background

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example 1: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/codespaces \
  -d '{
  "repository_id": 1,
  "ref": "main",
  "geo": "UsWest"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a codespace in a repository](#create-a-codespace-in-a-repository).

#### Example 2: Status Code 202

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/codespaces \
  -d '{
  "repository_id": 1,
  "ref": "main",
  "geo": "UsWest"
}'
```

**Response schema (Status: 202):**

Same response schema as [Create a codespace in a repository](#create-a-codespace-in-a-repository).

## Get a codespace for the authenticated user

```
GET /user/codespaces/{codespace_name}
```

Gets information about a user's codespace.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

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
  -X GET \
  https://api.github.com/user/codespaces/CODESPACE_NAME
```

**Response schema (Status: 200):**

Same response schema as [Create a codespace in a repository](#create-a-codespace-in-a-repository).

## Update a codespace for the authenticated user

```
PATCH /user/codespaces/{codespace_name}
```

Updates a codespace owned by the authenticated user. Currently only the codespace's machine type and recent folders can be modified using this endpoint.
If you specify a new machine type it will be applied the next time your codespace is started.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`codespace_name`** (string) (required)
  The name of the codespace.

#### Body parameters

* **`machine`** (string)
  A valid machine to transition this codespace to.

* **`display_name`** (string)
  Display name for this codespace

* **`recent_folders`** (array of strings)
  Recently opened folders inside the codespace. It is currently used by the clients to determine the folder path to load the codespace in.

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/user/codespaces/CODESPACE_NAME \
  -d '{
  "machine": "standardLinux"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a codespace in a repository](#create-a-codespace-in-a-repository).

## Delete a codespace for the authenticated user

```
DELETE /user/codespaces/{codespace_name}
```

Deletes a user's codespace.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

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
  https://api.github.com/user/codespaces/CODESPACE_NAME
```

**Response schema (Status: 202):**

object

## Export a codespace for the authenticated user

```
POST /user/codespaces/{codespace_name}/exports
```

Triggers an export of the specified codespace and returns a URL and ID where the status of the export can be monitored.
If changes cannot be pushed to the codespace's repository, they will be pushed to a new or previously-existing fork instead.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`codespace_name`** (string) (required)
  The name of the codespace.

### HTTP response status codes

* **202** - Accepted

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/codespaces/CODESPACE_NAME/exports
```

**Response schema (Status: 202):**

* `state`: string or null
* `completed_at`: string or null, format: date-time
* `branch`: string or null
* `sha`: string or null
* `id`: string
* `export_url`: string
* `html_url`: string or null

## Get details about a codespace export

```
GET /user/codespaces/{codespace_name}/exports/{export_id}
```

Gets information about an export of a codespace.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`codespace_name`** (string) (required)
  The name of the codespace.

* **`export_id`** (string) (required)
  The ID of the export operation, or latest. Currently only latest is currently supported.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/codespaces/CODESPACE_NAME/exports/EXPORT_ID
```

**Response schema (Status: 200):**

Same response schema as [Export a codespace for the authenticated user](#export-a-codespace-for-the-authenticated-user).

## Create a repository from an unpublished codespace

```
POST /user/codespaces/{codespace_name}/publish
```

Publishes an unpublished codespace, creating a new repository and assigning it to the codespace.
The codespace's token is granted write permissions to the repository, allowing the user to push their changes.
This will fail for a codespace that is already published, meaning it has an associated repository.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`codespace_name`** (string) (required)
  The name of the codespace.

#### Body parameters

* **`name`** (string)
  A name for the new repository.

* **`private`** (boolean)
  Whether the new repository should be private.
  Default: `false`

### HTTP response status codes

* **201** - Created

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/codespaces/CODESPACE_NAME/publish \
  -d '{
  "repository": "monalisa-octocat-hello-world-g4wpq6h95q",
  "private": false
}'
```

**Response schema (Status: 201):**

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
* `repository`: required, `Full Repository`:
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
  * `git_url`: required, string
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
  * `ssh_url`: required, string
  * `stargazers_url`: required, string, format: uri
  * `statuses_url`: required, string
  * `subscribers_url`: required, string, format: uri
  * `subscription_url`: required, string, format: uri
  * `tags_url`: required, string, format: uri
  * `teams_url`: required, string, format: uri
  * `trees_url`: required, string
  * `clone_url`: required, string
  * `mirror_url`: required, string or null, format: uri
  * `hooks_url`: required, string, format: uri
  * `svn_url`: required, string, format: uri
  * `homepage`: required, string or null, format: uri
  * `language`: required, string or null
  * `forks_count`: required, integer
  * `stargazers_count`: required, integer
  * `watchers_count`: required, integer
  * `size`: required, integer
  * `default_branch`: required, string
  * `open_issues_count`: required, integer
  * `is_template`: boolean
  * `topics`: array of string
  * `has_issues`: required, boolean
  * `has_projects`: required, boolean
  * `has_wiki`: required, boolean
  * `has_pages`: required, boolean
  * `has_discussions`: required, boolean
  * `has_pull_requests`: boolean
  * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
  * `archived`: required, boolean
  * `disabled`: required, boolean
  * `visibility`: string
  * `pushed_at`: required, string, format: date-time
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `permissions`: object:
    * `admin`: required, boolean
    * `maintain`: boolean
    * `push`: required, boolean
    * `triage`: boolean
    * `pull`: required, boolean
  * `allow_rebase_merge`: boolean
  * `template_repository`: any of:
    * **null**
    * **Repository**
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `name`: required, string
      * `full_name`: required, string
      * `license`: required, any of:
        * **null**
        * **License Simple**
          * `key`: required, string
          * `name`: required, string
          * `url`: required, string or null, format: uri
          * `spdx_id`: required, string or null
          * `node_id`: required, string
          * `html_url`: string, format: uri
      * `forks`: required, integer
      * `permissions`: object:
        * `admin`: required, boolean
        * `pull`: required, boolean
        * `triage`: boolean
        * `push`: required, boolean
        * `maintain`: boolean
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
      * `private`: required, boolean, default: `false`
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
      * `git_url`: required, string
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
      * `ssh_url`: required, string
      * `stargazers_url`: required, string, format: uri
      * `statuses_url`: required, string
      * `subscribers_url`: required, string, format: uri
      * `subscription_url`: required, string, format: uri
      * `tags_url`: required, string, format: uri
      * `teams_url`: required, string, format: uri
      * `trees_url`: required, string
      * `clone_url`: required, string
      * `mirror_url`: required, string or null, format: uri
      * `hooks_url`: required, string, format: uri
      * `svn_url`: required, string, format: uri
      * `homepage`: required, string or null, format: uri
      * `language`: required, string or null
      * `forks_count`: required, integer
      * `stargazers_count`: required, integer
      * `watchers_count`: required, integer
      * `size`: required, integer
      * `default_branch`: required, string
      * `open_issues_count`: required, integer
      * `is_template`: boolean, default: `false`
      * `topics`: array of string
      * `has_issues`: required, boolean, default: `true`
      * `has_projects`: required, boolean, default: `true`
      * `has_wiki`: required, boolean, default: `true`
      * `has_pages`: required, boolean
      * `has_discussions`: boolean, default: `false`
      * `has_pull_requests`: boolean, default: `true`
      * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
      * `archived`: required, boolean, default: `false`
      * `disabled`: required, boolean
      * `visibility`: string, default: `"public"`
      * `pushed_at`: required, string or null, format: date-time
      * `created_at`: required, string or null, format: date-time
      * `updated_at`: required, string or null, format: date-time
      * `allow_rebase_merge`: boolean, default: `true`
      * `temp_clone_token`: string
      * `allow_squash_merge`: boolean, default: `true`
      * `allow_auto_merge`: boolean, default: `false`
      * `delete_branch_on_merge`: boolean, default: `false`
      * `allow_update_branch`: boolean, default: `false`
      * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
      * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
      * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
      * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
      * `allow_merge_commit`: boolean, default: `true`
      * `allow_forking`: boolean
      * `web_commit_signoff_required`: boolean, default: `false`
      * `open_issues`: required, integer
      * `watchers`: required, integer
      * `starred_at`: string
      * `anonymous_access_enabled`: boolean
      * `code_search_index_status`: object:
        * `lexical_search_ok`: boolean
        * `lexical_commit_sha`: string
  * `temp_clone_token`: string or null
  * `allow_squash_merge`: boolean
  * `allow_auto_merge`: boolean
  * `delete_branch_on_merge`: boolean
  * `allow_merge_commit`: boolean
  * `allow_update_branch`: boolean
  * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
  * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
  * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
  * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
  * `allow_forking`: boolean
  * `web_commit_signoff_required`: boolean
  * `subscribers_count`: required, integer
  * `network_count`: required, integer
  * `license`: required, any of:
    * **null**
    * **License Simple**
      * `key`: required, string
      * `name`: required, string
      * `url`: required, string or null, format: uri
      * `spdx_id`: required, string or null
      * `node_id`: required, string
      * `html_url`: string, format: uri
  * `organization`: any of:
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
  * `parent`: `Repository`:
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `name`: required, string
    * `full_name`: required, string
    * `license`: required, any of:
      * **null**
      * **License Simple**
        * `key`: required, string
        * `name`: required, string
        * `url`: required, string or null, format: uri
        * `spdx_id`: required, string or null
        * `node_id`: required, string
        * `html_url`: string, format: uri
    * `forks`: required, integer
    * `permissions`: object:
      * `admin`: required, boolean
      * `pull`: required, boolean
      * `triage`: boolean
      * `push`: required, boolean
      * `maintain`: boolean
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
    * `private`: required, boolean, default: `false`
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
    * `git_url`: required, string
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
    * `ssh_url`: required, string
    * `stargazers_url`: required, string, format: uri
    * `statuses_url`: required, string
    * `subscribers_url`: required, string, format: uri
    * `subscription_url`: required, string, format: uri
    * `tags_url`: required, string, format: uri
    * `teams_url`: required, string, format: uri
    * `trees_url`: required, string
    * `clone_url`: required, string
    * `mirror_url`: required, string or null, format: uri
    * `hooks_url`: required, string, format: uri
    * `svn_url`: required, string, format: uri
    * `homepage`: required, string or null, format: uri
    * `language`: required, string or null
    * `forks_count`: required, integer
    * `stargazers_count`: required, integer
    * `watchers_count`: required, integer
    * `size`: required, integer
    * `default_branch`: required, string
    * `open_issues_count`: required, integer
    * `is_template`: boolean, default: `false`
    * `topics`: array of string
    * `has_issues`: required, boolean, default: `true`
    * `has_projects`: required, boolean, default: `true`
    * `has_wiki`: required, boolean, default: `true`
    * `has_pages`: required, boolean
    * `has_discussions`: boolean, default: `false`
    * `has_pull_requests`: boolean, default: `true`
    * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
    * `archived`: required, boolean, default: `false`
    * `disabled`: required, boolean
    * `visibility`: string, default: `"public"`
    * `pushed_at`: required, string or null, format: date-time
    * `created_at`: required, string or null, format: date-time
    * `updated_at`: required, string or null, format: date-time
    * `allow_rebase_merge`: boolean, default: `true`
    * `temp_clone_token`: string
    * `allow_squash_merge`: boolean, default: `true`
    * `allow_auto_merge`: boolean, default: `false`
    * `delete_branch_on_merge`: boolean, default: `false`
    * `allow_update_branch`: boolean, default: `false`
    * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
    * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
    * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
    * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
    * `allow_merge_commit`: boolean, default: `true`
    * `allow_forking`: boolean
    * `web_commit_signoff_required`: boolean, default: `false`
    * `open_issues`: required, integer
    * `watchers`: required, integer
    * `starred_at`: string
    * `anonymous_access_enabled`: boolean
    * `code_search_index_status`: object:
      * `lexical_search_ok`: boolean
      * `lexical_commit_sha`: string
  * `source`: `Repository`:
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `name`: required, string
    * `full_name`: required, string
    * `license`: required, any of:
      * **null**
      * **License Simple**
        * `key`: required, string
        * `name`: required, string
        * `url`: required, string or null, format: uri
        * `spdx_id`: required, string or null
        * `node_id`: required, string
        * `html_url`: string, format: uri
    * `forks`: required, integer
    * `permissions`: object:
      * `admin`: required, boolean
      * `pull`: required, boolean
      * `triage`: boolean
      * `push`: required, boolean
      * `maintain`: boolean
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
    * `private`: required, boolean, default: `false`
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
    * `git_url`: required, string
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
    * `ssh_url`: required, string
    * `stargazers_url`: required, string, format: uri
    * `statuses_url`: required, string
    * `subscribers_url`: required, string, format: uri
    * `subscription_url`: required, string, format: uri
    * `tags_url`: required, string, format: uri
    * `teams_url`: required, string, format: uri
    * `trees_url`: required, string
    * `clone_url`: required, string
    * `mirror_url`: required, string or null, format: uri
    * `hooks_url`: required, string, format: uri
    * `svn_url`: required, string, format: uri
    * `homepage`: required, string or null, format: uri
    * `language`: required, string or null
    * `forks_count`: required, integer
    * `stargazers_count`: required, integer
    * `watchers_count`: required, integer
    * `size`: required, integer
    * `default_branch`: required, string
    * `open_issues_count`: required, integer
    * `is_template`: boolean, default: `false`
    * `topics`: array of string
    * `has_issues`: required, boolean, default: `true`
    * `has_projects`: required, boolean, default: `true`
    * `has_wiki`: required, boolean, default: `true`
    * `has_pages`: required, boolean
    * `has_discussions`: boolean, default: `false`
    * `has_pull_requests`: boolean, default: `true`
    * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
    * `archived`: required, boolean, default: `false`
    * `disabled`: required, boolean
    * `visibility`: string, default: `"public"`
    * `pushed_at`: required, string or null, format: date-time
    * `created_at`: required, string or null, format: date-time
    * `updated_at`: required, string or null, format: date-time
    * `allow_rebase_merge`: boolean, default: `true`
    * `temp_clone_token`: string
    * `allow_squash_merge`: boolean, default: `true`
    * `allow_auto_merge`: boolean, default: `false`
    * `delete_branch_on_merge`: boolean, default: `false`
    * `allow_update_branch`: boolean, default: `false`
    * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
    * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
    * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
    * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
    * `allow_merge_commit`: boolean, default: `true`
    * `allow_forking`: boolean
    * `web_commit_signoff_required`: boolean, default: `false`
    * `open_issues`: required, integer
    * `watchers`: required, integer
    * `starred_at`: string
    * `anonymous_access_enabled`: boolean
    * `code_search_index_status`: object:
      * `lexical_search_ok`: boolean
      * `lexical_commit_sha`: string
  * `forks`: required, integer
  * `master_branch`: string
  * `open_issues`: required, integer
  * `watchers`: required, integer
  * `anonymous_access_enabled`: boolean, default: `true`
  * `code_of_conduct`: `Code Of Conduct Simple`:
    * `url`: required, string, format: uri
    * `key`: required, string
    * `name`: required, string
    * `html_url`: required, string or null, format: uri
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

## Start a codespace for the authenticated user

```
POST /user/codespaces/{codespace_name}/start
```

Starts a user's codespace.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`codespace_name`** (string) (required)
  The name of the codespace.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **400** - Bad Request

* **401** - Requires authentication

* **402** - Payment required

* **403** - Forbidden

* **404** - Resource not found

* **409** - Conflict

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/codespaces/CODESPACE_NAME/start
```

**Response schema (Status: 200):**

Same response schema as [Create a codespace in a repository](#create-a-codespace-in-a-repository).

## Stop a codespace for the authenticated user

```
POST /user/codespaces/{codespace_name}/stop
```

Stops a user's codespace.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`codespace_name`** (string) (required)
  The name of the codespace.

### HTTP response status codes

* **200** - OK

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
  https://api.github.com/user/codespaces/CODESPACE_NAME/stop
```

**Response schema (Status: 200):**

Same response schema as [Create a codespace in a repository](#create-a-codespace-in-a-repository).