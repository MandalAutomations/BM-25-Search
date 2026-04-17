# REST API endpoints for self-hosted runners

Use the REST API to interact with self-hosted runners in GitHub Actions.

## About self-hosted runners in GitHub Actions

You can use the REST API to register, view, and delete self-hosted runners in GitHub Actions. Self-hosted runners allow you to host your own runners and customize the environment used to run jobs in your GitHub Actions workflows. For more information, see [Managing self-hosted runners](/en/actions/how-tos/managing-self-hosted-runners).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List self-hosted runners for an organization

```
GET /orgs/{org}/actions/runners
```

Lists all self-hosted runners configured in an organization.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint. If the repository is private, the repo scope is also required.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`name`** (string)
  The name of a self-hosted runner.

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
  https://api.github.com/orgs/ORG/actions/runners
```

**Response schema (Status: 200):**

* `total_count`: required, integer
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

## List runner applications for an organization

```
GET /orgs/{org}/actions/runners/downloads
```

Lists binaries for the runner application that you can download and run.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.  If the repository is private, the repo scope is also required.

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
  https://api.github.com/orgs/ORG/actions/runners/downloads
```

**Response schema (Status: 200):**

Array of `Runner Application`:

* `os`: required, string
* `architecture`: required, string
* `download_url`: required, string
* `filename`: required, string
* `temp_download_token`: string
* `sha256_checksum`: string

## Create configuration for a just-in-time runner for an organization

```
POST /orgs/{org}/actions/runners/generate-jitconfig
```

Generates a configuration that can be passed to the runner application at startup.
The authenticated user must have admin access to the organization.
OAuth tokens and personal access tokens (classic) need theadmin:org scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`name`** (string) (required)
  The name of the new runner.

* **`runner_group_id`** (integer) (required)
  The ID of the runner group to register the runner to.

* **`labels`** (array of strings) (required)
  The names of the custom labels to add to the runner. Minimum items: 1. Maximum items: 100.

* **`work_folder`** (string)
  The working directory to be used for job execution, relative to the runner install directory.
  Default: `_work`

### HTTP response status codes

* **201** - Created

* **404** - Resource not found

* **409** - Conflict

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/actions/runners/generate-jitconfig \
  -d '{
  "name": "New runner",
  "runner_group_id": 1,
  "labels": [
    "self-hosted",
    "X64",
    "macOS",
    "no-gpu"
  ],
  "work_folder": "_work"
}'
```

**Response schema (Status: 201):**

* `runner`: required, `Self hosted runners`:
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
* `encoded_jit_config`: required, string

## Create a registration token for an organization

```
POST /orgs/{org}/actions/runners/registration-token
```

Returns a token that you can pass to the config script. The token expires after one hour.
For example, you can replace TOKEN in the following example with the registration token provided by this endpoint to configure your self-hosted runner:
./config.sh --url <https://github.com/octo-org> --token TOKEN

Authenticated users must have admin access to the organization to use this endpoint.
OAuth tokens and personal access tokens (classic) need theadmin:org scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/actions/runners/registration-token
```

**Response schema (Status: 201):**

* `token`: required, string
* `expires_at`: required, string, format: date-time
* `permissions`: object
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
* `single_file`: string or null
* `repository_selection`: string, enum: `all`, `selected`

## Create a remove token for an organization

```
POST /orgs/{org}/actions/runners/remove-token
```

Returns a token that you can pass to the config script to remove a self-hosted runner from an organization. The token expires after one hour.
For example, you can replace TOKEN in the following example with the registration token provided by this endpoint to remove your self-hosted runner from an organization:
./config.sh remove --token TOKEN

Authenticated users must have admin access to the organization to use this endpoint.
OAuth tokens and personal access tokens (classic) need theadmin:org scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/actions/runners/remove-token
```

**Response schema (Status: 201):**

Same response schema as [Create a registration token for an organization](#create-a-registration-token-for-an-organization).

## Get a self-hosted runner for an organization

```
GET /orgs/{org}/actions/runners/{runner_id}
```

Gets a specific self-hosted runner configured in an organization.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint. If the repository is private, the repo scope is also required.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/runners/RUNNER_ID
```

**Response schema (Status: 200):**

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

## Delete a self-hosted runner from an organization

```
DELETE /orgs/{org}/actions/runners/{runner_id}
```

