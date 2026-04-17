# REST API endpoints for organizations

Use the REST API to interact with organizations.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List organizations

```
GET /organizations
```

Lists all organizations, in the order that they were created.
Note

Pagination is powered exclusively by the since parameter. Use the Link header to get the URL for the next page of organizations.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`since`** (integer)
  An organization ID. Only return organizations with an ID greater than this ID.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






### HTTP response status codes


- **200** - OK


- **304** - Not modified




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/organizations
```

**Response schema (Status: 200):**

Array of `Organization Simple`:
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





## Get an organization

```
GET /orgs/{org}
```

Gets information about an organization.
When the value of two_factor_requirement_enabled is true, the organization requires all members, billing managers, outside collaborators, guest collaborators, repository collaborators, or everyone with access to any repository within the organization to enable two-factor authentication.
To see the full details about an organization, the authenticated user must be an organization owner.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to see the full details about an organization.
To see information about an organization's GitHub plan, GitHub Apps need the Organization plan permission.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG
```

**Response schema (Status: 200):**

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
* `default_repository_branch`: string or null
* `members_can_create_repositories`: boolean or null
* `two_factor_requirement_enabled`: boolean or null
* `members_allowed_repository_creation_type`: string
* `members_can_create_public_repositories`: boolean
* `members_can_create_private_repositories`: boolean
* `members_can_create_internal_repositories`: boolean
* `members_can_create_pages`: boolean
* `members_can_create_public_pages`: boolean
* `members_can_create_private_pages`: boolean
* `members_can_delete_repositories`: boolean
* `members_can_change_repo_visibility`: boolean
* `members_can_invite_outside_collaborators`: boolean
* `members_can_delete_issues`: boolean
* `display_commenter_full_name_setting_enabled`: boolean
* `readers_can_create_discussions`: boolean
* `members_can_create_teams`: boolean
* `members_can_view_dependency_insights`: boolean
* `members_can_fork_private_repositories`: boolean or null
* `web_commit_signoff_required`: boolean
* `advanced_security_enabled_for_new_repositories`: boolean, deprecated
* `dependabot_alerts_enabled_for_new_repositories`: boolean, deprecated
* `dependabot_security_updates_enabled_for_new_repositories`: boolean, deprecated
* `dependency_graph_enabled_for_new_repositories`: boolean, deprecated
* `secret_scanning_enabled_for_new_repositories`: boolean, deprecated
* `secret_scanning_push_protection_enabled_for_new_repositories`: boolean, deprecated
* `secret_scanning_push_protection_custom_link`: string or null
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `archived_at`: required, string or null, format: date-time
* `deploy_keys_enabled_for_repositories`: boolean





## Update an organization

```
PATCH /orgs/{org}
```

Warning

Closing down notice: GitHub will replace and discontinue members_allowed_repository_creation_type in favor of more granular permissions. The new input parameters are members_can_create_public_repositories, members_can_create_private_repositories for all organizations and members_can_create_internal_repositories for organizations associated with an enterprise account using GitHub Enterprise Cloud or GitHub Enterprise Server 2.20+. For more information, see the blog post.

Warning

Closing down notice: Code security product enablement for new repositories through the organization API is closing down. Please use code security configurations to set defaults instead. For more information on setting a default security configuration, see the changelog.

Updates the organization's profile and member privileges.
The authenticated user must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`billing_email`** (string)
  Billing email address. This address is not publicized.

- **`company`** (string)
  The company name.

- **`email`** (string)
  The publicly visible email address.

- **`twitter_username`** (string)
  The Twitter username of the company.

- **`location`** (string)
  The location.

- **`name`** (string)
  The shorthand name of the company.

- **`description`** (string)
  The description of the company. The maximum size is 160 characters.

- **`has_organization_projects`** (boolean)
  Whether an organization can use organization projects.

- **`has_repository_projects`** (boolean)
  Whether repositories that belong to the organization can use repository projects.

- **`default_repository_permission`** (string)
  Default permission level members have for organization repositories.
  Default: `read`
  Can be one of: `read`, `write`, `admin`, `none`

