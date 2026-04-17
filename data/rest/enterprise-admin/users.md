# REST API endpoints for enterprise users

Use the REST API to suspend, unsuspend, promote, and demote users on your enterprise.

## About user administration

These endpoints are only available to [authenticated](/en/enterprise-server@3.20/rest/overview/authenticating-to-the-rest-api) site administrators. Normal users will receive a `403` response.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## List public keys

```
GET /admin/keys
```

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

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`sort`** (string)
  Default: `created`
  Can be one of: `created`, `updated`, `accessed`

* **`since`** (string)
  Only show public keys accessed after the given time.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/admin/keys
```

**Response schema (Status: 200):**

Array of objects:

* `id`: required, integer, format: int64
* `key`: required, string
* `user_id`: required, integer or null
* `repository_id`: required, integer or null, format: int64
* `url`: required, string
* `title`: required, string
* `read_only`: required, boolean
* `verified`: required, boolean
* `created_at`: required, string, format: date-time
* `added_by`: string or null
* `last_used`: required, string or null, format: date-time
* `enabled`: boolean

## Delete a public key

```
DELETE /admin/keys/{key_ids}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`key_ids`** (string) (required)
  The unique identifier of the key.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/admin/keys/KEY_IDS
```

**Response schema (Status: 204):**

## List personal access tokens

```
GET /admin/tokens
```

Lists personal access tokens for all users, including admin users.

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
  http(s)://HOSTNAME/api/v3/admin/tokens
```

**Response schema (Status: 200):**

Array of `Authorization`:

* `id`: required, integer, format: int64
* `url`: required, string, format: uri
* `scopes`: required, array of string or null
* `token`: required, string
* `token_last_eight`: required, string or null
* `hashed_token`: required, string or null
* `app`: required, object:
  * `client_id`: required, string
  * `name`: required, string
  * `url`: required, string, format: uri
* `note`: required, string or null
* `note_url`: required, string or null, format: uri
* `updated_at`: required, string, format: date-time
* `created_at`: required, string, format: date-time
* `fingerprint`: required, string or null
* `user`: any of:
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
* `installation`: any of:
  * **null**
  * **Scoped Installation**
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
      * `enterprise_administration`: string, enum: `read`, `write`
      * `enterprise_custom_properties`: string, enum: `read`, `write`
      * `enterprise_custom_properties_for_organizations`: string, enum: `read`, `write`, `admin`
      * `enterprise_organization_installations`: string, enum: `read`, `write`
      * `enterprise_organization_installation_repositories`: string, enum: `read`, `write`
    * `repository_selection`: required, string, enum: `all`, `selected`
    * `single_file_name`: required, string or null
    * `has_multiple_single_files`: boolean
    * `single_file_paths`: array of string
    * `repositories_url`: required, string, format: uri
    * `account`: required, `Simple User`:
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
* `expires_at`: required, string or null, format: date-time

## Delete a personal access token

```
DELETE /admin/tokens/{token_id}
```

Deletes a personal access token. Returns a 403 - Forbidden status when a personal access token is in use. For example, if you access this endpoint with the same personal access token that you are trying to delete, you will receive this error.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`token_id`** (integer) (required)
  The unique identifier of the token.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/admin/tokens/TOKEN_ID
```

**Response schema (Status: 204):**

## Create a user

```
POST /admin/users
```

If an external authentication mechanism is used, the login name should match the login name in the external system. If you are using LDAP authentication, you should also update the LDAP mapping for the user.
The login name will be normalized to only contain alphanumeric characters or single hyphens. For example, if you send "octo\_cat" as the login, a user named "octo-cat" will be created.
If the login name or email address is already associated with an account, the server will return a 422 response.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`login`** (string) (required)
  The user's username.

* **`email`** (string)
  Required for built-in authentication. The user's email
  address. This parameter can be omitted when using CAS, LDAP, or SAML.
  For more information, see "About authentication for your enterprise."

* **`suspended`** (boolean)
  Whether to set the user as suspended when the user is created.
  Default: `false`

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/users \
  -d '{
  "login": "monalisa",
  "email": "octocat@github.com"
}'
```

**Response schema (Status: 201):**

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

## Update the username for a user

```
PATCH /admin/users/{username}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

#### Body parameters

* **`login`** (string) (required)
  The user's new username.

### HTTP response status codes

* **202** - Accepted

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/admin/users/USERNAME \
  -d '{
  "login": "thenewmonalisa"
}'
```

**Response schema (Status: 202):**

* `message`: string
* `url`: string

## Delete a user

```
DELETE /admin/users/{username}
```

Deleting a user will delete all their repositories, gists, applications, and personal settings. Suspending a user is often a better option.
You can delete any user account except your own.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/admin/users/USERNAME
```

**Response schema (Status: 204):**

## Create an impersonation OAuth token

```
POST /admin/users/{username}/authorizations
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

#### Body parameters

* **`scopes`** (array of strings) (required)
  A list of scopes.

### HTTP response status codes

* **200** - Response when getting an existing impersonation OAuth token

