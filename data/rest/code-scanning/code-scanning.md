# REST API endpoints for code scanning

Use the REST API to retrieve and update code scanning alerts from a repository.

## About code scanning

You can retrieve and update code scanning alerts from a repository. You can use the endpoints to create automated reports for the code scanning alerts in an organization or upload analysis results generated using offline code scanning tools. For more information, see [Find and fix code vulnerabilities](/en/code-security/code-scanning).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List code scanning alerts for an organization

```
GET /orgs/{org}/code-scanning/alerts
```

Lists code scanning alerts for the default branch for all eligible repositories in an organization. Eligible repositories are repositories that are owned by organizations that you own or for which you are a security manager. For more information, see "Managing security managers in your organization."
The authenticated user must be an owner or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the security\_events or repos cope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`tool_name`** (string)
  The name of a code scanning tool. Only results by this tool will be listed. You can specify the tool by using either tool\_name or tool\_guid, but not both.

* **`tool_guid`** (string,null)
  The GUID of a code scanning tool. Only results by this tool will be listed. Note that some code scanning tools may not include a GUID in their analysis data. You can specify the tool by using either tool\_guid or tool\_name, but not both.

* **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

* **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`state`** (string)
  If specified, only code scanning alerts with this state will be returned.
  Can be one of: `open`, `closed`, `dismissed`, `fixed`

* **`sort`** (string)
  The property by which to sort the results.
  Default: `created`
  Can be one of: `created`, `updated`

* **`severity`** (string)
  If specified, only code scanning alerts with this severity will be returned.
  Can be one of: `critical`, `high`, `medium`, `low`, `warning`, `note`, `error`

* **`assignees`** (string)
  Filter alerts by assignees. Provide a comma-separated list of user handles (e.g., octocat or octocat,hubot).
  Use \* to list alerts with at least one assignee or none to list alerts with no assignees.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/code-scanning/alerts
```

**Response schema (Status: 200):**

Array of objects:

* `number`: required, integer, read-only
* `created_at`: required, string, format: date-time, read-only
* `updated_at`: string, format: date-time, read-only
* `url`: required, string, format: uri, read-only
* `html_url`: required, string, format: uri, read-only
* `instances_url`: required, string, format: uri, read-only
* `state`: required, string or null, enum: `open`, `dismissed`, `fixed`, `null`
* `fixed_at`: string or null, format: date-time, read-only
* `dismissed_by`: required, any of:
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
* `dismissed_at`: required, string or null, format: date-time, read-only
* `dismissed_reason`: required, string or null, enum: `false positive`, `won't fix`, `used in tests`, `null`
* `dismissed_comment`: string or null, maxLength: 280
* `rule`: required, object:
  * `id`: string or null
  * `name`: string
  * `severity`: string or null, enum: `none`, `note`, `warning`, `error`, `null`
  * `security_severity_level`: string or null, enum: `low`, `medium`, `high`, `critical`, `null`
  * `description`: string
  * `full_description`: string
  * `tags`: array of string or null
  * `help`: string or null
  * `help_uri`: string or null
* `tool`: required, object:
  * `name`: string
  * `version`: string or null
  * `guid`: string or null
* `most_recent_instance`: required, object:
  * `ref`: string
  * `analysis_key`: string
  * `environment`: string
  * `category`: string
  * `state`: string or null, enum: `open`, `dismissed`, `fixed`, `null`
  * `commit_sha`: string
  * `message`: object:
    * `text`: string
    * `markdown`: string
  * `location`: object:
    * `path`: string
    * `start_line`: integer
    * `end_line`: integer
    * `start_column`: integer
    * `end_column`: integer
  * `html_url`: string
  * `classifications`: array of string or null, enum: `source`, `generated`, `test`, `library`, `null`
* `repository`: required, `Simple Repository`:
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
* `dismissal_approved_by`: any of:
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
* `assignees`: array of `Simple User`:
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

## List code scanning alerts for a repository

```
GET /repos/{owner}/{repo}/code-scanning/alerts
```

Lists code scanning alerts.
The response includes a most\_recent\_instance object.
This provides details of the most recent instance of this alert
for the default branch (or for the specified Git reference if you used ref in the request).
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`tool_name`** (string)
  The name of a code scanning tool. Only results by this tool will be listed. You can specify the tool by using either tool\_name or tool\_guid, but not both.

* **`tool_guid`** (string,null)
  The GUID of a code scanning tool. Only results by this tool will be listed. Note that some code scanning tools may not include a GUID in their analysis data. You can specify the tool by using either tool\_guid or tool\_name, but not both.

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`ref`** (string)
  The Git reference for the results you want to list. The ref for a branch can be formatted either as refs/heads/<branch name> or simply <branch name>. To reference a pull request use refs/pull/<number>/merge.

* **`pr`** (integer)
  The number of the pull request for the results you want to list.

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

* **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

* **`sort`** (string)
  The property by which to sort the results.
  Default: `created`
  Can be one of: `created`, `updated`

* **`state`** (string)
  If specified, only code scanning alerts with this state will be returned.
  Can be one of: `open`, `closed`, `dismissed`, `fixed`

* **`severity`** (string)
  If specified, only code scanning alerts with this severity will be returned.
  Can be one of: `critical`, `high`, `medium`, `low`, `warning`, `note`, `error`

