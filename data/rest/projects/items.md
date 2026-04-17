# REST API endpoints for Project items

Use the REST API to manage Project items


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List items for an organization owned project

```
GET /orgs/{org}/projectsV2/{project_number}/items
```

List all items for a specific organization-owned project accessible by the authenticated user.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`q`** (string)
  Search query to filter items, see Filtering projects for more information.

- **`fields`** (string)
  Limit results to specific fields, by their IDs. If not specified, the title field will be returned.
Example: fields[]=123&fields[]=456&fields[]=789 or fields=123,456,789

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






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
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items
```

**Response schema (Status: 200):**

Array of `Projects v2 Item`:
  * `id`: required, number
  * `node_id`: string
  * `project_url`: string, format: uri
  * `content_type`: required, string, enum: `Issue`, `PullRequest`, `DraftIssue`
  * `content`: object or null, additional properties allowed
  * `creator`: `Simple User`:
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
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `archived_at`: required, string or null, format: date-time
  * `item_url`: string or null, format: uri
  * `fields`: array of object, additional properties allowed





## Add item to organization owned project

```
POST /orgs/{org}/projectsV2/{project_number}/items
```

Add an issue or pull request item to the specified organization owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`project_number`** (integer) (required)
  The project's number.






### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Add an issue using its unique ID

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items \
  -d '{
  "type": "Issue",
  "id": 3
}'
```

**Response schema (Status: 201):**

