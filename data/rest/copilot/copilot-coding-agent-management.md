# REST API endpoints for Copilot cloud agent management

Use the REST API to manage settings for Copilot cloud agent.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Set the coding agent policy for an enterprise

```
PUT /enterprises/{enterprise}/copilot/policies/coding_agent
```

Sets the policy for Copilot coding agent usage across an enterprise.
Enterprise owners can configure whether Copilot coding agent is enabled for all
organizations, disabled for all organizations, configured by individual organization
admins, or enabled for selected organizations only.
Only enterprise owners can set the coding agent policy for their enterprise.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or admin:enterprise scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`policy_state`** (string) (required)
  The policy state for Copilot coding agent in the enterprise. Can be one of enabled_for_all_orgs, disabled_for_all_orgs, enabled_for_selected_orgs, or configured_by_org_admins.
  Can be one of: `enabled_for_all_orgs`, `disabled_for_all_orgs`, `enabled_for_selected_orgs`, `configured_by_org_admins`





### HTTP response status codes


- **204** - A header with no content is returned.


- **400** - Bad Request




### Code examples



#### Enable coding agent for all organizations

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/copilot/policies/coding_agent \
  -d '{
  "policy_state": "enabled_for_all_orgs"
}'
```

**Response schema (Status: 204):**





## Add organizations to the enterprise coding agent policy

```
POST /enterprises/{enterprise}/copilot/policies/coding_agent/organizations
```

Enables Copilot coding agent for the specified organizations within the enterprise.
The enterprise's coding agent policy must be set to enabled_for_selected_orgs before
using this endpoint. Organizations can be specified by login or matched via custom properties.
Only organizations that have Copilot enabled and belong to the enterprise will be affected.
Only enterprise owners can add organizations to the coding agent policy.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or admin:enterprise scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`organizations`** (array of strings)
  List of organization logins within the enterprise to enable Copilot coding agent for.

- **`custom_properties`** (array of objects)
  List of custom property filters to match organizations. Organizations matching any of the specified property name/value pairs will be included. This is a one-time operation, setting the property on an organization in the future will not automatically update its coding agent policy.
  - **`property_name`** (string) (required)
    The name of the custom property to filter by.
  - **`values`** (array of strings) (required)
    The values of the custom property to match.





### HTTP response status codes


- **204** - A header with no content is returned.


- **400** - Bad Request




### Code examples



#### Add organizations that match a login or have a custom property

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/copilot/policies/coding_agent/organizations \
  -d '{
  "organizations": [
    "my-org-1",
    "my-org-2"
  ],
  "custom_properties": [
    {
      "property_name": "department",
      "values": [
        "engineering",
        "security"
      ]
    }
  ]
}'
```

**Response schema (Status: 204):**





## Remove organizations from the enterprise coding agent policy

```
DELETE /enterprises/{enterprise}/copilot/policies/coding_agent/organizations
```

Disables Copilot coding agent for the specified organizations within the enterprise.
The enterprise's coding agent policy must be set to enabled_for_selected_orgs before
using this endpoint. Organizations can be specified by login or matched via custom properties.
Only organizations that have Copilot enabled and belong to the enterprise will be affected.
Only enterprise owners can remove organizations from the coding agent policy.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot or admin:enterprise scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`organizations`** (array of strings)
  List of organization logins within the enterprise to disable Copilot coding agent for.

- **`custom_properties`** (array of objects)
  List of custom property filters to match organizations. Organizations matching any of the specified property name/value pairs will be included. This is a one-time operation, setting the property on an organization in the future will not automatically update its coding agent policy.
  - **`property_name`** (string) (required)
    The name of the custom property to filter by.
  - **`values`** (array of strings) (required)
    The values of the custom property to match.





### HTTP response status codes


- **204** - A header with no content is returned.


- **400** - Bad Request




### Code examples