* **`assignees`** (string)
  Filter alerts by assignees. Provide a comma-separated list of user handles (e.g., octocat or octocat,hubot).
  Use \* to list alerts with at least one assignee or none to list alerts with no assignees.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/alerts
```

**Response schema (Status: 200):**

Array of objects:

* `number`: required, integer, read-only
* `created_at`: required, string, format: date-time, read-only
* `updated_at`: string, format: date-time, read-only
* `url`: required, string, format: uri, read-only
* `html_url`: required, string, format: uri, read-only
* `instances_url`: required, string, format: uri, read-only
* `state`: required, string or null, enum: `open`, `dismissed`, `fixed`, `null`
* `fixed_at`: string or null, format: date-time, read-only
* `dismissed_by`: required, any of:
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
* `dismissed_at`: required, string or null, format: date-time, read-only
* `dismissed_reason`: required, string or null, enum: `false positive`, `won't fix`, `used in tests`, `null`
* `dismissed_comment`: string or null, maxLength: 280
* `rule`: required, object:
  * `id`: string or null
  * `name`: string
  * `severity`: string or null, enum: `none`, `note`, `warning`, `error`, `null`
  * `security_severity_level`: string or null, enum: `low`, `medium`, `high`, `critical`, `null`
  * `description`: string
  * `full_description`: string
  * `tags`: array of string or null
  * `help`: string or null
  * `help_uri`: string or null
* `tool`: required, object:
  * `name`: string
  * `version`: string or null
  * `guid`: string or null
* `most_recent_instance`: required, object:
  * `ref`: string
  * `analysis_key`: string
  * `environment`: string
  * `category`: string
  * `state`: string or null, enum: `open`, `dismissed`, `fixed`, `null`
  * `commit_sha`: string
  * `message`: object:
    * `text`: string
    * `markdown`: string
  * `location`: object:
    * `path`: string
    * `start_line`: integer
    * `end_line`: integer
    * `start_column`: integer
    * `end_column`: integer
  * `html_url`: string
  * `classifications`: array of string or null, enum: `source`, `generated`, `test`, `library`, `null`
* `dismissal_approved_by`: any of:
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
* `assignees`: array of `Simple User`:
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

## Get a code scanning alert

```
GET /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}
```

Gets a single code scanning alert.
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`alert_number`** (integer) (required)
  The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the number field in the response from the GET /repos/{owner}/{repo}/code-scanning/alerts operation.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/alerts/ALERT_NUMBER
```

**Response schema (Status: 200):**

* `number`: required, integer, read-only
* `created_at`: required, string, format: date-time, read-only
* `updated_at`: string, format: date-time, read-only
* `url`: required, string, format: uri, read-only
* `html_url`: required, string, format: uri, read-only
* `instances_url`: required, string, format: uri, read-only
* `state`: required, string or null, enum: `open`, `dismissed`, `fixed`, `null`
* `fixed_at`: string or null, format: date-time, read-only
* `dismissed_by`: required, any of:
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
* `dismissed_at`: required, string or null, format: date-time, read-only
* `dismissed_reason`: required, string or null, enum: `false positive`, `won't fix`, `used in tests`, `null`
* `dismissed_comment`: string or null, maxLength: 280
* `rule`: required, object:
  * `id`: string or null
  * `name`: string
  * `severity`: string or null, enum: `none`, `note`, `warning`, `error`, `null`
  * `security_severity_level`: string or null, enum: `low`, `medium`, `high`, `critical`, `null`
  * `description`: string
  * `full_description`: string
  * `tags`: array of string or null
  * `help`: string or null
  * `help_uri`: string or null
* `tool`: required, object:
  * `name`: string
  * `version`: string or null
  * `guid`: string or null
* `most_recent_instance`: required, object:
  * `ref`: string
  * `analysis_key`: string
  * `environment`: string
  * `category`: string
  * `state`: string or null, enum: `open`, `dismissed`, `fixed`, `null`
  * `commit_sha`: string
  * `message`: object:
    * `text`: string
    * `markdown`: string
  * `location`: object:
    * `path`: string
    * `start_line`: integer
    * `end_line`: integer
    * `start_column`: integer
    * `end_column`: integer
  * `html_url`: string
  * `classifications`: array of string or null, enum: `source`, `generated`, `test`, `library`, `null`
* `dismissal_approved_by`: any of:
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
* `assignees`: array of `Simple User`:
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

## Update a code scanning alert

```
PATCH /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}
```

Updates the status of a single code scanning alert.
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`alert_number`** (integer) (required)
  The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the number field in the response from the GET /repos/{owner}/{repo}/code-scanning/alerts operation.

#### Body parameters

* **`state`** (string)
  Sets the state of the code scanning alert. You must provide dismissed\_reason when you set the state to dismissed.
  Can be one of: `open`, `dismissed`

* **`dismissed_reason`** (string or null)
  Required when the state is dismissed. The reason for dismissing or closing the alert.
  Can be one of: `false positive`, `won't fix`, `used in tests`, `null`

* **`dismissed_comment`** (string or null)
  The dismissal comment associated with the dismissal of the alert.

* **`create_request`** (boolean)
  If true, attempt to create an alert dismissal request.

* **`assignees`** (array of strings)
  The list of users to assign to the code scanning alert. An empty array unassigns all previous assignees from the alert.

### HTTP response status codes

* **200** - OK

* **400** - Bad Request

