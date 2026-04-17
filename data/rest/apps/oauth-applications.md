# REST API endpoints for OAuth authorizations

Use the REST API to interact with OAuth apps and OAuth authorizations of GitHub Apps

## About OAuth apps and OAuth authorizations of GitHub Apps

You can use these endpoints to manage the OAuth tokens that OAuth apps or GitHub Apps use to access people's accounts on GitHub.

Tokens for OAuth apps have the prefix `gho_`, while OAuth tokens for GitHub Apps, used for authenticating on behalf of the user, have the prefix `ghu_`. You can use the following endpoints for both types of OAuth tokens.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Delete an app authorization

```
DELETE /applications/{client_id}/grant
```

OAuth and GitHub application owners can revoke a grant for their application and a specific user. You must provide a valid OAuth access_token as an input parameter and the grant for the token's owner will be deleted.
Deleting an application's grant will also delete all OAuth tokens associated with the application for the user. Once deleted, the application will have no access to the user's account and will no longer be listed on the application authorizations settings screen within GitHub.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`client_id`** (string) (required)
  The client ID of the GitHub app.




#### Body parameters

- **`access_token`** (string) (required)
  The OAuth access token used to authenticate to the GitHub API.





### HTTP response status codes


- **204** - No Content


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/applications/Iv1.8a61f9b3a7aba766/grant \
  -d '{
  "access_token": "e72e16c7e42f292c6912e7710c838347ae178b4a"
}'
```

**Response schema (Status: 204):**





## Check a token

```
POST /applications/{client_id}/token
```

OAuth applications and GitHub applications with OAuth authorizations can use this API method for checking OAuth token validity without exceeding the normal rate limits for failed login attempts. Authentication works differently with this particular endpoint. Invalid tokens will return 404 NOT FOUND.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`client_id`** (string) (required)
  The client ID of the GitHub app.




#### Body parameters

- **`access_token`** (string) (required)
  The access_token of the OAuth or GitHub application.





### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/applications/Iv1.8a61f9b3a7aba766/token \
  -d '{
  "access_token": "e72e16c7e42f292c6912e7710c838347ae178b4a"
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
      * `enterprise_custom_properties_for_organizations`: string, enum: `read`, `write`, `admin`
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





## Reset a token

```
PATCH /applications/{client_id}/token
```

OAuth applications and GitHub applications with OAuth authorizations can use this API method to reset a valid OAuth token without end-user involvement. Applications must save the "token" property in the response because changes take effect immediately. Invalid tokens will return 404 NOT FOUND.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`client_id`** (string) (required)
  The client ID of the GitHub app.




#### Body parameters

- **`access_token`** (string) (required)
  The access_token of the OAuth or GitHub application.





### HTTP response status codes


- **200** - OK


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/applications/Iv1.8a61f9b3a7aba766/token \
  -d '{
  "access_token": "e72e16c7e42f292c6912e7710c838347ae178b4a"
}'
```

**Response schema (Status: 200):**

Same response schema as [Check a token](#check-a-token).





## Delete an app token

```
DELETE /applications/{client_id}/token
```

OAuth  or GitHub application owners can revoke a single token for an OAuth application or a GitHub application with an OAuth authorization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`client_id`** (string) (required)
  The client ID of the GitHub app.




#### Body parameters

- **`access_token`** (string) (required)
  The OAuth access token used to authenticate to the GitHub API.





### HTTP response status codes


- **204** - No Content


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/applications/Iv1.8a61f9b3a7aba766/token \
  -d '{
  "access_token": "e72e16c7e42f292c6912e7710c838347ae178b4a"
}'
```

**Response schema (Status: 204):**