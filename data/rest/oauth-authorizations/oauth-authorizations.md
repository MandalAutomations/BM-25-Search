# REST API endpoints for OAuth app authorizations

Use the REST API to manage the access OAuth apps have to your account.

## About OAuth authorizations

You can use the REST API to manage the access OAuth apps have to your account. You can only access these endpoints via basic authentication using your username and password, not tokens.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.


## List your grants

```
GET /applications/grants
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.

You can use this API to list the set of OAuth applications that have been granted access to your account. Unlike the list your authorizations API, this API does not manage individual tokens. This API will return one entry for each OAuth application that has been granted access to your account, regardless of the number of tokens an application has generated for your user. The list of OAuth applications returned matches what is shown on the application authorizations settings screen within GitHub. The scopes returned are the union of scopes authorized for the application. For example, if an application has one token with repo scope and another token with user scope, the grant will return ["repo", "user"].


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

- **`client_id`** (string)
  The client ID of your GitHub app.






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/applications/grants
```

**Response schema (Status: 200):**

Array of `Application Grant`:
  * `id`: required, integer, format: int64
  * `url`: required, string, format: uri
  * `app`: required, object:
    * `client_id`: required, string
    * `name`: required, string
    * `url`: required, string, format: uri
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `scopes`: required, array of string
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





## Get a single grant

```
GET /applications/grants/{grant_id}
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`grant_id`** (integer) (required)
  The unique identifier of the grant.






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
  http(s)://HOSTNAME/api/v3/applications/grants/GRANT_ID
```

**Response schema (Status: 200):**

* `id`: required, integer, format: int64
* `url`: required, string, format: uri
* `app`: required, object:
  * `client_id`: required, string
  * `name`: required, string
  * `url`: required, string, format: uri
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `scopes`: required, array of string
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





## Delete a grant

```
DELETE /applications/grants/{grant_id}
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.

Deleting an OAuth application's grant will also delete all OAuth tokens associated with the application for your user. Once deleted, the application has no access to your account and is no longer listed on the application authorizations settings screen within GitHub.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`grant_id`** (integer) (required)
  The unique identifier of the grant.






### HTTP response status codes


- **204** - No Content


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/applications/grants/GRANT_ID
```

**Response schema (Status: 204):**





## List your authorizations

```
GET /authorizations
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.


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

- **`client_id`** (string)
  The client ID of your GitHub app.






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/authorizations
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





## Create a new authorization

```
POST /authorizations
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13 2020. For more information, including scheduled brownouts, see the blog post.

Warning

Apps must use the web application flow to obtain OAuth tokens that work with GitHub Enterprise Server SAML organizations. OAuth tokens created using the Authorizations API will be unable to access GitHub Enterprise Server SAML organizations. For more information, see the blog post.

Creates OAuth tokens using Basic Authentication. If you have two-factor authentication setup, Basic Authentication for this endpoint requires that you use a one-time password (OTP) and your username and password instead of tokens. For more information, see "Working with two-factor authentication."
To create tokens for a particular OAuth application using this endpoint, you must authenticate as the user you want to create an authorization for and provide the app's client ID and secret, found on your OAuth application's settings page. If your OAuth application intends to create multiple tokens for one user, use fingerprint to differentiate between them.
You can also create tokens on GitHub Enterprise Server from the personal access tokens settings page. Read more about these tokens in the GitHub Help documentation.
Organizations that enforce SAML SSO require personal access tokens to be allowed. For more information, see "About identity and access management with SAML single sign-on" in the GitHub Enterprise Cloud documentation.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.





#### Body parameters

- **`scopes`** (array of strings or null)
  A list of scopes that this authorization is in.

- **`note`** (string)
  A note to remind you what the OAuth token is for.

- **`note_url`** (string)
  A URL to remind you what app the OAuth token is for.

- **`client_id`** (string)
  The OAuth app client key for which to create the token.

- **`client_secret`** (string)
  The OAuth app client secret for which to create the token.

- **`fingerprint`** (string)
  A unique string to distinguish an authorization from others created for the same client ID and user.





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **410** - Gone


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Create an authorization

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/authorizations \
  -d '{
  "scopes": [
    "public_repo"
  ],
  "note": "optional note",
  "note_url": "http://optional/note/url",
  "client_id": "abcde12345fghij67890",
  "client_secret": "3ef4ad510c59ad37bac6bb4f80047fb3aee3cc7f"
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





## Get-or-create an authorization for a specific app