* `id`: required, number
* `node_id`: string
* `content`: one of:
  * **Issue**
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `repository_url`: required, string, format: uri
    * `labels_url`: required, string
    * `comments_url`: required, string, format: uri
    * `events_url`: required, string, format: uri
    * `html_url`: required, string, format: uri
    * `number`: required, integer
    * `state`: required, string
    * `state_reason`: string or null, enum: `completed`, `reopened`, `not_planned`, `duplicate`, `null`
    * `title`: required, string
    * `body`: string or null
    * `user`: required, any of:
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
    * `labels`: required, array of object
    * `assignees`: array of `Simple User`:
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
    * `milestone`: required, any of:
      * **null**
      * **Milestone**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `labels_url`: required, string, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `number`: required, integer
        * `state`: required, string, enum: `open`, `closed`, default: `"open"`
        * `title`: required, string
        * `description`: required, string or null
        * `creator`: required, any of:
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
        * `open_issues`: required, integer
        * `closed_issues`: required, integer
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `closed_at`: required, string or null, format: date-time
        * `due_on`: required, string or null, format: date-time
    * `locked`: required, boolean
    * `active_lock_reason`: string or null
    * `comments`: required, integer
    * `pull_request`: object:
      * `merged_at`: string or null, format: date-time
      * `diff_url`: required, string or null, format: uri
      * `html_url`: required, string or null, format: uri
      * `patch_url`: required, string or null, format: uri
      * `url`: required, string or null, format: uri
    * `closed_at`: required, string or null, format: date-time
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `draft`: boolean
    * `closed_by`: any of:
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
    * `body_html`: string
    * `body_text`: string
    * `timeline_url`: string, format: uri
    * `type`: `Issue Type`:
      * `id`: required, integer
      * `node_id`: required, string
      * `name`: required, string
      * `description`: required, string or null
      * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
      * `created_at`: string, format: date-time
      * `updated_at`: string, format: date-time
      * `is_enabled`: boolean
    * `repository`: `Repository`:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `name`: required, string
      * `full_name`: required, string
      * `license`: required, any of:
        * **null**
        * **License Simple**
          * `key`: required, string
          * `name`: required, string
          * `url`: required, string or null, format: uri
          * `spdx_id`: required, string or null
          * `node_id`: required, string
          * `html_url`: string, format: uri
      * `forks`: required, integer
      * `permissions`: object:
        * `admin`: required, boolean
        * `pull`: required, boolean
        * `triage`: boolean
        * `push`: required, boolean
        * `maintain`: boolean
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
      * `private`: required, boolean, default: `false`
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
      * `git_url`: required, string
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
      * `ssh_url`: required, string
      * `stargazers_url`: required, string, format: uri
      * `statuses_url`: required, string
      * `subscribers_url`: required, string, format: uri
      * `subscription_url`: required, string, format: uri
      * `tags_url`: required, string, format: uri
      * `teams_url`: required, string, format: uri
      * `trees_url`: required, string
      * `clone_url`: required, string
      * `mirror_url`: required, string or null, format: uri
      * `hooks_url`: required, string, format: uri
      * `svn_url`: required, string, format: uri
      * `homepage`: required, string or null, format: uri
      * `language`: required, string or null
      * `forks_count`: required, integer
      * `stargazers_count`: required, integer
      * `watchers_count`: required, integer
      * `size`: required, integer
      * `default_branch`: required, string
      * `open_issues_count`: required, integer
      * `is_template`: boolean, default: `false`
      * `topics`: array of string
      * `has_issues`: required, boolean, default: `true`
      * `has_projects`: required, boolean, default: `true`
      * `has_wiki`: required, boolean, default: `true`
      * `has_pages`: required, boolean
      * `has_discussions`: boolean, default: `false`
      * `has_pull_requests`: boolean, default: `true`
      * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
      * `archived`: required, boolean, default: `false`
      * `disabled`: required, boolean
      * `visibility`: string, default: `"public"`
      * `pushed_at`: required, string or null, format: date-time
      * `created_at`: required, string or null, format: date-time
      * `updated_at`: required, string or null, format: date-time
      * `allow_rebase_merge`: boolean, default: `true`
      * `temp_clone_token`: string
      * `allow_squash_merge`: boolean, default: `true`
      * `allow_auto_merge`: boolean, default: `false`
      * `delete_branch_on_merge`: boolean, default: `false`
      * `allow_update_branch`: boolean, default: `false`
      * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
      * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
      * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
      * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
      * `allow_merge_commit`: boolean, default: `true`
      * `allow_forking`: boolean
      * `web_commit_signoff_required`: boolean, default: `false`
      * `open_issues`: required, integer
      * `watchers`: required, integer
      * `starred_at`: string
      * `anonymous_access_enabled`: boolean
      * `code_search_index_status`: object:
        * `lexical_search_ok`: boolean
        * `lexical_commit_sha`: string
    * `performed_via_github_app`: any of:
      * **null**
      * **GitHub app**
        * `id`: required, integer
        * `slug`: string
        * `node_id`: required, string
        * `client_id`: string
        * `owner`: required, one of:
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
        * `name`: required, string
        * `description`: required, string or null
        * `external_url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `permissions`: required, object, additional properties: string:
          * `issues`: string
          * `checks`: string
          * `metadata`: string
          * `contents`: string
          * `deployments`: string
        * `events`: required, array of string
        * `installations_count`: integer
    * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
    * `reactions`: `Reaction Rollup`:
      * `url`: required, string, format: uri
      * `total_count`: required, integer
      * `+1`: required, integer
      * `-1`: required, integer
      * `laugh`: required, integer
      * `confused`: required, integer
      * `heart`: required, integer
      * `hooray`: required, integer
      * `eyes`: required, integer
      * `rocket`: required, integer
    * `sub_issues_summary`: `Sub-issues Summary`:
      * `total`: required, integer
      * `completed`: required, integer
      * `percent_completed`: required, integer
    * `parent_issue_url`: string or null, format: uri
    * `pinned_comment`: any of:
      * **null**
      * **Issue Comment**
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `url`: required, string, format: uri
        * `body`: string
        * `body_text`: string
        * `body_html`: string
        * `html_url`: required, string, format: uri
        * `user`: required, any of:
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
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `issue_url`: required, string, format: uri
        * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
        * `performed_via_github_app`: any of:
          * **null**
          * **GitHub app**
            * `id`: required, integer
            * `slug`: string
            * `node_id`: required, string
            * `client_id`: string
            * `owner`: required, one of:
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
            * `name`: required, string
            * `description`: required, string or null
            * `external_url`: required, string, format: uri
            * `html_url`: required, string, format: uri
            * `created_at`: required, string, format: date-time
            * `updated_at`: required, string, format: date-time
            * `permissions`: required, object, additional properties: string:
              * `issues`: string
              * `checks`: string
              * `metadata`: string
              * `contents`: string
              * `deployments`: string
            * `events`: required, array of string
            * `installations_count`: integer
        * `reactions`: `Reaction Rollup`:
          * `url`: required, string, format: uri
          * `total_count`: required, integer
          * `+1`: required, integer
          * `-1`: required, integer
          * `laugh`: required, integer
          * `confused`: required, integer
          * `heart`: required, integer
          * `hooray`: required, integer
          * `eyes`: required, integer
          * `rocket`: required, integer
        * `pin`: any of:
          * **null**
          * **Pinned Issue Comment**
            * `pinned_at`: required, string, format: date-time
            * `pinned_by`: required, any of:
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
    * `issue_dependencies_summary`: `Issue Dependencies Summary`:
      * `blocked_by`: required, integer
      * `blocking`: required, integer
      * `total_blocked_by`: required, integer
      * `total_blocking`: required, integer
    * `issue_field_values`: array of `Issue Field Value`:
      * `issue_field_id`: required, integer, format: int64
      * `node_id`: required, string
      * `data_type`: required, string, enum: `text`, `single_select`, `number`, `date`
      * `value`: required, any of:
        * **string**
        * **number**
        * **integer**
      * `single_select_option`: object or null:
        * `id`: required, integer, format: int64
        * `name`: required, string
        * `color`: required, string
  * **Pull Request Simple**
    * `url`: required, string, format: uri
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `html_url`: required, string, format: uri
    * `diff_url`: required, string, format: uri
    * `patch_url`: required, string, format: uri
    * `issue_url`: required, string, format: uri
    * `commits_url`: required, string, format: uri
    * `review_comments_url`: required, string, format: uri
    * `review_comment_url`: required, string
    * `comments_url`: required, string, format: uri
    * `statuses_url`: required, string, format: uri
    * `number`: required, integer
    * `state`: required, string
    * `locked`: required, boolean
    * `title`: required, string
    * `user`: required, any of:
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
    * `body`: required, string or null
    * `labels`: required, array of objects:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `url`: required, string
      * `name`: required, string
      * `description`: required, string
      * `color`: required, string
      * `default`: required, boolean
    * `milestone`: required, any of:
      * **null**
      * **Milestone**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `labels_url`: required, string, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `number`: required, integer
        * `state`: required, string, enum: `open`, `closed`, default: `"open"`
        * `title`: required, string
        * `description`: required, string or null
        * `creator`: required, any of:
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
        * `open_issues`: required, integer
        * `closed_issues`: required, integer
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `closed_at`: required, string or null, format: date-time
        * `due_on`: required, string or null, format: date-time
    * `active_lock_reason`: string or null
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `closed_at`: required, string or null, format: date-time
    * `merged_at`: required, string or null, format: date-time
    * `assignees`: array of `Simple User`:
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
    * `requested_reviewers`: array of `Simple User`:
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
    * `requested_teams`: array of `Team`:
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
    * `head`: required, object:
      * `label`: required, string
      * `ref`: required, string
      * `repo`: required, `Repository`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `name`: required, string
        * `full_name`: required, string
        * `license`: required, any of:
          * **null**
          * **License Simple**
            * `key`: required, string
            * `name`: required, string
            * `url`: required, string or null, format: uri
            * `spdx_id`: required, string or null
            * `node_id`: required, string
            * `html_url`: string, format: uri
        * `forks`: required, integer
        * `permissions`: object:
          * `admin`: required, boolean
          * `pull`: required, boolean
          * `triage`: boolean
          * `push`: required, boolean
          * `maintain`: boolean
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
        * `private`: required, boolean, default: `false`
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
        * `git_url`: required, string
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
        * `ssh_url`: required, string
        * `stargazers_url`: required, string, format: uri
        * `statuses_url`: required, string
        * `subscribers_url`: required, string, format: uri
        * `subscription_url`: required, string, format: uri
        * `tags_url`: required, string, format: uri
        * `teams_url`: required, string, format: uri
        * `trees_url`: required, string
        * `clone_url`: required, string
        * `mirror_url`: required, string or null, format: uri
        * `hooks_url`: required, string, format: uri
        * `svn_url`: required, string, format: uri
        * `homepage`: required, string or null, format: uri
        * `language`: required, string or null
        * `forks_count`: required, integer
        * `stargazers_count`: required, integer
        * `watchers_count`: required, integer
        * `size`: required, integer
        * `default_branch`: required, string
        * `open_issues_count`: required, integer
        * `is_template`: boolean, default: `false`
        * `topics`: array of string
        * `has_issues`: required, boolean, default: `true`
        * `has_projects`: required, boolean, default: `true`
        * `has_wiki`: required, boolean, default: `true`
        * `has_pages`: required, boolean
        * `has_discussions`: boolean, default: `false`
        * `has_pull_requests`: boolean, default: `true`
        * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
        * `archived`: required, boolean, default: `false`
        * `disabled`: required, boolean
        * `visibility`: string, default: `"public"`
        * `pushed_at`: required, string or null, format: date-time
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `allow_rebase_merge`: boolean, default: `true`
        * `temp_clone_token`: string
        * `allow_squash_merge`: boolean, default: `true`
        * `allow_auto_merge`: boolean, default: `false`
        * `delete_branch_on_merge`: boolean, default: `false`
        * `allow_update_branch`: boolean, default: `false`
        * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
        * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
        * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
        * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
        * `allow_merge_commit`: boolean, default: `true`
        * `allow_forking`: boolean
        * `web_commit_signoff_required`: boolean, default: `false`
        * `open_issues`: required, integer
        * `watchers`: required, integer
        * `starred_at`: string
        * `anonymous_access_enabled`: boolean
        * `code_search_index_status`: object:
          * `lexical_search_ok`: boolean
          * `lexical_commit_sha`: string
      * `sha`: required, string
      * `user`: required, any of:
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
    * `base`: required, object:
      * `label`: required, string
      * `ref`: required, string
      * `repo`: required, `Repository`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `name`: required, string
        * `full_name`: required, string
        * `license`: required, any of:
          * **null**
          * **License Simple**
            * `key`: required, string
            * `name`: required, string
            * `url`: required, string or null, format: uri
            * `spdx_id`: required, string or null
            * `node_id`: required, string
            * `html_url`: string, format: uri
        * `forks`: required, integer
        * `permissions`: object:
          * `admin`: required, boolean
          * `pull`: required, boolean
          * `triage`: boolean
          * `push`: required, boolean
          * `maintain`: boolean
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
        * `private`: required, boolean, default: `false`
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
        * `git_url`: required, string
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
        * `ssh_url`: required, string
        * `stargazers_url`: required, string, format: uri
        * `statuses_url`: required, string
        * `subscribers_url`: required, string, format: uri
        * `subscription_url`: required, string, format: uri
        * `tags_url`: required, string, format: uri
        * `teams_url`: required, string, format: uri
        * `trees_url`: required, string
        * `clone_url`: required, string
        * `mirror_url`: required, string or null, format: uri
        * `hooks_url`: required, string, format: uri
        * `svn_url`: required, string, format: uri
        * `homepage`: required, string or null, format: uri
        * `language`: required, string or null
        * `forks_count`: required, integer
        * `stargazers_count`: required, integer
        * `watchers_count`: required, integer
        * `size`: required, integer
        * `default_branch`: required, string
        * `open_issues_count`: required, integer
        * `is_template`: boolean, default: `false`
        * `topics`: array of string
        * `has_issues`: required, boolean, default: `true`
        * `has_projects`: required, boolean, default: `true`
        * `has_wiki`: required, boolean, default: `true`
        * `has_pages`: required, boolean
        * `has_discussions`: boolean, default: `false`
        * `has_pull_requests`: boolean, default: `true`
        * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
        * `archived`: required, boolean, default: `false`
        * `disabled`: required, boolean
        * `visibility`: string, default: `"public"`
        * `pushed_at`: required, string or null, format: date-time
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `allow_rebase_merge`: boolean, default: `true`
        * `temp_clone_token`: string
        * `allow_squash_merge`: boolean, default: `true`
        * `allow_auto_merge`: boolean, default: `false`
        * `delete_branch_on_merge`: boolean, default: `false`
        * `allow_update_branch`: boolean, default: `false`
        * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
        * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
        * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
        * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
        * `allow_merge_commit`: boolean, default: `true`
        * `allow_forking`: boolean
        * `web_commit_signoff_required`: boolean, default: `false`
        * `open_issues`: required, integer
        * `watchers`: required, integer
        * `starred_at`: string
        * `anonymous_access_enabled`: boolean
        * `code_search_index_status`: object:
          * `lexical_search_ok`: boolean
          * `lexical_commit_sha`: string
      * `sha`: required, string
      * `user`: required, any of:
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
    * `_links`: required, object:
      * `comments`: required, `Link`:
        * `href`: required, string
      * `commits`: required, `Link`:
        * `href`: required, string
      * `statuses`: required, `Link`:
        * `href`: required, string
      * `html`: required, `Link`:
        * `href`: required, string
      * `issue`: required, `Link`:
        * `href`: required, string
      * `review_comments`: required, `Link`:
        * `href`: required, string
      * `review_comment`: required, `Link`:
        * `href`: required, string
      * `self`: required, `Link`:
        * `href`: required, string
    * `author_association`: required, string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
    * `auto_merge`: required, `Auto merge`:
      * `enabled_by`: required, `Simple User`:
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
      * `merge_method`: required, string, enum: `merge`, `squash`, `rebase`
      * `commit_title`: required, string
      * `commit_message`: required, string
    * `draft`: boolean
  * **Draft Issue**
    * `id`: required, number
    * `node_id`: required, string
    * `title`: required, string
    * `body`: string or null
    * `user`: required, any of:
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
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
* `content_type`: required, string, enum: `Issue`, `PullRequest`, `DraftIssue`
* `creator`: `Simple User`:
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `archived_at`: required, string or null, format: date-time
* `project_url`: string, format: uri
* `item_url`: string, format: uri



#### Add a pull request using its unique ID

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items \
  -d '{
  "type": "PullRequest",
  "id": 3
}'
```

**Response schema (Status: 201):**