* **201** - Response when creating a new impersonation OAuth token

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/users/USERNAME/authorizations \
  -d '{
  "scopes": [
    "public_repo"
  ]
}'
```

**Response schema (Status: 200):**

* `id`: required, integer, format: int64
* `url`: required, string, format: uri
* `scopes`: required, array of string or null
* `token`: required, string
* `token_last_eight`: required, string or null
* `hashed_token`: required, string or null
* `app`: required, object:
  * `client_id`: required, string
  * `name`: required, string
  * `url`: required, string, format: uri
* `note`: required, string or null
* `note_url`: required, string or null, format: uri
* `updated_at`: required, string, format: date-time
* `created_at`: required, string, format: date-time
* `fingerprint`: required, string or null
* `user`: any of:
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
* `installation`: any of:
  * **null**
  * **Scoped Installation**
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
      * `enterprise_administration`: string, enum: `read`, `write`
      * `enterprise_custom_properties`: string, enum: `read`, `write`
      * `enterprise_custom_properties_for_organizations`: string, enum: `read`, `write`, `admin`
      * `enterprise_organization_installations`: string, enum: `read`, `write`
      * `enterprise_organization_installation_repositories`: string, enum: `read`, `write`
    * `repository_selection`: required, string, enum: `all`, `selected`
    * `single_file_name`: required, string or null
    * `has_multiple_single_files`: boolean
    * `single_file_paths`: array of string
    * `repositories_url`: required, string, format: uri
    * `account`: required, `Simple User`:
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
* `expires_at`: required, string or null, format: date-time

#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/users/USERNAME/authorizations \
  -d '{
  "scopes": [
    "public_repo"
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer, format: int64
* `url`: required, string, format: uri
* `scopes`: required, array of string or null
* `token`: required, string
* `token_last_eight`: required, string or null
* `hashed_token`: required, string or null
* `app`: required, object:
  * `client_id`: required, string
  * `name`: required, string
  * `url`: required, string, format: uri
* `note`: required, string or null
* `note_url`: required, string or null, format: uri
* `updated_at`: required, string, format: date-time
* `created_at`: required, string, format: date-time
* `fingerprint`: required, string or null
* `user`: any of:
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
* `installation`: any of:
  * **null**
  * **Scoped Installation**
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
      * `enterprise_administration`: string, enum: `read`, `write`
      * `enterprise_custom_properties`: string, enum: `read`, `write`
      * `enterprise_custom_properties_for_organizations`: string, enum: `read`, `write`, `admin`
      * `enterprise_organization_installations`: string, enum: `read`, `write`
      * `enterprise_organization_installation_repositories`: string, enum: `read`, `write`
    * `repository_selection`: required, string, enum: `all`, `selected`
    * `single_file_name`: required, string or null
    * `has_multiple_single_files`: boolean
    * `single_file_paths`: array of string
    * `repositories_url`: required, string, format: uri
    * `account`: required, `Simple User`:
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
* `expires_at`: required, string or null, format: date-time

## Delete an impersonation OAuth token

```
DELETE /admin/users/{username}/authorizations
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/admin/users/USERNAME/authorizations
```

**Response schema (Status: 204):**

## Promote a user to be a site administrator

```
PUT /users/{username}/site_admin
```

Note that you'll need to set Content-Length to zero when calling out to this endpoint. For more information, see "HTTP method."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/api/v3/users/USERNAME/site_admin
```

**Response schema (Status: 204):**

## Demote a site administrator

```
DELETE /users/{username}/site_admin
```

You can demote any user account except your own.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/users/USERNAME/site_admin
```

**Response schema (Status: 204):**

## Suspend a user

```
PUT /users/{username}/suspended
```

If your GitHub instance uses LDAP Sync with Active Directory LDAP servers, Active Directory LDAP-authenticated users cannot be suspended through this API. If you attempt to suspend an Active Directory LDAP-authenticated user through this API, it will return a 403 response.
You can suspend any user account except your own.
Note that, if you choose not to pass any parameters, you'll need to set Content-Length to zero when calling out to this endpoint. For more information, see "HTTP method."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

#### Body parameters

* **`reason`** (string)
  The reason the user is being suspended. This message will be logged in the audit log. If you don't provide a reason, it will default to "Suspended via API by SITE\_ADMINISTRATOR", where SITE\_ADMINISTRATOR is the person who performed the action.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/api/v3/users/USERNAME/suspended \
  -d '{
  "reason": "Suspended during leave of absence."
}'
```

**Response schema (Status: 204):**

## Unsuspend a user

```
DELETE /users/{username}/suspended
```

If your GitHub instance uses LDAP Sync with Active Directory LDAP servers, this API is disabled and will return a 403 response. Active Directory LDAP-authenticated users cannot be unsuspended using the API.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

#### Body parameters

* **`reason`** (string)
  The reason the user is being unsuspended. This message will be logged in the audit log. If you don't provide a reason, it will default to "Unsuspended via API by SITE\_ADMINISTRATOR", where SITE\_ADMINISTRATOR is the person who performed the action.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/users/USERNAME/suspended \
  -d '{
  "reason": "Unsuspended after leave of absence."
}'
```

**Response schema (Status: 204):**