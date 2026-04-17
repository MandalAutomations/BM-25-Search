# REST API endpoints for reactions

Use the REST API to interact with reactions on GitHub.

## About reactions

You can create and manage reactions to comments, issues, pull requests, and discussions on GitHub. When creating a reaction, the allowed values for the `content` parameter are as follows (with the corresponding emoji for reference):

<table style="width:20%">
<thead>
<tr>
<th scope="col" style="text-align:left">Content</th>
<th scope="col" style="text-align:left">Emoji</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left"><code>+1</code></td>
<td style="text-align:left">👍</td>
</tr>
<tr>
<td style="text-align:left"><code>-1</code></td>
<td style="text-align:left">👎</td>
</tr>
<tr>
<td style="text-align:left"><code>laugh</code></td>
<td style="text-align:left">😄</td>
</tr>
<tr>
<td style="text-align:left"><code>confused</code></td>
<td style="text-align:left">😕</td>
</tr>
<tr>
<td style="text-align:left"><code>heart</code></td>
<td style="text-align:left">❤️</td>
</tr>
<tr>
<td style="text-align:left"><code>hooray</code></td>
<td style="text-align:left">🎉</td>
</tr>
<tr>
<td style="text-align:left"><code>rocket</code></td>
<td style="text-align:left">🚀</td>
</tr>
<tr>
<td style="text-align:left"><code>eyes</code></td>
<td style="text-align:left">👀</td>
</tr>
</tbody>
</table>

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List reactions for a commit comment

```
GET /repos/{owner}/{repo}/comments/{comment_id}/reactions
```

List the reactions to a commit comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.

- **`content`** (string)
  Returns a single reaction type. Omit this parameter to list all reactions to a commit comment.
  Can be one of: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`

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
  https://api.github.com/repos/OWNER/REPO/comments/COMMENT_ID/reactions
```

**Response schema (Status: 200):**

Array of `Reaction`:
  * `id`: required, integer
  * `node_id`: required, string
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
  * `content`: required, string, enum: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`
  * `created_at`: required, string, format: date-time





## Create reaction for a commit comment

```
POST /repos/{owner}/{repo}/comments/{comment_id}/reactions
```

Create a reaction to a commit comment. A response with an HTTP 200 status means that you already added the reaction type to this commit comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.




#### Body parameters

- **`content`** (string) (required)
  The reaction type to add to the commit comment.
  Can be one of: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`





### HTTP response status codes


- **200** - Reaction exists


- **201** - Reaction created


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/comments/COMMENT_ID/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 200):**

* `id`: required, integer
* `node_id`: required, string
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
* `content`: required, string, enum: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`
* `created_at`: required, string, format: date-time



#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/comments/COMMENT_ID/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `node_id`: required, string
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
* `content`: required, string, enum: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`
* `created_at`: required, string, format: date-time





## Delete a commit comment reaction

```
DELETE /repos/{owner}/{repo}/comments/{comment_id}/reactions/{reaction_id}
```

Note

You can also specify a repository by repository_id using the route DELETE /repositories/:repository_id/comments/:comment_id/reactions/:reaction_id.

Delete a reaction to a commit comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.

- **`reaction_id`** (integer) (required)
  The unique identifier of the reaction.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/comments/COMMENT_ID/reactions/REACTION_ID
```

**Response schema (Status: 204):**





## List reactions for an issue comment

```
GET /repos/{owner}/{repo}/issues/comments/{comment_id}/reactions
```

List the reactions to an issue comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.

- **`content`** (string)
  Returns a single reaction type. Omit this parameter to list all reactions to an issue comment.
  Can be one of: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`

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
  https://api.github.com/repos/OWNER/REPO/issues/comments/COMMENT_ID/reactions
```

**Response schema (Status: 200):**

Same response schema as [List reactions for a commit comment](#list-reactions-for-a-commit-comment).





## Create reaction for an issue comment

```
POST /repos/{owner}/{repo}/issues/comments/{comment_id}/reactions
```

Create a reaction to an issue comment. A response with an HTTP 200 status means that you already added the reaction type to this issue comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.




#### Body parameters

- **`content`** (string) (required)
  The reaction type to add to the issue comment.
  Can be one of: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`





### HTTP response status codes


- **200** - Reaction exists