* `id`: required, number
* `node_id`: string
* `content`: one of:
  * **Issue**
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `repository_url`: required, string, format: uri
    * `labels_url`: required, string
    * `comments_url`: required, string, format: uri
    * `events_url`: required, string, format: uri
    * `html_url`: required, string, format: uri
    * `number`: required, integer
    * `state`: required, string
    * `state_reason`: string or null, enum: `completed`, `reopened`, `not_planned`, `duplicate`, `null`
    * `title`: required, string
    * `body`: string or null
    * `user`: required, any of:
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
    * `labels`: required, array of object
    * `assignees`: array of `Simple User`:
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
    * `milestone`: required, any of:
      * **null**
      * **Milestone**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `labels_url`: required, string, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `number`: required, integer
        * `state`: required, string, enum: `open`, `closed`, default: `"open"`
        * `title`: required, string
        * `description`: required, string or null
        * `creator`: required, any of:
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
        * `open_issues`: required, integer
        * `closed_issues`: required, integer
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `closed_at`: required, string or null, format: date-time
        * `due_on`: required, string or null, format: date-time
    * `locked`: required, boolean
    * `active_lock_reason`: string or null
    * `comments`: required, integer
    * `pull_request`: object:
      * `merged_at`: string or null, format: date-time
      * `diff_url`: required, string or null, format: uri
      * `html_url`: required, string or null, format: uri
      * `patch_url`: required, string or null, format: uri
      * `url`: required, string or null, format: uri
    * `closed_at`: required, string or null, format: date-time
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `draft`: boolean
    * `closed_by`: any of:
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
    * `body_html`: string
    * `body_text`: string
    * `timeline_url`: string, format: uri
    * `type`: `Issue Type`:
      * `id`: required, integer
      * `node_id`: required, string
      * `name`: required, string
      * `description`: required, string or null
      * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
      * `created_at`: string, format: date-time
      * `updated_at`: string, format: date-time
      * `is_enabled`: boolean
    * `repository`: `Repository`:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `name`: required, string
      * `full_name`: required, string
      * `license`: required, any of:
        * **null**
        * **License Simple**
          * `key`: required, string
          * `name`: required, string
          * `url`: required, string or null, format: uri
          * `spdx_id`: required, string or null
          * `node_id`: required, string
          * `html_url`: string, format: uri
      * `forks`: required, integer
      * `permissions`: object:
        * `admin`: required, boolean
        * `pull`: required, boolean
        * `triage`: boolean
        * `push`: required, boolean
        * `maintain`: boolean
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
      * `private`: required, boolean, default: `false`
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
      * `git_url`: required, string
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
      * `ssh_url`: required, string
      * `stargazers_url`: required, string, format: uri
      * `statuses_url`: required, string
      * `subscribers_url`: required, string, format: uri
      * `subscription_url`: required, string, format: uri
      * `tags_url`: required, string, format: uri
      * `teams_url`: required, string, format: uri
      * `trees_url`: required, string
      * `clone_url`: required, string
      * `mirror_url`: required, string or null, format: uri
      * `hooks_url`: required, string, format: uri
      * `svn_url`: required, string, format: uri
      * `homepage`: required, string or null, format: uri
      * `language`: required, string or null
      * `forks_count`: required, integer
      * `stargazers_count`: required, integer
      * `watchers_count`: required, integer
      * `size`: required, integer
      * `default_branch`: required, string
      * `open_issues_count`: required, integer
      * `is_template`: boolean, default: `false`
      * `topics`: array of string
      * `has_issues`: required, boolean, default: `true`
      * `has_projects`: required, boolean, default: `true`
      * `has_wiki`: required, boolean, default: `true`
      * `has_pages`: required, boolean
      * `has_discussions`: boolean, default: `false`
      * `has_pull_requests`: boolean, default: `true`
      * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
      * `archived`: required, boolean, default: `false`
      * `disabled`: required, boolean
      * `visibility`: string, default: `"public"`
      * `pushed_at`: required, string or null, format: date-time
      * `created_at`: required, string or null, format: date-time
      * `updated_at`: required, string or null, format: date-time
      * `allow_rebase_merge`: boolean, default: `true`
      * `temp_clone_token`: string
      * `allow_squash_merge`: boolean, default: `true`
      * `allow_auto_merge`: boolean, default: `false`
      * `delete_branch_on_merge`: boolean, default: `false`
      * `allow_update_branch`: boolean, default: `false`
      * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
      * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
      * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
      * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
      * `allow_merge_commit`: boolean, default: `true`
      * `allow_forking`: boolean
      * `web_commit_signoff_required`: boolean, default: `false`
      * `open_issues`: required, integer
      * `watchers`: required, integer
      * `starred_at`: string
      * `anonymous_access_enabled`: boolean
      * `code_search_index_status`: object:
        * `lexical_search_ok`: boolean
        * `lexical_commit_sha`: string
    * `performed_via_github_app`: any of:
      * **null**
      * **GitHub app**
        * `id`: required, integer
        * `slug`: string
        * `node_id`: required, string
        * `client_id`: string
        * `owner`: required, one of:
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
        * `name`: required, string
        * `description`: required, string or null
        * `external_url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `permissions`: required, object, additional properties: string:
          * `issues`: string
          * `checks`: string
          * `metadata`: string
          * `contents`: string
          * `deployments`: string
        * `events`: required, array of string
        * `installations_count`: integer
    * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
    * `reactions`: `Reaction Rollup`:
      * `url`: required, string, format: uri
      * `total_count`: required, integer
      * `+1`: required, integer
      * `-1`: required, integer
      * `laugh`: required, integer
      * `confused`: required, integer
      * `heart`: required, integer
      * `hooray`: required, integer
      * `eyes`: required, integer
      * `rocket`: required, integer
    * `sub_issues_summary`: `Sub-issues Summary`:
      * `total`: required, integer
      * `completed`: required, integer
      * `percent_completed`: required, integer
    * `parent_issue_url`: string or null, format: uri
    * `pinned_comment`: any of:
      * **null**
      * **Issue Comment**
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `url`: required, string, format: uri
        * `body`: string
        * `body_text`: string
        * `body_html`: string
        * `html_url`: required, string, format: uri
        * `user`: required, any of:
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
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `issue_url`: required, string, format: uri
        * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
        * `performed_via_github_app`: any of:
          * **null**
          * **GitHub app**
            * `id`: required, integer
            * `slug`: string
            * `node_id`: required, string
            * `client_id`: string
            * `owner`: required, one of:
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
            * `name`: required, string
            * `description`: required, string or null
            * `external_url`: required, string, format: uri
            * `html_url`: required, string, format: uri
            * `created_at`: required, string, format: date-time
            * `updated_at`: required, string, format: date-time
            * `permissions`: required, object, additional properties: string:
              * `issues`: string
              * `checks`: string
              * `metadata`: string
              * `contents`: string
              * `deployments`: string
            * `events`: required, array of string
            * `installations_count`: integer
        * `reactions`: `Reaction Rollup`:
          * `url`: required, string, format: uri
          * `total_count`: required, integer
          * `+1`: required, integer
          * `-1`: required, integer
          * `laugh`: required, integer
          * `confused`: required, integer
          * `heart`: required, integer
          * `hooray`: required, integer
          * `eyes`: required, integer
          * `rocket`: required, integer
        * `pin`: any of:
          * **null**
          * **Pinned Issue Comment**
            * `pinned_at`: required, string, format: date-time
            * `pinned_by`: required, any of:
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
    * `issue_dependencies_summary`: `Issue Dependencies Summary`:
      * `blocked_by`: required, integer
      * `blocking`: required, integer
      * `total_blocked_by`: required, integer
      * `total_blocking`: required, integer
    * `issue_field_values`: array of `Issue Field Value`:
      * `issue_field_id`: required, integer, format: int64
      * `node_id`: required, string
      * `data_type`: required, string, enum: `text`, `single_select`, `number`, `date`
      * `value`: required, any of:
        * **string**
        * **number**
        * **integer**
      * `single_select_option`: object or null:
        * `id`: required, integer, format: int64
        * `name`: required, string
        * `color`: required, string
  * **Pull Request Simple**
    * `url`: required, string, format: uri
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `html_url`: required, string, format: uri
    * `diff_url`: required, string, format: uri
    * `patch_url`: required, string, format: uri
    * `issue_url`: required, string, format: uri
    * `commits_url`: required, string, format: uri
    * `review_comments_url`: required, string, format: uri
    * `review_comment_url`: required, string
    * `comments_url`: required, string, format: uri
    * `statuses_url`: required, string, format: uri
    * `number`: required, integer
    * `state`: required, string
    * `locked`: required, boolean
    * `title`: required, string
    * `user`: required, any of:
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
    * `body`: required, string or null
    * `labels`: required, array of objects:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `url`: required, string
      * `name`: required, string
      * `description`: required, string
      * `color`: required, string
      * `default`: required, boolean
    * `milestone`: required, any of:
      * **null**
      * **Milestone**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `labels_url`: required, string, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `number`: required, integer
        * `state`: required, string, enum: `open`, `closed`, default: `"open"`
        * `title`: required, string
        * `description`: required, string or null
        * `creator`: required, any of:
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
        * `open_issues`: required, integer
        * `closed_issues`: required, integer
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `closed_at`: required, string or null, format: date-time
        * `due_on`: required, string or null, format: date-time
    * `active_lock_reason`: string or null
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `closed_at`: required, string or null, format: date-time
    * `merged_at`: required, string or null, format: date-time
    * `assignees`: array of `Simple User`:
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
    * `requested_reviewers`: array of `Simple User`:
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
    * `requested_teams`: array of `Team`:
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
    * `head`: required, object:
      * `label`: required, string
      * `ref`: required, string
      * `repo`: required, `Repository`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `name`: required, string
        * `full_name`: required, string
        * `license`: required, any of:
          * **null**
          * **License Simple**
            * `key`: required, string
            * `name`: required, string
            * `url`: required, string or null, format: uri
            * `spdx_id`: required, string or null
            * `node_id`: required, string
            * `html_url`: string, format: uri
        * `forks`: required, integer
        * `permissions`: object:
          * `admin`: required, boolean
          * `pull`: required, boolean
          * `triage`: boolean
          * `push`: required, boolean
          * `maintain`: boolean
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
        * `private`: required, boolean, default: `false`
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
        * `git_url`: required, string
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
        * `ssh_url`: required, string
        * `stargazers_url`: required, string, format: uri
        * `statuses_url`: required, string
        * `subscribers_url`: required, string, format: uri
        * `subscription_url`: required, string, format: uri
        * `tags_url`: required, string, format: uri
        * `teams_url`: required, string, format: uri
        * `trees_url`: required, string
        * `clone_url`: required, string
        * `mirror_url`: required, string or null, format: uri
        * `hooks_url`: required, string, format: uri
        * `svn_url`: required, string, format: uri
        * `homepage`: required, string or null, format: uri
        * `language`: required, string or null
        * `forks_count`: required, integer
        * `stargazers_count`: required, integer
        * `watchers_count`: required, integer
        * `size`: required, integer
        * `default_branch`: required, string
        * `open_issues_count`: required, integer
        * `is_template`: boolean, default: `false`
        * `topics`: array of string
        * `has_issues`: required, boolean, default: `true`
        * `has_projects`: required, boolean, default: `true`
        * `has_wiki`: required, boolean, default: `true`
        * `has_pages`: required, boolean
        * `has_discussions`: boolean, default: `false`
        * `has_pull_requests`: boolean, default: `true`
        * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
        * `archived`: required, boolean, default: `false`
        * `disabled`: required, boolean
        * `visibility`: string, default: `"public"`
        * `pushed_at`: required, string or null, format: date-time
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `allow_rebase_merge`: boolean, default: `true`
        * `temp_clone_token`: string
        * `allow_squash_merge`: boolean, default: `true`
        * `allow_auto_merge`: boolean, default: `false`
        * `delete_branch_on_merge`: boolean, default: `false`
        * `allow_update_branch`: boolean, default: `false`
        * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
        * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
        * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
        * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
        * `allow_merge_commit`: boolean, default: `true`
        * `allow_forking`: boolean
        * `web_commit_signoff_required`: boolean, default: `false`
        * `open_issues`: required, integer
        * `watchers`: required, integer
        * `starred_at`: string
        * `anonymous_access_enabled`: boolean
        * `code_search_index_status`: object:
          * `lexical_search_ok`: boolean
          * `lexical_commit_sha`: string
      * `sha`: required, string
      * `user`: required, any of:
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
    * `base`: required, object:
      * `label`: required, string
      * `ref`: required, string
      * `repo`: required, `Repository`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `name`: required, string
        * `full_name`: required, string
        * `license`: required, any of:
          * **null**
          * **License Simple**
            * `key`: required, string
            * `name`: required, string
            * `url`: required, string or null, format: uri
            * `spdx_id`: required, string or null
            * `node_id`: required, string
            * `html_url`: string, format: uri
        * `forks`: required, integer
        * `permissions`: object:
          * `admin`: required, boolean
          * `pull`: required, boolean
          * `triage`: boolean
          * `push`: required, boolean
          * `maintain`: boolean
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
        * `private`: required, boolean, default: `false`
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
        * `git_url`: required, string
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
        * `ssh_url`: required, string
        * `stargazers_url`: required, string, format: uri
        * `statuses_url`: required, string
        * `subscribers_url`: required, string, format: uri
        * `subscription_url`: required, string, format: uri
        * `tags_url`: required, string, format: uri
        * `teams_url`: required, string, format: uri
        * `trees_url`: required, string
        * `clone_url`: required, string
        * `mirror_url`: required, string or null, format: uri
        * `hooks_url`: required, string, format: uri
        * `svn_url`: required, string, format: uri
        * `homepage`: required, string or null, format: uri
        * `language`: required, string or null
        * `forks_count`: required, integer
        * `stargazers_count`: required, integer
        * `watchers_count`: required, integer
        * `size`: required, integer
        * `default_branch`: required, string
        * `open_issues_count`: required, integer
        * `is_template`: boolean, default: `false`
        * `topics`: array of string
        * `has_issues`: required, boolean, default: `true`
        * `has_projects`: required, boolean, default: `true`
        * `has_wiki`: required, boolean, default: `true`
        * `has_pages`: required, boolean
        * `has_discussions`: boolean, default: `false`
        * `has_pull_requests`: boolean, default: `true`
        * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
        * `archived`: required, boolean, default: `false`
        * `disabled`: required, boolean
        * `visibility`: string, default: `"public"`
        * `pushed_at`: required, string or null, format: date-time
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `allow_rebase_merge`: boolean, default: `true`
        * `temp_clone_token`: string
        * `allow_squash_merge`: boolean, default: `true`
        * `allow_auto_merge`: boolean, default: `false`
        * `delete_branch_on_merge`: boolean, default: `false`
        * `allow_update_branch`: boolean, default: `false`
        * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
        * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
        * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
        * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
        * `allow_merge_commit`: boolean, default: `true`
        * `allow_forking`: boolean
        * `web_commit_signoff_required`: boolean, default: `false`
        * `open_issues`: required, integer
        * `watchers`: required, integer
        * `starred_at`: string
        * `anonymous_access_enabled`: boolean
        * `code_search_index_status`: object:
          * `lexical_search_ok`: boolean
          * `lexical_commit_sha`: string
      * `sha`: required, string
      * `user`: required, any of:
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
    * `_links`: required, object:
      * `comments`: required, `Link`:
        * `href`: required, string
      * `commits`: required, `Link`:
        * `href`: required, string
      * `statuses`: required, `Link`:
        * `href`: required, string
      * `html`: required, `Link`:
        * `href`: required, string
      * `issue`: required, `Link`:
        * `href`: required, string
      * `review_comments`: required, `Link`:
        * `href`: required, string
      * `review_comment`: required, `Link`:
        * `href`: required, string
      * `self`: required, `Link`:
        * `href`: required, string
    * `author_association`: required, string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
    * `auto_merge`: required, `Auto merge`:
      * `enabled_by`: required, `Simple User`:
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
      * `merge_method`: required, string, enum: `merge`, `squash`, `rebase`
      * `commit_title`: required, string
      * `commit_message`: required, string
    * `draft`: boolean
  * **Draft Issue**
    * `id`: required, number
    * `node_id`: required, string
    * `title`: required, string
    * `body`: string or null
    * `user`: required, any of:
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
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
* `content_type`: required, string, enum: `Issue`, `PullRequest`, `DraftIssue`
* `creator`: `Simple User`:
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `archived_at`: required, string or null, format: date-time
* `project_url`: string, format: uri
* `item_url`: string, format: uri



#### Add an issue using repository owner, name, and issue number

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items \
  -d '{
  "type": "Issue",
  "owner": "octocat",
  "repo": "hello-world",
  "number": 42
}'
```

