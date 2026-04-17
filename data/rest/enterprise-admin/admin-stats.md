# REST API endpoints for admin stats

Use the REST API to retrieve a variety of metrics about your installation.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get GitHub Enterprise Server statistics

```
GET /enterprise-installation/{enterprise_or_org}/server-statistics
```

Returns aggregate usage metrics for your GitHub Enterprise Server 3.5+ instance for a specified time period up to 365 days.
To use this endpoint, your GitHub Enterprise Server instance must be connected to GitHub Enterprise Cloud using GitHub Connect. You must enable Server Statistics, and for the API request provide your enterprise account name or organization name connected to the GitHub Enterprise Server. For more information, see "Enabling Server Statistics for your enterprise" in the GitHub Enterprise Server documentation.
OAuth app tokens and personal access tokens (classic) need:

the read:enterprise scope if you connected your GitHub Enterprise Server to an enterprise account and enabled Server Statistics
the read:org scope if you connected your GitHub Enterprise Server to an organization account and enabled Server Statistics

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise_or_org`** (string) (required)
  The slug version of the enterprise name or the login of an organization.

* **`date_start`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for events after this cursor.

* **`date_end`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for events before this cursor.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprise-installation/ENTERPRISE_OR_ORG/server-statistics
```

**Response schema (Status: 200):**

Array of objects:

* `server_id`: string
* `collection_date`: string
* `schema_version`: string
* `ghes_version`: string
* `host_name`: string
* `github_connect`: object:
  * `features_enabled`: array of string
* `ghe_stats`: object:
  * `comments`: object:
    * `total_commit_comments`: integer
    * `total_gist_comments`: integer
    * `total_issue_comments`: integer
    * `total_pull_request_comments`: integer
  * `gists`: object:
    * `total_gists`: integer
    * `private_gists`: integer
    * `public_gists`: integer
  * `hooks`: object:
    * `total_hooks`: integer
    * `active_hooks`: integer
    * `inactive_hooks`: integer
  * `issues`: object:
    * `total_issues`: integer
    * `open_issues`: integer
    * `closed_issues`: integer
  * `milestones`: object:
    * `total_milestones`: integer
    * `open_milestones`: integer
    * `closed_milestones`: integer
  * `orgs`: object:
    * `total_orgs`: integer
    * `disabled_orgs`: integer
    * `total_teams`: integer
    * `total_team_members`: integer
  * `pages`: object:
    * `total_pages`: integer
  * `pulls`: object:
    * `total_pulls`: integer
    * `merged_pulls`: integer
    * `mergeable_pulls`: integer
    * `unmergeable_pulls`: integer
  * `repos`: object:
    * `total_repos`: integer
    * `root_repos`: integer
    * `fork_repos`: integer
    * `org_repos`: integer
    * `total_pushes`: integer
    * `total_wikis`: integer
  * `users`: object:
    * `total_users`: integer
    * `admin_users`: integer
    * `suspended_users`: integer
* `dormant_users`: object:
  * `total_dormant_users`: integer
  * `dormancy_threshold`: string
* `actions_stats`: object:
  * `number_of_repos_using_actions`: integer
  * `percentage_of_repos_using_actions`: string
* `packages_stats`: object:
  * `registry_enabled`: boolean
  * `registry_v2_enabled`: boolean
  * `ecosystems`: array of objects:
    * `name`: string, enum: `npm`, `maven`, `docker`, `nuget`, `rubygems`, `containers`
    * `enabled`: string, enum: `TRUE`, `FALSE`, `READONLY`
    * `published_packages_count`: integer
    * `private_packages_count`: integer
    * `public_packages_count`: integer
    * `internal_packages_count`: integer
    * `user_packages_count`: integer
    * `organization_packages_count`: integer
    * `daily_download_count`: integer
    * `daily_update_count`: integer
    * `daily_delete_count`: integer
    * `daily_create_count`: integer