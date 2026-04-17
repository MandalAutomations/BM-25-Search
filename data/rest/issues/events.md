# REST API endpoints for issue events

Use the REST API to retrieve events triggered by activity in issues and pull requests.

## About events

You can use the REST API to view different types of events triggered by activity in issues and pull requests. For more information about the specific events that you can receive, see [Issue event types](/en/webhooks-and-events/events/issue-event-types). To view GitHub activity outside of issues and pull requests, you can use the [Events](/en/webhooks-and-events/events/github-event-types) endpoints.

Every pull request is an issue, but not every issue is a pull request. For this reason, "shared" actions for both features, like managing assignees, labels, and milestones, are provided within the Issues endpoints.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List issue events for a repository

```
GET /repos/{owner}/{repo}/issues/events
```

Lists events for a repository.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/issues/events
```

**Response schema (Status: 200):**

Array of `Issue Event`:

* `id`: required, integer, format: int64
* `node_id`: required, string
* `url`: required, string, format: uri
* `actor`: required, any of:
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
* `event`: required, string
* `commit_id`: required, string or null
* `commit_url`: required, string or null
* `created_at`: required, string, format: date-time
* `issue`: any of:
  * **null**
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
* `label`: `Issue Event Label`:
  * `name`: required, string or null
  * `color`: required, string or null
* `assignee`: any of:
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
* `assigner`: any of:
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
* `review_requester`: any of:
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
* `requested_reviewer`: any of:
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
* `requested_team`: `Team`:
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
* `dismissed_review`: `Issue Event Dismissed Review`:
  * `state`: required, string
  * `review_id`: required, integer
  * `dismissal_message`: required, string or null
  * `dismissal_commit_id`: string or null
* `milestone`: `Issue Event Milestone`:
  * `title`: required, string
* `project_card`: `Issue Event Project Card`:
  * `url`: required, string, format: uri
  * `id`: required, integer
  * `project_url`: required, string, format: uri
  * `project_id`: required, integer
  * `column_name`: required, string
  * `previous_column_name`: string
* `rename`: `Issue Event Rename`:
  * `from`: required, string
  * `to`: required, string
* `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
* `lock_reason`: string or null
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

## Get an issue event

```
GET /repos/{owner}/{repo}/issues/events/{event_id}
```

Gets a single event by the event id.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`event_id`** (integer) (required)

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

* **410** - Gone

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/issues/events/EVENT_ID
```

**Response schema (Status: 200):**

* `id`: required, integer, format: int64
* `node_id`: required, string
* `url`: required, string, format: uri
* `actor`: required, any of:
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
* `event`: required, string
* `commit_id`: required, string or null
* `commit_url`: required, string or null
* `created_at`: required, string, format: date-time
* `issue`: any of:
  * **null**
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
* `label`: `Issue Event Label`:
  * `name`: required, string or null
  * `color`: required, string or null
* `assignee`: any of:
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
* `assigner`: any of:
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
* `review_requester`: any of:
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
* `requested_reviewer`: any of:
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
* `requested_team`: `Team`:
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
* `dismissed_review`: `Issue Event Dismissed Review`:
  * `state`: required, string
  * `review_id`: required, integer
  * `dismissal_message`: required, string or null
  * `dismissal_commit_id`: string or null
* `milestone`: `Issue Event Milestone`:
  * `title`: required, string
* `project_card`: `Issue Event Project Card`:
  * `url`: required, string, format: uri
  * `id`: required, integer
  * `project_url`: required, string, format: uri
  * `project_id`: required, integer
  * `column_name`: required, string
  * `previous_column_name`: string
* `rename`: `Issue Event Rename`:
  * `from`: required, string
  * `to`: required, string
* `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
* `lock_reason`: string or null
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

## List issue events

```
GET /repos/{owner}/{repo}/issues/{issue_number}/events
```

Lists all events for an issue.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`issue_number`** (integer) (required)
  The number that identifies the issue.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **410** - Gone

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/issues/ISSUE_NUMBER/events
```

**Response schema (Status: 200):**

Array of `Issue Event for Issue` objects: any of:

* **Labeled Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `label`: required, object:
    * `name`: required, string
    * `color`: required, string
* **Unlabeled Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `label`: required, object:
    * `name`: required, string
    * `color`: required, string
* **Assigned Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, `GitHub app`:
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
  * `assignee`: required, `Simple User`:
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
  * `assigner`: required, `Simple User`:
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
* **Unassigned Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `assignee`: required, `Simple User`:
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
  * `assigner`: required, `Simple User`:
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
* **Milestoned Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `milestone`: required, object:
    * `title`: required, string
* **Demilestoned Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `milestone`: required, object:
    * `title`: required, string
* **Renamed Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `rename`: required, object:
    * `from`: required, string
    * `to`: required, string
* **Review Requested Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `review_requester`: required, `Simple User`:
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
  * `requested_team`: `Team`:
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
  * `requested_reviewer`: `Simple User`:
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
* **Review Request Removed Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `review_requester`: required, `Simple User`:
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
  * `requested_team`: `Team`:
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
  * `requested_reviewer`: `Simple User`:
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
* **Review Dismissed Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `dismissed_review`: required, object:
    * `state`: required, string
    * `review_id`: required, integer
    * `dismissal_message`: required, string or null
    * `dismissal_commit_id`: string
* **Locked Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `lock_reason`: required, string or null
* **Added to Project Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `project_card`: object:
    * `id`: required, integer
    * `url`: required, string, format: uri
    * `project_id`: required, integer
    * `project_url`: required, string, format: uri
    * `column_name`: required, string
    * `previous_column_name`: string
* **Moved Column in Project Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `project_card`: object:
    * `id`: required, integer
    * `url`: required, string, format: uri
    * `project_id`: required, integer
    * `project_url`: required, string, format: uri
    * `column_name`: required, string
    * `previous_column_name`: string
* **Removed from Project Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, any of:
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
  * `project_card`: object:
    * `id`: required, integer
    * `url`: required, string, format: uri
    * `project_id`: required, integer
    * `project_url`: required, string, format: uri
    * `column_name`: required, string
    * `previous_column_name`: string
* **Converted Note to Issue Issue Event**
  * `id`: required, integer
  * `node_id`: required, string
  * `url`: required, string
  * `actor`: required, `Simple User`:
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
  * `event`: required, string
  * `commit_id`: required, string or null
  * `commit_url`: required, string or null
  * `created_at`: required, string
  * `performed_via_github_app`: required, `GitHub app`:
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
  * `project_card`: object:
    * `id`: required, integer
    * `url`: required, string, format: uri
    * `project_id`: required, integer
    * `project_url`: required, string, format: uri
    * `column_name`: required, string
    * `previous_column_name`: string