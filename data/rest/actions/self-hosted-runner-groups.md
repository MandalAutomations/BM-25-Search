# REST API endpoints for self-hosted runner groups

Use the REST API to interact with self-hosted runner groups for GitHub Actions.

## About self-hosted runner groups in GitHub Actions

You can use the REST API to manage groups of self-hosted runners in GitHub Actions. For more information, see [Managing access to self-hosted runners using groups](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups).

These endpoints are available for authenticated users, OAuth apps, and GitHub Apps. Access tokens require [`repo` scope](/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps#available-scopes) for private repositories and [`public_repo` scope](/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps#available-scopes) for public repositories. GitHub Apps must have the `administration` permission for repositories or the `organization_self_hosted_runners` permission for organizations. Authenticated users must have admin access to repositories or organizations, or the `manage_runners:enterprise` scope for enterprises to use these endpoints.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List self-hosted runner groups for an organization

```
GET /orgs/{org}/actions/runner-groups
```

Lists all self-hosted runner groups configured in an organization and inherited from an enterprise.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

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
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`visible_to_repository`** (string)
  Only return runner groups that are allowed to be used by this repository.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/runner-groups
```

**Response schema (Status: 200):**

* `total_count`: required, number
* `runner_groups`: required, array of objects:
  * `id`: required, number
  * `name`: required, string
  * `visibility`: required, string
  * `default`: required, boolean
  * `selected_repositories_url`: string
  * `runners_url`: required, string
  * `hosted_runners_url`: string
  * `network_configuration_id`: string
  * `inherited`: required, boolean
  * `inherited_allows_public_repositories`: boolean
  * `allows_public_repositories`: required, boolean
  * `workflow_restrictions_read_only`: boolean, default: `false`
  * `restricted_to_workflows`: boolean, default: `false`
  * `selected_workflows`: array of string

## Create a self-hosted runner group for an organization

```
POST /orgs/{org}/actions/runner-groups
```

Creates a new self-hosted runner group for an organization.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`name`** (string) (required)
  Name of the runner group.

* **`visibility`** (string)
  Visibility of a runner group. You can select all repositories, select individual repositories, or limit access to private repositories.
  Default: `all`
  Can be one of: `selected`, `all`, `private`

* **`selected_repository_ids`** (array of integers)
  List of repository IDs that can access the runner group.

* **`runners`** (array of integers)
  List of runner IDs to add to the runner group.

* **`allows_public_repositories`** (boolean)
  Whether the runner group can be used by public repositories.
  Default: `false`

* **`restricted_to_workflows`** (boolean)
  If true, the runner group will be restricted to running only the workflows specified in the selected\_workflows array.
  Default: `false`

* **`selected_workflows`** (array of strings)
  List of workflows the runner group should be allowed to run. This setting will be ignored unless restricted\_to\_workflows is set to true.

* **`network_configuration_id`** (string)
  The identifier of a hosted compute network configuration.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/actions/runner-groups \
  -d '{
  "name": "Expensive hardware runners",
  "visibility": "selected",
  "selected_repository_ids": [
    32,
    91
  ],
  "runners": [
    9,
    2
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, number
* `name`: required, string
* `visibility`: required, string
* `default`: required, boolean
* `selected_repositories_url`: string
* `runners_url`: required, string
* `hosted_runners_url`: string
* `network_configuration_id`: string
* `inherited`: required, boolean
* `inherited_allows_public_repositories`: boolean
* `allows_public_repositories`: required, boolean
* `workflow_restrictions_read_only`: boolean, default: `false`
* `restricted_to_workflows`: boolean, default: `false`
* `selected_workflows`: array of string

## Get a self-hosted runner group for an organization

```
GET /orgs/{org}/actions/runner-groups/{runner_group_id}
```

Gets a specific self-hosted runner group for an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a self-hosted runner group for an organization](#create-a-self-hosted-runner-group-for-an-organization).

## Update a self-hosted runner group for an organization

```
PATCH /orgs/{org}/actions/runner-groups/{runner_group_id}
```

Updates the name and visibility of a self-hosted runner group in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

#### Body parameters

* **`name`** (string) (required)
  Name of the runner group.

* **`visibility`** (string)
  Visibility of a runner group. You can select all repositories, select individual repositories, or all private repositories.
  Can be one of: `selected`, `all`, `private`

* **`allows_public_repositories`** (boolean)
  Whether the runner group can be used by public repositories.
  Default: `false`

* **`restricted_to_workflows`** (boolean)
  If true, the runner group will be restricted to running only the workflows specified in the selected\_workflows array.
  Default: `false`

* **`selected_workflows`** (array of strings)
  List of workflows the runner group should be allowed to run. This setting will be ignored unless restricted\_to\_workflows is set to true.

* **`network_configuration_id`** (string or null)
  The identifier of a hosted compute network configuration.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID \
  -d '{
  "name": "Expensive hardware runners",
  "visibility": "selected"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a self-hosted runner group for an organization](#create-a-self-hosted-runner-group-for-an-organization).

## Delete a self-hosted runner group from an organization

```
DELETE /orgs/{org}/actions/runner-groups/{runner_group_id}
```

Deletes a self-hosted runner group for an organization.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID
```

**Response schema (Status: 204):**

## List GitHub-hosted runners in a group for an organization

```
GET /orgs/{org}/actions/runner-groups/{runner_group_id}/hosted-runners
```

Lists the GitHub-hosted runners in an organization group.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

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
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/hosted-runners
```

**Response schema (Status: 200):**

* `total_count`: required, number
* `runners`: required, array of `GitHub-hosted hosted runner`:
  * `id`: required, integer
  * `name`: required, string
  * `runner_group_id`: integer
  * `image_details`: required, any of:
    * **null**
    * **GitHub-hosted runner image details.**
      * `id`: required, string
      * `size_gb`: required, integer
      * `display_name`: required, string
      * `source`: required, string, enum: `github`, `partner`, `custom`
      * `version`: string
  * `machine_size_details`: required, `Github-owned VM details.`:
    * `id`: required, string
    * `cpu_cores`: required, integer
    * `memory_gb`: required, integer
    * `storage_gb`: required, integer
  * `status`: required, string, enum: `Ready`, `Provisioning`, `Shutdown`, `Deleting`, `Stuck`
  * `platform`: required, string
  * `maximum_runners`: integer, default: `10`
  * `public_ip_enabled`: required, boolean
  * `public_ips`: array of `Public IP for a GitHub-hosted larger runners.`:
    * `enabled`: boolean
    * `prefix`: string
    * `length`: integer
  * `last_active_on`: string or null, format: date-time
  * `image_gen`: boolean

## List repository access to a self-hosted runner group in an organization

```
GET /orgs/{org}/actions/runner-groups/{runner_group_id}/repositories
```

Lists the repositories with access to a self-hosted runner group configured in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/repositories
```

**Response schema (Status: 200):**

* `total_count`: required, number
* `repositories`: required, array of `Minimal Repository`:
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

## Set repository access for a self-hosted runner group in an organization

```
PUT /orgs/{org}/actions/runner-groups/{runner_group_id}/repositories
```

Replaces the list of repositories that have access to a self-hosted runner group configured in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

#### Body parameters

* **`selected_repository_ids`** (array of integers) (required)
  List of repository IDs that can access the runner group.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/repositories \
  -d '{
  "selected_repository_ids": [
    32,
    91
  ]
}'
```

**Response schema (Status: 204):**

## Add repository access to a self-hosted runner group in an organization

```
PUT /orgs/{org}/actions/runner-groups/{runner_group_id}/repositories/{repository_id}
```

Adds a repository to the list of repositories that can access a self-hosted runner group. The runner group must have visibility set to selected. For more information, see "Create a self-hosted runner group for an organization."
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

* **`repository_id`** (integer) (required)
  The unique identifier of the repository.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**

## Remove repository access to a self-hosted runner group in an organization

```
DELETE /orgs/{org}/actions/runner-groups/{runner_group_id}/repositories/{repository_id}
```

Removes a repository from the list of selected repositories that can access a self-hosted runner group. The runner group must have visibility set to selected. For more information, see "Create a self-hosted runner group for an organization."
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

* **`repository_id`** (integer) (required)
  The unique identifier of the repository.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**

## List self-hosted runners in a group for an organization

```
GET /orgs/{org}/actions/runner-groups/{runner_group_id}/runners
```

Lists self-hosted runners that are in a specific organization group.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

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
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/runners
```