* **403** - Response if the repository is archived or if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/code-scanning/alerts/ALERT_NUMBER \
  -d '{
  "state": "dismissed",
  "dismissed_reason": "false positive",
  "dismissed_comment": "This alert is not actually correct, because there's a sanitizer included in the library.",
  "create_request": true
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a code scanning alert](#get-a-code-scanning-alert).

## Get the status of an autofix for a code scanning alert

```
GET /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}/autofix
```

Gets the status and description of an autofix for a code scanning alert.
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`alert_number`** (integer) (required)
  The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the number field in the response from the GET /repos/{owner}/{repo}/code-scanning/alerts operation.

### HTTP response status codes

* **200** - OK

* **400** - Bad Request

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/alerts/ALERT_NUMBER/autofix
```

**Response schema (Status: 200):**

* `status`: required, string, enum: `pending`, `error`, `success`, `outdated`
* `description`: required, string or null
* `started_at`: required, string, format: date-time, read-only

## Create an autofix for a code scanning alert

```
POST /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}/autofix
```

Creates an autofix for a code scanning alert.
If a new autofix is to be created as a result of this request or is currently being generated, then this endpoint will return a 202 Accepted response.
If an autofix already exists for a given alert, then this endpoint will return a 200 OK response.
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`alert_number`** (integer) (required)
  The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the number field in the response from the GET /repos/{owner}/{repo}/code-scanning/alerts operation.

### HTTP response status codes

* **200** - OK

* **202** - Accepted

* **400** - Bad Request

* **403** - Response if the repository is archived, if GitHub Advanced Security is not enabled for this repository or if rate limit is exceeded

* **404** - Resource not found

* **422** - Unprocessable Entity

* **503** - Service unavailable

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/code-scanning/alerts/ALERT_NUMBER/autofix
```

**Response schema (Status: 200):**

Same response schema as [Get the status of an autofix for a code scanning alert](#get-the-status-of-an-autofix-for-a-code-scanning-alert).

#### Example 2: Status Code 202

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/code-scanning/alerts/ALERT_NUMBER/autofix
```

**Response schema (Status: 202):**

Same response schema as [Get the status of an autofix for a code scanning alert](#get-the-status-of-an-autofix-for-a-code-scanning-alert).

## Commit an autofix for a code scanning alert

```
POST /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}/autofix/commits
```

Commits an autofix for a code scanning alert.
If an autofix is committed as a result of this request, then this endpoint will return a 201 Created response.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`alert_number`** (integer) (required)
  The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the number field in the response from the GET /repos/{owner}/{repo}/code-scanning/alerts operation.

#### Body parameters

* **`target_ref`** (string)
  The Git reference of target branch for the commit. Branch needs to already exist.  For more information, see "Git References" in the Git documentation.

* **`message`** (string)
  Commit message to be used.

### HTTP response status codes

* **201** - Created

* **400** - Bad Request

* **403** - Response if the repository is archived or if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **422** - Unprocessable Entity

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/code-scanning/alerts/ALERT_NUMBER/autofix/commits \
  -d '{
  "target_ref": "refs/heads/fix-bug",
  "message": "Let's fix this 🪲!"
}'
```

**Response schema (Status: 201):**

* `target_ref`: string
* `sha`: string

## List instances of a code scanning alert

```
GET /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}/instances
```

Lists all instances of the specified code scanning alert.
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`alert_number`** (integer) (required)
  The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the number field in the response from the GET /repos/{owner}/{repo}/code-scanning/alerts operation.

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`ref`** (string)
  The Git reference for the results you want to list. The ref for a branch can be formatted either as refs/heads/<branch name> or simply <branch name>. To reference a pull request use refs/pull/<number>/merge.

* **`pr`** (integer)
  The number of the pull request for the results you want to list.

### HTTP response status codes

* **200** - OK

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/alerts/ALERT_NUMBER/instances
```

**Response schema (Status: 200):**

Array of objects:

* `ref`: string
* `analysis_key`: string
* `environment`: string
* `category`: string
* `state`: string or null, enum: `open`, `fixed`, `null`
* `commit_sha`: string
* `message`: object:
  * `text`: string
* `location`: object:
  * `path`: string
  * `start_line`: integer
  * `end_line`: integer
  * `start_column`: integer
  * `end_column`: integer
* `html_url`: string
* `classifications`: array of string or null, enum: `source`, `generated`, `test`, `library`, `null`

## List code scanning analyses for a repository

```
GET /repos/{owner}/{repo}/code-scanning/analyses
```

Lists the details of all code scanning analyses for a repository,
starting with the most recent.
The response is paginated and you can use the page and per\_page parameters
to list the analyses you're interested in.
By default 30 analyses are listed per page.
The rules\_count field in the response give the number of rules
that were run in the analysis.
For very old analyses this data is not available,
and 0 is returned in this field.
Warning

Closing down notice: The tool\_name field is closing down and will, in future, not be included in the response for this endpoint. The example response reflects this change. The tool name can now be found inside the tool field.

OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`tool_name`** (string)
  The name of a code scanning tool. Only results by this tool will be listed. You can specify the tool by using either tool\_name or tool\_guid, but not both.

* **`tool_guid`** (string,null)
  The GUID of a code scanning tool. Only results by this tool will be listed. Note that some code scanning tools may not include a GUID in their analysis data. You can specify the tool by using either tool\_guid or tool\_name, but not both.

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`pr`** (integer)
  The number of the pull request for the results you want to list.

* **`ref`** (string)
  The Git reference for the analyses you want to list. The ref for a branch can be formatted either as refs/heads/<branch name> or simply <branch name>. To reference a pull request use refs/pull/<number>/merge.

* **`sarif_id`** (string)
  Filter analyses belonging to the same SARIF upload.

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`sort`** (string)
  The property by which to sort the results.
  Default: `created`
  Can be one of: `created`

### HTTP response status codes

* **200** - OK

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/analyses
```

