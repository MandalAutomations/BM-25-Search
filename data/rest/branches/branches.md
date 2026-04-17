# REST API endpoints for branches

Use the REST API to modify branches and their protection settings.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List branches

```
GET /repos/{owner}/{repo}/branches
```



### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`protected`** (boolean)
  Setting to true returns only branches protected by branch protections or rulesets. When set to false, only unprotected branches are returned. Omitting this parameter returns all branches.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/branches
```

**Response schema (Status: 200):**

Array of `Short Branch`:
  * `name`: required, string
  * `commit`: required, object:
    * `sha`: required, string
    * `url`: required, string, format: uri
  * `protected`: required, boolean
  * `protection`: `Branch Protection`:
    * `url`: string
    * `enabled`: boolean
    * `required_status_checks`: `Protected Branch Required Status Check`:
      * `url`: string
      * `enforcement_level`: string
      * `contexts`: required, array of string
      * `checks`: required, array of objects:
        * `context`: required, string
        * `app_id`: required, integer or null
      * `contexts_url`: string
      * `strict`: boolean
    * `enforce_admins`: `Protected Branch Admin Enforced`:
      * `url`: required, string, format: uri
      * `enabled`: required, boolean
    * `required_pull_request_reviews`: `Protected Branch Pull Request Review`:
      * `url`: string, format: uri
      * `dismissal_restrictions`: object:
        * `users`: array of object
        * `teams`: array of object
        * `apps`: array of object or null
        * `url`: string
        * `users_url`: string
        * `teams_url`: string
      * `bypass_pull_request_allowances`: object:
        * `users`: array of object
        * `teams`: array of object
        * `apps`: array of object or null
      * `dismiss_stale_reviews`: required, boolean
      * `require_code_owner_reviews`: required, boolean
      * `required_approving_review_count`: integer, minimum: 0, maximum: 6
      * `require_last_push_approval`: boolean, default: `false`
    * `restrictions`: `Branch Restriction Policy`:
      * `url`: required, string, format: uri
      * `users_url`: required, string, format: uri
      * `teams_url`: required, string, format: uri
      * `apps_url`: required, string, format: uri
      * `users`: required, array of objects:
        * `login`: string
        * `id`: integer, format: int64
        * `node_id`: string
        * `avatar_url`: string
        * `gravatar_id`: string
        * `url`: string
        * `html_url`: string
        * `followers_url`: string
        * `following_url`: string
        * `gists_url`: string
        * `starred_url`: string
        * `subscriptions_url`: string
        * `organizations_url`: string
        * `repos_url`: string
        * `events_url`: string
        * `received_events_url`: string
        * `type`: string
        * `site_admin`: boolean
        * `user_view_type`: string
      * `teams`: required, array of `Team`:
        * `id`: required, integer
        * `node_id`: required, string
        * `name`: required, string
        * `slug`: required, string
        * `description`: required, string or null
        * `privacy`: string
        * `notification_setting`: string
        * `permission`: required, string
        * `permissions`: object
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
      * `apps`: required, array of objects:
        * `id`: integer
        * `slug`: string
        * `node_id`: string
        * `owner`: object
        * `name`: string
        * `client_id`: string
        * `description`: string
        * `external_url`: string
        * `html_url`: string
        * `created_at`: string
        * `updated_at`: string
        * `permissions`: object
        * `events`: array of string
    * `required_linear_history`: object:
      * `enabled`: boolean
    * `allow_force_pushes`: object:
      * `enabled`: boolean
    * `allow_deletions`: object:
      * `enabled`: boolean
    * `block_creations`: object:
      * `enabled`: boolean
    * `required_conversation_resolution`: object:
      * `enabled`: boolean
    * `name`: string
    * `protection_url`: string
    * `required_signatures`: object:
      * `url`: required, string, format: uri
      * `enabled`: required, boolean
    * `lock_branch`: object:
      * `enabled`: boolean, default: `false`
    * `allow_fork_syncing`: object:
      * `enabled`: boolean, default: `false`
  * `protection_url`: string, format: uri





## Get a branch

```
GET /repos/{owner}/{repo}/branches/{branch}
```



### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`branch`** (string) (required)
  The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use the GraphQL API.






### HTTP response status codes


- **200** - OK


- **301** - Moved permanently


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/branches/BRANCH
```

