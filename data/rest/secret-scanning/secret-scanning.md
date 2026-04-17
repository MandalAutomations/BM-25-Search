# REST API endpoints for secret scanning

Use the REST API to retrieve and update secret alerts from a repository.

## About secret scanning

You can use the API to:

* Enable or disable secret scanning and push protection for a repository. For more information, see [REST API endpoints for repositories](/en/rest/repos/repos#update-a-repository) and expand the "Properties of the `security_and_analysis` object" section.
* Retrieve and update secret scanning alerts from a repository. For further details, see the sections below.

For more information about secret scanning, see [About secret scanning](/en/code-security/secret-scanning/introduction/about-secret-scanning).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List secret scanning alerts for an organization

```
GET /orgs/{org}/secret-scanning/alerts
```

Lists secret scanning alerts for eligible repositories in an organization, from newest to oldest.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo or security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`state`** (string)
  Set to open or resolved to only list secret scanning alerts in a specific state.
  Can be one of: `open`, `resolved`

* **`secret_type`** (string)
  A comma-separated list of secret types to return. All default secret patterns are returned. To return generic patterns, pass the token name(s) in the parameter. See "Supported secret scanning patterns" for a complete list of secret types.

* **`exclude_secret_types`** (string)
  A comma-separated list of secret types to exclude from the results. All default secret patterns are returned except those matching the specified types. Cannot be combined with the secret\_type parameter. See "Supported secret scanning patterns" for a complete list of secret types.

* **`exclude_providers`** (string)
  A comma-separated list of provider slugs to exclude from the results.
  Provider slugs use lowercase with underscores (e.g., github\_secret\_scanning, clojars).
  You can find the provider slug in the provider\_slug field of each alert.
  Cannot be combined with the providers parameter.

* **`providers`** (string)
  A comma-separated list of provider slugs to filter by.
  Provider slugs use lowercase with underscores (e.g., github\_secret\_scanning, clojars).
  You can find the provider slug in the provider\_slug field of each alert.
  Cannot be combined with the exclude\_providers parameter.

* **`resolution`** (string)
  A comma-separated list of resolutions. Only secret scanning alerts with one of these resolutions are listed. Valid resolutions are false\_positive, wont\_fix, revoked, pattern\_edited, pattern\_deleted or used\_in\_tests.

* **`assignee`** (string)
  Filters alerts by assignee. Use \* to get all assigned alerts, none to get all unassigned alerts, or a GitHub username to get alerts assigned to a specific user.

* **`sort`** (string)
  The property to sort the results by. created means when the alert was created. updated means when the alert was updated or resolved.
  Default: `created`
  Can be one of: `created`, `updated`

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for events before this cursor. To receive an initial cursor on your first request, include an empty "before" query string.

* **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for events after this cursor.  To receive an initial cursor on your first request, include an empty "after" query string.

* **`validity`** (string)
  A comma-separated list of validities that, when present, will return alerts that match the validities in this list. Valid options are active, inactive, and unknown.

* **`is_publicly_leaked`** (boolean)
  A boolean value representing whether or not to filter alerts by the publicly-leaked tag being present.
  Default: `false`

* **`is_multi_repo`** (boolean)
  A boolean value representing whether or not to filter alerts by the multi-repo tag being present.
  Default: `false`

* **`hide_secret`** (boolean)
  A boolean value representing whether or not to hide literal secrets in the results.
  Default: `false`

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
  https://api.github.com/orgs/ORG/secret-scanning/alerts
```

**Response schema (Status: 200):**

Array of objects:

* `number`: integer, read-only
* `created_at`: string, format: date-time, read-only
* `updated_at`: any of:
  * **null**
  * **string, format: date-time, read-only**
* `url`: string, format: uri, read-only
* `html_url`: string, format: uri, read-only
* `locations_url`: string, format: uri
* `state`: string, enum: `open`, `resolved`
* `resolution`: string or null, enum: `false_positive`, `wont_fix`, `revoked`, `used_in_tests`, `null`
* `resolved_at`: string or null, format: date-time
* `resolved_by`: any of:
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
* `secret_type`: string
* `secret_type_display_name`: string
* `provider`: string or null
* `provider_slug`: string or null
* `secret`: string
* `repository`: `Simple Repository`:
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
* `push_protection_bypassed`: boolean or null
* `push_protection_bypassed_by`: any of:
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
* `push_protection_bypassed_at`: string or null, format: date-time
* `push_protection_bypass_request_reviewer`: any of:
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
* `push_protection_bypass_request_reviewer_comment`: string or null
* `push_protection_bypass_request_comment`: string or null
* `push_protection_bypass_request_html_url`: string or null, format: uri
* `resolution_comment`: string or null
* `validity`: string, enum: `active`, `inactive`, `unknown`
* `publicly_leaked`: boolean or null
* `multi_repo`: boolean or null
* `is_base64_encoded`: boolean or null
* `first_location_detected`: any of:
  * **null**
  * **object**
* `has_more_locations`: boolean
* `assigned_to`: any of:
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
* `closure_request_comment`: string or null
* `closure_request_reviewer_comment`: string or null
* `closure_request_reviewer`: any of:
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

## List secret scanning alerts for a repository

```
GET /repos/{owner}/{repo}/secret-scanning/alerts
```

Lists secret scanning alerts for an eligible repository, from newest to oldest.
The authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo or security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`state`** (string)
  Set to open or resolved to only list secret scanning alerts in a specific state.
  Can be one of: `open`, `resolved`

* **`secret_type`** (string)
  A comma-separated list of secret types to return. All default secret patterns are returned. To return generic patterns, pass the token name(s) in the parameter. See "Supported secret scanning patterns" for a complete list of secret types.

* **`exclude_secret_types`** (string)
  A comma-separated list of secret types to exclude from the results. All default secret patterns are returned except those matching the specified types. Cannot be combined with the secret\_type parameter. See "Supported secret scanning patterns" for a complete list of secret types.

* **`exclude_providers`** (string)
  A comma-separated list of provider slugs to exclude from the results.
  Provider slugs use lowercase with underscores (e.g., github\_secret\_scanning, clojars).
  You can find the provider slug in the provider\_slug field of each alert.
  Cannot be combined with the providers parameter.

* **`providers`** (string)
  A comma-separated list of provider slugs to filter by.
  Provider slugs use lowercase with underscores (e.g., github\_secret\_scanning, clojars).
  You can find the provider slug in the provider\_slug field of each alert.
  Cannot be combined with the exclude\_providers parameter.

* **`resolution`** (string)
  A comma-separated list of resolutions. Only secret scanning alerts with one of these resolutions are listed. Valid resolutions are false\_positive, wont\_fix, revoked, pattern\_edited, pattern\_deleted or used\_in\_tests.

* **`assignee`** (string)
  Filters alerts by assignee. Use \* to get all assigned alerts, none to get all unassigned alerts, or a GitHub username to get alerts assigned to a specific user.

* **`sort`** (string)
  The property to sort the results by. created means when the alert was created. updated means when the alert was updated or resolved.
  Default: `created`
  Can be one of: `created`, `updated`

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for events before this cursor. To receive an initial cursor on your first request, include an empty "before" query string.

* **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for events after this cursor.  To receive an initial cursor on your first request, include an empty "after" query string.

* **`validity`** (string)
  A comma-separated list of validities that, when present, will return alerts that match the validities in this list. Valid options are active, inactive, and unknown.

* **`is_publicly_leaked`** (boolean)
  A boolean value representing whether or not to filter alerts by the publicly-leaked tag being present.
  Default: `false`

* **`is_multi_repo`** (boolean)
  A boolean value representing whether or not to filter alerts by the multi-repo tag being present.
  Default: `false`

* **`hide_secret`** (boolean)
  A boolean value representing whether or not to hide literal secrets in the results.
  Default: `false`

### HTTP response status codes

* **200** - OK

* **404** - Repository is public or secret scanning is disabled for the repository

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/alerts
```

**Response schema (Status: 200):**

Array of objects:

* `number`: integer, read-only
* `created_at`: string, format: date-time, read-only
* `updated_at`: any of:
  * **null**
  * **string, format: date-time, read-only**
* `url`: string, format: uri, read-only
* `html_url`: string, format: uri, read-only
* `locations_url`: string, format: uri
* `state`: string, enum: `open`, `resolved`
* `resolution`: string or null, enum: `false_positive`, `wont_fix`, `revoked`, `used_in_tests`, `null`
* `resolved_at`: string or null, format: date-time
* `resolved_by`: any of:
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
* `resolution_comment`: string or null
* `secret_type`: string
* `secret_type_display_name`: string
* `provider`: string or null
* `provider_slug`: string or null
* `secret`: string
* `push_protection_bypassed`: boolean or null
* `push_protection_bypassed_by`: any of:
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
* `push_protection_bypassed_at`: string or null, format: date-time
* `push_protection_bypass_request_reviewer`: any of:
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
* `push_protection_bypass_request_reviewer_comment`: string or null
* `push_protection_bypass_request_comment`: string or null
* `push_protection_bypass_request_html_url`: string or null, format: uri
* `validity`: string, enum: `active`, `inactive`, `unknown`
* `publicly_leaked`: boolean or null
* `multi_repo`: boolean or null
* `is_base64_encoded`: boolean or null
* `first_location_detected`: any of:
  * **null**
  * **object**
* `has_more_locations`: boolean
* `assigned_to`: any of:
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
* `closure_request_comment`: string or null
* `closure_request_reviewer_comment`: string or null
* `closure_request_reviewer`: any of:
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

## Get a secret scanning alert

```
GET /repos/{owner}/{repo}/secret-scanning/alerts/{alert_number}
```

Gets a single secret scanning alert detected in an eligible repository.
The authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo or security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

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

* **`hide_secret`** (boolean)
  A boolean value representing whether or not to hide literal secrets in the results.
  Default: `false`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **404** - Repository is public, or secret scanning is disabled for the repository, or the resource is not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/alerts/ALERT_NUMBER
```

**Response schema (Status: 200):**

* `number`: integer, read-only
* `created_at`: string, format: date-time, read-only
* `updated_at`: any of:
  * **null**
  * **string, format: date-time, read-only**
* `url`: string, format: uri, read-only
* `html_url`: string, format: uri, read-only
* `locations_url`: string, format: uri
* `state`: string, enum: `open`, `resolved`
* `resolution`: string or null, enum: `false_positive`, `wont_fix`, `revoked`, `used_in_tests`, `null`
* `resolved_at`: string or null, format: date-time
* `resolved_by`: any of:
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
* `resolution_comment`: string or null
* `secret_type`: string
* `secret_type_display_name`: string
* `provider`: string or null
* `provider_slug`: string or null
* `secret`: string
* `push_protection_bypassed`: boolean or null
* `push_protection_bypassed_by`: any of:
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
* `push_protection_bypassed_at`: string or null, format: date-time
* `push_protection_bypass_request_reviewer`: any of:
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
* `push_protection_bypass_request_reviewer_comment`: string or null
* `push_protection_bypass_request_comment`: string or null
* `push_protection_bypass_request_html_url`: string or null, format: uri
* `validity`: string, enum: `active`, `inactive`, `unknown`
* `publicly_leaked`: boolean or null
* `multi_repo`: boolean or null
* `is_base64_encoded`: boolean or null
* `first_location_detected`: any of:
  * **null**
  * **object**
* `has_more_locations`: boolean
* `assigned_to`: any of:
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
* `closure_request_comment`: string or null
* `closure_request_reviewer_comment`: string or null
* `closure_request_reviewer`: any of:
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

## Update a secret scanning alert

```
PATCH /repos/{owner}/{repo}/secret-scanning/alerts/{alert_number}
```

Updates the status of a secret scanning alert in an eligible repository.
You can also use this endpoint to assign or unassign an alert to a user who has write access to the repository.
The authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo or security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

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
  Sets the state of the secret scanning alert. You must provide resolution when you set the state to resolved.
  Can be one of: `open`, `resolved`

* **`resolution`** (string or null)
  Required when the state is resolved. The reason for resolving the alert.
  Can be one of: `false_positive`, `wont_fix`, `revoked`, `used_in_tests`, `null`

* **`resolution_comment`** (string or null)
  An optional comment when closing or reopening an alert. Cannot be updated or deleted.

* **`assignee`** (string or null)
  The username of the user to assign to the alert. Set to null to unassign the alert.

### HTTP response status codes

* **200** - OK

* **400** - Bad request, resolution comment is invalid or the resolution was not changed.

* **404** - Repository is public, or secret scanning is disabled for the repository, or the resource is not found

* **422** - State does not match the resolution or resolution comment, or assignee does not have write access to the repository

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/alerts/ALERT_NUMBER \
  -d '{
  "state": "resolved",
  "resolution": "false_positive"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a secret scanning alert](#get-a-secret-scanning-alert).

## List locations for a secret scanning alert

```
GET /repos/{owner}/{repo}/secret-scanning/alerts/{alert_number}/locations
```

Lists all locations for a given secret scanning alert for an eligible repository.
The authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo or security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

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

### HTTP response status codes

* **200** - OK

* **404** - Repository is public, or secret scanning is disabled for the repository, or the resource is not found

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/alerts/ALERT_NUMBER/locations
```

**Response schema (Status: 200):**

Array of objects:

* `type`: string, enum: `commit`, `wiki_commit`, `issue_title`, `issue_body`, `issue_comment`, `discussion_title`, `discussion_body`, `discussion_comment`, `pull_request_title`, `pull_request_body`, `pull_request_comment`, `pull_request_review`, `pull_request_review_comment`
* `details`: one of:
  * **object**
    * `path`: required, string
    * `start_line`: required, number
    * `end_line`: required, number
    * `start_column`: required, number
    * `end_column`: required, number
    * `blob_sha`: required, string
    * `blob_url`: required, string
    * `commit_sha`: required, string
    * `commit_url`: required, string
    * `html_url`: string, format: uri
  * **object**
    * `path`: required, string
    * `start_line`: required, number
    * `end_line`: required, number
    * `start_column`: required, number
    * `end_column`: required, number
    * `blob_sha`: required, string
    * `page_url`: required, string
    * `commit_sha`: required, string
    * `commit_url`: required, string
  * **object**
    * `issue_title_url`: required, string, format: uri
    * `html_url`: string, format: uri
  * **object**
    * `issue_body_url`: required, string, format: uri
    * `html_url`: string, format: uri
  * **object**
    * `issue_comment_url`: required, string, format: uri
    * `html_url`: string, format: uri
  * **object**
    * `discussion_title_url`: required, string, format: uri
  * **object**
    * `discussion_body_url`: required, string, format: uri
  * **object**
    * `discussion_comment_url`: required, string, format: uri
  * **object**
    * `pull_request_title_url`: required, string, format: uri
    * `html_url`: string, format: uri
  * **object**
    * `pull_request_body_url`: required, string, format: uri
    * `html_url`: string, format: uri
  * **object**
    * `pull_request_comment_url`: required, string, format: uri
    * `html_url`: string, format: uri
  * **object**
    * `pull_request_review_url`: required, string, format: uri
    * `html_url`: string, format: uri
  * **object**
    * `pull_request_review_comment_url`: required, string, format: uri
    * `html_url`: string, format: uri

## Create a push protection bypass

```
POST /repos/{owner}/{repo}/secret-scanning/push-protection-bypasses
```

Creates a bypass for a previously push protected secret.
The authenticated user must be the original author of the committed secret.
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

* **`reason`** (string) (required)
  The reason for bypassing push protection.
  Can be one of: `false_positive`, `used_in_tests`, `will_fix_later`

* **`placeholder_id`** (string) (required)
  The ID of the push protection bypass placeholder. This value is returned on any push protected routes.

### HTTP response status codes

* **200** - OK

* **403** - User does not have enough permissions to perform this action.

* **404** - Placeholder ID not found, or push protection is disabled on this repository.

* **422** - Bad request, input data missing or incorrect.

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/push-protection-bypasses \
  -d '{
  "reason": "will_fix_later",
  "placeholder_id": "2k4dM4tseyC5lPIsjl5emX9sPNk"
}'
```

**Response schema (Status: 200):**

* `reason`: string, enum: `false_positive`, `used_in_tests`, `will_fix_later`
* `expire_at`: string or null, format: date-time
* `token_type`: string

## Get secret scanning scan history for a repository

```
GET /repos/{owner}/{repo}/secret-scanning/scan-history
```

Lists the latest default incremental and backfill scans by type for a repository.
Note

This endpoint requires GitHub Advanced Security.

OAuth app tokens and personal access tokens (classic) need the repo or security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

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

* **404** - Repository does not have GitHub Advanced Security or secret scanning enabled

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/scan-history
```

**Response schema (Status: 200):**

* `incremental_scans`: array of objects:
  * `type`: string
  * `status`: string
  * `completed_at`: string or null, format: date-time
  * `started_at`: string or null, format: date-time
* `pattern_update_scans`: array of objects:
  * `type`: string
  * `status`: string
  * `completed_at`: string or null, format: date-time
  * `started_at`: string or null, format: date-time
* `backfill_scans`: array of objects:
  * `type`: string
  * `status`: string
  * `completed_at`: string or null, format: date-time
  * `started_at`: string or null, format: date-time
* `custom_pattern_backfill_scans`: array of object
* `generic_secrets_backfill_scans`: array of objects:
  * `type`: string
  * `status`: string
  * `completed_at`: string or null, format: date-time
  * `started_at`: string or null, format: date-time