- **`members_can_create_repositories`** (boolean)
  Whether of non-admin organization members can create repositories. Note: A parameter can override this parameter. See members_allowed_repository_creation_type in this table for details.
  Default: `true`

- **`members_can_create_internal_repositories`** (boolean)
  Whether organization members can create internal repositories, which are visible to all enterprise members. You can only allow members to create internal repositories if your organization is associated with an enterprise account using GitHub Enterprise Cloud or GitHub Enterprise Server 2.20+. For more information, see "Restricting repository creation in your organization" in the GitHub Help documentation.

- **`members_can_create_private_repositories`** (boolean)
  Whether organization members can create private repositories, which are visible to organization members with permission. For more information, see "Restricting repository creation in your organization" in the GitHub Help documentation.

- **`members_can_create_public_repositories`** (boolean)
  Whether organization members can create public repositories, which are visible to anyone. For more information, see "Restricting repository creation in your organization" in the GitHub Help documentation.

- **`members_allowed_repository_creation_type`** (string)
  Specifies which types of repositories non-admin organization members can create. private is only available to repositories that are part of an organization on GitHub Enterprise Cloud.
Note: This parameter is closing down and will be removed in the future. Its return value ignores internal repositories. Using this parameter overrides values set in members_can_create_repositories. See the parameter deprecation notice in the operation description for details.
  Can be one of: `all`, `private`, `none`

- **`members_can_create_pages`** (boolean)
  Whether organization members can create GitHub Pages sites. Existing published sites will not be impacted.
  Default: `true`

- **`members_can_create_public_pages`** (boolean)
  Whether organization members can create public GitHub Pages sites. Existing published sites will not be impacted.
  Default: `true`

- **`members_can_create_private_pages`** (boolean)
  Whether organization members can create private GitHub Pages sites. Existing published sites will not be impacted.
  Default: `true`

- **`members_can_fork_private_repositories`** (boolean)
  Whether organization members can fork private organization repositories.
  Default: `false`

- **`web_commit_signoff_required`** (boolean)
  Whether contributors to organization repositories are required to sign off on commits they make through GitHub's web interface.
  Default: `false`

- **`blog`** (string)

- **`advanced_security_enabled_for_new_repositories`** (boolean)
  Endpoint closing down notice. Please use code security configurations instead.
Whether GitHub Advanced Security is automatically enabled for new repositories and repositories transferred to this organization.
To use this parameter, you must have admin permissions for the repository or be an owner or security manager for the organization that owns the repository. For more information, see "Managing security managers in your organization."
You can check which security and analysis features are currently enabled by using a GET /orgs/{org} request.

- **`dependabot_alerts_enabled_for_new_repositories`** (boolean)
  Endpoint closing down notice. Please use code security configurations instead.
Whether Dependabot alerts are automatically enabled for new repositories and repositories transferred to this organization.
To use this parameter, you must have admin permissions for the repository or be an owner or security manager for the organization that owns the repository. For more information, see "Managing security managers in your organization."
You can check which security and analysis features are currently enabled by using a GET /orgs/{org} request.

- **`dependabot_security_updates_enabled_for_new_repositories`** (boolean)
  Endpoint closing down notice. Please use code security configurations instead.
Whether Dependabot security updates are automatically enabled for new repositories and repositories transferred to this organization.
To use this parameter, you must have admin permissions for the repository or be an owner or security manager for the organization that owns the repository. For more information, see "Managing security managers in your organization."
You can check which security and analysis features are currently enabled by using a GET /orgs/{org} request.

- **`dependency_graph_enabled_for_new_repositories`** (boolean)
  Endpoint closing down notice. Please use code security configurations instead.
Whether dependency graph is automatically enabled for new repositories and repositories transferred to this organization.
To use this parameter, you must have admin permissions for the repository or be an owner or security manager for the organization that owns the repository. For more information, see "Managing security managers in your organization."
You can check which security and analysis features are currently enabled by using a GET /orgs/{org} request.

- **`secret_scanning_enabled_for_new_repositories`** (boolean)
  Endpoint closing down notice. Please use code security configurations instead.