**Response schema (Status: 200):**

Array of objects:

* `ref`: required, string
* `commit_sha`: required, string, minLength: 40, maxLength: 40, pattern: `^[0-9a-fA-F]+$`
* `analysis_key`: required, string
* `environment`: required, string
* `category`: string
* `error`: required, string
* `created_at`: required, string, format: date-time, read-only
* `results_count`: required, integer
* `rules_count`: required, integer
* `id`: required, integer
* `url`: required, string, format: uri, read-only
* `sarif_id`: required, string
* `tool`: required, object:
  * `name`: string
  * `version`: string or null
  * `guid`: string or null
* `deletable`: required, boolean
* `warning`: required, string

## Get a code scanning analysis for a repository

```
GET /repos/{owner}/{repo}/code-scanning/analyses/{analysis_id}
```

Gets a specified code scanning analysis for a repository.
The default JSON response contains fields that describe the analysis.
This includes the Git reference and commit SHA to which the analysis relates,
the datetime of the analysis, the name of the code scanning tool,
and the number of alerts.
The rules\_count field in the default response give the number of rules
that were run in the analysis.
For very old analyses this data is not available,
and 0 is returned in this field.
This endpoint supports the following custom media types. For more information, see "Media types."

application/sarif+json: Instead of returning a summary of the analysis, this endpoint returns a subset of the analysis data that was uploaded. The data is formatted as SARIF version 2.1.0. It also returns additional data such as the github/alertNumber and github/alertUrl properties.

OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`analysis_id`** (integer) (required)
  The ID of the analysis, as returned from the GET /repos/{owner}/{repo}/code-scanning/analyses operation.

### HTTP response status codes

* **200** - OK

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **422** - Response if analysis could not be processed

* **503** - Service unavailable

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/analyses/ANALYSIS_ID
```

**Response schema (Status: 200):**

* `ref`: required, string
* `commit_sha`: required, string, minLength: 40, maxLength: 40, pattern: `^[0-9a-fA-F]+$`
* `analysis_key`: required, string
* `environment`: required, string
* `category`: string
* `error`: required, string
* `created_at`: required, string, format: date-time, read-only
* `results_count`: required, integer
* `rules_count`: required, integer
* `id`: required, integer
* `url`: required, string, format: uri, read-only
* `sarif_id`: required, string
* `tool`: required, object:
  * `name`: string
  * `version`: string or null
  * `guid`: string or null
* `deletable`: required, boolean
* `warning`: required, string

#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/analyses/ANALYSIS_ID
```

**Response schema (Status: 200):**

object, additional properties allowed

## Delete a code scanning analysis from a repository

```
DELETE /repos/{owner}/{repo}/code-scanning/analyses/{analysis_id}
```

Deletes a specified code scanning analysis from a repository.
You can delete one analysis at a time.
To delete a series of analyses, start with the most recent analysis and work backwards.
Conceptually, the process is similar to the undo function in a text editor.
When you list the analyses for a repository,
one or more will be identified as deletable in the response:
"deletable": true

An analysis is deletable when it's the most recent in a set of analyses.
Typically, a repository will have multiple sets of analyses
for each enabled code scanning tool,
where a set is determined by a unique combination of analysis values:

ref
tool
category

If you attempt to delete an analysis that is not the most recent in a set,
you'll get a 400 response with the message:
Analysis specified is not deletable.

The response from a successful DELETE operation provides you with
two alternative URLs for deleting the next analysis in the set:
next\_analysis\_url and confirm\_delete\_url.
Use the next\_analysis\_url URL if you want to avoid accidentally deleting the final analysis
in a set. This is a useful option if you want to preserve at least one analysis
for the specified tool in your repository.
Use the confirm\_delete\_url URL if you are content to remove all analyses for a tool.
When you delete the last analysis in a set, the value of next\_analysis\_url and confirm\_delete\_url
in the 200 response is null.
As an example of the deletion process,
let's imagine that you added a workflow that configured a particular code scanning tool
to analyze the code in a repository. This tool has added 15 analyses:
10 on the default branch, and another 5 on a topic branch.
You therefore have two separate sets of analyses for this tool.
You've now decided that you want to remove all of the analyses for the tool.
To do this you must make 15 separate deletion requests.
To start, you must find an analysis that's identified as deletable.
Each set of analyses always has one that's identified as deletable.
Having found the deletable analysis for one of the two sets,
delete this analysis and then continue deleting the next analysis in the set until they're all deleted.
Then repeat the process for the second set.
The procedure therefore consists of a nested loop:
Outer loop:

List the analyses for the repository, filtered by tool.

Parse this list to find a deletable analysis. If found:
Inner loop:

Delete the identified analysis.
Parse the response for the value of confirm\_delete\_url and, if found, use this in the next iteration.