**Response schema (Status: 200):**

* `name`: required, string
* `commit`: required, `Commit`:
  * `url`: required, string, format: uri
  * `sha`: required, string
  * `node_id`: required, string
  * `html_url`: required, string, format: uri
  * `comments_url`: required, string, format: uri
  * `commit`: required, object:
    * `url`: required, string, format: uri
    * `author`: required, any of:
      * **null**
      * **Git User**
        * `name`: string
        * `email`: string
        * `date`: string, format: date-time
    * `committer`: required, any of:
      * **null**
      * **Git User**
        * `name`: string
        * `email`: string
        * `date`: string, format: date-time
    * `message`: required, string
    * `comment_count`: required, integer
    * `tree`: required, object:
      * `sha`: required, string
      * `url`: required, string, format: uri
    * `verification`: `Verification`:
      * `verified`: required, boolean
      * `reason`: required, string
      * `payload`: required, string or null
      * `signature`: required, string or null
      * `verified_at`: required, string or null
  * `author`: required, one of:
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
    * **Empty Object**
  * `committer`: required, one of:
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
    * **Empty Object**
  * `parents`: required, array of objects:
    * `sha`: required, string
    * `url`: required, string, format: uri
    * `html_url`: string, format: uri
  * `stats`: object:
    * `additions`: integer
    * `deletions`: integer
    * `total`: integer
  * `files`: array of `Diff Entry`:
    * `sha`: required, string or null
    * `filename`: required, string
    * `status`: required, string, enum: `added`, `removed`, `modified`, `renamed`, `copied`, `changed`, `unchanged`
    * `additions`: required, integer
    * `deletions`: required, integer
    * `changes`: required, integer
    * `blob_url`: required, string, format: uri
    * `raw_url`: required, string, format: uri
    * `contents_url`: required, string, format: uri
    * `patch`: string
    * `previous_filename`: string
* `_links`: required, object:
  * `html`: required, string
  * `self`: required, string, format: uri