Whether secret scanning is automatically enabled for new repositories and repositories transferred to this organization.
To use this parameter, you must have admin permissions for the repository or be an owner or security manager for the organization that owns the repository. For more information, see "Managing security managers in your organization."
You can check which security and analysis features are currently enabled by using a GET /orgs/{org} request.

- **`secret_scanning_push_protection_enabled_for_new_repositories`** (boolean)
  Endpoint closing down notice. Please use code security configurations instead.
Whether secret scanning push protection is automatically enabled for new repositories and repositories transferred to this organization.
To use this parameter, you must have admin permissions for the repository or be an owner or security manager for the organization that owns the repository. For more information, see "Managing security managers in your organization."
You can check which security and analysis features are currently enabled by using a GET /orgs/{org} request.

- **`secret_scanning_push_protection_custom_link`** (string)
  If secret_scanning_push_protection_custom_link_enabled is true, the URL that will be displayed to contributors who are blocked from pushing a secret.

- **`deploy_keys_enabled_for_repositories`** (boolean)
  Controls whether or not deploy keys may be added and used for repositories in the organization.





### HTTP response status codes


- **200** - OK


- **409** - Conflict


- **422** - Validation failed




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG \
  -d '{
  "billing_email": "mona@github.com",
  "company": "GitHub",
  "email": "mona@github.com",
  "twitter_username": "github",
  "location": "San Francisco",
  "name": "github",
  "description": "GitHub, the company.",
  "default_repository_permission": "read",
  "members_can_create_repositories": true,
  "members_allowed_repository_creation_type": "all"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an organization](#get-an-organization).





## Delete an organization

```
DELETE /orgs/{org}
```

Deletes an organization and all its repositories.
The organization login will be unavailable for 90 days after deletion.
Please review the Terms of Service regarding account deletion before using this endpoint:
https://docs.github.com/site-policy/github-terms/github-terms-of-service


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **202** - Accepted


- **403** - Forbidden


- **404** - Resource not found


- **451** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG
```

**Response schema (Status: 202):**

object





## List app installations for an organization

```
GET /orgs/{org}/installations
```

Lists all GitHub Apps in an organization. The installation count includes
all GitHub Apps installed on repositories in the organization.
The authenticated user must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:read scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/installations
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `installations`: required, array of `Installation`:
  * `id`: required, integer
  * `account`: required, any of:
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
    * **Enterprise**
      * `description`: string or null
      * `html_url`: required, string, format: uri
      * `website_url`: string or null, format: uri
      * `id`: required, integer
      * `node_id`: required, string
      * `name`: required, string
      * `slug`: required, string
      * `created_at`: required, string or null, format: date-time
      * `updated_at`: required, string or null, format: date-time
      * `avatar_url`: required, string, format: uri
  * `repository_selection`: required, string, enum: `all`, `selected`
  * `access_tokens_url`: required, string, format: uri
  * `repositories_url`: required, string, format: uri
  * `html_url`: required, string, format: uri
  * `app_id`: required, integer
  * `client_id`: string
  * `target_id`: required, integer
  * `target_type`: required, string
  * `permissions`: required, `App Permissions`:
    * `actions`: string, enum: `read`, `write`
    * `administration`: string, enum: `read`, `write`
    * `artifact_metadata`: string, enum: `read`, `write`
    * `attestations`: string, enum: `read`, `write`
    * `checks`: string, enum: `read`, `write`
    * `codespaces`: string, enum: `read`, `write`
    * `contents`: string, enum: `read`, `write`
    * `dependabot_secrets`: string, enum: `read`, `write`
    * `deployments`: string, enum: `read`, `write`
    * `discussions`: string, enum: `read`, `write`
    * `environments`: string, enum: `read`, `write`
    * `issues`: string, enum: `read`, `write`
    * `merge_queues`: string, enum: `read`, `write`
    * `metadata`: string, enum: `read`, `write`
    * `packages`: string, enum: `read`, `write`
    * `pages`: string, enum: `read`, `write`
    * `pull_requests`: string, enum: `read`, `write`
    * `repository_custom_properties`: string, enum: `read`, `write`
    * `repository_hooks`: string, enum: `read`, `write`
    * `repository_projects`: string, enum: `read`, `write`, `admin`
    * `secret_scanning_alerts`: string, enum: `read`, `write`
    * `secrets`: string, enum: `read`, `write`
    * `security_events`: string, enum: `read`, `write`
    * `single_file`: string, enum: `read`, `write`
    * `statuses`: string, enum: `read`, `write`
    * `vulnerability_alerts`: string, enum: `read`, `write`
    * `workflows`: string, enum: `write`
    * `custom_properties_for_organizations`: string, enum: `read`, `write`
    * `members`: string, enum: `read`, `write`
    * `organization_administration`: string, enum: `read`, `write`
    * `organization_custom_roles`: string, enum: `read`, `write`
    * `organization_custom_org_roles`: string, enum: `read`, `write`
    * `organization_custom_properties`: string, enum: `read`, `write`, `admin`
    * `organization_copilot_seat_management`: string, enum: `write`
    * `organization_copilot_agent_settings`: string, enum: `read`, `write`
    * `organization_announcement_banners`: string, enum: `read`, `write`
    * `organization_events`: string, enum: `read`
    * `organization_hooks`: string, enum: `read`, `write`
    * `organization_personal_access_tokens`: string, enum: `read`, `write`
    * `organization_personal_access_token_requests`: string, enum: `read`, `write`
    * `organization_plan`: string, enum: `read`
    * `organization_projects`: string, enum: `read`, `write`, `admin`
    * `organization_packages`: string, enum: `read`, `write`
    * `organization_secrets`: string, enum: `read`, `write`
    * `organization_self_hosted_runners`: string, enum: `read`, `write`
    * `organization_user_blocking`: string, enum: `read`, `write`
    * `email_addresses`: string, enum: `read`, `write`
    * `followers`: string, enum: `read`, `write`
    * `git_ssh_keys`: string, enum: `read`, `write`
    * `gpg_keys`: string, enum: `read`, `write`
    * `interaction_limits`: string, enum: `read`, `write`
    * `profile`: string, enum: `write`
    * `starring`: string, enum: `read`, `write`
    * `enterprise_custom_properties_for_organizations`: string, enum: `read`, `write`, `admin`
  * `events`: required, array of string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `single_file_name`: required, string or null
  * `has_multiple_single_files`: boolean
  * `single_file_paths`: array of string
  * `app_slug`: required, string
  * `suspended_by`: required, any of:
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
  * `suspended_at`: required, string or null, format: date-time
  * `contact_email`: string or null





## Get immutable releases settings for an organization

```
GET /orgs/{org}/settings/immutable-releases
```

Gets the immutable releases policy for repositories in an organization.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - Immutable releases settings response




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/settings/immutable-releases
```

**Response schema (Status: 200):**

* `enforced_repositories`: required, string, enum: `all`, `none`, `selected`
* `selected_repositories_url`: string





## Set immutable releases settings for an organization

```
PUT /orgs/{org}/settings/immutable-releases
```

Sets the immutable releases policy for repositories in an organization.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`enforced_repositories`** (string) (required)
  The policy that controls how immutable releases are enforced in the organization.
  Can be one of: `all`, `none`, `selected`

- **`selected_repository_ids`** (array of integers)
  An array of repository ids for which immutable releases enforcement should be applied. You can only provide a list of repository ids when the enforced_repositories is set to selected. You can add and remove individual repositories using the Enable a selected repository for immutable releases in an organization and Disable a selected repository for immutable releases in an organization endpoints.





### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/settings/immutable-releases \
  -d '{
  "enforced_repositories": "all"
}'
```

**Response schema (Status: 204):**





## List selected repositories for immutable releases enforcement

```
GET /orgs/{org}/settings/immutable-releases/repositories
```

List all of the repositories that have been selected for immutable releases enforcement in an organization.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/settings/immutable-releases/repositories
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `repositories`: required, array of `Minimal Repository`:
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





## Set selected repositories for immutable releases enforcement

```
PUT /orgs/{org}/settings/immutable-releases/repositories
```

Replaces all repositories that have been selected for immutable releases enforcement in an organization. To use this endpoint, the organization immutable releases policy for enforced_repositories must be configured to selected.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`selected_repository_ids`** (array of integers) (required)
  An array of repository ids for which immutable releases enforcement should be applied. You can only provide a list of repository ids when the enforced_repositories is set to selected. You can add and remove individual repositories using the Enable a selected repository for immutable releases in an organization and Disable a selected repository for immutable releases in an organization endpoints.





### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/settings/immutable-releases/repositories \
  -d '{
  "selected_repository_ids": [
    64780797
  ]
}'
```