**Response schema (Status: 201):**

* `id`: required, number
* `node_id`: string
* `content`: one of:
  * **Issue**
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `repository_url`: required, string, format: uri
    * `labels_url`: required, string
    * `comments_url`: required, string, format: uri
    * `events_url`: required, string, format: uri
    * `html_url`: required, string, format: uri
    * `number`: required, integer
    * `state`: required, string
    * `state_reason`: string or null, enum: `completed`, `reopened`, `not_planned`, `duplicate`, `null`
    * `title`: required, string
    * `body`: string or null
    * `user`: required, any of:
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
    * `labels`: required, array of object
    * `assignees`: array of `Simple User`:
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
    * `milestone`: required, any of:
      * **null**
      * **Milestone**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `labels_url`: required, string, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `number`: required, integer
        * `state`: required, string, enum: `open`, `closed`, default: `"open"`
        * `title`: required, string
        * `description`: required, string or null
        * `creator`: required, any of:
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
        * `open_issues`: required, integer
        * `closed_issues`: required, integer
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `closed_at`: required, string or null, format: date-time
        * `due_on`: required, string or null, format: date-time
    * `locked`: required, boolean
    * `active_lock_reason`: string or null
    * `comments`: required, integer
    * `pull_request`: object:
      * `merged_at`: string or null, format: date-time
      * `diff_url`: required, string or null, format: uri
      * `html_url`: required, string or null, format: uri
      * `patch_url`: required, string or null, format: uri
      * `url`: required, string or null, format: uri
    * `closed_at`: required, string or null, format: date-time
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `draft`: boolean
    * `closed_by`: any of:
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
    * `body_html`: string
    * `body_text`: string
    * `timeline_url`: string, format: uri
    * `type`: `Issue Type`:
      * `id`: required, integer
      * `node_id`: required, string
      * `name`: required, string
      * `description`: required, string or null
      * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
      * `created_at`: string, format: date-time
      * `updated_at`: string, format: date-time
      * `is_enabled`: boolean
    * `repository`: `Repository`:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `name`: required, string
      * `full_name`: required, string
      * `license`: required, any of:
        * **null**
        * **License Simple**
          * `key`: required, string
          * `name`: required, string
          * `url`: required, string or null, format: uri
          * `spdx_id`: required, string or null
          * `node_id`: required, string
          * `html_url`: string, format: uri
      * `forks`: required, integer
      * `permissions`: object:
        * `admin`: required, boolean
        * `pull`: required, boolean
        * `triage`: boolean
        * `push`: required, boolean
        * `maintain`: boolean
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
      * `private`: required, boolean, default: `false`
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
      * `git_url`: required, string
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
      * `ssh_url`: required, string
      * `stargazers_url`: required, string, format: uri
      * `statuses_url`: required, string
      * `subscribers_url`: required, string, format: uri
      * `subscription_url`: required, string, format: uri
      * `tags_url`: required, string, format: uri
      * `teams_url`: required, string, format: uri
      * `trees_url`: required, string
      * `clone_url`: required, string
      * `mirror_url`: required, string or null, format: uri
      * `hooks_url`: required, string, format: uri
      * `svn_url`: required, string, format: uri
      * `homepage`: required, string or null, format: uri
      * `language`: required, string or null
      * `forks_count`: required, integer
      * `stargazers_count`: required, integer
      * `watchers_count`: required, integer
      * `size`: required, integer
      * `default_branch`: required, string
      * `open_issues_count`: required, integer
      * `is_template`: boolean, default: `false`
      * `topics`: array of string
      * `has_issues`: required, boolean, default: `true`
      * `has_projects`: required, boolean, default: `true`
      * `has_wiki`: required, boolean, default: `true`
      * `has_pages`: required, boolean
      * `has_discussions`: boolean, default: `false`
      * `has_pull_requests`: boolean, default: `true`
      * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
      * `archived`: required, boolean, default: `false`
      * `disabled`: required, boolean
      * `visibility`: string, default: `"public"`
      * `pushed_at`: required, string or null, format: date-time
      * `created_at`: required, string or null, format: date-time
      * `updated_at`: required, string or null, format: date-time
      * `allow_rebase_merge`: boolean, default: `true`
      * `temp_clone_token`: string
      * `allow_squash_merge`: boolean, default: `true`
      * `allow_auto_merge`: boolean, default: `false`
      * `delete_branch_on_merge`: boolean, default: `false`
      * `allow_update_branch`: boolean, default: `false`
      * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
      * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
      * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
      * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
      * `allow_merge_commit`: boolean, default: `true`
      * `allow_forking`: boolean
      * `web_commit_signoff_required`: boolean, default: `false`
      * `open_issues`: required, integer
      * `watchers`: required, integer
      * `starred_at`: string
      * `anonymous_access_enabled`: boolean
      * `code_search_index_status`: object:
        * `lexical_search_ok`: boolean
        * `lexical_commit_sha`: string
    * `performed_via_github_app`: any of:
      * **null**
      * **GitHub app**
        * `id`: required, integer
        * `slug`: string
        * `node_id`: required, string
        * `client_id`: string
        * `owner`: required, one of:
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
        * `name`: required, string
        * `description`: required, string or null
        * `external_url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `permissions`: required, object, additional properties: string:
          * `issues`: string
          * `checks`: string
          * `metadata`: string
          * `contents`: string
          * `deployments`: string
        * `events`: required, array of string
        * `installations_count`: integer
    * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
    * `reactions`: `Reaction Rollup`:
      * `url`: required, string, format: uri
      * `total_count`: required, integer
      * `+1`: required, integer
      * `-1`: required, integer
      * `laugh`: required, integer
      * `confused`: required, integer
      * `heart`: required, integer
      * `hooray`: required, integer
      * `eyes`: required, integer
      * `rocket`: required, integer
    * `sub_issues_summary`: `Sub-issues Summary`:
      * `total`: required, integer
      * `completed`: required, integer
      * `percent_completed`: required, integer
    * `parent_issue_url`: string or null, format: uri
    * `pinned_comment`: any of:
      * **null**
      * **Issue Comment**
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `url`: required, string, format: uri
        * `body`: string
        * `body_text`: string
        * `body_html`: string
        * `html_url`: required, string, format: uri
        * `user`: required, any of:
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
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `issue_url`: required, string, format: uri
        * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
        * `performed_via_github_app`: any of:
          * **null**
          * **GitHub app**
            * `id`: required, integer
            * `slug`: string
            * `node_id`: required, string
            * `client_id`: string
            * `owner`: required, one of:
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
            * `name`: required, string
            * `description`: required, string or null
            * `external_url`: required, string, format: uri
            * `html_url`: required, string, format: uri
            * `created_at`: required, string, format: date-time
            * `updated_at`: required, string, format: date-time
            * `permissions`: required, object, additional properties: string:
              * `issues`: string
              * `checks`: string
              * `metadata`: string
              * `contents`: string
              * `deployments`: string
            * `events`: required, array of string
            * `installations_count`: integer
        * `reactions`: `Reaction Rollup`:
          * `url`: required, string, format: uri
          * `total_count`: required, integer
          * `+1`: required, integer
          * `-1`: required, integer
          * `laugh`: required, integer
          * `confused`: required, integer
          * `heart`: required, integer
          * `hooray`: required, integer
          * `eyes`: required, integer
          * `rocket`: required, integer
        * `pin`: any of:
          * **null**
          * **Pinned Issue Comment**
            * `pinned_at`: required, string, format: date-time
            * `pinned_by`: required, any of:
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
    * `issue_dependencies_summary`: `Issue Dependencies Summary`:
      * `blocked_by`: required, integer
      * `blocking`: required, integer
      * `total_blocked_by`: required, integer
      * `total_blocking`: required, integer
    * `issue_field_values`: array of `Issue Field Value`:
      * `issue_field_id`: required, integer, format: int64
      * `node_id`: required, string
      * `data_type`: required, string, enum: `text`, `single_select`, `number`, `date`
      * `value`: required, any of:
        * **string**
        * **number**
        * **integer**
      * `single_select_option`: object or null:
        * `id`: required, integer, format: int64
        * `name`: required, string
        * `color`: required, string
  * **Pull Request Simple**
    * `url`: required, string, format: uri
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `html_url`: required, string, format: uri
    * `diff_url`: required, string, format: uri
    * `patch_url`: required, string, format: uri
    * `issue_url`: required, string, format: uri
    * `commits_url`: required, string, format: uri
    * `review_comments_url`: required, string, format: uri
    * `review_comment_url`: required, string
    * `comments_url`: required, string, format: uri
    * `statuses_url`: required, string, format: uri
    * `number`: required, integer
    * `state`: required, string
    * `locked`: required, boolean
    * `title`: required, string
    * `user`: required, any of:
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
    * `body`: required, string or null
    * `labels`: required, array of objects:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `url`: required, string
      * `name`: required, string
      * `description`: required, string
      * `color`: required, string
      * `default`: required, boolean
    * `milestone`: required, any of:
      * **null**
      * **Milestone**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `labels_url`: required, string, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `number`: required, integer
        * `state`: required, string, enum: `open`, `closed`, default: `"open"`
        * `title`: required, string
        * `description`: required, string or null
        * `creator`: required, any of:
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
        * `open_issues`: required, integer
        * `closed_issues`: required, integer
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `closed_at`: required, string or null, format: date-time
        * `due_on`: required, string or null, format: date-time
    * `active_lock_reason`: string or null
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `closed_at`: required, string or null, format: date-time
    * `merged_at`: required, string or null, format: date-time
    * `assignees`: array of `Simple User`:
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
    * `requested_reviewers`: array of `Simple User`:
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
    * `requested_teams`: array of `Team`:
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
    * `head`: required, object:
      * `label`: required, string
      * `ref`: required, string
      * `repo`: required, `Repository`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `name`: required, string
        * `full_name`: required, string
        * `license`: required, any of:
          * **null**
          * **License Simple**
            * `key`: required, string
            * `name`: required, string
            * `url`: required, string or null, format: uri
            * `spdx_id`: required, string or null
            * `node_id`: required, string
            * `html_url`: string, format: uri
        * `forks`: required, integer
        * `permissions`: object:
          * `admin`: required, boolean
          * `pull`: required, boolean
          * `triage`: boolean
          * `push`: required, boolean
          * `maintain`: boolean
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
        * `private`: required, boolean, default: `false`
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
        * `git_url`: required, string
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
        * `ssh_url`: required, string
        * `stargazers_url`: required, string, format: uri
        * `statuses_url`: required, string
        * `subscribers_url`: required, string, format: uri
        * `subscription_url`: required, string, format: uri
        * `tags_url`: required, string, format: uri
        * `teams_url`: required, string, format: uri
        * `trees_url`: required, string
        * `clone_url`: required, string
        * `mirror_url`: required, string or null, format: uri
        * `hooks_url`: required, string, format: uri
        * `svn_url`: required, string, format: uri
        * `homepage`: required, string or null, format: uri
        * `language`: required, string or null
        * `forks_count`: required, integer
        * `stargazers_count`: required, integer
        * `watchers_count`: required, integer
        * `size`: required, integer
        * `default_branch`: required, string
        * `open_issues_count`: required, integer
        * `is_template`: boolean, default: `false`
        * `topics`: array of string
        * `has_issues`: required, boolean, default: `true`
        * `has_projects`: required, boolean, default: `true`
        * `has_wiki`: required, boolean, default: `true`
        * `has_pages`: required, boolean
        * `has_discussions`: boolean, default: `false`
        * `has_pull_requests`: boolean, default: `true`
        * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
        * `archived`: required, boolean, default: `false`
        * `disabled`: required, boolean
        * `visibility`: string, default: `"public"`
        * `pushed_at`: required, string or null, format: date-time
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `allow_rebase_merge`: boolean, default: `true`
        * `temp_clone_token`: string
        * `allow_squash_merge`: boolean, default: `true`
        * `allow_auto_merge`: boolean, default: `false`
        * `delete_branch_on_merge`: boolean, default: `false`
        * `allow_update_branch`: boolean, default: `false`
        * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
        * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
        * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
        * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
        * `allow_merge_commit`: boolean, default: `true`
        * `allow_forking`: boolean
        * `web_commit_signoff_required`: boolean, default: `false`
        * `open_issues`: required, integer
        * `watchers`: required, integer
        * `starred_at`: string
        * `anonymous_access_enabled`: boolean
        * `code_search_index_status`: object:
          * `lexical_search_ok`: boolean
          * `lexical_commit_sha`: string
      * `sha`: required, string
      * `user`: required, any of:
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
    * `base`: required, object:
      * `label`: required, string
      * `ref`: required, string
      * `repo`: required, `Repository`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `name`: required, string
        * `full_name`: required, string
        * `license`: required, any of:
          * **null**
          * **License Simple**
            * `key`: required, string
            * `name`: required, string
            * `url`: required, string or null, format: uri
            * `spdx_id`: required, string or null
            * `node_id`: required, string
            * `html_url`: string, format: uri
        * `forks`: required, integer
        * `permissions`: object:
          * `admin`: required, boolean
          * `pull`: required, boolean
          * `triage`: boolean
          * `push`: required, boolean
          * `maintain`: boolean
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
        * `private`: required, boolean, default: `false`
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
        * `git_url`: required, string
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
        * `ssh_url`: required, string
        * `stargazers_url`: required, string, format: uri
        * `statuses_url`: required, string
        * `subscribers_url`: required, string, format: uri
        * `subscription_url`: required, string, format: uri
        * `tags_url`: required, string, format: uri
        * `teams_url`: required, string, format: uri
        * `trees_url`: required, string
        * `clone_url`: required, string
        * `mirror_url`: required, string or null, format: uri
        * `hooks_url`: required, string, format: uri
        * `svn_url`: required, string, format: uri
        * `homepage`: required, string or null, format: uri
        * `language`: required, string or null
        * `forks_count`: required, integer
        * `stargazers_count`: required, integer
        * `watchers_count`: required, integer
        * `size`: required, integer
        * `default_branch`: required, string
        * `open_issues_count`: required, integer
        * `is_template`: boolean, default: `false`
        * `topics`: array of string
        * `has_issues`: required, boolean, default: `true`
        * `has_projects`: required, boolean, default: `true`
        * `has_wiki`: required, boolean, default: `true`
        * `has_pages`: required, boolean
        * `has_discussions`: boolean, default: `false`
        * `has_pull_requests`: boolean, default: `true`
        * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
        * `archived`: required, boolean, default: `false`
        * `disabled`: required, boolean
        * `visibility`: string, default: `"public"`
        * `pushed_at`: required, string or null, format: date-time
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `allow_rebase_merge`: boolean, default: `true`
        * `temp_clone_token`: string
        * `allow_squash_merge`: boolean, default: `true`
        * `allow_auto_merge`: boolean, default: `false`
        * `delete_branch_on_merge`: boolean, default: `false`
        * `allow_update_branch`: boolean, default: `false`
        * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
        * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
        * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
        * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
        * `allow_merge_commit`: boolean, default: `true`
        * `allow_forking`: boolean
        * `web_commit_signoff_required`: boolean, default: `false`
        * `open_issues`: required, integer
        * `watchers`: required, integer
        * `starred_at`: string
        * `anonymous_access_enabled`: boolean
        * `code_search_index_status`: object:
          * `lexical_search_ok`: boolean
          * `lexical_commit_sha`: string
      * `sha`: required, string
      * `user`: required, any of:
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
    * `_links`: required, object:
      * `comments`: required, `Link`:
        * `href`: required, string
      * `commits`: required, `Link`:
        * `href`: required, string
      * `statuses`: required, `Link`:
        * `href`: required, string
      * `html`: required, `Link`:
        * `href`: required, string
      * `issue`: required, `Link`:
        * `href`: required, string
      * `review_comments`: required, `Link`:
        * `href`: required, string
      * `review_comment`: required, `Link`:
        * `href`: required, string
      * `self`: required, `Link`:
        * `href`: required, string
    * `author_association`: required, string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
    * `auto_merge`: required, `Auto merge`:
      * `enabled_by`: required, `Simple User`:
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
      * `merge_method`: required, string, enum: `merge`, `squash`, `rebase`
      * `commit_title`: required, string
      * `commit_message`: required, string
    * `draft`: boolean
  * **Draft Issue**
    * `id`: required, number
    * `node_id`: required, string
    * `title`: required, string
    * `body`: string or null
    * `user`: required, any of:
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
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
* `content_type`: required, string, enum: `Issue`, `PullRequest`, `DraftIssue`
* `creator`: `Simple User`:
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `archived_at`: required, string or null, format: date-time
* `project_url`: string, format: uri
* `item_url`: string, format: uri



#### Add a pull request using repository owner, name, and PR number

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items \
  -d '{
  "type": "PullRequest",
  "owner": "octocat",
  "repo": "hello-world",
  "number": 123
}'
```