Forces the removal of a self-hosted runner from an organization. You can use this endpoint to completely remove the runner when the machine you were using no longer exists.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth tokens and personal access tokens (classic) need theadmin:org scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **204** - No Content

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/runners/RUNNER_ID
```

**Response schema (Status: 204):**

## List labels for a self-hosted runner for an organization

```
GET /orgs/{org}/actions/runners/{runner_id}/labels
```

Lists all labels for a self-hosted runner configured in an organization.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint. If the repository is private, the repo scope is also required.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/runners/RUNNER_ID/labels
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `labels`: required, array of `Self hosted runner label`:
  * `id`: integer
  * `name`: required, string
  * `type`: string, enum: `read-only`, `custom`

## Add custom labels to a self-hosted runner for an organization

```
POST /orgs/{org}/actions/runners/{runner_id}/labels
```

Adds custom labels to a self-hosted runner configured in an organization.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

#### Body parameters

* **`labels`** (array of strings) (required)
  The names of the custom labels to add to the runner.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/actions/runners/RUNNER_ID/labels \
  -d '{
  "labels": [
    "gpu",
    "accelerated"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).

## Set custom labels for a self-hosted runner for an organization

```
PUT /orgs/{org}/actions/runners/{runner_id}/labels
```

Remove all previous custom labels and set the new custom labels for a specific
self-hosted runner configured in an organization.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint. If the repository is private, the repo scope is also required.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

#### Body parameters

* **`labels`** (array of strings) (required)
  The names of the custom labels to set for the runner. You can pass an empty array to remove all custom labels.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/runners/RUNNER_ID/labels \
  -d '{
  "labels": [
    "gpu",
    "accelerated"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).

## Remove all custom labels from a self-hosted runner for an organization

```
DELETE /orgs/{org}/actions/runners/{runner_id}/labels
```

Remove all custom labels from a self-hosted runner configured in an
organization. Returns the remaining read-only labels from the runner.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint. If the repository is private, the repo scope is also required.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/runners/RUNNER_ID/labels
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).

## Remove a custom label from a self-hosted runner for an organization

```
DELETE /orgs/{org}/actions/runners/{runner_id}/labels/{name}
```

Remove a custom label from a self-hosted runner configured
in an organization. Returns the remaining labels from the runner.
This endpoint returns a 404 Not Found status if the custom label is not
present on the runner.
Authenticated users must have admin access to the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint. If the repository is private, the repo scope is also required.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

* **`name`** (string) (required)
  The name of a self-hosted runner's custom label.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/runners/RUNNER_ID/labels/NAME
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).

## List self-hosted runners for a repository

```
GET /repos/{owner}/{repo}/actions/runners
```

Lists all self-hosted runners configured in a repository.
Authenticated users must have admin access to the repository to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`name`** (string)
  The name of a self-hosted runner.

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

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
  https://api.github.com/repos/OWNER/REPO/actions/runners
```

**Response schema (Status: 200):**

