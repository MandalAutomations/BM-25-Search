# REST API for managing organization GitHub App installations

Use the REST API to manage which GitHub Apps are installed in your enterprise's organizations.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get enterprise-owned organizations that can have GitHub Apps installed

```
GET /enterprises/{enterprise}/apps/installable_organizations
```

List the organizations owned by the enterprise, intended for use by GitHub Apps that are managing applications across the enterprise.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of organizations owned by the enterprise on which the authenticated GitHub App is installed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/apps/installable_organizations
```

**Response schema (Status: 200):**

Array of `Installable Organization`:
  * `id`: required, integer
  * `login`: required, string
  * `accessible_repositories_url`: string, format: uri





## Get repositories belonging to an enterprise-owned organization

```
GET /enterprises/{enterprise}/apps/installable_organizations/{org}/accessible_repositories
```

List the repositories belonging to an enterprise-owned organization that can be made accessible to a GitHub App installed on that organization. This API provides a shallow list of repositories in the organization, allowing the caller to then add or remove those repositories to an installation in that organization.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of repositories owned by the enterprise organization on which the authenticated GitHub App is installed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/apps/installable_organizations/ORG/accessible_repositories
```

**Response schema (Status: 200):**

Array of `Accessible Repository`:
  * `id`: required, integer, format: int64
  * `name`: required, string
  * `full_name`: required, string





## List GitHub Apps installed on an enterprise-owned organization

```
GET /enterprises/{enterprise}/apps/organizations/{org}/installations
```

Lists the GitHub App installations associated with the given enterprise-owned organization. This lists all GitHub Apps that have been installed on the organization, regardless of who owns the application.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of GitHub App installations that have been granted access to the organization




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/apps/organizations/ORG/installations
```

**Response schema (Status: 200):**

Array of `Enterprise Organization Installation`:
  * `id`: required, integer
  * `app_slug`: string
  * `client_id`: required, string
  * `repository_selection`: required, string, enum: `all`, `selected`
  * `repositories_url`: required, string, format: uri
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
    * `enterprise_organization_installations`: string, enum: `read`, `write`
    * `enterprise_organization_installation_repositories`: string, enum: `read`, `write`
  * `events`: array of string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time





## Install a GitHub App on an enterprise-owned organization

```
POST /enterprises/{enterprise}/apps/organizations/{org}/installations
```

Installs any valid GitHub App on the specified organization owned by the enterprise. If the app is already installed on the organization, and is suspended, it will be unsuspended.
If the app has a pending installation request, they will all be approved.
If the app is already installed and has a pending update request, it will be updated to the latest version. If the app is now requesting repository permissions, it will be given access to the repositories listed in the request or fail if no repository_selection is provided.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`client_id`** (string) (required)
  The Client ID of the GitHub App to install.

- **`repository_selection`** (string) (required)
  The repository selection for the GitHub App. Must be one of:

all - the installation can access all repositories in the organization.
selected - the installation can access only the listed repositories.
none - no repository permissions are requested. Only use when the app does not request repository permissions.
  Can be one of: `all`, `selected`, `none`

- **`repositories`** (array of strings)
  The names of the repositories to which the installation will be granted access. This is the simple name of the repository, not the full name (e.g., hello-world not octocat/hello-world). This is only required when repository_selection is selected.





### HTTP response status codes


- **200** - A GitHub App installation that was installed previously.


- **201** - A GitHub App installation.




### Code examples



#### Example of installing a GitHub App on an organization and granting access to all of its repositories.

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/apps/organizations/ORG/installations \
  -d '{
  "client_id": "Iv2abc123aabbcc",
  "repository_selection": "all"
}'
```

**Response schema (Status: 200):**

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
  * `enterprise_organization_installations`: string, enum: `read`, `write`
  * `enterprise_organization_installation_repositories`: string, enum: `read`, `write`
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





## Uninstall a GitHub App from an enterprise-owned organization

```
DELETE /enterprises/{enterprise}/apps/organizations/{org}/installations/{installation_id}
```

