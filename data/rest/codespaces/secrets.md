# REST API endpoints for Codespaces user secrets

Use the REST API manage secrets that the user has access to in a codespace.

## About Codespaces user secrets

You can create, list, and delete secrets (such as access tokens for cloud services) as well as assign secrets to repositories that the user has access to. These secrets are made available to the codespace at runtime. For more information, see [Managing your account-specific secrets for GitHub Codespaces](/en/codespaces/managing-your-codespaces/managing-your-account-specific-secrets-for-github-codespaces).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List secrets for the authenticated user

```
GET /user/codespaces/secrets
```

Lists all development environment secrets available for a user's codespaces without revealing their
encrypted values.
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

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

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/codespaces/secrets
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `secrets`: required, array of `Codespaces Secret`:
  * `name`: required, string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `visibility`: required, string, enum: `all`, `private`, `selected`
  * `selected_repositories_url`: required, string, format: uri

## Get public key for the authenticated user

```
GET /user/codespaces/secrets/public-key
```

Gets your public key, which you need to encrypt secrets. You need to encrypt a secret before you can create or update secrets.
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/codespaces/secrets/public-key
```

**Response schema (Status: 200):**

* `key_id`: required, string
* `key`: required, string

## Get a secret for the authenticated user

```
GET /user/codespaces/secrets/{secret_name}
```

Gets a development environment secret available to a user's codespaces without revealing its encrypted value.
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`secret_name`** (string) (required)
  The name of the secret.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/codespaces/secrets/SECRET_NAME
```

**Response schema (Status: 200):**

* `name`: required, string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `visibility`: required, string, enum: `all`, `private`, `selected`
* `selected_repositories_url`: required, string, format: uri

## Create or update a secret for the authenticated user

```
PUT /user/codespaces/secrets/{secret_name}
```

Creates or updates a development environment secret for a user's codespace with an encrypted value. Encrypt your secret using
LibSodium. For more information, see "Encrypting secrets for the REST API."
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`secret_name`** (string) (required)
  The name of the secret.

#### Body parameters

* **`encrypted_value`** (string)
  Value for your secret, encrypted with LibSodium using the public key retrieved from the Get the public key for the authenticated user endpoint.

* **`key_id`** (string) (required)
  ID of the key you used to encrypt the secret.

* **`selected_repository_ids`** (array)
  An array of repository ids that can access the user secret. You can manage the list of selected repositories using the List selected repositories for a user secret, Set selected repositories for a user secret, and Remove a selected repository from a user secret endpoints.

### HTTP response status codes

* **201** - Response after successfully creating a secret

* **204** - Response after successfully updating a secret

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example 1: Status Code 201

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/user/codespaces/secrets/SECRET_NAME \
  -d '{
  "encrypted_value": "c2VjcmV0",
  "key_id": "012345678912345678",
  "selected_repository_ids": [
    "1234567",
    "2345678"
  ]
}'
```

**Response schema (Status: 201):**

#### Example 2: Status Code 204

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/user/codespaces/secrets/SECRET_NAME \
  -d '{
  "encrypted_value": "c2VjcmV0",
  "key_id": "012345678912345678",
  "selected_repository_ids": [
    "1234567",
    "2345678"
  ]
}'
```

**Response schema (Status: 204):**

## Delete a secret for the authenticated user

```
DELETE /user/codespaces/secrets/{secret_name}
```

Deletes a development environment secret from a user's codespaces using the secret name. Deleting the secret will remove access from all codespaces that were allowed to access the secret.
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`secret_name`** (string) (required)
  The name of the secret.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/codespaces/secrets/SECRET_NAME
```

**Response schema (Status: 204):**

## List selected repositories for a user secret

```
GET /user/codespaces/secrets/{secret_name}/repositories
```

List the repositories that have been granted the ability to use a user's development environment secret.
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`secret_name`** (string) (required)
  The name of the secret.

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/codespaces/secrets/SECRET_NAME/repositories
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

## Set selected repositories for a user secret

```
PUT /user/codespaces/secrets/{secret_name}/repositories
```

Select the repositories that will use a user's development environment secret.
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`secret_name`** (string) (required)
  The name of the secret.

#### Body parameters

* **`selected_repository_ids`** (array of integers) (required)
  An array of repository ids for which a codespace can access the secret. You can manage the list of selected repositories using the List selected repositories for a user secret, Add a selected repository to a user secret, and Remove a selected repository from a user secret endpoints.

### HTTP response status codes

* **204** - No Content when repositories were added to the selected list

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/user/codespaces/secrets/SECRET_NAME/repositories \
  -d '{
  "selected_repository_ids": [
    "1296269",
    "1296280"
  ]
}'
```

**Response schema (Status: 204):**

## Add a selected repository to a user secret

```
PUT /user/codespaces/secrets/{secret_name}/repositories/{repository_id}
```

Adds a repository to the selected repositories for a user's development environment secret.
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`secret_name`** (string) (required)
  The name of the secret.

* **`repository_id`** (integer) (required)

### HTTP response status codes

* **204** - No Content when repository was added to the selected list

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/user/codespaces/secrets/SECRET_NAME/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**

## Remove a selected repository from a user secret

```
DELETE /user/codespaces/secrets/{secret_name}/repositories/{repository_id}
```

Removes a repository from the selected repositories for a user's development environment secret.
The authenticated user must have Codespaces access to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the codespace or codespace:secrets scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`secret_name`** (string) (required)
  The name of the secret.

* **`repository_id`** (integer) (required)

### HTTP response status codes

* **204** - No Content when repository was removed from the selected list

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/codespaces/secrets/SECRET_NAME/repositories/REPOSITORY_ID
```

**Response schema (Status: 204):**