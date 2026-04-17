# REST API endpoints for events

Use the REST API to interact with GitHub events.

## About GitHub events

GitHub events power the various activity streams on the site.

You can use the REST API to return different types of events triggered by activity on GitHub. For more information about the specific events that you can receive, see [GitHub event types](/en/webhooks-and-events/events/github-event-types). Endpoints for repository issues are also available. For more information, see [REST API endpoints for issue events](/en/rest/issues/events).

Events are optimized for polling with the "ETag" header. If no new events have been triggered, you will see a "304 Not Modified" response, and your current rate limit will be untouched. There is also an "X-Poll-Interval" header that specifies how often (in seconds) you are allowed to poll. In times of high server load, the time may increase. Please obey the header.

```shell
$ curl -I https://api.github.com/users/tater/events
> HTTP/2 200
> X-Poll-Interval: 60
> ETag: "a18c3bded88eb5dbb5c849a489412bf3"

# The quotes around the ETag value are important
$ curl -I https://api.github.com/users/tater/events \
$    -H 'If-None-Match: "a18c3bded88eb5dbb5c849a489412bf3"'
> HTTP/2 304
> X-Poll-Interval: 60
```

The timeline will include up to 300 events. Only events created within the past 30 days will be included. Events older than 30 days will not be included (even if the total number of events in the timeline is less than 300).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List public events