**Response schema (Status: 201):**

* `id`: required, number
* `node_id`: string
* `content`: one of:
  * **Issue**
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `url`: required, string, format: uri
    * `repository_url`: required, string, format: uri
    * `labels_url`: required, string
    * `comments_url`: required, string, format: uri
    * `events_url`: required, string, format: uri
    * `html_url`: required, string, format: uri
    * `number`: required, integer
    * `state`: required, string
    * `state_reason`: string or null, enum: `completed`, `reopened`, `not_planned`, `duplicate`, `null`
    * `title`: required, string
    * `body`: string or null
    * `user`: required, any of:
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
    * `labels`: required, array of object
    * `assignees`: array of `Simple User`:
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
    * `milestone`: required, any of:
      * **null**
      * **Milestone**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `labels_url`: required, string, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `number`: required, integer
        * `state`: required, string, enum: `open`, `closed`, default: `"open"`
        * `title`: required, string
        * `description`: required, string or null
        * `creator`: required, any of:
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
        * `open_issues`: required, integer
        * `closed_issues`: required, integer
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `closed_at`: required, string or null, format: date-time
        * `due_on`: required, string or null, format: date-time
    * `locked`: required, boolean
    * `active_lock_reason`: string or null
    * `comments`: required, integer
    * `pull_request`: object:
      * `merged_at`: string or null, format: date-time
      * `diff_url`: required, string or null, format: uri
      * `html_url`: required, string or null, format: uri
      * `patch_url`: required, string or null, format: uri
      * `url`: required, string or null, format: uri
    * `closed_at`: required, string or null, format: date-time
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `draft`: boolean
    * `closed_by`: any of:
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
    * `body_html`: string
    * `body_text`: string
    * `timeline_url`: string, format: uri
    * `type`: `Issue Type`:
      * `id`: required, integer
      * `node_id`: required, string
      * `name`: required, string
      * `description`: required, string or null
      * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
      * `created_at`: string, format: date-time
      * `updated_at`: string, format: date-time
      * `is_enabled`: boolean
    * `repository`: `Repository`:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `name`: required, string
      * `full_name`: required, string
      * `license`: required, any of:
        * **null**
        * **License Simple**
          * `key`: required, string
          * `name`: required, string
          * `url`: required, string or null, format: uri
          * `spdx_id`: required, string or null
          * `node_id`: required, string
          * `html_url`: string, format: uri
      * `forks`: required, integer
      * `permissions`: object:
        * `admin`: required, boolean
        * `pull`: required, boolean
        * `triage`: boolean
        * `push`: required, boolean
        * `maintain`: boolean
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
      * `private`: required, boolean, default: `false`
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
      * `git_url`: required, string
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
      * `ssh_url`: required, string
      * `stargazers_url`: required, string, format: uri
      * `statuses_url`: required, string
      * `subscribers_url`: required, string, format: uri
      * `subscription_url`: required, string, format: uri
      * `tags_url`: required, string, format: uri
      * `teams_url`: required, string, format: uri
      * `trees_url`: required, string
      * `clone_url`: required, string
      * `mirror_url`: required, string or null, format: uri
      * `hooks_url`: required, string, format: uri
      * `svn_url`: required, string, format: uri
      * `homepage`: required, string or null, format: uri
      * `language`: required, string or null
      * `forks_count`: required, integer
      * `stargazers_count`: required, integer
      * `watchers_count`: required, integer
      * `size`: required, integer
      * `default_branch`: required, string
      * `open_issues_count`: required, integer
      * `is_template`: boolean, default: `false`
      * `topics`: array of string
      * `has_issues`: required, boolean, default: `true`
      * `has_projects`: required, boolean, default: `true`
      * `has_wiki`: required, boolean, default: `true`
      * `has_pages`: required, boolean
      * `has_discussions`: boolean, default: `false`
      * `has_pull_requests`: boolean, default: `true`
      * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
      * `archived`: required, boolean, default: `false`
      * `disabled`: required, boolean
      * `visibility`: string, default: `"public"`
      * `pushed_at`: required, string or null, format: date-time
      * `created_at`: required, string or null, format: date-time
      * `updated_at`: required, string or null, format: date-time
      * `allow_rebase_merge`: boolean, default: `true`
      * `temp_clone_token`: string
      * `allow_squash_merge`: boolean, default: `true`
      * `allow_auto_merge`: boolean, default: `false`
      * `delete_branch_on_merge`: boolean, default: `false`
      * `allow_update_branch`: boolean, default: `false`
      * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
      * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
      * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
      * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
      * `allow_merge_commit`: boolean, default: `true`
      * `allow_forking`: boolean
      * `web_commit_signoff_required`: boolean, default: `false`
      * `open_issues`: required, integer
      * `watchers`: required, integer
      * `starred_at`: string
      * `anonymous_access_enabled`: boolean
      * `code_search_index_status`: object:
        * `lexical_search_ok`: boolean
        * `lexical_commit_sha`: string
    * `performed_via_github_app`: any of:
      * **null**
      * **GitHub app**
        * `id`: required, integer
        * `slug`: string
        * `node_id`: required, string
        * `client_id`: string
        * `owner`: required, one of:
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
        * `name`: required, string
        * `description`: required, string or null
        * `external_url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `permissions`: required, object, additional properties: string:
          * `issues`: string
          * `checks`: string
          * `metadata`: string
          * `contents`: string
          * `deployments`: string
        * `events`: required, array of string
        * `installations_count`: integer
    * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
    * `reactions`: `Reaction Rollup`:
      * `url`: required, string, format: uri
      * `total_count`: required, integer
      * `+1`: required, integer
      * `-1`: required, integer
      * `laugh`: required, integer
      * `confused`: required, integer
      * `heart`: required, integer
      * `hooray`: required, integer
      * `eyes`: required, integer
      * `rocket`: required, integer
    * `sub_issues_summary`: `Sub-issues Summary`:
      * `total`: required, integer
      * `completed`: required, integer
      * `percent_completed`: required, integer
    * `parent_issue_url`: string or null, format: uri
    * `pinned_comment`: any of:
      * **null**
      * **Issue Comment**
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `url`: required, string, format: uri
        * `body`: string
        * `body_text`: string
        * `body_html`: string
        * `html_url`: required, string, format: uri
        * `user`: required, any of:
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
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `issue_url`: required, string, format: uri
        * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
        * `performed_via_github_app`: any of:
          * **null**
          * **GitHub app**
            * `id`: required, integer
            * `slug`: string
            * `node_id`: required, string
            * `client_id`: string
            * `owner`: required, one of:
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
            * `name`: required, string
            * `description`: required, string or null
            * `external_url`: required, string, format: uri
            * `html_url`: required, string, format: uri
            * `created_at`: required, string, format: date-time
            * `updated_at`: required, string, format: date-time
            * `permissions`: required, object, additional properties: string:
              * `issues`: string
              * `checks`: string
              * `metadata`: string
              * `contents`: string
              * `deployments`: string
            * `events`: required, array of string
            * `installations_count`: integer
        * `reactions`: `Reaction Rollup`:
          * `url`: required, string, format: uri
          * `total_count`: required, integer
          * `+1`: required, integer
          * `-1`: required, integer
          * `laugh`: required, integer
          * `confused`: required, integer
          * `heart`: required, integer
          * `hooray`: required, integer
          * `eyes`: required, integer
          * `rocket`: required, integer
        * `pin`: any of:
          * **null**
          * **Pinned Issue Comment**
            * `pinned_at`: required, string, format: date-time
            * `pinned_by`: required, any of:
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
    * `issue_dependencies_summary`: `Issue Dependencies Summary`:
      * `blocked_by`: required, integer
      * `blocking`: required, integer
      * `total_blocked_by`: required, integer
      * `total_blocking`: required, integer
    * `issue_field_values`: array of `Issue Field Value`:
      * `issue_field_id`: required, integer, format: int64
      * `node_id`: required, string
      * `data_type`: required, string, enum: `text`, `single_select`, `number`, `date`
      * `value`: required, any of:
        * **string**
        * **number**
        * **integer**
      * `single_select_option`: object or null:
        * `id`: required, integer, format: int64
        * `name`: required, string
        * `color`: required, string
  * **Pull Request Simple**
    * `url`: required, string, format: uri
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `html_url`: required, string, format: uri
    * `diff_url`: required, string, format: uri
    * `patch_url`: required, string, format: uri
    * `issue_url`: required, string, format: uri
    * `commits_url`: required, string, format: uri
    * `review_comments_url`: required, string, format: uri
    * `review_comment_url`: required, string
    * `comments_url`: required, string, format: uri
    * `statuses_url`: required, string, format: uri
    * `number`: required, integer
    * `state`: required, string
    * `locked`: required, boolean
    * `title`: required, string
    * `user`: required, any of:
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
    * `body`: required, string or null
    * `labels`: required, array of objects:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `url`: required, string
      * `name`: required, string
      * `description`: required, string
      * `color`: required, string
      * `default`: required, boolean
    * `milestone`: required, any of:
      * **null**
      * **Milestone**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `labels_url`: required, string, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `number`: required, integer
        * `state`: required, string, enum: `open`, `closed`, default: `"open"`
        * `title`: required, string
        * `description`: required, string or null
        * `creator`: required, any of:
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
        * `open_issues`: required, integer
        * `closed_issues`: required, integer
        * `created_at`: required, string, format: date-time
        * `updated_at`: required, string, format: date-time
        * `closed_at`: required, string or null, format: date-time
        * `due_on`: required, string or null, format: date-time
    * `active_lock_reason`: string or null
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `closed_at`: required, string or null, format: date-time
    * `merged_at`: required, string or null, format: date-time
    * `assignees`: array of `Simple User`:
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
    * `requested_reviewers`: array of `Simple User`:
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
    * `requested_teams`: array of `Team`:
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
    * `head`: required, object:
      * `label`: required, string
      * `ref`: required, string
      * `repo`: required, `Repository`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `name`: required, string
        * `full_name`: required, string
        * `license`: required, any of:
          * **null**
          * **License Simple**
            * `key`: required, string
            * `name`: required, string
            * `url`: required, string or null, format: uri
            * `spdx_id`: required, string or null
            * `node_id`: required, string
            * `html_url`: string, format: uri
        * `forks`: required, integer
        * `permissions`: object:
          * `admin`: required, boolean
          * `pull`: required, boolean
          * `triage`: boolean
          * `push`: required, boolean
          * `maintain`: boolean
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
        * `private`: required, boolean, default: `false`
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
        * `git_url`: required, string
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
        * `ssh_url`: required, string
        * `stargazers_url`: required, string, format: uri
        * `statuses_url`: required, string
        * `subscribers_url`: required, string, format: uri
        * `subscription_url`: required, string, format: uri
        * `tags_url`: required, string, format: uri
        * `teams_url`: required, string, format: uri
        * `trees_url`: required, string
        * `clone_url`: required, string
        * `mirror_url`: required, string or null, format: uri
        * `hooks_url`: required, string, format: uri
        * `svn_url`: required, string, format: uri
        * `homepage`: required, string or null, format: uri
        * `language`: required, string or null
        * `forks_count`: required, integer
        * `stargazers_count`: required, integer
        * `watchers_count`: required, integer
        * `size`: required, integer
        * `default_branch`: required, string
        * `open_issues_count`: required, integer
        * `is_template`: boolean, default: `false`
        * `topics`: array of string
        * `has_issues`: required, boolean, default: `true`
        * `has_projects`: required, boolean, default: `true`
        * `has_wiki`: required, boolean, default: `true`
        * `has_pages`: required, boolean
        * `has_discussions`: boolean, default: `false`
        * `has_pull_requests`: boolean, default: `true`
        * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
        * `archived`: required, boolean, default: `false`
        * `disabled`: required, boolean
        * `visibility`: string, default: `"public"`
        * `pushed_at`: required, string or null, format: date-time
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `allow_rebase_merge`: boolean, default: `true`
        * `temp_clone_token`: string
        * `allow_squash_merge`: boolean, default: `true`
        * `allow_auto_merge`: boolean, default: `false`
        * `delete_branch_on_merge`: boolean, default: `false`
        * `allow_update_branch`: boolean, default: `false`
        * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
        * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
        * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
        * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
        * `allow_merge_commit`: boolean, default: `true`
        * `allow_forking`: boolean
        * `web_commit_signoff_required`: boolean, default: `false`
        * `open_issues`: required, integer
        * `watchers`: required, integer
        * `starred_at`: string
        * `anonymous_access_enabled`: boolean
        * `code_search_index_status`: object:
          * `lexical_search_ok`: boolean
          * `lexical_commit_sha`: string
      * `sha`: required, string
      * `user`: required, any of:
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
    * `base`: required, object:
      * `label`: required, string
      * `ref`: required, string
      * `repo`: required, `Repository`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `name`: required, string
        * `full_name`: required, string
        * `license`: required, any of:
          * **null**
          * **License Simple**
            * `key`: required, string
            * `name`: required, string
            * `url`: required, string or null, format: uri
            * `spdx_id`: required, string or null
            * `node_id`: required, string
            * `html_url`: string, format: uri
        * `forks`: required, integer
        * `permissions`: object:
          * `admin`: required, boolean
          * `pull`: required, boolean
          * `triage`: boolean
          * `push`: required, boolean
          * `maintain`: boolean
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
        * `private`: required, boolean, default: `false`
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
        * `git_url`: required, string
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
        * `ssh_url`: required, string
        * `stargazers_url`: required, string, format: uri
        * `statuses_url`: required, string
        * `subscribers_url`: required, string, format: uri
        * `subscription_url`: required, string, format: uri
        * `tags_url`: required, string, format: uri
        * `teams_url`: required, string, format: uri
        * `trees_url`: required, string
        * `clone_url`: required, string
        * `mirror_url`: required, string or null, format: uri
        * `hooks_url`: required, string, format: uri
        * `svn_url`: required, string, format: uri
        * `homepage`: required, string or null, format: uri
        * `language`: required, string or null
        * `forks_count`: required, integer
        * `stargazers_count`: required, integer
        * `watchers_count`: required, integer
        * `size`: required, integer
        * `default_branch`: required, string
        * `open_issues_count`: required, integer
        * `is_template`: boolean, default: `false`
        * `topics`: array of string
        * `has_issues`: required, boolean, default: `true`
        * `has_projects`: required, boolean, default: `true`
        * `has_wiki`: required, boolean, default: `true`
        * `has_pages`: required, boolean
        * `has_discussions`: boolean, default: `false`
        * `has_pull_requests`: boolean, default: `true`
        * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
        * `archived`: required, boolean, default: `false`
        * `disabled`: required, boolean
        * `visibility`: string, default: `"public"`
        * `pushed_at`: required, string or null, format: date-time
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `allow_rebase_merge`: boolean, default: `true`
        * `temp_clone_token`: string
        * `allow_squash_merge`: boolean, default: `true`
        * `allow_auto_merge`: boolean, default: `false`
        * `delete_branch_on_merge`: boolean, default: `false`
        * `allow_update_branch`: boolean, default: `false`
        * `squash_merge_commit_title`: string, enum: `PR_TITLE`, `COMMIT_OR_PR_TITLE`
        * `squash_merge_commit_message`: string, enum: `PR_BODY`, `COMMIT_MESSAGES`, `BLANK`
        * `merge_commit_title`: string, enum: `PR_TITLE`, `MERGE_MESSAGE`
        * `merge_commit_message`: string, enum: `PR_BODY`, `PR_TITLE`, `BLANK`
        * `allow_merge_commit`: boolean, default: `true`
        * `allow_forking`: boolean
        * `web_commit_signoff_required`: boolean, default: `false`
        * `open_issues`: required, integer
        * `watchers`: required, integer
        * `starred_at`: string
        * `anonymous_access_enabled`: boolean
        * `code_search_index_status`: object:
          * `lexical_search_ok`: boolean
          * `lexical_commit_sha`: string
      * `sha`: required, string
      * `user`: required, any of:
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
    * `_links`: required, object:
      * `comments`: required, `Link`:
        * `href`: required, string
      * `commits`: required, `Link`:
        * `href`: required, string
      * `statuses`: required, `Link`:
        * `href`: required, string
      * `html`: required, `Link`:
        * `href`: required, string
      * `issue`: required, `Link`:
        * `href`: required, string
      * `review_comments`: required, `Link`:
        * `href`: required, string
      * `review_comment`: required, `Link`:
        * `href`: required, string
      * `self`: required, `Link`:
        * `href`: required, string
    * `author_association`: required, string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
    * `auto_merge`: required, `Auto merge`:
      * `enabled_by`: required, `Simple User`:
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
      * `merge_method`: required, string, enum: `merge`, `squash`, `rebase`
      * `commit_title`: required, string
      * `commit_message`: required, string
    * `draft`: boolean
  * **Draft Issue**
    * `id`: required, number
    * `node_id`: required, string
    * `title`: required, string
    * `body`: string or null
    * `user`: required, any of:
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
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
* `content_type`: required, string, enum: `Issue`, `PullRequest`, `DraftIssue`
* `creator`: `Simple User`:
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `archived_at`: required, string or null, format: date-time
* `project_url`: string, format: uri
* `item_url`: string, format: uri





## Get an item for an organization owned project

```
GET /orgs/{org}/projectsV2/{project_number}/items/{item_id}
```

Get a specific item from an organization-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`item_id`** (integer) (required)
  The unique identifier of the project item.

- **`fields`** (string)
  Limit results to specific fields, by their IDs. If not specified, the title field will be returned.
Example: fields[]=123&fields[]=456&fields[]=789 or fields=123,456,789






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
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items/ITEM_ID
```