* `protected`: required, boolean
* `protection`: required, `Branch Protection`:
  * `url`: string
  * `enabled`: boolean
  * `required_status_checks`: `Protected Branch Required Status Check`:
    * `url`: string
    * `enforcement_level`: string
    * `contexts`: required, array of string
    * `checks`: required, array of objects:
      * `context`: required, string
      * `app_id`: required, integer or null
    * `contexts_url`: string
    * `strict`: boolean
  * `enforce_admins`: `Protected Branch Admin Enforced`:
    * `url`: required, string, format: uri
    * `enabled`: required, boolean
  * `required_pull_request_reviews`: `Protected Branch Pull Request Review`:
    * `url`: string, format: uri
    * `dismissal_restrictions`: object:
      * `users`: array of `Simple User`:
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
      * `teams`: array of `Team`:
        * `id`: required, integer
        * `node_id`: required, string
        * `name`: required, string
        * `slug`: required, string
        * `description`: required, string or null
        * `privacy`: string
        * `notification_setting`: string
        * `permission`: required, string
        * `permissions`: object
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
      * `apps`: array of `GitHub app`:
        * `id`: required, integer
        * `slug`: string
        * `node_id`: required, string
        * `client_id`: string
        * `owner`: required, one of:
          * **Simple User**
          * **Enterprise**
        * `name`: required, string
        * `description`: required, string or null
        * `external_url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `permissions`: required, object, additional properties: string
        * `events`: required, array of string
        * `installations_count`: integer
      * `url`: string
      * `users_url`: string
      * `teams_url`: string
    * `bypass_pull_request_allowances`: object:
      * `users`: array of `Simple User`:
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
      * `teams`: array of `Team`:
        * `id`: required, integer
        * `node_id`: required, string
        * `name`: required, string
        * `slug`: required, string
        * `description`: required, string or null
        * `privacy`: string
        * `notification_setting`: string
        * `permission`: required, string
        * `permissions`: object
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
      * `apps`: array of `GitHub app`:
        * `id`: required, integer
        * `slug`: string
        * `node_id`: required, string
        * `client_id`: string
        * `owner`: required, one of:
          * **Simple User**
          * **Enterprise**
        * `name`: required, string
        * `description`: required, string or null
        * `external_url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `permissions`: required, object, additional properties: string
        * `events`: required, array of string
        * `installations_count`: integer
    * `dismiss_stale_reviews`: required, boolean
    * `require_code_owner_reviews`: required, boolean
    * `required_approving_review_count`: integer, minimum: 0, maximum: 6
    * `require_last_push_approval`: boolean, default: `false`
  * `restrictions`: `Branch Restriction Policy`:
    * `url`: required, string, format: uri
    * `users_url`: required, string, format: uri
    * `teams_url`: required, string, format: uri
    * `apps_url`: required, string, format: uri
    * `users`: required, array of objects:
      * `login`: string
      * `id`: integer, format: int64
      * `node_id`: string
      * `avatar_url`: string
      * `gravatar_id`: string
      * `url`: string
      * `html_url`: string
      * `followers_url`: string
      * `following_url`: string
      * `gists_url`: string
      * `starred_url`: string
      * `subscriptions_url`: string
      * `organizations_url`: string
      * `repos_url`: string
      * `events_url`: string
      * `received_events_url`: string
      * `type`: string
      * `site_admin`: boolean
      * `user_view_type`: string
    * `teams`: required, array of `Team`:
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
    * `apps`: required, array of objects:
      * `id`: integer
      * `slug`: string
      * `node_id`: string
      * `owner`: object:
        * `login`: string
        * `id`: integer
        * `node_id`: string
        * `url`: string
        * `repos_url`: string
        * `events_url`: string
        * `hooks_url`: string
        * `issues_url`: string
        * `members_url`: string
        * `public_members_url`: string
        * `avatar_url`: string
        * `description`: string
        * `gravatar_id`: string
        * `html_url`: string
        * `followers_url`: string
        * `following_url`: string
        * `gists_url`: string
        * `starred_url`: string
        * `subscriptions_url`: string
        * `organizations_url`: string
        * `received_events_url`: string
        * `type`: string
        * `site_admin`: boolean
        * `user_view_type`: string
      * `name`: string
      * `client_id`: string
      * `description`: string
      * `external_url`: string
      * `html_url`: string
      * `created_at`: string
      * `updated_at`: string
      * `permissions`: object:
        * `metadata`: string
        * `contents`: string
        * `issues`: string
        * `single_file`: string
      * `events`: array of string
  * `required_linear_history`: object:
    * `enabled`: boolean
  * `allow_force_pushes`: object:
    * `enabled`: boolean
  * `allow_deletions`: object:
    * `enabled`: boolean
  * `block_creations`: object:
    * `enabled`: boolean
  * `required_conversation_resolution`: object:
    * `enabled`: boolean
  * `name`: string
  * `protection_url`: string
  * `required_signatures`: object:
    * `url`: required, string, format: uri
    * `enabled`: required, boolean
  * `lock_branch`: object:
    * `enabled`: boolean, default: `false`
  * `allow_fork_syncing`: object:
    * `enabled`: boolean, default: `false`
* `protection_url`: required, string, format: uri
* `pattern`: string
* `required_approving_review_count`: integer





## Rename a branch

```
POST /repos/{owner}/{repo}/branches/{branch}/rename
```

Renames a branch in a repository.
Note