```
GET /events
```

Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `15`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/events
```

**Response schema (Status: 200):**

Array of `Event`:

* `id`: required, string
* `type`: required, string or null
* `actor`: required, `Actor`:
  * `id`: required, integer
  * `login`: required, string
  * `display_login`: string
  * `gravatar_id`: required, string or null
  * `url`: required, string, format: uri
  * `avatar_url`: required, string, format: uri
* `repo`: required, object:
  * `id`: required, integer
  * `name`: required, string
  * `url`: required, string, format: uri
* `org`: `Actor`:
  * `id`: required, integer
  * `login`: required, string
  * `display_login`: string
  * `gravatar_id`: required, string or null
  * `url`: required, string, format: uri
  * `avatar_url`: required, string, format: uri
* `payload`: required, one of:
  * **CreateEvent**
    * `ref`: required, string
    * `ref_type`: required, string
    * `full_ref`: required, string
    * `master_branch`: required, string
    * `description`: string or null
    * `pusher_type`: required, string
  * **DeleteEvent**
    * `ref`: required, string
    * `ref_type`: required, string
    * `full_ref`: required, string
    * `pusher_type`: required, string
  * **DiscussionEvent**
    * `action`: required, string
    * `discussion`: required, `Discussion`:
      * `active_lock_reason`: required, string or null
      * `answer_chosen_at`: required, string or null
      * `answer_chosen_by`: required, `User`:
        * `avatar_url`: string, format: uri
        * `deleted`: boolean
        * `email`: string or null
        * `events_url`: string, format: uri-template
        * `followers_url`: string, format: uri
        * `following_url`: string, format: uri-template
        * `gists_url`: string, format: uri-template
        * `gravatar_id`: string
        * `html_url`: string, format: uri
        * `id`: required, integer
        * `login`: required, string
        * `name`: string
        * `node_id`: string
        * `organizations_url`: string, format: uri
        * `received_events_url`: string, format: uri
        * `repos_url`: string, format: uri
        * `site_admin`: boolean
        * `starred_url`: string, format: uri-template
        * `subscriptions_url`: string, format: uri
        * `type`: string, enum: `Bot`, `User`, `Organization`
        * `url`: string, format: uri
        * `user_view_type`: string
      * `answer_html_url`: required, string or null
      * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
      * `body`: required, string
      * `category`: required, object:
        * `created_at`: required, string, format: date-time
        * `description`: required, string
        * `emoji`: required, string
        * `id`: required, integer
        * `is_answerable`: required, boolean
        * `name`: required, string
        * `node_id`: string
        * `repository_id`: required, integer
        * `slug`: required, string
        * `updated_at`: required, string
      * `comments`: required, integer
      * `created_at`: required, string, format: date-time
      * `html_url`: required, string
      * `id`: required, integer
      * `locked`: required, boolean
      * `node_id`: required, string
      * `number`: required, integer
      * `reactions`: `Reactions`:
        * `+1`: required, integer
        * `-1`: required, integer
        * `confused`: required, integer
        * `eyes`: required, integer
        * `heart`: required, integer
        * `hooray`: required, integer
        * `laugh`: required, integer
        * `rocket`: required, integer
        * `total_count`: required, integer
        * `url`: required, string, format: uri
      * `repository_url`: required, string
      * `state`: required, string, enum: `open`, `closed`, `locked`, `converting`, `transferring`
      * `state_reason`: required, string or null, enum: `resolved`, `outdated`, `duplicate`, `reopened`, `null`
      * `timeline_url`: string
      * `title`: required, string
      * `updated_at`: required, string, format: date-time
      * `user`: required, `User`:
        * `avatar_url`: string, format: uri
        * `deleted`: boolean
        * `email`: string or null
        * `events_url`: string, format: uri-template
        * `followers_url`: string, format: uri
        * `following_url`: string, format: uri-template
        * `gists_url`: string, format: uri-template
        * `gravatar_id`: string
        * `html_url`: string, format: uri
        * `id`: required, integer, format: int64
        * `login`: required, string
        * `name`: string
        * `node_id`: string
        * `organizations_url`: string, format: uri
        * `received_events_url`: string, format: uri
        * `repos_url`: string, format: uri
        * `site_admin`: boolean
        * `starred_url`: string, format: uri-template
        * `subscriptions_url`: string, format: uri
        * `type`: string, enum: `Bot`, `User`, `Organization`
        * `url`: string, format: uri
        * `user_view_type`: string
      * `labels`: array of `Label`:
        * `id`: required, integer, format: int64
        * `node_id`: required, string
        * `url`: required, string, format: uri
        * `name`: required, string
        * `description`: required, string or null
        * `color`: required, string
        * `default`: required, boolean
  * **IssuesEvent**
    * `action`: required, string
    * `issue`: required, `Issue`:
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
        * `forks`: required, integer
        * `permissions`: object
        * `owner`: required, object
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
        * `code_search_index_status`: object
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
          * `created_at`: required, string, format: date-time
          * `updated_at`: required, string, format: date-time
          * `issue_url`: required, string, format: uri
          * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
          * `performed_via_github_app`: any of:
            * **null**
            * **GitHub app**
          * `reactions`: object
          * `pin`: any of:
            * **null**
            * **Pinned Issue Comment**
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
        * `single_select_option`: object or null
    * `assignee`: `Simple User`:
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
    * `label`: `Label`:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `url`: required, string, format: uri
      * `name`: required, string
      * `description`: required, string or null
      * `color`: required, string
      * `default`: required, boolean
    * `labels`: array of `Label`:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `url`: required, string, format: uri
      * `name`: required, string
      * `description`: required, string or null
      * `color`: required, string
      * `default`: required, boolean
  * **IssueCommentEvent**
    * `action`: required, string
    * `issue`: required, `Issue`:
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
        * `forks`: required, integer
        * `permissions`: object
        * `owner`: required, object
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
        * `code_search_index_status`: object
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
          * `created_at`: required, string, format: date-time
          * `updated_at`: required, string, format: date-time
          * `issue_url`: required, string, format: uri
          * `author_association`: string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`
          * `performed_via_github_app`: any of:
            * **null**
            * **GitHub app**
          * `reactions`: object
          * `pin`: any of:
            * **null**
            * **Pinned Issue Comment**
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
        * `single_select_option`: object or null
    * `comment`: required, `Issue Comment`:
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
  * **ForkEvent**
    * `action`: required, string
    * `forkee`: required, object:
      * `id`: integer
      * `node_id`: string
      * `name`: string
      * `full_name`: string
      * `private`: boolean
      * `owner`: `Simple User`:
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
      * `html_url`: string
      * `description`: string or null
      * `fork`: boolean
      * `url`: string
      * `forks_url`: string
      * `keys_url`: string
      * `collaborators_url`: string
      * `teams_url`: string
      * `hooks_url`: string
      * `issue_events_url`: string
      * `events_url`: string
      * `assignees_url`: string
      * `branches_url`: string
      * `tags_url`: string
      * `blobs_url`: string
      * `git_tags_url`: string
      * `git_refs_url`: string
      * `trees_url`: string
      * `statuses_url`: string
      * `languages_url`: string
      * `stargazers_url`: string
      * `contributors_url`: string
      * `subscribers_url`: string
      * `subscription_url`: string
      * `commits_url`: string
      * `git_commits_url`: string
      * `comments_url`: string
      * `issue_comment_url`: string
      * `contents_url`: string
      * `compare_url`: string
      * `merges_url`: string
      * `archive_url`: string
      * `downloads_url`: string
      * `issues_url`: string
      * `pulls_url`: string
      * `milestones_url`: string
      * `notifications_url`: string
      * `labels_url`: string
      * `releases_url`: string
      * `deployments_url`: string
      * `created_at`: string or null, format: date-time
      * `updated_at`: string or null, format: date-time
      * `pushed_at`: string or null, format: date-time
      * `git_url`: string
      * `ssh_url`: string
      * `clone_url`: string
      * `svn_url`: string
      * `homepage`: string or null
      * `size`: integer
      * `stargazers_count`: integer
      * `watchers_count`: integer
      * `language`: string or null
      * `has_issues`: boolean
      * `has_projects`: boolean
      * `has_downloads`: boolean
      * `has_wiki`: boolean
      * `has_pages`: boolean
      * `has_discussions`: boolean
      * `has_pull_requests`: boolean
      * `pull_request_creation_policy`: string, enum: `all`, `collaborators_only`
      * `forks_count`: integer
      * `mirror_url`: string or null
      * `archived`: boolean
      * `disabled`: boolean
      * `open_issues_count`: integer
      * `license`: any of:
        * **null**
        * **License Simple**
          * `key`: required, string
          * `name`: required, string
          * `url`: required, string or null, format: uri
          * `spdx_id`: required, string or null
          * `node_id`: required, string
          * `html_url`: string, format: uri
      * `allow_forking`: boolean
      * `is_template`: boolean
      * `web_commit_signoff_required`: boolean
      * `topics`: array of string
      * `visibility`: string
      * `forks`: integer
      * `open_issues`: integer
      * `watchers`: integer
      * `default_branch`: string
      * `public`: boolean
  * **GollumEvent**
    * `pages`: required, array of objects:
      * `page_name`: string or null
      * `title`: string or null
      * `summary`: string or null
      * `action`: string
      * `sha`: string
      * `html_url`: string
  * **MemberEvent**
    * `action`: required, string
    * `member`: required, `Simple User`:
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
  * **PublicEvent**
  * **PushEvent**
    * `repository_id`: required, integer
    * `push_id`: required, integer
    * `ref`: required, string
    * `head`: required, string
    * `before`: required, string
  * **PullRequestEvent**
    * `action`: required, string
    * `number`: required, integer
    * `pull_request`: required, `Pull Request Minimal`:
      * `id`: required, integer, format: int64
      * `number`: required, integer
      * `url`: required, string
      * `head`: required, object:
        * `ref`: required, string
        * `sha`: required, string
        * `repo`: required, object
      * `base`: required, object:
        * `ref`: required, string
        * `sha`: required, string
        * `repo`: required, object
    * `assignee`: `Simple User`:
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
    * `label`: `Label`:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `url`: required, string, format: uri
      * `name`: required, string
      * `description`: required, string or null
      * `color`: required, string
      * `default`: required, boolean
    * `labels`: array of `Label`:
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `url`: required, string, format: uri
      * `name`: required, string
      * `description`: required, string or null
      * `color`: required, string
      * `default`: required, boolean
  * **PullRequestReviewCommentEvent**
    * `action`: required, string
    * `pull_request`: required, `Pull Request Minimal`:
      * `id`: required, integer, format: int64
      * `number`: required, integer
      * `url`: required, string
      * `head`: required, object:
        * `ref`: required, string
        * `sha`: required, string
        * `repo`: required, object
      * `base`: required, object:
        * `ref`: required, string
        * `sha`: required, string
        * `repo`: required, object
    * `comment`: required, object:
      * `id`: required, integer
      * `node_id`: required, string
      * `url`: required, string, format: uri
      * `pull_request_review_id`: required, integer or null
      * `diff_hunk`: required, string
      * `path`: required, string
      * `position`: required, integer or null
      * `original_position`: required, integer
      * `subject_type`: string or null
      * `commit_id`: required, string
      * `user`: required, `User`:
        * `avatar_url`: string, format: uri
        * `deleted`: boolean
        * `email`: string or null
        * `events_url`: string, format: uri-template
        * `followers_url`: string, format: uri
        * `following_url`: string, format: uri-template
        * `gists_url`: string, format: uri-template
        * `gravatar_id`: string
        * `html_url`: string, format: uri
        * `id`: integer, format: int64
        * `login`: string
        * `name`: string
        * `node_id`: string
        * `organizations_url`: string, format: uri
        * `received_events_url`: string, format: uri
        * `repos_url`: string, format: uri
        * `site_admin`: boolean
        * `starred_url`: string, format: uri-template
        * `subscriptions_url`: string, format: uri
        * `type`: string, enum: `Bot`, `User`, `Organization`
        * `url`: string, format: uri
        * `user_view_type`: string
      * `body`: required, string
      * `created_at`: required, string, format: date-time
      * `updated_at`: required, string, format: date-time
      * `html_url`: required, string, format: uri
      * `pull_request_url`: required, string, format: uri
      * `_links`: required, object:
        * `html`: required, object
        * `pull_request`: required, object
        * `self`: required, object
      * `original_commit_id`: required, string
      * `reactions`: required, `Reactions`:
        * `+1`: integer
        * `-1`: integer
        * `confused`: integer
        * `eyes`: integer
        * `heart`: integer
        * `hooray`: integer
        * `laugh`: integer
        * `rocket`: integer
        * `total_count`: integer
        * `url`: string, format: uri
      * `in_reply_to_id`: integer
  * **PullRequestReviewEvent**
    * `action`: required, string
    * `review`: required, object:
      * `id`: integer
      * `node_id`: string
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
      * `body`: string
      * `commit_id`: string
      * `submitted_at`: string or null
      * `state`: string
      * `html_url`: string, format: uri
      * `pull_request_url`: string, format: uri
      * `_links`: object:
        * `html`: required, object
        * `pull_request`: required, object
      * `updated_at`: string
    * `pull_request`: required, `Pull Request Minimal`:
      * `id`: required, integer, format: int64
      * `number`: required, integer
      * `url`: required, string
      * `head`: required, object:
        * `ref`: required, string
        * `sha`: required, string
        * `repo`: required, object
      * `base`: required, object:
        * `ref`: required, string
        * `sha`: required, string
        * `repo`: required, object
  * **CommitCommentEvent**
    * `action`: required, string
    * `comment`: required, object:
      * `html_url`: string, format: uri
      * `url`: string, format: uri
      * `id`: integer
      * `node_id`: string
      * `body`: string
      * `path`: string or null
      * `position`: integer or null
      * `line`: integer or null
      * `commit_id`: string
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
      * `created_at`: string, format: date-time
      * `updated_at`: string, format: date-time
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
  * **ReleaseEvent**
    * `action`: required, string
    * `release`: required, all of:
      * **Release**
        * `url`: required, string, format: uri
        * `html_url`: required, string, format: uri
        * `assets_url`: required, string, format: uri
        * `upload_url`: required, string
        * `tarball_url`: required, string or null, format: uri
        * `zipball_url`: required, string or null, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `tag_name`: required, string
        * `target_commitish`: required, string
        * `name`: required, string or null
        * `body`: string or null
        * `draft`: required, boolean
        * `prerelease`: required, boolean
        * `immutable`: boolean
        * `created_at`: required, string, format: date-time
        * `published_at`: required, string or null, format: date-time
        * `updated_at`: string or null, format: date-time
        * `author`: required, `Simple User`:
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
        * `assets`: required, array of `Release Asset`:
          * `url`: required, string, format: uri
          * `browser_download_url`: required, string, format: uri
          * `id`: required, integer
          * `node_id`: required, string
          * `name`: required, string
          * `label`: required, string or null
          * `state`: required, string, enum: `uploaded`, `open`
          * `content_type`: required, string
          * `size`: required, integer
          * `digest`: required, string or null
          * `download_count`: required, integer
          * `created_at`: required, string, format: date-time
          * `updated_at`: required, string, format: date-time
          * `uploader`: required, any of:
            * **null**
            * **Simple User**
        * `body_html`: string
        * `body_text`: string
        * `mentions_count`: integer
        * `discussion_url`: string, format: uri
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
      * **object**
        * `is_short_description_html_truncated`: boolean
        * `short_description_html`: string
  * **WatchEvent**
    * `action`: required, string