**Response schema (Status: 200):**

* `id`: required, number
* `node_id`: string
* `project_url`: string, format: uri
* `content_type`: required, string, enum: `Issue`, `PullRequest`, `DraftIssue`
* `content`: object or null, additional properties allowed
* `creator`: `Simple User`:
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `archived_at`: required, string or null, format: date-time
* `item_url`: string or null, format: uri
* `fields`: array of object, additional properties allowed





## Update project item for organization

```
PATCH /orgs/{org}/projectsV2/{project_number}/items/{item_id}
```

Update a specific item in an organization-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`item_id`** (integer) (required)
  The unique identifier of the project item.




#### Body parameters

- **`fields`** (array of objects) (required)
  A list of field updates to apply.
  - **`id`** (integer) (required)
    The ID of the project field to update.
  - **`value`** (null or string or number) (required)
    The new value for the field:

For text, number, and date fields, provide the new value directly.
For single select and iteration fields, provide the ID of the option or iteration.
To clear the field, set this to null.





### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Update a text field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 123,
      "value": "Updated text value"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).



#### Update a number field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 456,
      "value": 42.5
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).



#### Update a date field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 789,
      "value": "2023-10-05"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).



#### Update a single select field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 789,
      "value": "47fc9ee4"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).



#### Update an iteration field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 1011,
      "value": "866ee5b8"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).





