# REST API endpoints for teams

Use the REST API to create and manage teams in your GitHub organization.

## About teams

These endpoints are only available to authenticated members of the team's [organization](/en/rest/orgs). OAuth access tokens require the `read:org` [scope](/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps). GitHub generates the team's `slug` from the team `name`.

Where `pull` and `push` permissions are accepted, these will map to the **Read** and **Write** roles for an organization repository. For more information about repository roles, see [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List teams

```
GET /orgs/{org}/teams
```

Lists all teams in an organization that are visible to the authenticated user.

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

* **`team_type`** (string)
  Filter team results by their type. For more information, see "What kind of team should I use?"
  Default: `all`
  Can be one of: `all`, `enterprise`, `organization`

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/teams
```

**Response schema (Status: 200):**

Array of `Team`:

* `id`: required, integer
* `node_id`: required, string
* `name`: required, string
* `slug`: required, string
* `description`: required, string or null
* `privacy`: string
* `notification_setting`: string
* `permission`: required, string
* `permissions`: object:
  * `pull`: required, boolean
  * `triage`: required, boolean
  * `push`: required, boolean
  * `maintain`: required, boolean
  * `admin`: required, boolean
* `url`: required, string, format: uri
* `html_url`: required, string, format: uri
* `members_url`: required, string
* `repositories_url`: required, string, format: uri
* `type`: required, string, enum: `enterprise`, `organization`
* `organization_id`: integer
* `enterprise_id`: integer
* `parent`: required, any of:
  * **null**
  * **Team Simple**
    * `id`: required, integer
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `members_url`: required, string
    * `name`: required, string
    * `description`: required, string or null
    * `permission`: required, string
    * `privacy`: string
    * `notification_setting`: string
    * `html_url`: required, string, format: uri
    * `repositories_url`: required, string, format: uri
    * `slug`: required, string
    * `ldap_dn`: string
    * `type`: required, string, enum: `enterprise`, `organization`
    * `organization_id`: integer
    * `enterprise_id`: integer

## Create a team

```
POST /orgs/{org}/teams
```

To create a team, the authenticated user must be a member or owner of {org}. By default, organization members can create teams. Organization owners can limit team creation to organization owners. For more information, see "Setting team creation permissions."
When you create a new team, you automatically become a team maintainer without explicitly adding yourself to the optional array of maintainers. For more information, see "About teams".

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`name`** (string) (required)
  The name of the team.

* **`description`** (string)
  The description of the team.

* **`maintainers`** (array of strings)
  List GitHub usernames for organization members who will become team maintainers.

* **`repo_names`** (array of strings)
  The full name (e.g., "organization-name/repository-name") of repositories to add the team to.

* **`privacy`** (string)
  The level of privacy this team should have. The options are:
  For a non-nested team:

secret - only visible to organization owners and members of this team.
closed - visible to all members of this organization.
Default: secret
For a parent or child team:
closed - visible to all members of this organization.
Default for child team: closed
Can be one of: `secret`, `closed`

* **`notification_setting`** (string)
  The notification setting the team has chosen. The options are:

notifications\_enabled - team members receive notifications when the team is @mentioned.
notifications\_disabled - no one receives notifications.
Default: notifications\_enabled
Can be one of: `notifications_enabled`, `notifications_disabled`

* **`parent_team_id`** (integer)
  The ID of a team to set as the parent team.

### HTTP response status codes

* **201** - Created

* **403** - Forbidden

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/teams \
  -d '{
  "name": "Justice League",
  "description": "A great team",
  "permission": "push",
  "notification_setting": "notifications_enabled",
  "privacy": "closed"
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `node_id`: required, string
* `url`: required, string, format: uri
* `html_url`: required, string, format: uri
* `name`: required, string
* `slug`: required, string
* `description`: required, string or null
* `privacy`: string, enum: `closed`, `secret`
* `notification_setting`: string, enum: `notifications_enabled`, `notifications_disabled`
* `permission`: required, string
* `members_url`: required, string
* `repositories_url`: required, string, format: uri
* `parent`: any of:
  * **null**
  * **Team Simple**
    * `id`: required, integer
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `members_url`: required, string
    * `name`: required, string
    * `description`: required, string or null
    * `permission`: required, string
    * `privacy`: string
    * `notification_setting`: string
    * `html_url`: required, string, format: uri
    * `repositories_url`: required, string, format: uri
    * `slug`: required, string
    * `ldap_dn`: string
    * `type`: required, string, enum: `enterprise`, `organization`
    * `organization_id`: integer
    * `enterprise_id`: integer
* `members_count`: required, integer
* `repos_count`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `organization`: required, `Team Organization`:
  * `login`: required, string
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string, format: uri
  * `repos_url`: required, string, format: uri
  * `events_url`: required, string, format: uri
  * `hooks_url`: required, string
  * `issues_url`: required, string
  * `members_url`: required, string
  * `public_members_url`: required, string
  * `avatar_url`: required, string
  * `description`: required, string or null
  * `name`: string
  * `company`: string
  * `blog`: string, format: uri
  * `location`: string
  * `email`: string, format: email
  * `twitter_username`: string or null
  * `is_verified`: boolean
  * `has_organization_projects`: required, boolean
  * `has_repository_projects`: required, boolean
  * `public_repos`: required, integer
  * `public_gists`: required, integer
  * `followers`: required, integer
  * `following`: required, integer
  * `html_url`: required, string, format: uri
  * `created_at`: required, string, format: date-time
  * `type`: required, string
  * `total_private_repos`: integer
  * `owned_private_repos`: integer
  * `private_gists`: integer or null
  * `disk_usage`: integer or null
  * `collaborators`: integer or null
  * `billing_email`: string or null, format: email
  * `plan`: object:
    * `name`: required, string
    * `space`: required, integer
    * `private_repos`: required, integer
    * `filled_seats`: integer
    * `seats`: integer
  * `default_repository_permission`: string or null
  * `members_can_create_repositories`: boolean or null
  * `two_factor_requirement_enabled`: boolean or null
  * `members_allowed_repository_creation_type`: string
  * `members_can_create_public_repositories`: boolean
  * `members_can_create_private_repositories`: boolean
  * `members_can_create_internal_repositories`: boolean
  * `members_can_create_pages`: boolean
  * `members_can_create_public_pages`: boolean
  * `members_can_create_private_pages`: boolean
  * `members_can_fork_private_repositories`: boolean or null
  * `web_commit_signoff_required`: boolean
  * `updated_at`: required, string, format: date-time
  * `archived_at`: required, string or null, format: date-time
* `ldap_dn`: string
* `type`: required, string, enum: `enterprise`, `organization`
* `organization_id`: integer
* `enterprise_id`: integer

## Get a team by name

```
GET /orgs/{org}/teams/{team_slug}
```

Gets a team using the team's slug. To create the slug, GitHub replaces special characters in the name string, changes all words to lowercase, and replaces spaces with a - separator. For example, "My TEam Näme" would become my-team-name.
Note

You can also specify a team by org\_id and team\_id using the route GET /organizations/{org\_id}/team/{team\_id}.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG
```

**Response schema (Status: 200):**

Same response schema as [Create a team](#create-a-team).

## Update a team

```
PATCH /orgs/{org}/teams/{team_slug}
```

To edit a team, the authenticated user must either be an organization owner or a team maintainer.
Note

You can also specify a team by org\_id and team\_id using the route PATCH /organizations/{org\_id}/team/{team\_id}.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

#### Body parameters

* **`name`** (string)
  The name of the team.

* **`description`** (string)
  The description of the team.

* **`privacy`** (string)
  The level of privacy this team should have. Editing teams without specifying this parameter leaves privacy intact. When a team is nested, the privacy for parent teams cannot be secret. The options are:
  For a non-nested team:

secret - only visible to organization owners and members of this team.
closed - visible to all members of this organization.
For a parent or child team:
closed - visible to all members of this organization.
Can be one of: `secret`, `closed`

* **`notification_setting`** (string)
  The notification setting the team has chosen. Editing teams without specifying this parameter leaves notification\_setting intact. The options are:

notifications\_enabled - team members receive notifications when the team is @mentioned.
notifications\_disabled - no one receives notifications.
Can be one of: `notifications_enabled`, `notifications_disabled`

* **`permission`** (string)
  Closing down notice. The permission that new repositories will be added to the team with when none is specified.
  Default: `pull`
  Can be one of: `pull`, `push`, `admin`

* **`parent_team_id`** (integer or null)
  The ID of a team to set as the parent team.

### HTTP response status codes

* **200** - Response when the updated information already exists

* **201** - Created

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG \
  -d '{
  "name": "new team name",
  "description": "new team description",
  "privacy": "closed",
  "notification_setting": "notifications_enabled"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a team](#create-a-team).

#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG \
  -d '{
  "name": "new team name",
  "description": "new team description",
  "privacy": "closed",
  "notification_setting": "notifications_enabled"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a team](#create-a-team).

## Delete a team

```
DELETE /orgs/{org}/teams/{team_slug}
```

To delete a team, the authenticated user must be an organization owner or team maintainer.
If you are an organization owner, deleting a parent team will delete all of its child teams as well.
Note

You can also specify a team by org\_id and team\_id using the route DELETE /organizations/{org\_id}/team/{team\_id}.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

### HTTP response status codes

* **204** - No Content

* **422** - Unprocessable entity if you attempt to modify an enterprise team at the organization level.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG
```

**Response schema (Status: 204):**

## List team repositories

```
GET /orgs/{org}/teams/{team_slug}/repos
```

Lists a team's repositories visible to the authenticated user.
Note

You can also specify a team by org\_id and team\_id using the route GET /organizations/{org\_id}/team/{team\_id}/repos.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

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
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/repos
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

## Check team permissions for a repository

```
GET /orgs/{org}/teams/{team_slug}/repos/{owner}/{repo}
```

Checks whether a team has admin, push, maintain, triage, or pull permission for a repository. Repositories inherited through a parent team will also be checked.
You can also get information about the specified repository, including what permissions the team grants on it, by passing the following custom media type via the application/vnd.github.v3.repository+json accept header.
If a team doesn't have permission for the repository, you will receive a 404 Not Found response status.
If the repository is private, you must have at least read permission for that repository, and your token must have the repo or admin:org scope. Otherwise, you will receive a 404 Not Found response status.
Note

You can also specify a team by org\_id and team\_id using the route GET /organizations/{org\_id}/team/{team\_id}/repos/{owner}/{repo}.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - Alternative response with repository permissions

* **204** - Response if team has permission for the repository. This is the response when the repository media type hasn't been provded in the Accept header.

* **404** - Not Found if team does not have permission for the repository

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/repos/OWNER/REPO
```

**Response schema (Status: 200):**

* `id`: required, integer
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
* `role_name`: string
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
* `allow_merge_commit`: boolean, default: `true`
* `allow_forking`: boolean, default: `false`
* `web_commit_signoff_required`: boolean, default: `false`
* `subscribers_count`: integer
* `network_count`: integer
* `open_issues`: required, integer
* `watchers`: required, integer
* `master_branch`: string

## Add or update team repository permissions

```
PUT /orgs/{org}/teams/{team_slug}/repos/{owner}/{repo}
```

To add a repository to a team or update the team's permission on a repository, the authenticated user must have admin access to the repository, and must be able to see the team. The repository must be owned by the organization, or a direct fork of a repository owned by the organization. You will get a 422 Unprocessable Entity status if you attempt to add a repository to a team that is not owned by the organization. Note that, if you choose not to pass any parameters, you'll need to set Content-Length to zero when calling out to this endpoint. For more information, see "HTTP method."
Note

You can also specify a team by org\_id and team\_id using the route PUT /organizations/{org\_id}/team/{team\_id}/repos/{owner}/{repo}.

For more information about the permission levels, see "Repository permission levels for an organization".

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`permission`** (string)
  The permission to grant the team on this repository. We accept the following permissions to be set: pull, triage, push, maintain, admin and you can also specify a custom repository role name, if the owning organization has defined any. If no permission is specified, the team's permission attribute will be used to determine what permission to grant the team on this repository.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Adding a team to an organization repository with the write role

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/repos/OWNER/REPO \
  -d '{
  "permission": "push"
}'
```

**Response schema (Status: 204):**

## Remove a repository from a team

```
DELETE /orgs/{org}/teams/{team_slug}/repos/{owner}/{repo}
```

If the authenticated user is an organization owner or a team maintainer, they can remove any repositories from the team. To remove a repository from a team as an organization member, the authenticated user must have admin access to the repository and must be able to see the team. This does not delete the repository, it just removes it from the team.
Note

You can also specify a team by org\_id and team\_id using the route DELETE /organizations/{org\_id}/team/{team\_id}/repos/{owner}/{repo}.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

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
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/repos/OWNER/REPO
```

**Response schema (Status: 204):**

## List child teams

```
GET /orgs/{org}/teams/{team_slug}/teams
```

Lists the child teams of the team specified by {team\_slug}.
Note

You can also specify a team by org\_id and team\_id using the route GET /organizations/{org\_id}/team/{team\_id}/teams.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`team_slug`** (string) (required)
  The slug of the team name.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - if child teams exist

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/teams
```

**Response schema (Status: 200):**

Same response schema as [List teams](#list-teams).

## Get a team (Legacy)

```
GET /teams/{team_id}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the Get a team by name endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/teams/TEAM_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a team](#create-a-team).

## Update a team (Legacy)

```
PATCH /teams/{team_id}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new Update a team endpoint.

To edit a team, the authenticated user must either be an organization owner or a team maintainer.
Note

With nested teams, the privacy for parent teams cannot be secret.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

#### Body parameters

* **`name`** (string) (required)
  The name of the team.

* **`description`** (string)
  The description of the team.

* **`privacy`** (string)
  The level of privacy this team should have. Editing teams without specifying this parameter leaves privacy intact. The options are:
  For a non-nested team:

secret - only visible to organization owners and members of this team.
closed - visible to all members of this organization.
For a parent or child team:
closed - visible to all members of this organization.
Can be one of: `secret`, `closed`

* **`notification_setting`** (string)
  The notification setting the team has chosen. Editing teams without specifying this parameter leaves notification\_setting intact. The options are:

notifications\_enabled - team members receive notifications when the team is @mentioned.
notifications\_disabled - no one receives notifications.
Can be one of: `notifications_enabled`, `notifications_disabled`

* **`permission`** (string)
  Closing down notice. The permission that new repositories will be added to the team with when none is specified.
  Default: `pull`
  Can be one of: `pull`, `push`, `admin`

* **`parent_team_id`** (integer or null)
  The ID of a team to set as the parent team.

### HTTP response status codes

* **200** - Response when the updated information already exists

* **201** - Created

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/teams/TEAM_ID \
  -d '{
  "name": "new team name",
  "description": "new team description",
  "privacy": "closed",
  "notification_setting": "notifications_enabled"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a team](#create-a-team).

#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/teams/TEAM_ID \
  -d '{
  "name": "new team name",
  "description": "new team description",
  "privacy": "closed",
  "notification_setting": "notifications_enabled"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a team](#create-a-team).

## Delete a team (Legacy)

```
DELETE /teams/{team_id}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new Delete a team endpoint.

To delete a team, the authenticated user must be an organization owner or team maintainer.
If you are an organization owner, deleting a parent team will delete all of its child teams as well.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/teams/TEAM_ID
```

**Response schema (Status: 204):**

## List team repositories (Legacy)

```
GET /teams/{team_id}/repos
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new List team repositories endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

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
  https://api.github.com/teams/TEAM_ID/repos
```

**Response schema (Status: 200):**

Same response schema as [List team repositories](#list-team-repositories).

## Check team permissions for a repository (Legacy)

```
GET /teams/{team_id}/repos/{owner}/{repo}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new Check team permissions for a repository endpoint.

Note

Repositories inherited through a parent team will also be checked.

You can also get information about the specified repository, including what permissions the team grants on it, by passing the following custom media type via the Accept header:

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - Alternative response with extra repository information

* **204** - Response if repository is managed by this team

* **404** - Not Found if repository is not managed by this team

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/teams/TEAM_ID/repos/OWNER/REPO
```

**Response schema (Status: 200):**

Same response schema as [Check team permissions for a repository](#check-team-permissions-for-a-repository).

## Add or update team repository permissions (Legacy)

```
PUT /teams/{team_id}/repos/{owner}/{repo}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new "Add or update team repository permissions" endpoint.

To add a repository to a team or update the team's permission on a repository, the authenticated user must have admin access to the repository, and must be able to see the team. The repository must be owned by the organization, or a direct fork of a repository owned by the organization. You will get a 422 Unprocessable Entity status if you attempt to add a repository to a team that is not owned by the organization.
Note that, if you choose not to pass any parameters, you'll need to set Content-Length to zero when calling out to this endpoint. For more information, see "HTTP method."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`permission`** (string)
  The permission to grant the team on this repository. If no permission is specified, the team's permission attribute will be used to determine what permission to grant the team on this repository.
  Can be one of: `pull`, `push`, `admin`

### HTTP response status codes

* **204** - No Content

* **403** - Forbidden

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example of setting permission to pull

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/teams/TEAM_ID/repos/OWNER/REPO \
  -d '{
  "permission": "push"
}'
```

**Response schema (Status: 204):**

## Remove a repository from a team (Legacy)

```
DELETE /teams/{team_id}/repos/{owner}/{repo}
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new Remove a repository from a team endpoint.