```
PUT /authorizations/clients/{client_id}
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.

Warning

Apps must use the web application flow to obtain OAuth tokens that work with GitHub Enterprise Server SAML organizations. OAuth tokens created using the Authorizations API will be unable to access GitHub Enterprise Server SAML organizations. For more information, see the blog post.

Creates a new authorization for the specified OAuth application, only if an authorization for that application doesn't already exist for the user. The URL includes the 20 character client ID for the OAuth app that is requesting the token. It returns the user's existing authorization for the application if one is present. Otherwise, it creates and returns a new one.
If you have two-factor authentication setup, Basic Authentication for this endpoint requires that you use a one-time password (OTP) and your username and password instead of tokens. For more information, see "Working with two-factor authentication."


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`client_id`** (string) (required)
  The client ID of the OAuth app.




#### Body parameters

- **`client_secret`** (string) (required)
  The OAuth app client secret for which to create the token.

- **`scopes`** (array of strings or null)
  A list of scopes that this authorization is in.

- **`note`** (string)
  A note to remind you what the OAuth token is for.

- **`note_url`** (string)
  A URL to remind you what app the OAuth token is for.

- **`fingerprint`** (string)
  A unique string to distinguish an authorization from others created for the same client ID and user.





### HTTP response status codes


- **200** - if returning an existing token


- **201** - Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Create an authorization for an app 1: Status Code 200

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/api/v3/authorizations/clients/abcde12345fghij67890 \
  -d '{
  "client_secret": "3ef4ad510c59ad37bac6bb4f80047fb3aee3cc7f",
  "scopes": [
    "public_repo"
  ],
  "note": "optional note",
  "note_url": "http://optional/note/url"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a new authorization](#create-a-new-authorization).



#### Create an authorization for an app 2: Status Code 201

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/api/v3/authorizations/clients/abcde12345fghij67890 \
  -d '{
  "client_secret": "3ef4ad510c59ad37bac6bb4f80047fb3aee3cc7f",
  "scopes": [
    "public_repo"
  ],
  "note": "optional note",
  "note_url": "http://optional/note/url"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a new authorization](#create-a-new-authorization).





## Get-or-create an authorization for a specific app and fingerprint

```
PUT /authorizations/clients/{client_id}/{fingerprint}
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.

Warning

Apps must use the web application flow to obtain OAuth tokens that work with GitHub Enterprise Server SAML organizations. OAuth tokens created using the Authorizations API will be unable to access GitHub Enterprise Server SAML organizations. For more information, see the blog post.

This method will create a new authorization for the specified OAuth application, only if an authorization for that application and fingerprint do not already exist for the user. The URL includes the 20 character client ID for the OAuth app that is requesting the token. fingerprint is a unique string to distinguish an authorization from others created for the same client ID and user. It returns the user's existing authorization for the application if one is present. Otherwise, it creates and returns a new one.
If you have two-factor authentication setup, Basic Authentication for this endpoint requires that you use a one-time password (OTP) and your username and password instead of tokens. For more information, see "Working with two-factor authentication."


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`client_id`** (string) (required)
  The client ID of the OAuth app.

- **`fingerprint`** (string) (required)




#### Body parameters

- **`client_secret`** (string) (required)
  The OAuth app client secret for which to create the token.

- **`scopes`** (array of strings or null)
  A list of scopes that this authorization is in.

- **`note`** (string)
  A note to remind you what the OAuth token is for.

- **`note_url`** (string)
  A URL to remind you what app the OAuth token is for.





### HTTP response status codes


- **200** - if returning an existing token


- **201** - Response if returning a new token


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Create an authorization for an app and fingerprint 1: Status Code 200

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/api/v3/authorizations/clients/abcde12345fghij67890/FINGERPRINT \
  -d '{
  "client_secret": "3ef4ad510c59ad37bac6bb4f80047fb3aee3cc7f",
  "scopes": [
    "public_repo"
  ],
  "note": "optional note",
  "note_url": "http://optional/note/url"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a new authorization](#create-a-new-authorization).



#### Create an authorization for an app and fingerprint 2: Status Code 201

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/api/v3/authorizations/clients/abcde12345fghij67890/FINGERPRINT \
  -d '{
  "client_secret": "3ef4ad510c59ad37bac6bb4f80047fb3aee3cc7f",
  "scopes": [
    "public_repo"
  ],
  "note": "optional note",
  "note_url": "http://optional/note/url"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a new authorization](#create-a-new-authorization).





## Get a single authorization

```
GET /authorizations/{authorization_id}
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`authorization_id`** (integer) (required)
  The unique identifier of the authorization.






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
  http(s)://HOSTNAME/api/v3/authorizations/AUTHORIZATION_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a new authorization](#create-a-new-authorization).





## Update an existing authorization

```
PATCH /authorizations/{authorization_id}
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.

If you have two-factor authentication setup, Basic Authentication for this endpoint requires that you use a one-time password (OTP) and your username and password instead of tokens. For more information, see "Working with two-factor authentication."
You can only send one of these scope keys at a time.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`authorization_id`** (integer) (required)
  The unique identifier of the authorization.




#### Body parameters

- **`scopes`** (array of strings or null)
  A list of scopes that this authorization is in.

- **`add_scopes`** (array of strings)
  A list of scopes to add to this authorization.

- **`remove_scopes`** (array of strings)
  A list of scopes to remove from this authorization.

- **`note`** (string)
  A note to remind you what the OAuth token is for.

- **`note_url`** (string)
  A URL to remind you what app the OAuth token is for.

- **`fingerprint`** (string)
  A unique string to distinguish an authorization from others created for the same client ID and user.





### HTTP response status codes


- **200** - OK


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example of updating scopes and note

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/authorizations/AUTHORIZATION_ID \
  -d '{
  "add_scopes": [
    "public_repo"
  ],
  "remove_scopes": [
    "user"
  ],
  "note": "optional note"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a new authorization](#create-a-new-authorization).





## Delete an authorization

```
DELETE /authorizations/{authorization_id}
```

Warning

Closing down notice: GitHub Enterprise Server will discontinue the OAuth Authorizations API, which is used by integrations to create personal access tokens and OAuth tokens, and you must now create these tokens using our web application flow. The OAuth Authorizations API will be removed on November 13, 2020. For more information, including scheduled brownouts, see the blog post.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`authorization_id`** (integer) (required)
  The unique identifier of the authorization.






### HTTP response status codes


- **204** - No Content


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/authorizations/AUTHORIZATION_ID
```

**Response schema (Status: 204):**