**Response schema (Status: 204):**





## Enable a selected repository for immutable releases in an organization

```
PUT /orgs/{org}/settings/immutable-releases/repositories/{repository_id}
```

Adds a repository to the list of selected repositories that are enforced for immutable releases in an organization. To use this endpoint, the organization immutable releases policy for enforced_repositories must be configured to selected.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`repository_id`** (integer) (required)
  The unique identifier of the repository.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/settings/immutable-releases/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**





## Disable a selected repository for immutable releases in an organization

```
DELETE /orgs/{org}/settings/immutable-releases/repositories/{repository_id}
```

Removes a repository from the list of selected repositories that are enforced for immutable releases in an organization. To use this endpoint, the organization immutable releases policy for enforced_repositories must be configured to selected.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`repository_id`** (integer) (required)
  The unique identifier of the repository.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/settings/immutable-releases/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**





## Enable or disable a security feature for an organization

```
POST /orgs/{org}/{security_product}/{enablement}
```

Warning

Closing down notice: The ability to enable or disable a security feature for all eligible repositories in an organization is closing down. Please use code security configurations instead. For more information, see the changelog.

Enables or disables the specified security feature for all eligible repositories in an organization. For more information, see "Managing security managers in your organization."
The authenticated user must be an organization owner or be member of a team with the security manager role to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org, write:org, or repo scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`security_product`** (string) (required)
  The security feature to enable or disable.
  Can be one of: `dependency_graph`, `dependabot_alerts`, `dependabot_security_updates`, `advanced_security`, `code_scanning_default_setup`, `secret_scanning`, `secret_scanning_push_protection`