## Delete project item for organization

```
DELETE /orgs/{org}/projectsV2/{project_number}/items/{item_id}
```

Delete a specific item from an organization-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`item_id`** (integer) (required)
  The unique identifier of the project item.






### HTTP response status codes


- **204** - No Content


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/items/ITEM_ID
```

**Response schema (Status: 204):**





## List items for an organization project view

```
GET /orgs/{org}/projectsV2/{project_number}/views/{view_number}/items
```

List items in an organization project with the saved view's filter applied.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`view_number`** (integer) (required)
  The number that identifies the project view.

- **`fields`** (string)
  Limit results to specific fields, by their IDs. If not specified, the
title field will be returned.
Example: fields[]=123&fields[]=456&fields[]=789 or fields=123,456,789

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






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
  https://api.github.com/orgs/ORG/projectsV2/PROJECT_NUMBER/views/VIEW_NUMBER/items
```

**Response schema (Status: 200):**

Same response schema as [List items for an organization owned project](#list-items-for-an-organization-owned-project).





## List items for a user owned project

```
GET /users/{username}/projectsV2/{project_number}/items
```

List all items for a specific user-owned project accessible by the authenticated user.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`q`** (string)
  Search query to filter items, see Filtering projects for more information.

- **`fields`** (string)
  Limit results to specific fields, by their IDs. If not specified, the title field will be returned.
Example: fields[]=123&fields[]=456&fields[]=789 or fields=123,456,789






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
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items
```

**Response schema (Status: 200):**

Same response schema as [List items for an organization owned project](#list-items-for-an-organization-owned-project).





## Add item to user owned project

```
POST /users/{username}/projectsV2/{project_number}/items
```

Add an issue or pull request item to the specified user owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`project_number`** (integer) (required)
  The project's number.






### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Add an issue using its unique ID

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items \
  -d '{
  "type": "Issue",
  "id": 3
}'
```

**Response schema (Status: 201):**

Same response schema as [Add item to organization owned project](#add-item-to-organization-owned-project).



#### Add a pull request using its unique ID

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items \
  -d '{
  "type": "PullRequest",
  "id": 3
}'
```

**Response schema (Status: 201):**

Same response schema as [Add item to organization owned project](#add-item-to-organization-owned-project).



#### Add an issue using repository owner, name, and issue number

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items \
  -d '{
  "type": "Issue",
  "owner": "octocat",
  "repo": "hello-world",
  "number": 42
}'
```

**Response schema (Status: 201):**

Same response schema as [Add item to organization owned project](#add-item-to-organization-owned-project).



#### Add a pull request using repository owner, name, and PR number

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items \
  -d '{
  "type": "PullRequest",
  "owner": "octocat",
  "repo": "hello-world",
  "number": 123
}'
```

**Response schema (Status: 201):**

Same response schema as [Add item to organization owned project](#add-item-to-organization-owned-project).





## Get an item for a user owned project

```
GET /users/{username}/projectsV2/{project_number}/items/{item_id}
```

Get a specific item from a user-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`item_id`** (integer) (required)
  The unique identifier of the project item.

- **`fields`** (string)
  Limit results to specific fields, by their IDs. If not specified, the title field will be returned.
Example: fields[]=123&fields[]=456&fields[]=789 or fields=123,456,789






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
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items/ITEM_ID
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).





## Update project item for user

```
PATCH /users/{username}/projectsV2/{project_number}/items/{item_id}
```

Update a specific item in a user-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`item_id`** (integer) (required)
  The unique identifier of the project item.




#### Body parameters

- **`fields`** (array of objects) (required)
  A list of field updates to apply.
  - **`id`** (integer) (required)
    The ID of the project field to update.
  - **`value`** (null or string or number) (required)
    The new value for the field:

For text, number, and date fields, provide the new value directly.
For single select and iteration fields, provide the ID of the option or iteration.
To clear the field, set this to null.





### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Update a text field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 123,
      "value": "Updated text value"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).



#### Update a number field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 456,
      "value": 42.5
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).



#### Update a date field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 789,
      "value": "2023-10-05"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).



#### Update a single select field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 789,
      "value": "47fc9ee4"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).



#### Update an iteration field

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items/ITEM_ID \
  -d '{
  "fields": [
    {
      "id": 1011,
      "value": "866ee5b8"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an item for an organization owned project](#get-an-item-for-an-organization-owned-project).





## Delete project item for user

```
DELETE /users/{username}/projectsV2/{project_number}/items/{item_id}
```

Delete a specific item from a user-owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`item_id`** (integer) (required)
  The unique identifier of the project item.






### HTTP response status codes


- **204** - No Content


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/items/ITEM_ID
```

**Response schema (Status: 204):**





## List items for a user project view

```
GET /users/{username}/projectsV2/{project_number}/views/{view_number}/items
```

List items in a user project with the saved view's filter applied.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`project_number`** (integer) (required)
  The project's number.

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`view_number`** (integer) (required)
  The number that identifies the project view.

- **`fields`** (string)
  Limit results to specific fields, by their IDs. If not specified, the
title field will be returned.
Example: fields[]=123&fields[]=456&fields[]=789 or fields=123,456,789

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






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
  https://api.github.com/users/USERNAME/projectsV2/PROJECT_NUMBER/views/VIEW_NUMBER/items
```

**Response schema (Status: 200):**

Same response schema as [List items for an organization owned project](#list-items-for-an-organization-owned-project).