Uninstall a GitHub App from an organization. Any app installed on the organization can be removed.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`installation_id`** (integer) (required)
  The unique identifier of the installation.






### HTTP response status codes


- **204** - An empty response indicates that the installation was successfully removed.


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/apps/organizations/ORG/installations/1
```

**Response schema (Status: 204):**





## Get the repositories accessible to a given GitHub App installation

```
GET /enterprises/{enterprise}/apps/organizations/{org}/installations/{installation_id}/repositories
```

Lists the repositories accessible to a given GitHub App installation on an enterprise-owned organization.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`installation_id`** (integer) (required)
  The unique identifier of the installation.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of repositories owned by the enterprise organization to which the installation has access.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/apps/organizations/ORG/installations/1/repositories
```

**Response schema (Status: 200):**

Same response schema as [Get repositories belonging to an enterprise-owned organization](#get-repositories-belonging-to-an-enterprise-owned-organization).





## Toggle installation repository access between selected and all repositories

```
PATCH /enterprises/{enterprise}/apps/organizations/{org}/installations/{installation_id}/repositories
```

Toggle repository access for a GitHub App installation between all repositories and selected repositories. You must provide at least one repository when changing the access to 'selected'. If you change the access to 'all', the repositories list must not be provided.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`installation_id`** (integer) (required)
  The unique identifier of the installation.




#### Body parameters

- **`repository_selection`** (string) (required)
  One of either 'all' or 'selected'
  Can be one of: `all`, `selected`

- **`repositories`** (array of strings)
  The repository names to add to the installation. Only required when repository_selection is 'selected'





### HTTP response status codes


- **200** - The GitHub App installation that was updated.




### Code examples



#### Change the repositories accessible to a GitHub App from 'all repositories' to a specified subset.

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/apps/organizations/ORG/installations/1/repositories \
  -d '{
  "repository_selection": "selected",
  "repositories": [
    "hello-world",
    "hello-world-2"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Install a GitHub App on an enterprise-owned organization](#install-a-github-app-on-an-enterprise-owned-organization).





## Grant repository access to an organization installation

```
PATCH /enterprises/{enterprise}/apps/organizations/{org}/installations/{installation_id}/repositories/add
```

Grant repository access to an organization installation. You can add up to 50 repositories at a time. If the installation already has access to the repository, it will not be added again.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`installation_id`** (integer) (required)
  The unique identifier of the installation.




#### Body parameters

- **`repositories`** (array of strings) (required)
  The repository names to add to the installation.





### HTTP response status codes


- **200** - A list of repositories which the authenticated GitHub App should be granted access to.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/apps/organizations/ORG/installations/1/repositories/add \
  -d '{
  "repositories": [
    "hello-world",
    "hello-world-2"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get repositories belonging to an enterprise-owned organization](#get-repositories-belonging-to-an-enterprise-owned-organization).





## Remove repository access from an organization installation

```
PATCH /enterprises/{enterprise}/apps/organizations/{org}/installations/{installation_id}/repositories/remove
```

Remove repository access from a GitHub App installed on an organization. You can remove up to 50 repositories at a time. You cannot remove repositories from an app installed on all repositories, nor can you remove the last repository for an app. If you attempt to do so, the API will return a 422 Unprocessable Entity error.
This API can only be called by a GitHub App installed on the enterprise that owns the organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`installation_id`** (integer) (required)
  The unique identifier of the installation.




#### Body parameters

- **`repositories`** (array of strings) (required)
  The repository names to remove from the installation.





### HTTP response status codes


- **200** - A list of repositories which the authenticated GitHub App has lost access to.


- **422** - The request was well-formed but was unable to be followed due to semantic errors. This can happen if you attempt to remove a repository from an installation that has access to all repositories, or if you attempt to remove the last repository from an installation.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/apps/organizations/ORG/installations/1/repositories/remove \
  -d '{
  "repositories": [
    "hello-world",
    "hello-world-2"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get repositories belonging to an enterprise-owned organization](#get-repositories-belonging-to-an-enterprise-owned-organization).