#### Remove organizations that match a login or have a custom property

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/copilot/policies/coding_agent/organizations \
  -d '{
  "organizations": [
    "my-org-1",
    "my-org-2"
  ],
  "custom_properties": [
    {
      "property_name": "department",
      "values": [
        "engineering",
        "security"
      ]
    }
  ]
}'
```

**Response schema (Status: 204):**





## Get Copilot coding agent permissions for an organization

```
GET /orgs/{org}/copilot/coding-agent/permissions
```

Note

This endpoint is in public preview and is subject to change.

Gets information about which repositories in an organization have been enabled
or disabled for the Copilot coding agent.
Organization owners can configure whether Copilot coding agent is enabled for
all repositories, selected repositories, or no repositories owned by organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/coding-agent/permissions
```

**Response schema (Status: 200):**

* `enabled_repositories`: required, string, enum: `all`, `selected`, `none`
* `selected_repositories_url`: string



#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/coding-agent/permissions
```

**Response schema (Status: 200):**

* `enabled_repositories`: required, string, enum: `all`, `selected`, `none`
* `selected_repositories_url`: string



#### Example 3: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/coding-agent/permissions
```

**Response schema (Status: 200):**

* `enabled_repositories`: required, string, enum: `all`, `selected`, `none`
* `selected_repositories_url`: string





## Set Copilot coding agent permissions for an organization

```
PUT /orgs/{org}/copilot/coding-agent/permissions
```

Note

This endpoint is in public preview and is subject to change.

Sets the policy for which repositories in an organization can use Copilot coding agent.
Organization owners can configure whether Copilot coding agent is enabled for
all repositories, selected repositories, or no repositories owned by the organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`enabled_repositories`** (string) (required)
  The policy for which repositories can use Copilot coding agent. Can be one of all, selected, or none.
  Can be one of: `all`, `selected`, `none`





### HTTP response status codes


- **204** - No Content


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot/coding-agent/permissions \
  -d '{
  "enabled_repositories": "selected"
}'
```

**Response schema (Status: 204):**





## List repositories enabled for Copilot coding agent in an organization

```
GET /orgs/{org}/copilot/coding-agent/permissions/repositories
```

Note

This endpoint is in public preview and is subject to change.

Lists the selected repositories that are enabled for Copilot coding agent in an organization.
Organization owners can use this endpoint when the coding agent repository policy
is set to selected to see which repositories have been enabled.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


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


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/coding-agent/permissions/repositories
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





## Set selected repositories for Copilot coding agent in an organization

```
PUT /orgs/{org}/copilot/coding-agent/permissions/repositories
```

Note

This endpoint is in public preview and is subject to change.

Replaces the list of selected repositories that are enabled for Copilot coding
agent in an organization. This method can only be called when the coding agent
repository policy is set to selected.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`selected_repository_ids`** (array of integers) (required)
  List of repository IDs to enable for Copilot coding agent.





### HTTP response status codes


- **204** - No Content


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot/coding-agent/permissions/repositories \
  -d '{
  "selected_repository_ids": [
    32,
    42
  ]
}'
```

**Response schema (Status: 204):**





## Enable a repository for Copilot coding agent in an organization

```
PUT /orgs/{org}/copilot/coding-agent/permissions/repositories/{repository_id}
```

Note

This endpoint is in public preview and is subject to change.

Adds a repository to the list of selected repositories enabled for Copilot
coding agent in an organization. This method can only be called when the
coding agent repository policy is set to selected.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


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


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot/coding-agent/permissions/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**





## Disable a repository for Copilot coding agent in an organization

```
DELETE /orgs/{org}/copilot/coding-agent/permissions/repositories/{repository_id}
```

Note

This endpoint is in public preview and is subject to change.

Removes a repository from the list of selected repositories enabled for Copilot
coding agent in an organization. This method can only be called when the
coding agent repository policy is set to selected.
OAuth app tokens and personal access tokens (classic) need the admin:org scopes to use this endpoint.


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


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/copilot/coding-agent/permissions/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**