# REST API endpoints for GitHub Actions permissions

Use the REST API to interact with permissions for GitHub Actions.

## About permissions for GitHub Actions

You can use the REST API to set permissions for the organizations and repositories that are allowed to run GitHub Actions, and the actions and reusable workflows that are allowed to run. For more information, see [Billing and usage](/en/actions/learn-github-actions/usage-limits-billing-and-administration#disabling-or-limiting-github-actions-for-your-repository-or-organization).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get GitHub Actions permissions for an organization

```
GET /orgs/{org}/actions/permissions
```

Gets the GitHub Actions permissions policy for repositories and allowed actions and reusable workflows in an organization.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/permissions
```

**Response schema (Status: 200):**

* `enabled_repositories`: required, string, enum: `all`, `none`, `selected`
* `selected_repositories_url`: string
* `allowed_actions`: string, enum: `all`, `local_only`, `selected`
* `selected_actions_url`: string
* `sha_pinning_required`: boolean

## Set GitHub Actions permissions for an organization

```
PUT /orgs/{org}/actions/permissions
```

Sets the GitHub Actions permissions policy for repositories and allowed actions and reusable workflows in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`enabled_repositories`** (string) (required)
  The policy that controls the repositories in the organization that are allowed to run GitHub Actions.
  Can be one of: `all`, `none`, `selected`

* **`allowed_actions`** (string)
  The permissions policy that controls the actions and reusable workflows that are allowed to run.
  Can be one of: `all`, `local_only`, `selected`

* **`sha_pinning_required`** (boolean)
  Whether actions must be pinned to a full-length commit SHA.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions \
  -d '{
  "enabled_repositories": "all",
  "allowed_actions": "selected",
  "sha_pinning_required": true
}'
```

**Response schema (Status: 204):**

## Get artifact and log retention settings for an organization

```
GET /orgs/{org}/actions/permissions/artifact-and-log-retention
```

Gets artifact and log retention settings for an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/actions/permissions/artifact-and-log-retention
```

**Response schema (Status: 200):**

* `days`: required, integer
* `maximum_allowed_days`: required, integer

## Set artifact and log retention settings for an organization

```
PUT /orgs/{org}/actions/permissions/artifact-and-log-retention
```

Sets artifact and log retention settings for an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`days`** (integer) (required)
  The number of days to retain artifacts and logs

### HTTP response status codes

* **204** - No content

* **403** - Forbidden

* **404** - Resource not found

* **409** - Conflict

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/artifact-and-log-retention \
  -d '{
  "days": 100
}'
```

**Response schema (Status: 204):**

## Get fork PR contributor approval permissions for an organization

```
GET /orgs/{org}/actions/permissions/fork-pr-contributor-approval
```

Gets the fork PR contributor approval policy for an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/permissions/fork-pr-contributor-approval
```

**Response schema (Status: 200):**

* `approval_policy`: required, string, enum: `first_time_contributors_new_to_github`, `first_time_contributors`, `all_external_contributors`

## Set fork PR contributor approval permissions for an organization

```
PUT /orgs/{org}/actions/permissions/fork-pr-contributor-approval
```

Sets the fork PR contributor approval policy for an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`approval_policy`** (string) (required)
  The policy that controls when fork PR workflows require approval from a maintainer.
  Can be one of: `first_time_contributors_new_to_github`, `first_time_contributors`, `all_external_contributors`

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Set approval policy to first time contributors

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/fork-pr-contributor-approval \
  -d '{
  "approval_policy": "first_time_contributors"
}'
```

**Response schema (Status: 204):**

## Get private repo fork PR workflow settings for an organization

```
GET /orgs/{org}/actions/permissions/fork-pr-workflows-private-repos
```

Gets the settings for whether workflows from fork pull requests can run on private repositories in an organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/actions/permissions/fork-pr-workflows-private-repos
```

**Response schema (Status: 200):**

* `run_workflows_from_fork_pull_requests`: required, boolean
* `send_write_tokens_to_workflows`: required, boolean
* `send_secrets_and_variables`: required, boolean
* `require_approval_for_fork_pr_workflows`: required, boolean

## Set private repo fork PR workflow settings for an organization

```
PUT /orgs/{org}/actions/permissions/fork-pr-workflows-private-repos
```

Sets the settings for whether workflows from fork pull requests can run on private repositories in an organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`run_workflows_from_fork_pull_requests`** (boolean) (required)
  Whether workflows triggered by pull requests from forks are allowed to run on private repositories.

* **`send_write_tokens_to_workflows`** (boolean)
  Whether GitHub Actions can create pull requests or submit approving pull request reviews from a workflow triggered by a fork pull request.

* **`send_secrets_and_variables`** (boolean)
  Whether to make secrets and variables available to workflows triggered by pull requests from forks.

* **`require_approval_for_fork_pr_workflows`** (boolean)
  Whether workflows triggered by pull requests from forks require approval from a repository administrator to run.

### HTTP response status codes

* **204** - Empty response for successful settings update

* **403** - Forbidden - Fork PR workflow settings for private repositories are managed by the enterprise owner

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/fork-pr-workflows-private-repos \
  -d '{
  "run_workflows_from_fork_pull_requests": true,
  "send_write_tokens_to_workflows": false,
  "send_secrets_and_variables": false,
  "require_approval_for_fork_pr_workflows": true
}'
```

**Response schema (Status: 204):**

## List selected repositories enabled for GitHub Actions in an organization

```
GET /orgs/{org}/actions/permissions/repositories
```

Lists the selected repositories that are enabled for GitHub Actions in an organization. To use this endpoint, the organization permission policy for enabled\_repositories must be configured to selected. For more information, see "Set GitHub Actions permissions for an organization."
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

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/permissions/repositories
```

**Response schema (Status: 200):**

* `total_count`: required, number
* `repositories`: required, array of `Repository`:
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

## Set selected repositories enabled for GitHub Actions in an organization

```
PUT /orgs/{org}/actions/permissions/repositories
```

Replaces the list of selected repositories that are enabled for GitHub Actions in an organization. To use this endpoint, the organization permission policy for enabled\_repositories must be configured to selected. For more information, see "Set GitHub Actions permissions for an organization."
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`selected_repository_ids`** (array of integers) (required)
  List of repository IDs to enable for GitHub Actions.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/repositories \
  -d '{
  "selected_repository_ids": [
    32,
    42
  ]
}'
```

**Response schema (Status: 204):**

## Enable a selected repository for GitHub Actions in an organization

```
PUT /orgs/{org}/actions/permissions/repositories/{repository_id}
```

Adds a repository to the list of selected repositories that are enabled for GitHub Actions in an organization. To use this endpoint, the organization permission policy for enabled\_repositories must be must be configured to selected. For more information, see "Set GitHub Actions permissions for an organization."
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/actions/permissions/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**

## Disable a selected repository for GitHub Actions in an organization

```
DELETE /orgs/{org}/actions/permissions/repositories/{repository_id}
```

Removes a repository from the list of selected repositories that are enabled for GitHub Actions in an organization. To use this endpoint, the organization permission policy for enabled\_repositories must be configured to selected. For more information, see "Set GitHub Actions permissions for an organization."
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/actions/permissions/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**

## Get allowed actions and reusable workflows for an organization

```
GET /orgs/{org}/actions/permissions/selected-actions
```

Gets the selected actions and reusable workflows that are allowed in an organization. To use this endpoint, the organization permission policy for allowed\_actions must be configured to selected. For more information, see "Set GitHub Actions permissions for an organization."
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/permissions/selected-actions
```

**Response schema (Status: 200):**

* `github_owned_allowed`: boolean
* `verified_allowed`: boolean
* `patterns_allowed`: array of string

## Set allowed actions and reusable workflows for an organization

```
PUT /orgs/{org}/actions/permissions/selected-actions
```

Sets the actions and reusable workflows that are allowed in an organization. To use this endpoint, the organization permission policy for allowed\_actions must be configured to selected. For more information, see "Set GitHub Actions permissions for an organization."
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`github_owned_allowed`** (boolean)
  Whether GitHub-owned actions are allowed. For example, this includes the actions in the actions organization.

* **`verified_allowed`** (boolean)
  Whether actions from GitHub Marketplace verified creators are allowed. Set to true to allow all actions by GitHub Marketplace verified creators.

* **`patterns_allowed`** (array of strings)
  Specifies a list of string-matching patterns to allow specific action(s) and reusable workflow(s). Wildcards, tags, and SHAs are allowed. For example, monalisa/octocat@*, monalisa/octocat\@v2, monalisa/*.
  Note

The patterns\_allowed setting only applies to public repositories.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/selected-actions \
  -d '{
  "github_owned_allowed": true,
  "verified_allowed": false,
  "patterns_allowed": [
    "monalisa/octocat@*",
    "docker/*"
  ]
}'
```

**Response schema (Status: 204):**

## Get self-hosted runners settings for an organization

```
GET /orgs/{org}/actions/permissions/self-hosted-runners
```

Gets the settings for self-hosted runners for an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/actions/permissions/self-hosted-runners
```

**Response schema (Status: 200):**

* `enabled_repositories`: required, string, enum: `all`, `selected`, `none`
* `selected_repositories_url`: string

## Set self-hosted runners settings for an organization

```
PUT /orgs/{org}/actions/permissions/self-hosted-runners
```

Sets the settings for self-hosted runners for an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`enabled_repositories`** (string) (required)
  The policy that controls whether self-hosted runners can be used in the organization
  Can be one of: `all`, `selected`, `none`

### HTTP response status codes

* **204** - No content

* **403** - Forbidden

* **404** - Resource not found

* **409** - Conflict

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/self-hosted-runners \
  -d '{
  "enabled_repositories": "all"
}'
```

**Response schema (Status: 204):**

## List repositories allowed to use self-hosted runners in an organization

```
GET /orgs/{org}/actions/permissions/self-hosted-runners/repositories
```

Lists repositories that are allowed to use self-hosted runners in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

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
  https://api.github.com/orgs/ORG/actions/permissions/self-hosted-runners/repositories
```

**Response schema (Status: 200):**

* `total_count`: integer
* `repositories`: array of `Repository`:
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

## Set repositories allowed to use self-hosted runners in an organization

```
PUT /orgs/{org}/actions/permissions/self-hosted-runners/repositories
```

Sets repositories that are allowed to use self-hosted runners in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`selected_repository_ids`** (array of integers) (required)
  IDs of repositories that can use repository-level self-hosted runners

### HTTP response status codes

* **204** - No content

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/self-hosted-runners/repositories \
  -d '{
  "selected_repository_ids": [
    1,
    2,
    3
  ]
}'
```

**Response schema (Status: 204):**

## Add a repository to the list of repositories allowed to use self-hosted runners in an organization

```
PUT /orgs/{org}/actions/permissions/self-hosted-runners/repositories/{repository_id}
```

Adds a repository to the list of repositories that are allowed to use self-hosted runners in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`repository_id`** (integer) (required)
  The unique identifier of the repository.

### HTTP response status codes

* **204** - No content

* **403** - Forbidden

* **404** - Resource not found

* **409** - Conflict

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/self-hosted-runners/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**

## Remove a repository from the list of repositories allowed to use self-hosted runners in an organization

```
DELETE /orgs/{org}/actions/permissions/self-hosted-runners/repositories/{repository_id}
```

Removes a repository from the list of repositories that are allowed to use self-hosted runners in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope or the "Actions policies" fine-grained permission to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`repository_id`** (integer) (required)
  The unique identifier of the repository.

### HTTP response status codes

* **204** - No content

* **403** - Forbidden

* **404** - Resource not found

* **409** - Conflict

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/permissions/self-hosted-runners/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**

## Get default workflow permissions for an organization

```
GET /orgs/{org}/actions/permissions/workflow
```

Gets the default workflow permissions granted to the GITHUB\_TOKEN when running workflows in an organization,
as well as whether GitHub Actions can submit approving pull request reviews. For more information, see
"Setting the permissions of the GITHUB\_TOKEN for your organization."
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/permissions/workflow
```

**Response schema (Status: 200):**

* `default_workflow_permissions`: required, string, enum: `read`, `write`
* `can_approve_pull_request_reviews`: required, boolean

## Set default workflow permissions for an organization

```
PUT /orgs/{org}/actions/permissions/workflow
```

Sets the default workflow permissions granted to the GITHUB\_TOKEN when running workflows in an organization, and sets if GitHub Actions
can submit approving pull request reviews. For more information, see
"Setting the permissions of the GITHUB\_TOKEN for your organization."
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`default_workflow_permissions`** (string)
  The default workflow permissions granted to the GITHUB\_TOKEN when running workflows.
  Can be one of: `read`, `write`

* **`can_approve_pull_request_reviews`** (boolean)
  Whether GitHub Actions can approve pull requests. Enabling this can be a security risk.

### HTTP response status codes

* **204** - Success response

### Code examples

#### Give read-only permission, and allow approving PRs.

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/permissions/workflow \
  -d '{
  "default_workflow_permissions": "read",
  "can_approve_pull_request_reviews": true
}'
```

**Response schema (Status: 204):**

## Get GitHub Actions permissions for a repository

```
GET /repos/{owner}/{repo}/actions/permissions
```

Gets the GitHub Actions permissions policy for a repository, including whether GitHub Actions is enabled and the actions and reusable workflows allowed to run in the repository.
OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/permissions
```

**Response schema (Status: 200):**

* `enabled`: required, boolean
* `allowed_actions`: string, enum: `all`, `local_only`, `selected`
* `selected_actions_url`: string
* `sha_pinning_required`: boolean

## Set GitHub Actions permissions for a repository

```
PUT /repos/{owner}/{repo}/actions/permissions
```

Sets the GitHub Actions permissions policy for enabling GitHub Actions and allowed actions and reusable workflows in the repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`enabled`** (boolean) (required)
  Whether GitHub Actions is enabled on the repository.

* **`allowed_actions`** (string)
  The permissions policy that controls the actions and reusable workflows that are allowed to run.
  Can be one of: `all`, `local_only`, `selected`

* **`sha_pinning_required`** (boolean)
  Whether actions must be pinned to a full-length commit SHA.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/permissions \
  -d '{
  "enabled": true,
  "allowed_actions": "selected",
  "sha_pinning_required": true
}'
```

**Response schema (Status: 204):**

## Get the level of access for workflows outside of the repository

```
GET /repos/{owner}/{repo}/actions/permissions/access
```

Gets the level of access that workflows outside of the repository have to actions and reusable workflows in the repository.
This endpoint only applies to private repositories.
For more information, see "Allowing access to components in a private repository."
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/access
```

**Response schema (Status: 200):**

* `access_level`: required, string, enum: `none`, `user`, `organization`

## Set the level of access for workflows outside of the repository

```
PUT /repos/{owner}/{repo}/actions/permissions/access
```

Sets the level of access that workflows outside of the repository have to actions and reusable workflows in the repository.
This endpoint only applies to private repositories.
For more information, see "Allowing access to components in a private repository".
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`access_level`** (string) (required)
  Defines the level of access that workflows outside of the repository have to actions and reusable workflows within the
  repository.
  none means the access is only possible from workflows in this repository. user level access allows sharing across user owned private repositories only. organization level access allows sharing across the organization.
  Can be one of: `none`, `user`, `organization`

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/access \
  -d '{
  "access_level": "organization"
}'
```

**Response schema (Status: 204):**

## Get artifact and log retention settings for a repository

```
GET /repos/{owner}/{repo}/actions/permissions/artifact-and-log-retention
```

Gets artifact and log retention settings for a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/artifact-and-log-retention
```

**Response schema (Status: 200):**

Same response schema as [Get artifact and log retention settings for an organization](#get-artifact-and-log-retention-settings-for-an-organization).

## Set artifact and log retention settings for a repository

```
PUT /repos/{owner}/{repo}/actions/permissions/artifact-and-log-retention
```

Sets artifact and log retention settings for a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`days`** (integer) (required)
  The number of days to retain artifacts and logs

### HTTP response status codes

* **204** - Empty response for successful settings update

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Set retention days

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/artifact-and-log-retention \
  -d '{
  "days": 90
}'
```

**Response schema (Status: 204):**

## Get fork PR contributor approval permissions for a repository

```
GET /repos/{owner}/{repo}/actions/permissions/fork-pr-contributor-approval
```

Gets the fork PR contributor approval policy for a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/fork-pr-contributor-approval
```

**Response schema (Status: 200):**

Same response schema as [Get fork PR contributor approval permissions for an organization](#get-fork-pr-contributor-approval-permissions-for-an-organization).

## Set fork PR contributor approval permissions for a repository

```
PUT /repos/{owner}/{repo}/actions/permissions/fork-pr-contributor-approval
```

Sets the fork PR contributor approval policy for a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`approval_policy`** (string) (required)
  The policy that controls when fork PR workflows require approval from a maintainer.
  Can be one of: `first_time_contributors_new_to_github`, `first_time_contributors`, `all_external_contributors`

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Set approval policy to first time contributors

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/fork-pr-contributor-approval \
  -d '{
  "approval_policy": "first_time_contributors"
}'
```

**Response schema (Status: 204):**

## Get private repo fork PR workflow settings for a repository

```
GET /repos/{owner}/{repo}/actions/permissions/fork-pr-workflows-private-repos
```

Gets the settings for whether workflows from fork pull requests can run on a private repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

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
  https://api.github.com/repos/OWNER/REPO/actions/permissions/fork-pr-workflows-private-repos
```

**Response schema (Status: 200):**

Same response schema as [Get private repo fork PR workflow settings for an organization](#get-private-repo-fork-pr-workflow-settings-for-an-organization).

## Set private repo fork PR workflow settings for a repository

```
PUT /repos/{owner}/{repo}/actions/permissions/fork-pr-workflows-private-repos
```

Sets the settings for whether workflows from fork pull requests can run on a private repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`run_workflows_from_fork_pull_requests`** (boolean) (required)
  Whether workflows triggered by pull requests from forks are allowed to run on private repositories.

* **`send_write_tokens_to_workflows`** (boolean)
  Whether GitHub Actions can create pull requests or submit approving pull request reviews from a workflow triggered by a fork pull request.

* **`send_secrets_and_variables`** (boolean)
  Whether to make secrets and variables available to workflows triggered by pull requests from forks.

* **`require_approval_for_fork_pr_workflows`** (boolean)
  Whether workflows triggered by pull requests from forks require approval from a repository administrator to run.

### HTTP response status codes

* **204** - Empty response for successful settings update

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/fork-pr-workflows-private-repos \
  -d '{
  "run_workflows_from_fork_pull_requests": true,
  "send_write_tokens_to_workflows": false,
  "send_secrets_and_variables": false,
  "require_approval_for_fork_pr_workflows": true
}'
```

**Response schema (Status: 204):**

## Get allowed actions and reusable workflows for a repository

```
GET /repos/{owner}/{repo}/actions/permissions/selected-actions
```

Gets the settings for selected actions and reusable workflows that are allowed in a repository. To use this endpoint, the repository policy for allowed\_actions must be configured to selected. For more information, see "Set GitHub Actions permissions for a repository."
OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/selected-actions
```

**Response schema (Status: 200):**

Same response schema as [Get allowed actions and reusable workflows for an organization](#get-allowed-actions-and-reusable-workflows-for-an-organization).

## Set allowed actions and reusable workflows for a repository

```
PUT /repos/{owner}/{repo}/actions/permissions/selected-actions
```

Sets the actions and reusable workflows that are allowed in a repository. To use this endpoint, the repository permission policy for allowed\_actions must be configured to selected. For more information, see "Set GitHub Actions permissions for a repository."
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`github_owned_allowed`** (boolean)
  Whether GitHub-owned actions are allowed. For example, this includes the actions in the actions organization.

* **`verified_allowed`** (boolean)
  Whether actions from GitHub Marketplace verified creators are allowed. Set to true to allow all actions by GitHub Marketplace verified creators.

* **`patterns_allowed`** (array of strings)
  Specifies a list of string-matching patterns to allow specific action(s) and reusable workflow(s). Wildcards, tags, and SHAs are allowed. For example, monalisa/octocat@*, monalisa/octocat\@v2, monalisa/*.
  Note

The patterns\_allowed setting only applies to public repositories.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/selected-actions \
  -d '{
  "github_owned_allowed": true,
  "verified_allowed": false,
  "patterns_allowed": [
    "monalisa/octocat@*",
    "docker/*"
  ]
}'
```

**Response schema (Status: 204):**

## Get default workflow permissions for a repository

```
GET /repos/{owner}/{repo}/actions/permissions/workflow
```

Gets the default workflow permissions granted to the GITHUB\_TOKEN when running workflows in a repository,
as well as if GitHub Actions can submit approving pull request reviews.
For more information, see "Setting the permissions of the GITHUB\_TOKEN for your repository."
OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/workflow
```

**Response schema (Status: 200):**

Same response schema as [Get default workflow permissions for an organization](#get-default-workflow-permissions-for-an-organization).

## Set default workflow permissions for a repository

```
PUT /repos/{owner}/{repo}/actions/permissions/workflow
```

Sets the default workflow permissions granted to the GITHUB\_TOKEN when running workflows in a repository, and sets if GitHub Actions
can submit approving pull request reviews.
For more information, see "Setting the permissions of the GITHUB\_TOKEN for your repository."
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`default_workflow_permissions`** (string)
  The default workflow permissions granted to the GITHUB\_TOKEN when running workflows.
  Can be one of: `read`, `write`

* **`can_approve_pull_request_reviews`** (boolean)
  Whether GitHub Actions can approve pull requests. Enabling this can be a security risk.

### HTTP response status codes

* **204** - Success response

* **409** - Conflict response when changing a setting is prevented by the owning organization

### Code examples

#### Give read-only permission, and allow approving PRs.

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/permissions/workflow \
  -d '{
  "default_workflow_permissions": "read",
  "can_approve_pull_request_reviews": true
}'
```

**Response schema (Status: 204):**