- **201** - Reaction created


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/issues/comments/COMMENT_ID/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create reaction for a commit comment](#create-reaction-for-a-commit-comment).



#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/issues/comments/COMMENT_ID/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create reaction for a commit comment](#create-reaction-for-a-commit-comment).





## Delete an issue comment reaction

```
DELETE /repos/{owner}/{repo}/issues/comments/{comment_id}/reactions/{reaction_id}
```

Note

You can also specify a repository by repository_id using the route DELETE delete /repositories/:repository_id/issues/comments/:comment_id/reactions/:reaction_id.

Delete a reaction to an issue comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.

- **`reaction_id`** (integer) (required)
  The unique identifier of the reaction.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/issues/comments/COMMENT_ID/reactions/REACTION_ID
```

**Response schema (Status: 204):**





## List reactions for an issue

```
GET /repos/{owner}/{repo}/issues/{issue_number}/reactions
```

List the reactions to an issue.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`issue_number`** (integer) (required)
  The number that identifies the issue.

- **`content`** (string)
  Returns a single reaction type. Omit this parameter to list all reactions to an issue.
  Can be one of: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **410** - Gone




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/issues/ISSUE_NUMBER/reactions
```

**Response schema (Status: 200):**

Same response schema as [List reactions for a commit comment](#list-reactions-for-a-commit-comment).





## Create reaction for an issue

```
POST /repos/{owner}/{repo}/issues/{issue_number}/reactions
```

Create a reaction to an issue. A response with an HTTP 200 status means that you already added the reaction type to this issue.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`issue_number`** (integer) (required)
  The number that identifies the issue.




#### Body parameters

- **`content`** (string) (required)
  The reaction type to add to the issue.
  Can be one of: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`





### HTTP response status codes


- **200** - OK


- **201** - Created


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/issues/ISSUE_NUMBER/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create reaction for a commit comment](#create-reaction-for-a-commit-comment).



#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/issues/ISSUE_NUMBER/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create reaction for a commit comment](#create-reaction-for-a-commit-comment).





## Delete an issue reaction

```
DELETE /repos/{owner}/{repo}/issues/{issue_number}/reactions/{reaction_id}
```

Note

You can also specify a repository by repository_id using the route DELETE /repositories/:repository_id/issues/:issue_number/reactions/:reaction_id.

Delete a reaction to an issue.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`issue_number`** (integer) (required)
  The number that identifies the issue.

- **`reaction_id`** (integer) (required)
  The unique identifier of the reaction.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/issues/ISSUE_NUMBER/reactions/REACTION_ID
```

**Response schema (Status: 204):**





## List reactions for a pull request review comment

```
GET /repos/{owner}/{repo}/pulls/comments/{comment_id}/reactions
```

List the reactions to a pull request review comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.

- **`content`** (string)
  Returns a single reaction type. Omit this parameter to list all reactions to a pull request review comment.
  Can be one of: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`

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
  https://api.github.com/repos/OWNER/REPO/pulls/comments/COMMENT_ID/reactions
```

**Response schema (Status: 200):**

Same response schema as [List reactions for a commit comment](#list-reactions-for-a-commit-comment).





## Create reaction for a pull request review comment

```
POST /repos/{owner}/{repo}/pulls/comments/{comment_id}/reactions
```

Create a reaction to a pull request review comment. A response with an HTTP 200 status means that you already added the reaction type to this pull request review comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.




#### Body parameters

- **`content`** (string) (required)
  The reaction type to add to the pull request review comment.
  Can be one of: `+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`





### HTTP response status codes


- **200** - Reaction exists


- **201** - Reaction created


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pulls/comments/COMMENT_ID/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create reaction for a commit comment](#create-reaction-for-a-commit-comment).



#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pulls/comments/COMMENT_ID/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create reaction for a commit comment](#create-reaction-for-a-commit-comment).





## Delete a pull request comment reaction

```
DELETE /repos/{owner}/{repo}/pulls/comments/{comment_id}/reactions/{reaction_id}
```

Note

You can also specify a repository by repository_id using the route DELETE /repositories/:repository_id/pulls/comments/:comment_id/reactions/:reaction_id.

Delete a reaction to a pull request review comment.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`comment_id`** (integer) (required)
  The unique identifier of the comment.

- **`reaction_id`** (integer) (required)
  The unique identifier of the reaction.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/pulls/comments/COMMENT_ID/reactions/REACTION_ID
```

**Response schema (Status: 204):**





## List reactions for a release

```
GET /repos/{owner}/{repo}/releases/{release_id}/reactions
```

List the reactions to a release.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`release_id`** (integer) (required)
  The unique identifier of the release.

- **`content`** (string)
  Returns a single reaction type. Omit this parameter to list all reactions to a release.
  Can be one of: `+1`, `laugh`, `heart`, `hooray`, `rocket`, `eyes`

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
  https://api.github.com/repos/OWNER/REPO/releases/RELEASE_ID/reactions
```

**Response schema (Status: 200):**

Same response schema as [List reactions for a commit comment](#list-reactions-for-a-commit-comment).





## Create reaction for a release

```
POST /repos/{owner}/{repo}/releases/{release_id}/reactions
```

Create a reaction to a release. A response with a Status: 200 OK means that you already added the reaction type to this release.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`release_id`** (integer) (required)
  The unique identifier of the release.




#### Body parameters

- **`content`** (string) (required)
  The reaction type to add to the release.
  Can be one of: `+1`, `laugh`, `heart`, `hooray`, `rocket`, `eyes`





### HTTP response status codes


- **200** - Reaction exists


- **201** - Reaction created


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/releases/RELEASE_ID/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create reaction for a commit comment](#create-reaction-for-a-commit-comment).



#### Example 2: Status Code 201

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/releases/RELEASE_ID/reactions \
  -d '{
  "content": "heart"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create reaction for a commit comment](#create-reaction-for-a-commit-comment).





## Delete a release reaction

```
DELETE /repos/{owner}/{repo}/releases/{release_id}/reactions/{reaction_id}
```

Note

You can also specify a repository by repository_id using the route DELETE delete /repositories/:repository_id/releases/:release_id/reactions/:reaction_id.

Delete a reaction to a release.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`release_id`** (integer) (required)
  The unique identifier of the release.

- **`reaction_id`** (integer) (required)
  The unique identifier of the reaction.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/releases/RELEASE_ID/reactions/REACTION_ID
```

**Response schema (Status: 204):**