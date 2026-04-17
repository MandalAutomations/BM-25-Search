# REST API endpoints for organization migrations

Use the REST API to export one or more repositories so you can move them to  GitHub Enterprise Server.

## About organization migrations

These endpoints are only available to authenticated organization owners. For more information, see [Roles in an organization](/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#permission-levels-for-an-organization) and [Authenticating to the REST API](/en/rest/overview/authenticating-to-the-rest-api).

You can use these endpoints to export one or more repositories so you can move them to a GitHub Enterprise Server instance. For more information, see [Exporting migration data from GitHub.com](/en/migrations/using-ghe-migrator/exporting-migration-data-from-githubcom).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List organization migrations

```
GET /orgs/{org}/migrations
```

Lists the most recent migrations, including both exports (which can be started through the REST API) and imports (which cannot be started using the REST API).
A list of repositories is only returned for export migrations.

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

* **`exclude`** (array)
  Exclude attributes from the API response to improve performance

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/migrations
```

**Response schema (Status: 200):**

Array of `Migration`:

* `id`: required, integer, format: int64
* `owner`: required, any of:
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
* `guid`: required, string
* `state`: required, string
* `lock_repositories`: required, boolean
* `exclude_metadata`: required, boolean
* `exclude_git_data`: required, boolean
* `exclude_attachments`: required, boolean
* `exclude_releases`: required, boolean
* `exclude_owner_projects`: required, boolean
* `org_metadata_only`: required, boolean
* `repositories`: required, array of `Simple Repository`:
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
  * `stargazers_url`: required, string, format: uri
  * `statuses_url`: required, string
  * `subscribers_url`: required, string, format: uri
  * `subscription_url`: required, string, format: uri
  * `tags_url`: required, string, format: uri
  * `teams_url`: required, string, format: uri
  * `trees_url`: required, string
  * `hooks_url`: required, string, format: uri
* `url`: required, string, format: uri
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `node_id`: required, string
* `archive_url`: string, format: uri
* `exclude`: array of string

## Start an organization migration

```
POST /orgs/{org}/migrations
```

Initiates the generation of a migration archive.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`repositories`** (array of strings) (required)
  A list of arrays indicating which repositories should be migrated.

* **`lock_repositories`** (boolean)
  Indicates whether repositories should be locked (to prevent manipulation) while migrating data.
  Default: `false`

* **`exclude_metadata`** (boolean)
  Indicates whether metadata should be excluded and only git source should be included for the migration.
  Default: `false`

* **`exclude_git_data`** (boolean)
  Indicates whether the repository git data should be excluded from the migration.
  Default: `false`

* **`exclude_attachments`** (boolean)
  Indicates whether attachments should be excluded from the migration (to reduce migration archive file size).
  Default: `false`

* **`exclude_releases`** (boolean)
  Indicates whether releases should be excluded from the migration (to reduce migration archive file size).
  Default: `false`

* **`exclude_owner_projects`** (boolean)
  Indicates whether projects owned by the organization or users should be excluded. from the migration.
  Default: `false`

* **`org_metadata_only`** (boolean)
  Indicates whether this should only include organization metadata (repositories array should be empty and will ignore other flags).
  Default: `false`

* **`exclude`** (array of strings)
  Exclude related items from being returned in the response in order to improve performance of the request.
  Supported values are: repositories

### HTTP response status codes

* **201** - Created

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/migrations \
  -d '{
  "repositories": [
    "github/Hello-World"
  ],
  "lock_repositories": true
}'
```

**Response schema (Status: 201):**

* `id`: required, integer, format: int64
* `owner`: required, any of:
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
* `guid`: required, string
* `state`: required, string
* `lock_repositories`: required, boolean
* `exclude_metadata`: required, boolean
* `exclude_git_data`: required, boolean
* `exclude_attachments`: required, boolean
* `exclude_releases`: required, boolean
* `exclude_owner_projects`: required, boolean
* `org_metadata_only`: required, boolean
* `repositories`: required, array of `Simple Repository`:
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
  * `stargazers_url`: required, string, format: uri
  * `statuses_url`: required, string
  * `subscribers_url`: required, string, format: uri
  * `subscription_url`: required, string, format: uri
  * `tags_url`: required, string, format: uri
  * `teams_url`: required, string, format: uri
  * `trees_url`: required, string
  * `hooks_url`: required, string, format: uri
* `url`: required, string, format: uri
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `node_id`: required, string
* `archive_url`: string, format: uri
* `exclude`: array of string

## Get an organization migration status

```
GET /orgs/{org}/migrations/{migration_id}
```

Fetches the status of a migration.
The state of a migration can be one of the following values:

pending, which means the migration hasn't started yet.
exporting, which means the migration is in progress.
exported, which means the migration finished successfully.
failed, which means the migration failed.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

* **`exclude`** (array)
  Exclude attributes from the API response to improve performance

### HTTP response status codes

* **200** - pending, which means the migration hasn't started yet.
  exporting, which means the migration is in progress.
  exported, which means the migration finished successfully.
  failed, which means the migration failed.

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/migrations/MIGRATION_ID
```

**Response schema (Status: 200):**

Same response schema as [Start an organization migration](#start-an-organization-migration).

## Download an organization migration archive

```
GET /orgs/{org}/migrations/{migration_id}/archive
```

Fetches the URL to a migration archive.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

### HTTP response status codes

* **302** - Found

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/migrations/MIGRATION_ID/archive
```

**Response schema (Status: 302):**

## Delete an organization migration archive

```
DELETE /orgs/{org}/migrations/{migration_id}/archive
```

Deletes a previous migration archive. Migration archives are automatically deleted after seven days.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/migrations/MIGRATION_ID/archive
```

**Response schema (Status: 204):**

## Unlock an organization repository

```
DELETE /orgs/{org}/migrations/{migration_id}/repos/{repo_name}/lock
```

Unlocks a repository that was locked for migration. You should unlock each migrated repository and delete them when the migration is complete and you no longer need the source data.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

* **`repo_name`** (string) (required)
  repo\_name parameter

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/migrations/MIGRATION_ID/repos/REPO_NAME/lock
```

**Response schema (Status: 204):**

## List repositories in an organization migration

```
GET /orgs/{org}/migrations/{migration_id}/repositories
```

List all the repositories for this organization migration.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

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
  https://api.github.com/orgs/ORG/migrations/MIGRATION_ID/repositories
```

**Response schema (Status: 200):**