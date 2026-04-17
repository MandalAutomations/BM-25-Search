# REST API endpoints for {% data variables.product.prodname\_dependabot\_alerts %}

Use the REST API to interact with Dependabot alerts for a repository.

> \[!NOTE]
> The ability to use the REST API to manage Dependabot alerts is currently in public preview and subject to change.

## About Dependabot alerts

You can view Dependabot alerts for a repository and update individual alerts with the REST API. For more information, see [About Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List Dependabot alerts for an enterprise

```
GET /enterprises/{enterprise}/dependabot/alerts
```

Lists Dependabot alerts for repositories that are owned by the specified enterprise.
The authenticated user must be a member of the enterprise to use this endpoint.
Alerts are only returned for organizations in the enterprise for which you are an organization owner or a security manager. For more information about security managers, see "Managing security managers in your organization."
OAuth app tokens and personal access tokens (classic) need the repo or security\_events scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`classification`** (string)
  A comma-separated list of vulnerability classifications. If specified, only alerts for vulnerabilities with these classifications will be returned.
  Can be: malware, general

* **`state`** (string)
  A comma-separated list of states. If specified, only alerts with these states will be returned.
  Can be: auto\_dismissed, dismissed, fixed, open

* **`severity`** (string)
  A comma-separated list of severities. If specified, only alerts with these severities will be returned.
  Can be: low, medium, high, critical

* **`ecosystem`** (string)
  A comma-separated list of ecosystems. If specified, only alerts for these ecosystems will be returned.
  Can be: composer, go, maven, npm, nuget, pip, pub, rubygems, rust

* **`package`** (string)
  A comma-separated list of package names. If specified, only alerts for these packages will be returned.

* **`epss_percentage`** (string)
  CVE Exploit Prediction Scoring System (EPSS) percentage. Can be specified as:

An exact number (n)
Comparators such as >n, \<n, >=n, <=n
A range like n..n, where n is a number from 0.0 to 1.0

Filters the list of alerts based on EPSS percentages. If specified, only alerts with the provided EPSS percentages will be returned.

* **`has`** (string)
  Filters the list of alerts based on whether the alert has the given value. If specified, only alerts meeting this criterion will be returned.
  Multiple has filters can be passed to filter for alerts that have all of the values. Currently, only patch is supported.

* **`assignee`** (string)
  Filter alerts by assignees.
  Provide a comma-separated list of user handles (e.g., octocat or octocat,hubot) to return alerts assigned to any of the specified users.
  Use \* to list alerts with at least one assignee or none to list alerts with no assignees.

* **`scope`** (string)
  The scope of the vulnerable dependency. If specified, only alerts with this scope will be returned.
  Can be one of: `development`, `runtime`

* **`sort`** (string)
  The property by which to sort the results.
  created means when the alert was created.
  updated means when the alert's state last changed.
  epss\_percentage sorts alerts by the Exploit Prediction Scoring System (EPSS) percentage.
  Default: `created`
  Can be one of: `created`, `updated`, `epss_percentage`

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

* **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/dependabot/alerts
```

**Response schema (Status: 200):**

Array of objects:

* `number`: required, integer, read-only
* `state`: required, string, enum: `auto_dismissed`, `dismissed`, `fixed`, `open`, read-only
* `dependency`: required, object, read-only:
  * `package`: object, read-only:
    * `ecosystem`: required, string, read-only
    * `name`: required, string, read-only
  * `manifest_path`: string, read-only
  * `scope`: string or null, enum: `development`, `runtime`, `null`, read-only
  * `relationship`: string or null, enum: `unknown`, `direct`, `transitive`, `inconclusive`, `null`, read-only
* `security_advisory`: required, object, read-only:
  * `ghsa_id`: required, string, read-only
  * `cve_id`: required, string or null, read-only
  * `summary`: required, string, read-only, maxLength: 1024
  * `description`: required, string, read-only
  * `vulnerabilities`: required, array of objects:
    * `package`: required, object, read-only:
      * `ecosystem`: required, string, read-only
      * `name`: required, string, read-only
    * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
    * `vulnerable_version_range`: required, string, read-only
    * `first_patched_version`: required, object or null, read-only:
      * `identifier`: required, string, read-only
  * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
  * `classification`: string, enum: `general`, `malware`, read-only
  * `cvss_severities`: object or null:
    * `cvss_v3`: object or null:
      * `vector_string`: required, string or null
      * `score`: required, number or null, read-only, minimum: 0, maximum: 10
    * `cvss_v4`: object or null:
      * `vector_string`: required, string or null
      * `score`: required, number or null, read-only, minimum: 0, maximum: 10
  * `epss`: object or null, read-only:
    * `percentage`: number, minimum: 0, maximum: 100
    * `percentile`: number, minimum: 0, maximum: 100
  * `cwes`: required, array of objects:
    * `cwe_id`: required, string, read-only
    * `name`: required, string, read-only
  * `identifiers`: required, array of objects:
    * `type`: required, string, enum: `CVE`, `GHSA`, read-only
    * `value`: required, string, read-only
  * `references`: required, array of objects:
    * `url`: required, string, format: uri, read-only
  * `published_at`: required, string, format: date-time, read-only
  * `updated_at`: required, string, format: date-time, read-only
  * `withdrawn_at`: required, string or null, format: date-time, read-only
* `security_vulnerability`: required, object, read-only:
  * `package`: required, object, read-only:
    * `ecosystem`: required, string, read-only
    * `name`: required, string, read-only
  * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
  * `vulnerable_version_range`: required, string, read-only
  * `first_patched_version`: required, object or null, read-only:
    * `identifier`: required, string, read-only
* `url`: required, string, format: uri, read-only
* `html_url`: required, string, format: uri, read-only
* `created_at`: required, string, format: date-time, read-only
* `updated_at`: required, string, format: date-time, read-only
* `dismissed_at`: required, string or null, format: date-time, read-only
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
* `dismissed_reason`: required, string or null, enum: `fix_started`, `inaccurate`, `no_bandwidth`, `not_used`, `tolerable_risk`, `null`
* `dismissed_comment`: required, string or null, maxLength: 280
* `fixed_at`: required, string or null, format: date-time, read-only
* `auto_dismissed_at`: string or null, format: date-time, read-only
* `dismissal_request`: `Dependabot alert dismissal request`:
  * `id`: integer
  * `status`: string, enum: `pending`, `approved`, `rejected`, `cancelled`
  * `requester`: object:
    * `id`: integer
    * `login`: string
  * `created_at`: string, format: date-time
  * `url`: string, format: uri
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

## List Dependabot alerts for an organization

```
GET /orgs/{org}/dependabot/alerts
```

Lists Dependabot alerts for an organization.
The authenticated user must be an owner or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`classification`** (string)
  A comma-separated list of vulnerability classifications. If specified, only alerts for vulnerabilities with these classifications will be returned.
  Can be: malware, general

* **`state`** (string)
  A comma-separated list of states. If specified, only alerts with these states will be returned.
  Can be: auto\_dismissed, dismissed, fixed, open

* **`severity`** (string)
  A comma-separated list of severities. If specified, only alerts with these severities will be returned.
  Can be: low, medium, high, critical

* **`ecosystem`** (string)
  A comma-separated list of ecosystems. If specified, only alerts for these ecosystems will be returned.
  Can be: composer, go, maven, npm, nuget, pip, pub, rubygems, rust

* **`package`** (string)
  A comma-separated list of package names. If specified, only alerts for these packages will be returned.

* **`epss_percentage`** (string)
  CVE Exploit Prediction Scoring System (EPSS) percentage. Can be specified as:

An exact number (n)
Comparators such as >n, \<n, >=n, <=n
A range like n..n, where n is a number from 0.0 to 1.0

Filters the list of alerts based on EPSS percentages. If specified, only alerts with the provided EPSS percentages will be returned.

* **`artifact_registry_url`** (string)
  A comma-separated list of artifact registry URLs. If specified, only alerts for repositories with storage records matching these URLs will be returned.

* **`artifact_registry`** (string)
  A comma-separated list of Artifact Registry name strings. If specified, only alerts for repositories with storage records matching these registries will be returned.
  Can be: jfrog-artifactory

* **`has`** (string)
  Filters the list of alerts based on whether the alert has the given value. If specified, only alerts meeting this criterion will be returned.
  Multiple has filters can be passed to filter for alerts that have all of the values.

* **`assignee`** (string)
  Filter alerts by assignees.
  Provide a comma-separated list of user handles (e.g., octocat or octocat,hubot) to return alerts assigned to any of the specified users.
  Use \* to list alerts with at least one assignee or none to list alerts with no assignees.

* **`runtime_risk`** (string)
  A comma-separated list of runtime risk strings. If specified, only alerts for repositories with deployment records matching these risks will be returned.
  Can be: critical-resource, internet-exposed, sensitive-data, lateral-movement

* **`scope`** (string)
  The scope of the vulnerable dependency. If specified, only alerts with this scope will be returned.
  Can be one of: `development`, `runtime`

* **`sort`** (string)
  The property by which to sort the results.
  created means when the alert was created.
  updated means when the alert's state last changed.
  epss\_percentage sorts alerts by the Exploit Prediction Scoring System (EPSS) percentage.
  Default: `created`
  Can be one of: `created`, `updated`, `epss_percentage`

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

* **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/dependabot/alerts
```

**Response schema (Status: 200):**

Same response schema as [List Dependabot alerts for an enterprise](#list-dependabot-alerts-for-an-enterprise).

## List Dependabot alerts for a repository

```
GET /repos/{owner}/{repo}/dependabot/alerts
```

OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`classification`** (string)
  A comma-separated list of vulnerability classifications. If specified, only alerts for vulnerabilities with these classifications will be returned.
  Can be: malware, general

* **`state`** (string)
  A comma-separated list of states. If specified, only alerts with these states will be returned.
  Can be: auto\_dismissed, dismissed, fixed, open

* **`severity`** (string)
  A comma-separated list of severities. If specified, only alerts with these severities will be returned.
  Can be: low, medium, high, critical

* **`ecosystem`** (string)
  A comma-separated list of ecosystems. If specified, only alerts for these ecosystems will be returned.
  Can be: composer, go, maven, npm, nuget, pip, pub, rubygems, rust

* **`package`** (string)
  A comma-separated list of package names. If specified, only alerts for these packages will be returned.

* **`manifest`** (string)
  A comma-separated list of full manifest paths. If specified, only alerts for these manifests will be returned.

* **`epss_percentage`** (string)
  CVE Exploit Prediction Scoring System (EPSS) percentage. Can be specified as:

An exact number (n)
Comparators such as >n, \<n, >=n, <=n
A range like n..n, where n is a number from 0.0 to 1.0

Filters the list of alerts based on EPSS percentages. If specified, only alerts with the provided EPSS percentages will be returned.

* **`has`** (string)
  Filters the list of alerts based on whether the alert has the given value. If specified, only alerts meeting this criterion will be returned.
  Multiple has filters can be passed to filter for alerts that have all of the values. Currently, only patch is supported.

* **`assignee`** (string)
  Filter alerts by assignees.
  Provide a comma-separated list of user handles (e.g., octocat or octocat,hubot) to return alerts assigned to any of the specified users.
  Use \* to list alerts with at least one assignee or none to list alerts with no assignees.

* **`scope`** (string)
  The scope of the vulnerable dependency. If specified, only alerts with this scope will be returned.
  Can be one of: `development`, `runtime`

* **`sort`** (string)
  The property by which to sort the results.
  created means when the alert was created.
  updated means when the alert's state last changed.
  epss\_percentage sorts alerts by the Exploit Prediction Scoring System (EPSS) percentage.
  Default: `created`
  Can be one of: `created`, `updated`, `epss_percentage`

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

* **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dependabot/alerts
```

**Response schema (Status: 200):**

Array of objects:

* `number`: required, integer, read-only
* `state`: required, string, enum: `auto_dismissed`, `dismissed`, `fixed`, `open`, read-only
* `dependency`: required, object, read-only:
  * `package`: object, read-only:
    * `ecosystem`: required, string, read-only
    * `name`: required, string, read-only
  * `manifest_path`: string, read-only
  * `scope`: string or null, enum: `development`, `runtime`, `null`, read-only
  * `relationship`: string or null, enum: `unknown`, `direct`, `transitive`, `inconclusive`, `null`, read-only
* `security_advisory`: required, object, read-only:
  * `ghsa_id`: required, string, read-only
  * `cve_id`: required, string or null, read-only
  * `summary`: required, string, read-only, maxLength: 1024
  * `description`: required, string, read-only
  * `vulnerabilities`: required, array of objects:
    * `package`: required, object, read-only:
      * `ecosystem`: required, string, read-only
      * `name`: required, string, read-only
    * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
    * `vulnerable_version_range`: required, string, read-only
    * `first_patched_version`: required, object or null, read-only:
      * `identifier`: required, string, read-only
  * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
  * `classification`: string, enum: `general`, `malware`, read-only
  * `cvss_severities`: object or null:
    * `cvss_v3`: object or null:
      * `vector_string`: required, string or null
      * `score`: required, number or null, read-only, minimum: 0, maximum: 10
    * `cvss_v4`: object or null:
      * `vector_string`: required, string or null
      * `score`: required, number or null, read-only, minimum: 0, maximum: 10
  * `epss`: object or null, read-only:
    * `percentage`: number, minimum: 0, maximum: 100
    * `percentile`: number, minimum: 0, maximum: 100
  * `cwes`: required, array of objects:
    * `cwe_id`: required, string, read-only
    * `name`: required, string, read-only
  * `identifiers`: required, array of objects:
    * `type`: required, string, enum: `CVE`, `GHSA`, read-only
    * `value`: required, string, read-only
  * `references`: required, array of objects:
    * `url`: required, string, format: uri, read-only
  * `published_at`: required, string, format: date-time, read-only
  * `updated_at`: required, string, format: date-time, read-only
  * `withdrawn_at`: required, string or null, format: date-time, read-only
* `security_vulnerability`: required, object, read-only:
  * `package`: required, object, read-only:
    * `ecosystem`: required, string, read-only
    * `name`: required, string, read-only
  * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
  * `vulnerable_version_range`: required, string, read-only
  * `first_patched_version`: required, object or null, read-only:
    * `identifier`: required, string, read-only
* `url`: required, string, format: uri, read-only
* `html_url`: required, string, format: uri, read-only
* `created_at`: required, string, format: date-time, read-only
* `updated_at`: required, string, format: date-time, read-only
* `dismissed_at`: required, string or null, format: date-time, read-only
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
* `dismissed_reason`: required, string or null, enum: `fix_started`, `inaccurate`, `no_bandwidth`, `not_used`, `tolerable_risk`, `null`
* `dismissed_comment`: required, string or null, maxLength: 280
* `fixed_at`: required, string or null, format: date-time, read-only
* `auto_dismissed_at`: string or null, format: date-time, read-only
* `dismissal_request`: `Dependabot alert dismissal request`:
  * `id`: integer
  * `status`: string, enum: `pending`, `approved`, `rejected`, `cancelled`
  * `requester`: object:
    * `id`: integer
    * `login`: string
  * `created_at`: string, format: date-time
  * `url`: string, format: uri
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

## Get a Dependabot alert

```
GET /repos/{owner}/{repo}/dependabot/alerts/{alert_number}
```

OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

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
  The number that identifies a Dependabot alert in its repository.
  You can find this at the end of the URL for a Dependabot alert within GitHub,
  or in number fields in the response from the
  GET /repos/{owner}/{repo}/dependabot/alerts operation.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dependabot/alerts/ALERT_NUMBER
```

**Response schema (Status: 200):**

* `number`: required, integer, read-only
* `state`: required, string, enum: `auto_dismissed`, `dismissed`, `fixed`, `open`, read-only
* `dependency`: required, object, read-only:
  * `package`: object, read-only:
    * `ecosystem`: required, string, read-only
    * `name`: required, string, read-only
  * `manifest_path`: string, read-only
  * `scope`: string or null, enum: `development`, `runtime`, `null`, read-only
  * `relationship`: string or null, enum: `unknown`, `direct`, `transitive`, `inconclusive`, `null`, read-only
* `security_advisory`: required, object, read-only:
  * `ghsa_id`: required, string, read-only
  * `cve_id`: required, string or null, read-only
  * `summary`: required, string, read-only, maxLength: 1024
  * `description`: required, string, read-only
  * `vulnerabilities`: required, array of objects:
    * `package`: required, object, read-only:
      * `ecosystem`: required, string, read-only
      * `name`: required, string, read-only
    * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
    * `vulnerable_version_range`: required, string, read-only
    * `first_patched_version`: required, object or null, read-only:
      * `identifier`: required, string, read-only
  * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
  * `classification`: string, enum: `general`, `malware`, read-only
  * `cvss_severities`: object or null:
    * `cvss_v3`: object or null:
      * `vector_string`: required, string or null
      * `score`: required, number or null, read-only, minimum: 0, maximum: 10
    * `cvss_v4`: object or null:
      * `vector_string`: required, string or null
      * `score`: required, number or null, read-only, minimum: 0, maximum: 10
  * `epss`: object or null, read-only:
    * `percentage`: number, minimum: 0, maximum: 100
    * `percentile`: number, minimum: 0, maximum: 100
  * `cwes`: required, array of objects:
    * `cwe_id`: required, string, read-only
    * `name`: required, string, read-only
  * `identifiers`: required, array of objects:
    * `type`: required, string, enum: `CVE`, `GHSA`, read-only
    * `value`: required, string, read-only
  * `references`: required, array of objects:
    * `url`: required, string, format: uri, read-only
  * `published_at`: required, string, format: date-time, read-only
  * `updated_at`: required, string, format: date-time, read-only
  * `withdrawn_at`: required, string or null, format: date-time, read-only
* `security_vulnerability`: required, object, read-only:
  * `package`: required, object, read-only:
    * `ecosystem`: required, string, read-only
    * `name`: required, string, read-only
  * `severity`: required, string, enum: `low`, `medium`, `high`, `critical`, read-only
  * `vulnerable_version_range`: required, string, read-only
  * `first_patched_version`: required, object or null, read-only:
    * `identifier`: required, string, read-only
* `url`: required, string, format: uri, read-only
* `html_url`: required, string, format: uri, read-only
* `created_at`: required, string, format: date-time, read-only
* `updated_at`: required, string, format: date-time, read-only
* `dismissed_at`: required, string or null, format: date-time, read-only
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
* `dismissed_reason`: required, string or null, enum: `fix_started`, `inaccurate`, `no_bandwidth`, `not_used`, `tolerable_risk`, `null`
* `dismissed_comment`: required, string or null, maxLength: 280
* `fixed_at`: required, string or null, format: date-time, read-only
* `auto_dismissed_at`: string or null, format: date-time, read-only
* `dismissal_request`: `Dependabot alert dismissal request`:
  * `id`: integer
  * `status`: string, enum: `pending`, `approved`, `rejected`, `cancelled`
  * `requester`: object:
    * `id`: integer
    * `login`: string
  * `created_at`: string, format: date-time
  * `url`: string, format: uri
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

## Update a Dependabot alert

```
PATCH /repos/{owner}/{repo}/dependabot/alerts/{alert_number}
```

The authenticated user must have access to security alerts for the repository to use this endpoint. For more information, see "Granting access to security alerts."
OAuth app tokens and personal access tokens (classic) need the security\_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public\_repo scope instead.

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
  The number that identifies a Dependabot alert in its repository.
  You can find this at the end of the URL for a Dependabot alert within GitHub,
  or in number fields in the response from the
  GET /repos/{owner}/{repo}/dependabot/alerts operation.

#### Body parameters

* **`state`** (string)
  The state of the Dependabot alert.
  A dismissed\_reason must be provided when setting the state to dismissed.
  Can be one of: `dismissed`, `open`

* **`dismissed_reason`** (string)
  Required when state is dismissed. A reason for dismissing the alert.
  Can be one of: `fix_started`, `inaccurate`, `no_bandwidth`, `not_used`, `tolerable_risk`

* **`dismissed_comment`** (string)
  An optional comment associated with dismissing the alert.

* **`assignees`** (array of strings)
  Usernames to assign to this Dependabot Alert.
  Pass one or more user logins to replace the set of assignees on this alert.
  Send an empty array (\[]) to clear all assignees from the alert.

### HTTP response status codes

* **200** - OK

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

* **409** - Conflict

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/dependabot/alerts/ALERT_NUMBER \
  -d '{
  "state": "dismissed",
  "dismissed_reason": "tolerable_risk",
  "dismissed_comment": "This alert is accurate but we use a sanitizer."
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a Dependabot alert](#get-a-dependabot-alert).