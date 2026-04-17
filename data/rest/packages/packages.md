# REST API endpoints for packages

Use the REST API to interact with GitHub Packages.

## About GitHub Packages

GitHub Packages supports a range of package managers for publishing packages. For more information, see [Introduction to GitHub Packages](/en/packages/learn-github-packages/introduction-to-github-packages#supported-clients-and-formats).

After you publish a package, you can use the REST API to manage the package in your GitHub repositories and organizations. For more information, see [Deleting and restoring a package](/en/packages/learn-github-packages/deleting-and-restoring-a-package).

To use the REST API to manage GitHub Packages, you must authenticate using a personal access token (classic).

* To access package metadata, your token must include the `read:packages` scope.
* To delete packages and package versions, your token must include the `read:packages` and `delete:packages` scopes.
* To restore packages and package versions, your token must include the `read:packages` and `write:packages` scopes.

If your package is in a registry that supports granular permissions, then your token does not need the `repo` scope to access or manage this package. If your package is in a registry that only supports repository-scoped permissions, then your token must also include the `repo` scope since your package inherits permissions from a GitHub repository. For a list of registries that only support repository-scoped permissions, see [About permissions for GitHub Packages](/en/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get list of conflicting packages during Docker migration for organization

```
GET /orgs/{org}/docker/conflicts
```

Lists all packages that are in a specific organization, are readable by the requesting user, and that encountered a conflict during a Docker migration.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/docker/conflicts
```

**Response schema (Status: 200):**

Array of `Package`:

* `id`: required, integer
* `name`: required, string
* `package_type`: required, string, enum: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`
* `url`: required, string
* `html_url`: required, string
* `version_count`: required, integer
* `visibility`: required, string, enum: `private`, `public`
* `owner`: any of:
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
* `repository`: any of:
  * **null**
  * **Minimal Repository**
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time

## List packages for an organization

```
GET /orgs/{org}/packages
```

Lists packages in an organization readable by the user.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`visibility`** (string)
  The selected visibility of the packages.  This parameter is optional and only filters an existing result set.
  The internal visibility is only supported for GitHub Packages registries that allow for granular permissions. For other ecosystems internal is synonymous with private.
  For the list of GitHub Packages registries that support granular permissions, see "About permissions for GitHub Packages."
  Can be one of: `public`, `private`, `internal`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

* **200** - OK

* **400** - The value of per\_page multiplied by page cannot be greater than 10000.

* **401** - Requires authentication

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/packages
```

**Response schema (Status: 200):**

Same response schema as [Get list of conflicting packages during Docker migration for organization](#get-list-of-conflicting-packages-during-docker-migration-for-organization).

## Get a package for an organization

```
GET /orgs/{org}/packages/{package_type}/{package_name}
```

Gets a specific package in an organization.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/packages/PACKAGE_TYPE/PACKAGE_NAME
```

**Response schema (Status: 200):**

* `id`: required, integer
* `name`: required, string
* `package_type`: required, string, enum: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`
* `url`: required, string
* `html_url`: required, string
* `version_count`: required, integer
* `visibility`: required, string, enum: `private`, `public`
* `owner`: any of:
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
* `repository`: any of:
  * **null**
  * **Minimal Repository**
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time

## Delete a package for an organization

```
DELETE /orgs/{org}/packages/{package_type}/{package_name}
```

Deletes an entire package in an organization. You cannot delete a public package if any version of the package has more than 5,000 downloads. In this scenario, contact GitHub support for further assistance.
The authenticated user must have admin permissions in the organization to use this endpoint. If the package\_type belongs to a GitHub Packages registry that supports granular permissions, the authenticated user must also have admin permissions to the package. For the list of these registries, see "About permissions for GitHub Packages."
OAuth app tokens and personal access tokens (classic) need the read:packages and delete:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/packages/PACKAGE_TYPE/PACKAGE_NAME
```

**Response schema (Status: 204):**

## Restore a package for an organization

```
POST /orgs/{org}/packages/{package_type}/{package_name}/restore
```

Restores an entire package in an organization.
You can restore a deleted package under the following conditions:

The package was deleted within the last 30 days.
The same package namespace and version is still available and not reused for a new package. If the same package namespace is not available, you will not be able to restore your package. In this scenario, to restore the deleted package, you must delete the new package that uses the deleted package's namespace first.

The authenticated user must have admin permissions in the organization to use this endpoint. If the package\_type belongs to a GitHub Packages registry that supports granular permissions, the authenticated user must also have admin permissions to the package. For the list of these registries, see "About permissions for GitHub Packages."
OAuth app tokens and personal access tokens (classic) need the read:packages and write:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`token`** (string)
  package token

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/packages/PACKAGE_TYPE/PACKAGE_NAME/restore
```

**Response schema (Status: 204):**

## List package versions for a package owned by an organization

```
GET /orgs/{org}/packages/{package_type}/{package_name}/versions
```

Lists package versions for a package owned by an organization.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`state`** (string)
  The state of the package, either active or deleted.
  Default: `active`
  Can be one of: `active`, `deleted`

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/packages/PACKAGE_TYPE/PACKAGE_NAME/versions
```

**Response schema (Status: 200):**

Array of `Package Version`:

* `id`: required, integer
* `name`: required, string
* `url`: required, string
* `package_html_url`: required, string
* `html_url`: string
* `license`: string
* `description`: string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `deleted_at`: string, format: date-time
* `metadata`: `Package Version Metadata`:
  * `package_type`: required, string, enum: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`
  * `container`: `Container Metadata`:
    * `tags`: required, array of string
  * `docker`: `Docker Metadata`:
    * `tag`: array of string

## Get a package version for an organization

```
GET /orgs/{org}/packages/{package_type}/{package_name}/versions/{package_version_id}
```

Gets a specific package version in an organization.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID
```

**Response schema (Status: 200):**

* `id`: required, integer
* `name`: required, string
* `url`: required, string
* `package_html_url`: required, string
* `html_url`: string
* `license`: string
* `description`: string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `deleted_at`: string, format: date-time
* `metadata`: `Package Version Metadata`:
  * `package_type`: required, string, enum: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`
  * `container`: `Container Metadata`:
    * `tags`: required, array of string
  * `docker`: `Docker Metadata`:
    * `tag`: array of string

## Delete package version for an organization

```
DELETE /orgs/{org}/packages/{package_type}/{package_name}/versions/{package_version_id}
```

Deletes a specific package version in an organization. If the package is public and the package version has more than 5,000 downloads, you cannot delete the package version. In this scenario, contact GitHub support for further assistance.
The authenticated user must have admin permissions in the organization to use this endpoint. If the package\_type belongs to a GitHub Packages registry that supports granular permissions, the authenticated user must also have admin permissions to the package. For the list of these registries, see "About permissions for GitHub Packages."
OAuth app tokens and personal access tokens (classic) need the read:packages and delete:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID
```

**Response schema (Status: 204):**

## Restore package version for an organization

```
POST /orgs/{org}/packages/{package_type}/{package_name}/versions/{package_version_id}/restore
```

Restores a specific package version in an organization.
You can restore a deleted package under the following conditions:

The package was deleted within the last 30 days.
The same package namespace and version is still available and not reused for a new package. If the same package namespace is not available, you will not be able to restore your package. In this scenario, to restore the deleted package, you must delete the new package that uses the deleted package's namespace first.

The authenticated user must have admin permissions in the organization to use this endpoint. If the package\_type belongs to a GitHub Packages registry that supports granular permissions, the authenticated user must also have admin permissions to the package. For the list of these registries, see "About permissions for GitHub Packages."
OAuth app tokens and personal access tokens (classic) need the read:packages and write:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID/restore
```

**Response schema (Status: 204):**

## Get list of conflicting packages during Docker migration for authenticated-user

```
GET /user/docker/conflicts
```

Lists all packages that are owned by the authenticated user within the user's namespace, and that encountered a conflict during a Docker migration.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/docker/conflicts
```

**Response schema (Status: 200):**

Same response schema as [Get list of conflicting packages during Docker migration for organization](#get-list-of-conflicting-packages-during-docker-migration-for-organization).

## List packages for the authenticated user's namespace

```
GET /user/packages
```

Lists packages owned by the authenticated user within the user's namespace.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`visibility`** (string)
  The selected visibility of the packages.  This parameter is optional and only filters an existing result set.
  The internal visibility is only supported for GitHub Packages registries that allow for granular permissions. For other ecosystems internal is synonymous with private.
  For the list of GitHub Packages registries that support granular permissions, see "About permissions for GitHub Packages."
  Can be one of: `public`, `private`, `internal`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

* **200** - OK

* **400** - The value of per\_page multiplied by page cannot be greater than 10000.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/packages
```

**Response schema (Status: 200):**

Same response schema as [Get list of conflicting packages during Docker migration for organization](#get-list-of-conflicting-packages-during-docker-migration-for-organization).

## Get a package for the authenticated user

```
GET /user/packages/{package_type}/{package_name}
```

Gets a specific package for a package owned by the authenticated user.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/packages/PACKAGE_TYPE/PACKAGE_NAME
```

**Response schema (Status: 200):**

Same response schema as [Get a package for an organization](#get-a-package-for-an-organization).

## Delete a package for the authenticated user

```
DELETE /user/packages/{package_type}/{package_name}
```

Deletes a package owned by the authenticated user. You cannot delete a public package if any version of the package has more than 5,000 downloads. In this scenario, contact GitHub support for further assistance.
OAuth app tokens and personal access tokens (classic) need the read:packages and delete:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/packages/PACKAGE_TYPE/PACKAGE_NAME
```

**Response schema (Status: 204):**

## Restore a package for the authenticated user

```
POST /user/packages/{package_type}/{package_name}/restore
```

Restores a package owned by the authenticated user.
You can restore a deleted package under the following conditions:

The package was deleted within the last 30 days.
The same package namespace and version is still available and not reused for a new package. If the same package namespace is not available, you will not be able to restore your package. In this scenario, to restore the deleted package, you must delete the new package that uses the deleted package's namespace first.

OAuth app tokens and personal access tokens (classic) need the read:packages and write:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`token`** (string)
  package token

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/packages/PACKAGE_TYPE/PACKAGE_NAME/restore
```

**Response schema (Status: 204):**

## List package versions for a package owned by the authenticated user

```
GET /user/packages/{package_type}/{package_name}/versions
```

Lists package versions for a package owned by the authenticated user.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`state`** (string)
  The state of the package, either active or deleted.
  Default: `active`
  Can be one of: `active`, `deleted`

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/packages/PACKAGE_TYPE/PACKAGE_NAME/versions
```

**Response schema (Status: 200):**

Same response schema as [List package versions for a package owned by an organization](#list-package-versions-for-a-package-owned-by-an-organization).

## Get a package version for the authenticated user

```
GET /user/packages/{package_type}/{package_name}/versions/{package_version_id}
```

Gets a specific package version for a package owned by the authenticated user.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID
```

**Response schema (Status: 200):**

Same response schema as [Get a package version for an organization](#get-a-package-version-for-an-organization).

## Delete a package version for the authenticated user

```
DELETE /user/packages/{package_type}/{package_name}/versions/{package_version_id}
```

Deletes a specific package version for a package owned by the authenticated user.  If the package is public and the package version has more than 5,000 downloads, you cannot delete the package version. In this scenario, contact GitHub support for further assistance.
The authenticated user must have admin permissions in the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:packages and delete:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID
```

**Response schema (Status: 204):**

## Restore a package version for the authenticated user

```
POST /user/packages/{package_type}/{package_name}/versions/{package_version_id}/restore
```

Restores a package version owned by the authenticated user.
You can restore a deleted package version under the following conditions:

The package was deleted within the last 30 days.
The same package namespace and version is still available and not reused for a new package. If the same package namespace is not available, you will not be able to restore your package. In this scenario, to restore the deleted package, you must delete the new package that uses the deleted package's namespace first.

OAuth app tokens and personal access tokens (classic) need the read:packages and write:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID/restore
```

**Response schema (Status: 204):**

## Get list of conflicting packages during Docker migration for user

```
GET /users/{username}/docker/conflicts
```

Lists all packages that are in a specific user's namespace, that the requesting user has access to, and that encountered a conflict during Docker migration.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/docker/conflicts
```

**Response schema (Status: 200):**

Same response schema as [Get list of conflicting packages during Docker migration for organization](#get-list-of-conflicting-packages-during-docker-migration-for-organization).

## List packages for a user

```
GET /users/{username}/packages
```

Lists all packages in a user's namespace for which the requesting user has access.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`visibility`** (string)
  The selected visibility of the packages.  This parameter is optional and only filters an existing result set.
  The internal visibility is only supported for GitHub Packages registries that allow for granular permissions. For other ecosystems internal is synonymous with private.
  For the list of GitHub Packages registries that support granular permissions, see "About permissions for GitHub Packages."
  Can be one of: `public`, `private`, `internal`

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

* **200** - OK

* **400** - The value of per\_page multiplied by page cannot be greater than 10000.

* **401** - Requires authentication

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/packages
```

**Response schema (Status: 200):**

Same response schema as [Get list of conflicting packages during Docker migration for organization](#get-list-of-conflicting-packages-during-docker-migration-for-organization).

## Get a package for a user

```
GET /users/{username}/packages/{package_type}/{package_name}
```

Gets a specific package metadata for a public package owned by a user.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/packages/PACKAGE_TYPE/PACKAGE_NAME
```

**Response schema (Status: 200):**

Same response schema as [Get a package for an organization](#get-a-package-for-an-organization).

## Delete a package for a user

```
DELETE /users/{username}/packages/{package_type}/{package_name}
```

Deletes an entire package for a user. You cannot delete a public package if any version of the package has more than 5,000 downloads. In this scenario, contact GitHub support for further assistance.
If the package\_type belongs to a GitHub Packages registry that supports granular permissions, the authenticated user must have admin permissions to the package. For the list of these registries, see "About permissions for GitHub Packages."
OAuth app tokens and personal access tokens (classic) need the read:packages and delete:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/packages/PACKAGE_TYPE/PACKAGE_NAME
```

**Response schema (Status: 204):**

## Restore a package for a user

```
POST /users/{username}/packages/{package_type}/{package_name}/restore
```

Restores an entire package for a user.
You can restore a deleted package under the following conditions:

The package was deleted within the last 30 days.
The same package namespace and version is still available and not reused for a new package. If the same package namespace is not available, you will not be able to restore your package. In this scenario, to restore the deleted package, you must delete the new package that uses the deleted package's namespace first.

If the package\_type belongs to a GitHub Packages registry that supports granular permissions, the authenticated user must have admin permissions to the package. For the list of these registries, see "About permissions for GitHub Packages."
OAuth app tokens and personal access tokens (classic) need the read:packages and write:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`token`** (string)
  package token

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/packages/PACKAGE_TYPE/PACKAGE_NAME/restore
```

**Response schema (Status: 204):**

## List package versions for a package owned by a user

```
GET /users/{username}/packages/{package_type}/{package_name}/versions
```

Lists package versions for a public package owned by a specified user.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/packages/PACKAGE_TYPE/PACKAGE_NAME/versions
```

**Response schema (Status: 200):**

Same response schema as [List package versions for a package owned by an organization](#list-package-versions-for-a-package-owned-by-an-organization).

## Get a package version for a user

```
GET /users/{username}/packages/{package_type}/{package_name}/versions/{package_version_id}
```

Gets a specific package version for a public package owned by a specified user.
OAuth app tokens and personal access tokens (classic) need the read:packages scope to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID
```

**Response schema (Status: 200):**

Same response schema as [Get a package version for an organization](#get-a-package-version-for-an-organization).

## Delete package version for a user

```
DELETE /users/{username}/packages/{package_type}/{package_name}/versions/{package_version_id}
```

Deletes a specific package version for a user. If the package is public and the package version has more than 5,000 downloads, you cannot delete the package version. In this scenario, contact GitHub support for further assistance.
If the package\_type belongs to a GitHub Packages registry that supports granular permissions, the authenticated user must have admin permissions to the package. For the list of these registries, see "About permissions for GitHub Packages."
OAuth app tokens and personal access tokens (classic) need the read:packages and delete:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID
```

**Response schema (Status: 204):**

## Restore package version for a user

```
POST /users/{username}/packages/{package_type}/{package_name}/versions/{package_version_id}/restore
```

Restores a specific package version for a user.
You can restore a deleted package under the following conditions:

The package was deleted within the last 30 days.
The same package namespace and version is still available and not reused for a new package. If the same package namespace is not available, you will not be able to restore your package. In this scenario, to restore the deleted package, you must delete the new package that uses the deleted package's namespace first.

If the package\_type belongs to a GitHub Packages registry that supports granular permissions, the authenticated user must have admin permissions to the package. For the list of these registries, see "About permissions for GitHub Packages."
OAuth app tokens and personal access tokens (classic) need the read:packages and write:packages scopes to use this endpoint. For more information, see "About permissions for GitHub Packages."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`package_type`** (string) (required)
  The type of supported package. Packages in GitHub's Gradle registry have the type maven. Docker images pushed to GitHub's Container registry (ghcr.io) have the type container. You can use the type docker to find images that were pushed to GitHub's Docker registry (docker.pkg.github.com), even if these have now been migrated to the Container registry.
  Can be one of: `npm`, `maven`, `rubygems`, `docker`, `nuget`, `container`

* **`package_name`** (string) (required)
  The name of the package.

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`package_version_id`** (integer) (required)
  Unique identifier of the package version.

### HTTP response status codes

* **204** - No Content

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/packages/PACKAGE_TYPE/PACKAGE_NAME/versions/PACKAGE_VERSION_ID/restore
```

**Response schema (Status: 204):**