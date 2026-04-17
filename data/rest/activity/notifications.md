# REST API endpoints for notifications

Use the REST API to manage GitHub notifications.

## About GitHub notifications

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

You can use the REST API to manage GitHub notifications. For more information about notifications, see [About notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/about-notifications).

All calls to these endpoints require the `notifications` or `repo` scopes. You will need the `repo` scope to access issues and commits from their respective endpoints.

Notifications are returned as "threads". A thread contains information about the current discussion of an issue, pull request, or commit.

Notifications are optimized for polling with the `Last-Modified` header. If there are no new notifications, you will see a `304 Not Modified` response, leaving your current rate limit untouched. There is an `X-Poll-Interval` header that specifies how often (in seconds) you are allowed to poll. In times of high server load, the time may increase. Please obey the header.

```shell
# Add authentication to your requests
$ curl -I https://api.github.com/notifications
HTTP/2 200
Last-Modified: Thu, 25 Oct 2012 15:16:27 GMT
X-Poll-Interval: 60

# Pass the Last-Modified header exactly
$ curl -I https://api.github.com/notifications
$    -H "If-Modified-Since: Thu, 25 Oct 2012 15:16:27 GMT"
> HTTP/2 304
> X-Poll-Interval: 60
```

### About notification reasons

These GET endpoints return a `reason` key. These `reason`s correspond to events that trigger a notification.

There are a few potential `reason`s for receiving a notification.

| Reason Name                | Description                                                                                                                                                         |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `approval_requested`       | You were requested to review and approve a deployment. For more information, see [Reviewing deployments](/en/actions/managing-workflow-runs/reviewing-deployments). |
| `assign`                   | You were assigned to the issue.                                                                                                                                     |
| `author`                   | You created the thread.                                                                                                                                             |
| `ci_activity`              | A GitHub Actions workflow run that you triggered was completed.                                                                                                     |
| `comment`                  | You commented on the thread.                                                                                                                                        |
| `invitation`               | You accepted an invitation to contribute to the repository.                                                                                                         |
| `manual`                   | You subscribed to the thread (via an issue or pull request).                                                                                                        |
| `member_feature_requested` | Organization members have requested to enable a feature such as Copilot.                                                                                            |
| `mention`                  | You were specifically **@mentioned** in the content.                                                                                                                |
| `review_requested`         | You, or a team you're a member of, were requested to review a pull request.                                                                                         |
| `security_advisory_credit` | You were credited for contributing to a security advisory.                                                                                                          |
| `security_alert`           | GitHub discovered a [security vulnerability](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts) in your repository.                            |
| `state_change`             | You changed the thread state (for example, closing an issue or merging a pull request).                                                                             |
| `subscribed`               | You're watching the repository.                                                                                                                                     |
| `team_mention`             | You were on a team that was mentioned.                                                                                                                              |

Note that the `reason` is modified on a per-thread basis, and can change, if the `reason` on a later notification is different.

For example, if you are the author of an issue, subsequent notifications on that issue will have a `reason` of `author`. If you're then **@mentioned** on the same issue, the notifications you fetch thereafter will have a `reason` of `mention`. The `reason` remains as `mention`, regardless of whether you're ever mentioned again.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List notifications for the authenticated user

```
GET /notifications
```

List all notifications for the current user, sorted by most recently updated.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`all`** (boolean)
  If true, show notifications marked as read.
  Default: `false`

* **`participating`** (boolean)
  If true, only shows notifications in which the user is directly participating or mentioned.
  Default: `false`

* **`since`** (string)
  Only show results that were last updated after the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

* **`before`** (string)
  Only show notifications updated before the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 50). For more information, see "Using pagination in the REST API."
  Default: `50`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/notifications
```

**Response schema (Status: 200):**

Array of `Thread`:

* `id`: required, string
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
* `subject`: required, object:
  * `title`: required, string
  * `url`: required, string
  * `latest_comment_url`: required, string
  * `type`: required, string
* `reason`: required, string
* `unread`: required, boolean
* `updated_at`: required, string
* `last_read_at`: required, string or null
* `url`: required, string
* `subscription_url`: required, string

## Mark notifications as read

```
PUT /notifications
```

Marks all notifications as "read" for the current user. If the number of notifications is too large to complete in one request, you will receive a 202 Accepted status and GitHub will run an asynchronous process to mark notifications as "read." To check whether any "unread" notifications remain, you can use the List notifications for the authenticated user endpoint and pass the query parameter all=false.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`last_read_at`** (string)
  Describes the last point that notifications were checked. Anything updated since this time will not be marked as read. If you omit this parameter, all notifications are marked as read. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ. Default: The current timestamp.

* **`read`** (boolean)
  Whether the notification has been read.

### HTTP response status codes

* **202** - Accepted

* **205** - Reset Content

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/notifications \
  -d '{
  "last_read_at": "2022-06-10T00:00:00Z",
  "read": true
}'
```

**Response schema (Status: 202):**

* `message`: string

## Get a thread

```
GET /notifications/threads/{thread_id}
```

Gets information about a notification thread.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`thread_id`** (integer) (required)
  The unique identifier of the notification thread. This corresponds to the value returned in the id field when you retrieve notifications (for example with the GET /notifications operation).

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
  https://api.github.com/notifications/threads/THREAD_ID
