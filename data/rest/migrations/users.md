# REST API endpoints for user migrations

Use the REST API to review, backup, or migrate your user data stored on GitHub.

## About user migrations

These endpoints are only available to authenticated account owners. For more information, see [Authenticating to the REST API](/en/rest/overview/authenticating-to-the-rest-api).

You can use these endpoints to review, backup, or migrate your user data stored on GitHub.com. For a list of migration data that you can download, see [Download a user migration archive](#download-a-user-migration-archive).

To download an archive, you'll need to start a user migration first. Once the status of the migration is `exported`, you can download the migration.

Once you've created a migration archive, it will be available to download for seven days. But, you can delete the user migration archive sooner if you'd like. You can unlock your repository when the migration is `exported` to begin using your repository again or delete the repository if you no longer need the source data.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List user migrations

```
GET /user/migrations
```

Lists all migrations a user has started.

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

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/migrations
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

## Start a user migration

```
POST /user/migrations
```

Initiates the generation of a user migration archive.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`lock_repositories`** (boolean)
  Lock the repositories being migrated at the start of the migration

* **`exclude_metadata`** (boolean)
  Indicates whether metadata should be excluded and only git source should be included for the migration.

* **`exclude_git_data`** (boolean)
  Indicates whether the repository git data should be excluded from the migration.

* **`exclude_attachments`** (boolean)
  Do not include attachments in the migration

* **`exclude_releases`** (boolean)
  Do not include releases in the migration

* **`exclude_owner_projects`** (boolean)
  Indicates whether projects owned by the organization or users should be excluded.

* **`org_metadata_only`** (boolean)
  Indicates whether this should only include organization metadata (repositories array should be empty and will ignore other flags).
  Default: `false`

* **`exclude`** (array of strings)
  Exclude attributes from the API response to improve performance
  Supported values are: repositories

* **`repositories`** (array of strings) (required)

### HTTP response status codes

* **201** - Created

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/migrations \
  -d '{
  "repositories": [
    "octocat/Hello-World"
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

## Get a user migration status

```
GET /user/migrations/{migration_id}
```

Fetches a single user migration. The response includes the state of the migration, which can be one of the following values:

pending - the migration hasn't started yet.
exporting - the migration is in progress.
exported - the migration finished successfully.
failed - the migration failed.

Once the migration has been exported you can download the migration archive.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

* **`exclude`** (array)

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/migrations/MIGRATION_ID
```

**Response schema (Status: 200):**

Same response schema as [Start a user migration](#start-a-user-migration).

## Download a user migration archive

```
GET /user/migrations/{migration_id}/archive
```

Fetches the URL to download the migration archive as a tar.gz file. Depending on the resources your repository uses, the migration archive can contain JSON files with data for these objects:

attachments
bases
commit\_comments
issue\_comments
issue\_events
issues
milestones
organizations
projects
protected\_branches
pull\_request\_reviews
pull\_requests
releases
repositories
review\_comments
schema
users

The archive will also contain an attachments directory that includes all attachment files uploaded to GitHub.com and a repositories directory that contains the repository's Git data.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

### HTTP response status codes

* **302** - Found

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

## Delete a user migration archive

```
DELETE /user/migrations/{migration_id}/archive
```

Deletes a previous migration archive. Downloadable migration archives are automatically deleted after seven days. Migration metadata, which is returned in the List user migrations and Get a user migration status endpoints, will continue to be available even after an archive is deleted.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/migrations/MIGRATION_ID/archive
```

**Response schema (Status: 204):**

## Unlock a user repository

```
DELETE /user/migrations/{migration_id}/repos/{repo_name}/lock
```

Unlocks a repository. You can lock repositories when you start a user migration. Once the migration is complete you can unlock each repository to begin using it again or delete the repository if you no longer need the source data. Returns a status of 404 Not Found if the repository is not locked.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`migration_id`** (integer) (required)
  The unique identifier of the migration.

* **`repo_name`** (string) (required)
  repo\_name parameter

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/migrations/MIGRATION_ID/repos/REPO_NAME/lock
```

**Response schema (Status: 204):**

## List repositories for a user migration

```
GET /user/migrations/{migration_id}/repositories
```

Lists all the repositories for this user migration.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

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
  https://api.github.com/user/migrations/MIGRATION_ID/repositories
```

**Response schema (Status: 200):**