- **`enablement`** (string) (required)
  The action to take.
enable_all means to enable the specified security feature for all repositories in the organization.
disable_all means to disable the specified security feature for all repositories in the organization.
  Can be one of: `enable_all`, `disable_all`




#### Body parameters

- **`query_suite`** (string)
  CodeQL query suite to be used. If you specify the query_suite parameter, the default setup will be configured with this query suite only on all repositories that didn't have default setup already configured. It will not change the query suite on repositories that already have default setup configured.
If you don't specify any query_suite in your request, the preferred query suite of the organization will be applied.
  Can be one of: `default`, `extended`





### HTTP response status codes


- **204** - Action started


- **422** - The action could not be taken due to an in progress enablement, or a policy is preventing enablement




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/SECURITY_PRODUCT/ENABLEMENT
```

**Response schema (Status: 204):**





## List organizations for the authenticated user

```
GET /user/orgs
```

List organizations for the authenticated user.
For OAuth app tokens and personal access tokens (classic), this endpoint only lists organizations that your authorization allows you to operate on in some way (e.g., you can list teams with read:org scope, you can publicize your organization membership with user scope, etc.). Therefore, this API requires at least user or read:org scope for OAuth app tokens and personal access tokens (classic). Requests with insufficient scope will receive a 403 Forbidden response.
Note

Requests using a fine-grained access token will receive a 200 Success response with an empty list.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/orgs
```

**Response schema (Status: 200):**

Same response schema as [List organizations](#list-organizations).





## List organizations for a user

```
GET /users/{username}/orgs
```

List public organization memberships for the specified user.
This method only lists public memberships, regardless of authentication. If you need to fetch all of the organization memberships (public and private) for the authenticated user, use the List organizations for the authenticated user API instead.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/orgs
```

**Response schema (Status: 200):**

Same response schema as [List organizations](#list-organizations).