Same response schema as [List self-hosted runners for an organization](#list-self-hosted-runners-for-an-organization).

## List runner applications for a repository

```
GET /repos/{owner}/{repo}/actions/runners/downloads
```

Lists binaries for the runner application that you can download and run.
Authenticated users must have admin access to the repository to use this endpoint.
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
  https://api.github.com/repos/OWNER/REPO/actions/runners/downloads
```

**Response schema (Status: 200):**

Same response schema as [List runner applications for an organization](#list-runner-applications-for-an-organization).

## Create configuration for a just-in-time runner for a repository

```
POST /repos/{owner}/{repo}/actions/runners/generate-jitconfig
```

Generates a configuration that can be passed to the runner application at startup.
The authenticated user must have admin access to the repository.
OAuth tokens and personal access tokens (classic) need therepo scope to use this endpoint.

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

* **`name`** (string) (required)
  The name of the new runner.

* **`runner_group_id`** (integer) (required)
  The ID of the runner group to register the runner to.

* **`labels`** (array of strings) (required)
  The names of the custom labels to add to the runner. Minimum items: 1. Maximum items: 100.

* **`work_folder`** (string)
  The working directory to be used for job execution, relative to the runner install directory.
  Default: `_work`

### HTTP response status codes

* **201** - Created

* **404** - Resource not found

* **409** - Conflict

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/actions/runners/generate-jitconfig \
  -d '{
  "name": "New runner",
  "runner_group_id": 1,
  "labels": [
    "self-hosted",
    "X64",
    "macOS",
    "no-gpu"
  ],
  "work_folder": "_work"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create configuration for a just-in-time runner for an organization](#create-configuration-for-a-just-in-time-runner-for-an-organization).

## Create a registration token for a repository

```
POST /repos/{owner}/{repo}/actions/runners/registration-token
```

Returns a token that you can pass to the config script. The token expires after one hour.
For example, you can replace TOKEN in the following example with the registration token provided by this endpoint to configure your self-hosted runner:
./config.sh --url <https://github.com/octo-org> --token TOKEN

Authenticated users must have admin access to the repository to use this endpoint.
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

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/actions/runners/registration-token
```

**Response schema (Status: 201):**

Same response schema as [Create a registration token for an organization](#create-a-registration-token-for-an-organization).

## Create a remove token for a repository

```
POST /repos/{owner}/{repo}/actions/runners/remove-token
```

Returns a token that you can pass to the config script to remove a self-hosted runner from an repository. The token expires after one hour.
For example, you can replace TOKEN in the following example with the registration token provided by this endpoint to remove your self-hosted runner from an organization:
./config.sh remove --token TOKEN

Authenticated users must have admin access to the repository to use this endpoint.
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

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/actions/runners/remove-token
```

**Response schema (Status: 201):**

Same response schema as [Create a registration token for an organization](#create-a-registration-token-for-an-organization).

## Get a self-hosted runner for a repository

```
GET /repos/{owner}/{repo}/actions/runners/{runner_id}
```

Gets a specific self-hosted runner configured in a repository.
Authenticated users must have admin access to the repository to use this endpoint.
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

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/runners/RUNNER_ID
```

**Response schema (Status: 200):**

Same response schema as [Get a self-hosted runner for an organization](#get-a-self-hosted-runner-for-an-organization).

## Delete a self-hosted runner from a repository

```
DELETE /repos/{owner}/{repo}/actions/runners/{runner_id}
```

Forces the removal of a self-hosted runner from a repository. You can use this endpoint to completely remove the runner when the machine you were using no longer exists.
Authenticated users must have admin access to the repository to use this endpoint.
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

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **204** - No Content

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/actions/runners/RUNNER_ID
```

**Response schema (Status: 204):**

## List labels for a self-hosted runner for a repository

```
GET /repos/{owner}/{repo}/actions/runners/{runner_id}/labels
```

Lists all labels for a self-hosted runner configured in a repository.
Authenticated users must have admin access to the repository to use this endpoint.
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

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/runners/RUNNER_ID/labels
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).

## Add custom labels to a self-hosted runner for a repository

```
POST /repos/{owner}/{repo}/actions/runners/{runner_id}/labels
```

Adds custom labels to a self-hosted runner configured in a repository.
Authenticated users must have admin access to the organization to use this endpoint.
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

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

#### Body parameters

* **`labels`** (array of strings) (required)
  The names of the custom labels to add to the runner.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/actions/runners/RUNNER_ID/labels \
  -d '{
  "labels": [
    "gpu",
    "accelerated"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).

## Set custom labels for a self-hosted runner for a repository

```
PUT /repos/{owner}/{repo}/actions/runners/{runner_id}/labels
```

Remove all previous custom labels and set the new custom labels for a specific
self-hosted runner configured in a repository.
Authenticated users must have admin access to the repository to use this endpoint.
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

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

#### Body parameters

* **`labels`** (array of strings) (required)
  The names of the custom labels to set for the runner. You can pass an empty array to remove all custom labels.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/runners/RUNNER_ID/labels \
  -d '{
  "labels": [
    "gpu",
    "accelerated"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).

## Remove all custom labels from a self-hosted runner for a repository

```
DELETE /repos/{owner}/{repo}/actions/runners/{runner_id}/labels
```

Remove all custom labels from a self-hosted runner configured in a
repository. Returns the remaining read-only labels from the runner.
Authenticated users must have admin access to the repository to use this endpoint.
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

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/actions/runners/RUNNER_ID/labels
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).

## Remove a custom label from a self-hosted runner for a repository

```
DELETE /repos/{owner}/{repo}/actions/runners/{runner_id}/labels/{name}
```

Remove a custom label from a self-hosted runner configured
in a repository. Returns the remaining labels from the runner.
This endpoint returns a 404 Not Found status if the custom label is not
present on the runner.
Authenticated users must have admin access to the repository to use this endpoint.
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

* **`runner_id`** (integer) (required)
  Unique identifier of the self-hosted runner.

* **`name`** (string) (required)
  The name of a self-hosted runner's custom label.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/actions/runners/RUNNER_ID/labels/NAME
```

**Response schema (Status: 200):**

Same response schema as [List labels for a self-hosted runner for an organization](#list-labels-for-a-self-hosted-runner-for-an-organization).