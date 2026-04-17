# REST API endpoints for personal access tokens

Use the REST API to manage fine-grained personal access tokens.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List requests to access organization resources with fine-grained personal access tokens

```
GET /orgs/{org}/personal-access-token-requests
```

Lists requests from organization members to access organization resources with a fine-grained personal access token.
Only GitHub Apps can use this endpoint.


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

- **`sort`** (string)
  The property by which to sort the results.
  Default: `created_at`
  Can be one of: `created_at`

- **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`owner`** (array)
  A list of owner usernames to use to filter the results.

- **`repository`** (string)
  The name of the repository to use to filter the results.

- **`permission`** (string)
  The permission to use to filter the results.

- **`last_used_before`** (string)
  Only show fine-grained personal access tokens used before the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`last_used_after`** (string)
  Only show fine-grained personal access tokens used after the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`token_id`** (array)
  The ID of the token






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/personal-access-token-requests
```

**Response schema (Status: 200):**

Array of `Simple Organization Programmatic Access Grant Request`:
  * `id`: required, integer
  * `reason`: required, string or null
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
  * `repository_selection`: required, string, enum: `none`, `all`, `subset`
  * `repositories_url`: required, string
  * `permissions`: required, object:
    * `organization`: object, additional properties: string
    * `repository`: object, additional properties: string
    * `other`: object, additional properties: string
  * `created_at`: required, string
  * `token_id`: required, integer
  * `token_name`: required, string
  * `token_expired`: required, boolean
  * `token_expires_at`: required, string or null
  * `token_last_used_at`: required, string or null





## Review requests to access organization resources with fine-grained personal access tokens

```
POST /orgs/{org}/personal-access-token-requests
```

Approves or denies multiple pending requests to access organization resources via a fine-grained personal access token.
Only GitHub Apps can use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`pat_request_ids`** (array of integers)
  Unique identifiers of the requests for access via fine-grained personal access token. Must be formed of between 1 and 100 pat_request_id values.

- **`action`** (string) (required)
  Action to apply to the requests.
  Can be one of: `approve`, `deny`

- **`reason`** (string or null)
  Reason for approving or denying the requests. Max 1024 characters.





### HTTP response status codes


- **202** - Accepted


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example of denying a request

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/personal-access-token-requests \
  -d '{
  "pat_request_ids": [
    42,
    73
  ],
  "action": "deny",
  "reason": "Access is too broad."
}'
```

**Response schema (Status: 202):**

object





## Review a request to access organization resources with a fine-grained personal access token

```
POST /orgs/{org}/personal-access-token-requests/{pat_request_id}
```

Approves or denies a pending request to access organization resources via a fine-grained personal access token.
Only GitHub Apps can use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`pat_request_id`** (integer) (required)
  Unique identifier of the request for access via fine-grained personal access token.




#### Body parameters

- **`action`** (string) (required)
  Action to apply to the request.
  Can be one of: `approve`, `deny`

- **`reason`** (string or null)
  Reason for approving or denying the request. Max 1024 characters.





### HTTP response status codes


- **204** - A header with no content is returned.


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example of denying a request

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/personal-access-token-requests/PAT_REQUEST_ID \
  -d '{
  "action": "deny",
  "reason": "This request is denied because the access is too broad."
}'
```

**Response schema (Status: 204):**





## List repositories requested to be accessed by a fine-grained personal access token

```
GET /orgs/{org}/personal-access-token-requests/{pat_request_id}/repositories
```

Lists the repositories a fine-grained personal access token request is requesting access to.
Only GitHub Apps can use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`pat_request_id`** (integer) (required)
  Unique identifier of the request for access via fine-grained personal access token.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/personal-access-token-requests/PAT_REQUEST_ID/repositories
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





## List fine-grained personal access tokens with access to organization resources

```
GET /orgs/{org}/personal-access-tokens
```

Lists approved fine-grained personal access tokens owned by organization members that can access organization resources.
Only GitHub Apps can use this endpoint.


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

- **`sort`** (string)
  The property by which to sort the results.
  Default: `created_at`
  Can be one of: `created_at`

- **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`owner`** (array)
  A list of owner usernames to use to filter the results.

- **`repository`** (string)
  The name of the repository to use to filter the results.

- **`permission`** (string)
  The permission to use to filter the results.

- **`last_used_before`** (string)
  Only show fine-grained personal access tokens used before the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`last_used_after`** (string)
  Only show fine-grained personal access tokens used after the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`token_id`** (array)
  The ID of the token






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/personal-access-tokens
```

**Response schema (Status: 200):**

Array of `Organization Programmatic Access Grant`:
  * `id`: required, integer
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
  * `repository_selection`: required, string, enum: `none`, `all`, `subset`
  * `repositories_url`: required, string
  * `permissions`: required, object:
    * `organization`: object, additional properties: string
    * `repository`: object, additional properties: string
    * `other`: object, additional properties: string
  * `access_granted_at`: required, string
  * `token_id`: required, integer
  * `token_name`: required, string
  * `token_expired`: required, boolean
  * `token_expires_at`: required, string or null
  * `token_last_used_at`: required, string or null





## Update the access to organization resources via fine-grained personal access tokens

```
POST /orgs/{org}/personal-access-tokens
```

Updates the access organization members have to organization resources via fine-grained personal access tokens. Limited to revoking a token's existing access.
Only GitHub Apps can use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`action`** (string) (required)
  Action to apply to the fine-grained personal access token.
  Can be one of: `revoke`

- **`pat_ids`** (array of integers) (required)
  The IDs of the fine-grained personal access tokens.





### HTTP response status codes


- **202** - Accepted


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example of revoking a fine-grained personal access token.

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/personal-access-tokens \
  -d '{
  "action": "revoke",
  "pat_ids": [
    1296269,
    1296280
  ]
}'
```

**Response schema (Status: 202):**

Same response schema as [Review requests to access organization resources with fine-grained personal access tokens](#review-requests-to-access-organization-resources-with-fine-grained-personal-access-tokens).





## Update the access a fine-grained personal access token has to organization resources

```
POST /orgs/{org}/personal-access-tokens/{pat_id}
```

Updates the access an organization member has to organization resources via a fine-grained personal access token. Limited to revoking the token's existing access. Limited to revoking a token's existing access.
Only GitHub Apps can use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`pat_id`** (integer) (required)
  The unique identifier of the fine-grained personal access token.




#### Body parameters

- **`action`** (string) (required)
  Action to apply to the fine-grained personal access token.
  Can be one of: `revoke`





### HTTP response status codes


- **204** - A header with no content is returned.


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example of revoking a fine-grained personal access token.

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/personal-access-tokens/PAT_ID \
  -d '{
  "action": "revoke"
}'
```

**Response schema (Status: 204):**





## List repositories a fine-grained personal access token has access to

```
GET /orgs/{org}/personal-access-tokens/{pat_id}/repositories
```

Lists the repositories a fine-grained personal access token has access to.
Only GitHub Apps can use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`pat_id`** (integer) (required)
  Unique identifier of the fine-grained personal access token.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/personal-access-tokens/PAT_ID/repositories
```

**Response schema (Status: 200):**

Same response schema as [List repositories requested to be accessed by a fine-grained personal access token](#list-repositories-requested-to-be-accessed-by-a-fine-grained-personal-access-token).