* `public`: required, boolean
* `created_at`: required, string or null, format: date-time

## List public events for a network of repositories

```
GET /networks/{owner}/{repo}/events
```

Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

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

* **301** - Moved permanently

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/networks/OWNER/REPO/events
```

**Response schema (Status: 200):**

Same response schema as [List public events](#list-public-events).

## List public organization events

```
GET /orgs/{org}/events
```

Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/events
```

**Response schema (Status: 200):**

Same response schema as [List public events](#list-public-events).

## List repository events

```
GET /repos/{owner}/{repo}/events
```

Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

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

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/events
```

**Response schema (Status: 200):**

Same response schema as [List public events](#list-public-events).

## List events for the authenticated user

```
GET /users/{username}/events
```

If you are authenticated as the given user, you will see your private events. Otherwise, you'll only see public events. Optional: use the fine-grained token with following permission set to view private events: "Events" user permissions (read).
Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

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
  https://api.github.com/users/USERNAME/events
```

**Response schema (Status: 200):**

Same response schema as [List public events](#list-public-events).

## List organization events for the authenticated user

```
GET /users/{username}/events/orgs/{org}
```

This is the user's organization dashboard. You must be authenticated as the user to view this.
Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/users/USERNAME/events/orgs/ORG
```

**Response schema (Status: 200):**

Same response schema as [List public events](#list-public-events).

## List public events for a user

```
GET /users/{username}/events/public
```

Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

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
  https://api.github.com/users/USERNAME/events/public
```

**Response schema (Status: 200):**

Same response schema as [List public events](#list-public-events).

## List events received by the authenticated user

```
GET /users/{username}/received_events
```

These are events that you've received by watching repositories and following users. If you are authenticated as the
given user, you will see private events. Otherwise, you'll only see public events.
Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

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
  https://api.github.com/users/USERNAME/received_events
```

**Response schema (Status: 200):**

Same response schema as [List public events](#list-public-events).

## List public events received by a user

```
GET /users/{username}/received_events/public
```

Note

This API is not built to serve real-time use cases. Depending on the time of day, event latency can be anywhere from 30s to 6h.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

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
  https://api.github.com/users/USERNAME/received_events/public
```

**Response schema (Status: 200):**

Same response schema as [List public events](#list-public-events).