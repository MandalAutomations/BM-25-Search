# REST API endpoints for watching

Use the REST API to subscribe to notifications for activity in a repository.

## About watching

You can use the REST API to subscribe to notifications for activity in a repository. To bookmark a repository instead, see [REST API endpoints for starring](/en/rest/activity/starring).

### Watching versus starring

In August 2012, we [changed the way watching
works](https://github.com/blog/1204-notifications-stars) on GitHub. Some API
client applications may still be using the original "watcher" endpoints for accessing
this data. You should now use the "star" endpoints instead. For more information, [REST API endpoints for starring](/en/rest/activity/starring) and the [changelog post](https://developer.github.com/changes/2012-09-05-watcher-api/).

In responses from the REST API, `subscribers_count` corresponds to the number of watchers, whereas `watchers`, `watchers_count`, and `stargazers_count` correspond to the number of users that have starred a repository.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List watchers

```
GET /repos/{owner}/{repo}/subscribers
```

Lists the people watching the specified repository.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

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
  https://api.github.com/repos/OWNER/REPO/subscribers
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

## Get a repository subscription

```
GET /repos/{owner}/{repo}/subscription
```

Gets information about whether the authenticated user is subscribed to the repository.

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

* **200** - if you subscribe to the repository

* **403** - Forbidden

* **404** - Not Found if you don't subscribe to the repository

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/subscription
```

**Response schema (Status: 200):**

* `subscribed`: required, boolean
* `ignored`: required, boolean
* `reason`: required, string or null
* `created_at`: required, string, format: date-time
* `url`: required, string, format: uri
* `repository_url`: required, string, format: uri

## Set a repository subscription

```
PUT /repos/{owner}/{repo}/subscription
```

If you would like to watch a repository, set subscribed to true. If you would like to ignore notifications made within a repository, set ignored to true. If you would like to stop watching a repository, delete the repository's subscription completely.

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

* **`subscribed`** (boolean)
  Determines if notifications should be received from this repository.

* **`ignored`** (boolean)
  Determines if all notifications should be blocked from this repository.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/subscription \
  -d '{
  "subscribed": true,
  "ignored": false
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a repository subscription](#get-a-repository-subscription).

## Delete a repository subscription

```
DELETE /repos/{owner}/{repo}/subscription
```

This endpoint should only be used to stop watching a repository. To control whether or not you wish to receive notifications from a repository, set the repository's subscription manually.

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

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/subscription
```

**Response schema (Status: 204):**

## List repositories watched by the authenticated user

```
GET /user/subscriptions
```

Lists repositories the authenticated user is watching.

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
  https://api.github.com/user/subscriptions
```

**Response schema (Status: 200):**

Array of `Minimal Repository`:

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

## List repositories watched by a user

```
GET /users/{username}/subscriptions
```

Lists repositories a user is watching.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

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
  https://api.github.com/users/USERNAME/subscriptions
```

**Response schema (Status: 200):**

Same response schema as [List repositories watched by the authenticated user](#list-repositories-watched-by-the-authenticated-user).