The above process assumes that you want to remove all trace of the tool's analyses from the GitHub user interface, for the specified repository, and it therefore uses the confirm\_delete\_url value. Alternatively, you could use the next\_analysis\_url value, which would leave the last analysis in each set undeleted to avoid removing a tool's analysis entirely.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`analysis_id`** (integer) (required)
  The ID of the analysis, as returned from the GET /repos/{owner}/{repo}/code-scanning/analyses operation.

* **`confirm_delete`** (string,null)
  Allow deletion if the specified analysis is the last in a set. If you attempt to delete the final analysis in a set without setting this parameter to true, you'll get a 400 response with the message: Analysis is last of its type and deletion may result in the loss of historical alert data. Please specify confirm\_delete.

### HTTP response status codes

* **200** - OK

* **400** - Bad Request

* **403** - Response if the repository is archived or if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/code-scanning/analyses/ANALYSIS_ID
```

**Response schema (Status: 200):**

* `next_analysis_url`: required, string or null, format: uri, read-only
* `confirm_delete_url`: required, string or null, format: uri, read-only

## List CodeQL databases for a repository

```
GET /repos/{owner}/{repo}/code-scanning/codeql/databases
```

Lists the CodeQL databases that are available in a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

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

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/codeql/databases
```

**Response schema (Status: 200):**

Array of `CodeQL Database`:

* `id`: required, integer
* `name`: required, string
* `language`: required, string
* `uploader`: required, `Simple User`:
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
* `content_type`: required, string
* `size`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `url`: required, string, format: uri
* `commit_oid`: string or null

## Get a CodeQL database for a repository

```
GET /repos/{owner}/{repo}/code-scanning/codeql/databases/{language}
```

Gets a CodeQL database for a language in a repository.
By default this endpoint returns JSON metadata about the CodeQL database. To
download the CodeQL database binary content, set the Accept header of the request
to application/zip, and make sure
your HTTP client is configured to follow redirects or use the Location header
to make a second request to get the redirect URL.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`language`** (string) (required)
  The language of the CodeQL database.

### HTTP response status codes

* **200** - OK

* **302** - Found

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/codeql/databases/LANGUAGE
```

**Response schema (Status: 200):**

* `id`: required, integer
* `name`: required, string
* `language`: required, string
* `uploader`: required, `Simple User`:
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
* `content_type`: required, string
* `size`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `url`: required, string, format: uri
* `commit_oid`: string or null

## Delete a CodeQL database

```
DELETE /repos/{owner}/{repo}/code-scanning/codeql/databases/{language}
```

Deletes a CodeQL database for a language in a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`language`** (string) (required)
  The language of the CodeQL database.

### HTTP response status codes

* **204** - No Content

* **403** - Response if the repository is archived or if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/code-scanning/codeql/databases/LANGUAGE
```

**Response schema (Status: 204):**

## Create a CodeQL variant analysis

```
POST /repos/{owner}/{repo}/code-scanning/codeql/variant-analyses
```

Creates a new CodeQL variant analysis, which will run a CodeQL query against one or more repositories.
Get started by learning more about running CodeQL queries at scale with Multi-Repository Variant Analysis.
Use the owner and repo parameters in the URL to specify the controller repository that
will be used for running GitHub Actions workflows and storing the results of the CodeQL variant analysis.
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

* **201** - Variant analysis submitted for processing

* **404** - Resource not found

* **422** - Unable to process variant analysis submission

* **503** - Service unavailable

### Code examples