```

**Response schema (Status: 200):**

* `id`: required, string
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
* `subject`: required, object:
  * `title`: required, string
  * `url`: required, string
  * `latest_comment_url`: required, string
  * `type`: required, string
* `reason`: required, string
* `unread`: required, boolean
* `updated_at`: required, string
* `last_read_at`: required, string or null
* `url`: required, string
* `subscription_url`: required, string

## Mark a thread as read

```
PATCH /notifications/threads/{thread_id}
```

Marks a thread as "read." Marking a thread as "read" is equivalent to clicking a notification in your notification inbox on GitHub: <https://github.com/notifications>.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`thread_id`** (integer) (required)
  The unique identifier of the notification thread. This corresponds to the value returned in the id field when you retrieve notifications (for example with the GET /notifications operation).

### HTTP response status codes

* **205** - Reset Content

* **304** - Not modified

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/notifications/threads/THREAD_ID
```

**Response schema (Status: 205):**

## Mark a thread as done

```
DELETE /notifications/threads/{thread_id}
```

Marks a thread as "done." Marking a thread as "done" is equivalent to marking a notification in your notification inbox on GitHub as done: <https://github.com/notifications>.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`thread_id`** (integer) (required)
  The unique identifier of the notification thread. This corresponds to the value returned in the id field when you retrieve notifications (for example with the GET /notifications operation).

### HTTP response status codes

* **204** - No content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/notifications/threads/THREAD_ID
```

**Response schema (Status: 204):**

## Get a thread subscription for the authenticated user

```
GET /notifications/threads/{thread_id}/subscription
```

This checks to see if the current user is subscribed to a thread. You can also get a repository subscription.
Note that subscriptions are only generated if a user is participating in a conversation--for example, they've replied to the thread, were @mentioned, or manually subscribe to a thread.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`thread_id`** (integer) (required)
  The unique identifier of the notification thread. This corresponds to the value returned in the id field when you retrieve notifications (for example with the GET /notifications operation).

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
  https://api.github.com/notifications/threads/THREAD_ID/subscription
```

**Response schema (Status: 200):**

* `subscribed`: required, boolean
* `ignored`: required, boolean
* `reason`: required, string or null
* `created_at`: required, string or null, format: date-time
* `url`: required, string, format: uri
* `thread_url`: string, format: uri
* `repository_url`: string, format: uri

## Set a thread subscription

```
PUT /notifications/threads/{thread_id}/subscription
```

If you are watching a repository, you receive notifications for all threads by default. Use this endpoint to ignore future notifications for threads until you comment on the thread or get an @mention.
You can also use this endpoint to subscribe to threads that you are currently not receiving notifications for or to subscribed to threads that you have previously ignored.
Unsubscribing from a conversation in a repository that you are not watching is functionally equivalent to the Delete a thread subscription endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`thread_id`** (integer) (required)
  The unique identifier of the notification thread. This corresponds to the value returned in the id field when you retrieve notifications (for example with the GET /notifications operation).

#### Body parameters

* **`ignored`** (boolean)
  Whether to block all notifications from a thread.
  Default: `false`

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
  -X PUT \
  https://api.github.com/notifications/threads/THREAD_ID/subscription \
  -d '{
  "ignored": false
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a thread subscription for the authenticated user](#get-a-thread-subscription-for-the-authenticated-user).

## Delete a thread subscription

```
DELETE /notifications/threads/{thread_id}/subscription
```

Mutes all future notifications for a conversation until you comment on the thread or get an @mention. If you are watching the repository of the thread, you will still receive notifications. To ignore future notifications for a repository you are watching, use the Set a thread subscription endpoint and set ignore to true.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`thread_id`** (integer) (required)
  The unique identifier of the notification thread. This corresponds to the value returned in the id field when you retrieve notifications (for example with the GET /notifications operation).

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/notifications/threads/THREAD_ID/subscription
```

**Response schema (Status: 204):**

## List repository notifications for the authenticated user

```
GET /repos/{owner}/{repo}/notifications
```

Lists all notifications for the current user in the specified repository.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`all`** (boolean)
  If true, show notifications marked as read.
  Default: `false`

* **`participating`** (boolean)
  If true, only shows notifications in which the user is directly participating or mentioned.
  Default: `false`

* **`since`** (string)
  Only show results that were last updated after the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

* **`before`** (string)
  Only show notifications updated before the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

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
  https://api.github.com/repos/OWNER/REPO/notifications
```

**Response schema (Status: 200):**

Same response schema as [List notifications for the authenticated user](#list-notifications-for-the-authenticated-user).

## Mark repository notifications as read

```
PUT /repos/{owner}/{repo}/notifications
```

Marks all notifications in a repository as "read" for the current user. If the number of notifications is too large to complete in one request, you will receive a 202 Accepted status and GitHub will run an asynchronous process to mark notifications as "read." To check whether any "unread" notifications remain, you can use the List repository notifications for the authenticated user endpoint and pass the query parameter all=false.

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

* **`last_read_at`** (string)
  Describes the last point that notifications were checked. Anything updated since this time will not be marked as read. If you omit this parameter, all notifications are marked as read. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ. Default: The current timestamp.

### HTTP response status codes

* **202** - Accepted

* **205** - Reset Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/notifications \
  -d '{
  "last_read_at": "2019-01-01T00:00:00Z"
}'
```

**Response schema (Status: 202):**

* `message`: string
* `url`: string