If the authenticated user is an organization owner or a team maintainer, they can remove any repositories from the team. To remove a repository from a team as an organization member, the authenticated user must have admin access to the repository and must be able to see the team. NOTE: This does not delete the repository, it just removes it from the team.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

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
  https://api.github.com/teams/TEAM_ID/repos/OWNER/REPO
```

**Response schema (Status: 204):**

## List child teams (Legacy)

```
GET /teams/{team_id}/teams
```

Warning

Endpoint closing down notice: This endpoint route is closing down and will be removed from the Teams API. We recommend migrating your existing code to use the new List child teams endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`team_id`** (integer) (required)
  The unique identifier of the team.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - if child teams exist

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/teams/TEAM_ID/teams
```

**Response schema (Status: 200):**

Same response schema as [List teams](#list-teams).

## List teams for the authenticated user

```
GET /user/teams
```

List all of the teams across all of the organizations to which the authenticated
user belongs.
OAuth app tokens and personal access tokens (classic) need the user, repo, or read:org scope to use this endpoint.
When using a fine-grained personal access token, the resource owner of the token must be a single organization, and the response will only include the teams from that organization.

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

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/teams
```

**Response schema (Status: 200):**

Array of `Full Team`:

* `id`: required, integer
* `node_id`: required, string
* `url`: required, string, format: uri
* `html_url`: required, string, format: uri
* `name`: required, string
* `slug`: required, string
* `description`: required, string or null
* `privacy`: string, enum: `closed`, `secret`
* `notification_setting`: string, enum: `notifications_enabled`, `notifications_disabled`
* `permission`: required, string
* `members_url`: required, string
* `repositories_url`: required, string, format: uri
* `parent`: any of:
  * **null**
  * **Team Simple**
    * `id`: required, integer
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `members_url`: required, string
    * `name`: required, string
    * `description`: required, string or null
    * `permission`: required, string
    * `privacy`: string
    * `notification_setting`: string
    * `html_url`: required, string, format: uri
    * `repositories_url`: required, string, format: uri
    * `slug`: required, string
    * `ldap_dn`: string
    * `type`: required, string, enum: `enterprise`, `organization`
    * `organization_id`: integer
    * `enterprise_id`: integer
* `members_count`: required, integer
* `repos_count`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `organization`: required, `Team Organization`:
  * `login`: required, string
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string, format: uri
  * `repos_url`: required, string, format: uri
  * `events_url`: required, string, format: uri
  * `hooks_url`: required, string
  * `issues_url`: required, string
  * `members_url`: required, string
  * `public_members_url`: required, string
  * `avatar_url`: required, string
  * `description`: required, string or null
  * `name`: string
  * `company`: string
  * `blog`: string, format: uri
  * `location`: string
  * `email`: string, format: email
  * `twitter_username`: string or null
  * `is_verified`: boolean
  * `has_organization_projects`: required, boolean
  * `has_repository_projects`: required, boolean
  * `public_repos`: required, integer
  * `public_gists`: required, integer
  * `followers`: required, integer
  * `following`: required, integer
  * `html_url`: required, string, format: uri
  * `created_at`: required, string, format: date-time
  * `type`: required, string
  * `total_private_repos`: integer
  * `owned_private_repos`: integer
  * `private_gists`: integer or null
  * `disk_usage`: integer or null
  * `collaborators`: integer or null
  * `billing_email`: string or null, format: email
  * `plan`: object:
    * `name`: required, string
    * `space`: required, integer
    * `private_repos`: required, integer
    * `filled_seats`: integer
    * `seats`: integer
  * `default_repository_permission`: string or null
  * `members_can_create_repositories`: boolean or null
  * `two_factor_requirement_enabled`: boolean or null
  * `members_allowed_repository_creation_type`: string
  * `members_can_create_public_repositories`: boolean
  * `members_can_create_private_repositories`: boolean
  * `members_can_create_internal_repositories`: boolean
  * `members_can_create_pages`: boolean
  * `members_can_create_public_pages`: boolean
  * `members_can_create_private_pages`: boolean
  * `members_can_fork_private_repositories`: boolean or null
  * `web_commit_signoff_required`: boolean
  * `updated_at`: required, string, format: date-time
  * `archived_at`: required, string or null, format: date-time
* `ldap_dn`: string
* `type`: required, string, enum: `enterprise`, `organization`
* `organization_id`: integer
* `enterprise_id`: integer