#### Using the "repositories" field. "query\_pack" is abridged for brevity.

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/code-scanning/codeql/variant-analyses \
  -d '{
  "language": "csharp",
  "query_pack": "aGVsbG8=",
  "repositories": [
    "octocat/Hello-World",
    "octocat/example"
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `controller_repo`: required, `Simple Repository`:
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
* `actor`: required, `Simple User`:
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
* `query_language`: required, string, enum: `actions`, `cpp`, `csharp`, `go`, `java`, `javascript`, `python`, `ruby`, `rust`, `swift`
* `query_pack_url`: required, string
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time
* `completed_at`: string or null, format: date-time
* `status`: required, string, enum: `in_progress`, `succeeded`, `failed`, `cancelled`
* `actions_workflow_run_id`: integer
* `failure_reason`: string, enum: `no_repos_queried`, `actions_workflow_run_failed`, `internal_error`
* `scanned_repositories`: array of objects:
  * `repository`: required, `Repository Identifier`:
    * `id`: required, integer
    * `name`: required, string
    * `full_name`: required, string
    * `private`: required, boolean
    * `stargazers_count`: required, integer
    * `updated_at`: required, string or null, format: date-time
  * `analysis_status`: required, string, enum: `pending`, `in_progress`, `succeeded`, `failed`, `canceled`, `timed_out`
  * `result_count`: integer
  * `artifact_size_in_bytes`: integer
  * `failure_message`: string
* `skipped_repositories`: object:
  * `access_mismatch_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time
  * `not_found_repos`: required, object:
    * `repository_count`: required, integer
    * `repository_full_names`: required, array of string
  * `no_codeql_db_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time
  * `over_limit_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time

#### Using the "repository\_owners" field. "query\_pack" is abridged.

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/code-scanning/codeql/variant-analyses \
  -d '{
  "language": "csharp",
  "query_pack": "aGVsbG8=",
  "repository_owners": [
    "octocat"
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `controller_repo`: required, `Simple Repository`:
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
* `actor`: required, `Simple User`:
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
* `query_language`: required, string, enum: `actions`, `cpp`, `csharp`, `go`, `java`, `javascript`, `python`, `ruby`, `rust`, `swift`
* `query_pack_url`: required, string
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time
* `completed_at`: string or null, format: date-time
* `status`: required, string, enum: `in_progress`, `succeeded`, `failed`, `cancelled`
* `actions_workflow_run_id`: integer
* `failure_reason`: string, enum: `no_repos_queried`, `actions_workflow_run_failed`, `internal_error`
* `scanned_repositories`: array of objects:
  * `repository`: required, `Repository Identifier`:
    * `id`: required, integer
    * `name`: required, string
    * `full_name`: required, string
    * `private`: required, boolean
    * `stargazers_count`: required, integer
    * `updated_at`: required, string or null, format: date-time
  * `analysis_status`: required, string, enum: `pending`, `in_progress`, `succeeded`, `failed`, `canceled`, `timed_out`
  * `result_count`: integer
  * `artifact_size_in_bytes`: integer
  * `failure_message`: string
* `skipped_repositories`: object:
  * `access_mismatch_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time
  * `not_found_repos`: required, object:
    * `repository_count`: required, integer
    * `repository_full_names`: required, array of string
  * `no_codeql_db_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time
  * `over_limit_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time

#### Using the "repository\_lists" field. "query\_pack" is abridged.

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/code-scanning/codeql/variant-analyses \
  -d '{
  "language": "csharp",
  "query_pack": "aGVsbG8=",
  "repository_lists": [
    "top-100-csharp"
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `controller_repo`: required, `Simple Repository`:
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
* `actor`: required, `Simple User`:
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
* `query_language`: required, string, enum: `actions`, `cpp`, `csharp`, `go`, `java`, `javascript`, `python`, `ruby`, `rust`, `swift`
* `query_pack_url`: required, string
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time
* `completed_at`: string or null, format: date-time
* `status`: required, string, enum: `in_progress`, `succeeded`, `failed`, `cancelled`
* `actions_workflow_run_id`: integer
* `failure_reason`: string, enum: `no_repos_queried`, `actions_workflow_run_failed`, `internal_error`
* `scanned_repositories`: array of objects:
  * `repository`: required, `Repository Identifier`:
    * `id`: required, integer
    * `name`: required, string
    * `full_name`: required, string
    * `private`: required, boolean
    * `stargazers_count`: required, integer
    * `updated_at`: required, string or null, format: date-time
  * `analysis_status`: required, string, enum: `pending`, `in_progress`, `succeeded`, `failed`, `canceled`, `timed_out`
  * `result_count`: integer
  * `artifact_size_in_bytes`: integer
  * `failure_message`: string
* `skipped_repositories`: object:
  * `access_mismatch_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time
  * `not_found_repos`: required, object:
    * `repository_count`: required, integer
    * `repository_full_names`: required, array of string
  * `no_codeql_db_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time
  * `over_limit_repos`: required, object:
    * `repository_count`: required, integer
    * `repositories`: required, array of `Repository Identifier`:
      * `id`: required, integer
      * `name`: required, string
      * `full_name`: required, string
      * `private`: required, boolean
      * `stargazers_count`: required, integer
      * `updated_at`: required, string or null, format: date-time

## Get the summary of a CodeQL variant analysis

```
GET /repos/{owner}/{repo}/code-scanning/codeql/variant-analyses/{codeql_variant_analysis_id}
```

Gets the summary of a CodeQL variant analysis.
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`codeql_variant_analysis_id`** (integer) (required)
  The unique identifier of the variant analysis.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/codeql/variant-analyses/CODEQL_VARIANT_ANALYSIS_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a CodeQL variant analysis](#create-a-codeql-variant-analysis).

## Get the analysis status of a repository in a CodeQL variant analysis

```
GET /repos/{owner}/{repo}/code-scanning/codeql/variant-analyses/{codeql_variant_analysis_id}/repos/{repo_owner}/{repo_name}
```

Gets the analysis status of a repository in a CodeQL variant analysis.
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the controller repository.

* **`codeql_variant_analysis_id`** (integer) (required)
  The ID of the variant analysis.

* **`repo_owner`** (string) (required)
  The account owner of the variant analysis repository. The name is not case sensitive.

* **`repo_name`** (string) (required)
  The name of the variant analysis repository.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/codeql/variant-analyses/CODEQL_VARIANT_ANALYSIS_ID/repos/REPO_OWNER/REPO_NAME
```

**Response schema (Status: 200):**

* `repository`: required, `Simple Repository`:
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
* `analysis_status`: required, string, enum: `pending`, `in_progress`, `succeeded`, `failed`, `canceled`, `timed_out`
* `artifact_size_in_bytes`: integer
* `result_count`: integer
* `failure_message`: string
* `database_commit_sha`: string
* `source_location_prefix`: string
* `artifact_url`: string

## Get a code scanning default setup configuration

```
GET /repos/{owner}/{repo}/code-scanning/default-setup
```

Gets a code scanning default setup configuration.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

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

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/default-setup
```

**Response schema (Status: 200):**

* `state`: string, enum: `configured`, `not-configured`
* `languages`: array of string, enum: `actions`, `c-cpp`, `csharp`, `go`, `java-kotlin`, `javascript-typescript`, `python`, `ruby`, `swift`
* `runner_type`: string or null, enum: `standard`, `labeled`, `null`
* `runner_label`: string or null
* `query_suite`: string, enum: `default`, `extended`
* `threat_model`: string, enum: `remote`, `remote_and_local`
* `updated_at`: string or null, format: date-time
* `schedule`: string or null, enum: `weekly`, `null`

## Update a code scanning default setup configuration

```
PATCH /repos/{owner}/{repo}/code-scanning/default-setup
```

Updates a code scanning default setup configuration.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

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

* **`state`** (string)
  The desired state of code scanning default setup.
  Can be one of: `configured`, `not-configured`

* **`runner_type`** (string)
  Runner type to be used.
  Can be one of: `standard`, `labeled`

* **`runner_label`** (string or null)
  Runner label to be used if the runner type is labeled.

* **`query_suite`** (string)
  CodeQL query suite to be used.
  Can be one of: `default`, `extended`

* **`threat_model`** (string)
  Threat model to be used for code scanning analysis. Use remote to analyze only network sources and remote\_and\_local to include local sources like filesystem access, command-line arguments, database reads, environment variable and standard input.
  Can be one of: `remote`, `remote_and_local`

* **`languages`** (array of strings)
  CodeQL languages to be analyzed.
  Supported values are: actions, c-cpp, csharp, go, java-kotlin, javascript-typescript, python, ruby, swift

### HTTP response status codes

* **200** - OK

* **202** - Accepted

* **403** - Response if the repository is archived or if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **409** - Response if there is already a validation run in progress with a different default setup configuration

* **422** - Response if the configuration change cannot be made because the repository is not in the required state

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/code-scanning/default-setup \
  -d '{
  "state": "configured",
  "threat_model": "remote_and_local"
}'
```

**Response schema (Status: 202):**

* `run_id`: integer
* `run_url`: string

## Upload an analysis as SARIF data

```
POST /repos/{owner}/{repo}/code-scanning/sarifs
```

Uploads SARIF data containing the results of a code scanning analysis to make the results available in a repository. For troubleshooting information, see "Troubleshooting SARIF uploads."
There are two places where you can upload code scanning results.

If you upload to a pull request, for example --ref refs/pull/42/merge or --ref refs/pull/42/head, then the results appear as alerts in a pull request check. For more information, see "Triaging code scanning alerts in pull requests."
If you upload to a branch, for example --ref refs/heads/my-branch, then the results appear in the Security tab for your repository. For more information, see "Managing code scanning alerts for your repository."

You must compress the SARIF-formatted analysis data that you want to upload, using gzip, and then encode it as a Base64 format string. For example:
gzip -c analysis-data.sarif | base64 -w0

SARIF upload supports a maximum number of entries per the following data objects, and an analysis will be rejected if any of these objects is above its maximum value. For some objects, there are additional values over which the entries will be ignored while keeping the most important entries whenever applicable.
To get the most out of your analysis when it includes data above the supported limits, try to optimize the analysis configuration. For example, for the CodeQL tool, identify and remove the most noisy queries. For more information, see "SARIF results exceed one or more limits."

SARIF dataMaximum valuesAdditional limitsRuns per file20Results per run25,000Only the top 5,000 results will be included, prioritized by severity.Rules per run25,000Tool extensions per run100Thread Flow Locations per result10,000Only the top 1,000 Thread Flow Locations will be included, using prioritization.Location per result1,000Only 100 locations will be included.Tags per rule20Only 10 tags will be included.
The 202 Accepted response includes an id value.
You can use this ID to check the status of the upload by using it in the /sarifs/{sarif\_id} endpoint.
For more information, see "Get information about a SARIF upload."
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.
This endpoint is limited to 1,000 requests per hour for each user or app installation calling it.

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

* **`commit_sha`** (string) (required)
  The SHA of the commit to which the analysis you are uploading relates.

* **`ref`** (string) (required)
  The full Git reference, formatted as refs/heads/<branch name>,
  refs/tags/<tag>, refs/pull/<number>/merge, or refs/pull/<number>/head.

* **`sarif`** (string) (required)
  A Base64 string representing the SARIF file to upload. You must first compress your SARIF file using gzip and then translate the contents of the file into a Base64 encoding string. For more information, see "SARIF support for code scanning."

* **`checkout_uri`** (string)
  The base directory used in the analysis, as it appears in the SARIF file.
  This property is used to convert file paths from absolute to relative, so that alerts can be mapped to their correct location in the repository.

* **`started_at`** (string)
  The time that the analysis run began. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

* **`tool_name`** (string)
  The name of the tool used to generate the code scanning analysis. If this parameter is not used, the tool name defaults to "API". If the uploaded SARIF contains a tool GUID, this will be available for filtering using the tool\_guid parameter of operations such as GET /repos/{owner}/{repo}/code-scanning/alerts.

* **`validate`** (boolean)
  Whether the SARIF file will be validated according to the code scanning specifications.
  This parameter is intended to help integrators ensure that the uploaded SARIF files are correctly rendered by code scanning.

### HTTP response status codes

* **202** - Accepted

* **400** - Bad Request if the sarif field is invalid

* **403** - Response if the repository is archived or if GitHub Advanced Security is not enabled for this repository

* **404** - Resource not found

* **413** - Payload Too Large if the sarif field is too large

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/code-scanning/sarifs \
  -d '{
  "commit_sha": "4b6472266afd7b471e86085a6659e8c7f2b119da",
  "ref": "refs/heads/master",
  "sarif": "H4sICMLGdF4AA2V4YW1wbGUuc2FyaWYAvVjdbts2FL7PUxDCijaA/CM7iRNfLkPXYgHSNstumlzQ0pHFVCI1korjFgH2ONtr7Ul2KFmy/mOn6QIkjsjDw0/nfN85NL8dEGL9pNwAImqRObECrWM1H40kXQ2XTAfJIlEgXcE1cD10RTQSVDE10K4aKSqZP1AxuKOIKg1ydJU60jSfSh8Hk6EzHA/vlOCWbfa7B6kYPpj90rlsWCZcmbHP5Bs+4oAWIjQD2SMOeJLh2vIQDnIaQerqXHjw8YIgxohybxAyDsS4cAPKsp03K4RcUs6+Up2D+JXpd8mibKIQN9fM/aMCdbyBujGSSQgVxJtx5qX2d2qUcIweQhEuDQf3GBO6CKHkogx/N3MVCKl/AeVKFuf4y5ubsMGDTj1ep+5I7sgmLIpxtU38hLtmMRGSuCFVyip5eKzs5ydh+LztVL6f2m6oih1BkYiuyQIIJWodxVpERPj4sEiWBNNH8EWT0DMG8EAjzKVHXCrB4FkPu/F64NMk1OeC+2yZSNoBOoR7CC0EzYWGbm+xFDFIzbI011+cLjfZtyJkmMZfumAh02uL3NpV2y+MZ6RAjxibyKrNxxJcVjANSb4eBGwZ1M0KsuyR2poLr5rMl8vaDSeVn6eTWEO2j2xIEcmhwlTKNOi4GMOI8gfuZYkvJ7b4v5Tiumyz7RnHeodFzpS8ASIZCH/AYdWi2z3sG8JtFxJ6fF9yR9CdifBr9Pd6d5V2+zbJKjjCFGGmsHuYFy2ytJq9tUxcLSRSQecppOGKrpUxYfxefMEFK+wOGa4hudQByBVT0L+EKtyACxnRsABhEx1QjVDs1KNI9MbpnhqfE45B6FJvu3hRu5VRU9MhZLmK7fqkKyQSTHNoyMqUFMqXCV3CwAeqEwmVokraK8IuBaGvHjQ0gMYrKjnjyw7uk9uD8tgmsBbFMPnU1bV2ZhkJNkuolUiWys3UPWzs5aaIUz9TBe8zMb+6+nT+6fLy91dlE3xzeDDT4zYszb0bW6NjJd0Rvn2EnLvWLFSdKPpBzInzfRgu8ETyMcH8nIfMnJCeC2PyfTA+UKngcnGH7Hw2hGkVQs5YlIRCtdWZYQ4/73es2JlxkfViOEIhoWJq5Oo6UBBfiKIqFBWhiE3jJGbFwVoxBHTRSuIS67sMeplei24X20shLjG+8gqbKC/bESiNMC+wd5q5id0yeS7CJEqXzmrTWNq3k05l84P6f4/bEmXFJjI0fIt1BGQssUnUDkBYeVhE5TqPnMH3jqogDcP0zKcTgLPTMSzOjhbjuVOmW23l1fYNStulfo6sXlFsGLhbDy5RECPRYGCTgOj2bd4nUQEivEd0H7KKYxqnEhFohuur3a3UPskbH/+Yg0+M5P2MHRJu3ziHh3Z2NCrWt3XF1rWTw8Ne/pfbWYXnDSE0SNZQQt1i18q7te2vOhu7ehWuvVyeu0wbLZi24mhoo6aOOTltzG/lgdVvVoXQq5V+pewkFIzL8fjEcadT55jOjpzFzHuOTtDNrMkJPMVQDd7F09RID72O/UPZ0tmctqZ7kWX6EmSZnDpP8GU67SXM8XE3YSrxbKsx6UReZ4y6n/FVZfJjs9Z7stma75W5yQtkzjk5eSJxk1lv4o7+j8TlhaJ2lsKWZO6lruDPBLib3x5ZN/KGWzZ+pn///evv7OOf4iIBv3oY9L/l1wiJ9p0Tc+F1zZnOE9NxXWEus6IQhr5pMfoqxi8WPsuu0azsns4UC6WzNzHIzbeEx4P/AJ3SefgcFAAA"
}'
```

**Response schema (Status: 202):**

* `id`: string
* `url`: string, format: uri, read-only

## Get information about a SARIF upload

```
GET /repos/{owner}/{repo}/code-scanning/sarifs/{sarif_id}
```

Gets information about a SARIF upload, including the status and the URL of the analysis that was uploaded so that you can retrieve details of the analysis. For more information, see "Get a code scanning analysis for a repository."
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint with private or public repositories, or the public\_repo scope to use this endpoint with only public repositories.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`sarif_id`** (string) (required)
  The SARIF ID obtained after uploading.

### HTTP response status codes

* **200** - OK

* **403** - Response if GitHub Advanced Security is not enabled for this repository

* **404** - Not Found if the sarif id does not match any upload

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-scanning/sarifs/SARIF_ID
```

**Response schema (Status: 200):**

* `processing_status`: string, enum: `pending`, `complete`, `failed`
* `analyses_url`: string or null, format: uri, read-only
* `errors`: array of string or null