Although the API responds immediately, the branch rename process might take some extra time to complete in the background. You won't be able to push to the old branch name while the rename process is in progress. For more information, see "Renaming a branch".

The authenticated user must have push access to the branch. If the branch is the default branch, the authenticated user must also have admin or owner permissions.
In order to rename the default branch, fine-grained access tokens also need the administration:write repository permission.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`branch`** (string) (required)
  The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use the GraphQL API.




#### Body parameters

- **`new_name`** (string) (required)
  The new name of the branch.





### HTTP response status codes


- **201** - Created


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/branches/BRANCH/rename \
  -d '{
  "new_name": "my_renamed_branch"
}'
```

**Response schema (Status: 201):**

Same response schema as [Get a branch](#get-a-branch).





## Sync a fork branch with the upstream repository

```
POST /repos/{owner}/{repo}/merge-upstream
```

Sync a branch of a forked repository to keep it up-to-date with the upstream repository.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.




#### Body parameters

- **`branch`** (string) (required)
  The name of the branch which should be updated to match upstream.





### HTTP response status codes


- **200** - The branch has been successfully synced with the upstream repository


- **409** - The branch could not be synced because of a merge conflict


- **422** - The branch could not be synced for some other reason




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/merge-upstream \
  -d '{
  "branch": "main"
}'
```

**Response schema (Status: 200):**

* `message`: string
* `merge_type`: string, enum: `merge`, `fast-forward`, `none`
* `base_branch`: string





## Merge a branch

```
POST /repos/{owner}/{repo}/merges
```



### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.




#### Body parameters

- **`base`** (string) (required)
  The name of the base branch that the head will be merged into.

- **`head`** (string) (required)
  The head to merge. This can be a branch name or a commit SHA1.

- **`commit_message`** (string)
  Commit message to use for the merge commit. If omitted, a default message will be used.





### HTTP response status codes


- **201** - Successful Response (The resulting merge commit)


- **204** - Response when already merged


- **403** - Forbidden


- **404** - Not Found when the base or head does not exist


- **409** - Conflict when there is a merge conflict


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/merges \
  -d '{
  "base": "master",
  "head": "cool_feature",
  "commit_message": "Shipped cool_feature!"
}'
```

**Response schema (Status: 201):**

* `url`: required, string, format: uri
* `sha`: required, string
* `node_id`: required, string
* `html_url`: required, string, format: uri
* `comments_url`: required, string, format: uri
* `commit`: required, object:
  * `url`: required, string, format: uri
  * `author`: required, any of:
    * **null**
    * **Git User**
      * `name`: string
      * `email`: string
      * `date`: string, format: date-time
  * `committer`: required, any of:
    * **null**
    * **Git User**
      * `name`: string
      * `email`: string
      * `date`: string, format: date-time
  * `message`: required, string
  * `comment_count`: required, integer
  * `tree`: required, object:
    * `sha`: required, string
    * `url`: required, string, format: uri
  * `verification`: `Verification`:
    * `verified`: required, boolean
    * `reason`: required, string
    * `payload`: required, string or null
    * `signature`: required, string or null
    * `verified_at`: required, string or null
* `author`: required, one of:
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
  * **Empty Object**
* `committer`: required, one of:
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
  * **Empty Object**
* `parents`: required, array of objects:
  * `sha`: required, string
  * `url`: required, string, format: uri
  * `html_url`: string, format: uri
* `stats`: object:
  * `additions`: integer
  * `deletions`: integer
  * `total`: integer
* `files`: array of `Diff Entry`:
  * `sha`: required, string or null
  * `filename`: required, string
  * `status`: required, string, enum: `added`, `removed`, `modified`, `renamed`, `copied`, `changed`, `unchanged`
  * `additions`: required, integer
  * `deletions`: required, integer
  * `changes`: required, integer
  * `blob_url`: required, string, format: uri
  * `raw_url`: required, string, format: uri
  * `contents_url`: required, string, format: uri
  * `patch`: string
  * `previous_filename`: string