**Response schema (Status: 200):**

* `total_count`: required, number
* `runners`: required, array of `Self hosted runners`:
  * `id`: required, integer
  * `runner_group_id`: integer
  * `name`: required, string
  * `os`: required, string
  * `status`: required, string
  * `busy`: required, boolean
  * `labels`: required, array of `Self hosted runner label`:
    * `id`: integer
    * `name`: required, string
    * `type`: string, enum: `read-only`, `custom`
  * `ephemeral`: boolean

## Set self-hosted runners in a group for an organization

```
PUT /orgs/{org}/actions/runner-groups/{runner_group_id}/runners
```

Replaces the list of self-hosted runners that are part of an organization runner group.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

#### Body parameters

* **`runners`** (array of integers) (required)
  List of runner IDs to add to the runner group.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/runners \
  -d '{
  "runners": [
    9,
    2
  ]
}'
```

**Response schema (Status: 204):**

## Add a self-hosted runner to a group for an organization

```
PUT /orgs/{org}/actions/runner-groups/{runner_group_id}/runners/{runner_id}
```

Adds a self-hosted runner to a runner group configured in an organization.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/runners/RUNNER_ID
```

**Response schema (Status: 204):**

## Remove a self-hosted runner from a group for an organization

```
DELETE /orgs/{org}/actions/runner-groups/{runner_group_id}/runners/{runner_id}
```

Removes a self-hosted runner from a group configured in an organization. The runner is then returned to the default group.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_group_id`** (integer) (required)
  Unique identifier of the self-hosted runner group.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/runner-groups/RUNNER_GROUP_ID/runners/RUNNER_ID
```

**Response schema (Status: 204):**