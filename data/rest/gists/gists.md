# REST API endpoints for gists

Use the REST API to list, create, update and delete the public gists on GitHub.

## About gists

You can use the REST API to view and modify gists. For more information about gists, see [Editing and sharing content with gists](/en/get-started/writing-on-github/editing-and-sharing-content-with-gists).

### Authentication

You can read public gists  anonymously, but you must be signed into GitHub to create gists. To read or write gists on a user's behalf, you need the gist OAuth scope and a token. For more information, see [Scopes for OAuth apps](/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps).

<!-- When an OAuth client does not have the gists scope, the API will return a 404 "Not Found" response regardless of the validity of the credentials. The API will return a 401 "Bad credentials" response if the gists scope was given to the application but the credentials are invalid. -->

### Truncation

The API provides up to one megabyte of content for each file in the gist. Each file returned for a gist through the API has a key called `truncated`. If `truncated` is `true`, the file is too large and only a portion of the contents were returned in `content`.

If you need the full contents of the file, you can make a `GET` request to the URL specified by `raw_url`. Be aware that for files larger than ten megabytes, you'll need to clone the gist via the URL provided by `git_pull_url`.

In addition to a specific file's contents being truncated, the entire files list may be truncated if the total number exceeds 300 files. If the top level `truncated` key is `true`, only the first 300 files have been returned in the files list. If you need to fetch all of the gist's files, you'll need to clone the gist via the URL provided by `git_pull_url`.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List gists for the authenticated user

```
GET /gists
```

Lists the authenticated user's gists or if called anonymously, this endpoint returns all public gists:

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`since`** (string)
  Only show results that were last updated after the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gists
```

**Response schema (Status: 200):**

Array of `Base Gist`:

* `url`: required, string, format: uri
* `forks_url`: required, string, format: uri
* `commits_url`: required, string, format: uri
* `id`: required, string
* `node_id`: required, string
* `git_pull_url`: required, string, format: uri
* `git_push_url`: required, string, format: uri
* `html_url`: required, string, format: uri
* `files`: required, object, additional properties: object
* `public`: required, boolean
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `description`: required, string or null
* `comments`: required, integer
* `comments_enabled`: boolean
* `comments_url`: required, string, format: uri
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
* `truncated`: boolean

## Create a gist

```
POST /gists
```

Allows you to add a new gist with one or more files.
Note

Don't name your files "gistfile" with a numerical suffix. This is the format of the automatic naming scheme that Gist uses internally.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`description`** (string)
  Description of the gist

* **`files`** (object) (required)
  Names and content for the files that make up the gist
  * **`key`** (object)
    A user-defined key to represent an item in files.
    * **`content`** (string) (required)
      Content of the file

* **`public`** (boolean or string)
  Flag indicating whether the gist is public

### HTTP response status codes

* **201** - Created

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Creating a gist

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/gists \
  -d '{
  "description": "Example of a gist",
  "public": false,
  "files": {
    "README.md": {
      "content": "Hello World"
    }
  }
}'
```

**Response schema (Status: 201):**

* `fork_of`: `Gist`:
  * `url`: required, string, format: uri
  * `forks_url`: required, string, format: uri
  * `commits_url`: required, string, format: uri
  * `id`: required, string
  * `node_id`: required, string
  * `git_pull_url`: required, string, format: uri
  * `git_push_url`: required, string, format: uri
  * `html_url`: required, string, format: uri
  * `files`: required, object, additional properties: object
  * `public`: required, boolean
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `description`: required, string or null
  * `comments`: required, integer
  * `comments_enabled`: boolean
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
  * `comments_url`: required, string, format: uri
  * `owner`: any of:
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
  * `truncated`: boolean
  * `forks`: array of object
  * `history`: array of object
* `url`: string
* `forks_url`: string
* `commits_url`: string
* `id`: string
* `node_id`: string
* `git_pull_url`: string
* `git_push_url`: string
* `html_url`: string
* `files`: object, additional properties: object or null
* `public`: boolean
* `created_at`: string
* `updated_at`: string
* `description`: string or null
* `comments`: integer
* `comments_enabled`: boolean
* `user`: string or null
* `comments_url`: string
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
* `truncated`: boolean

## List public gists

```
GET /gists/public
```

List public gists sorted by most recently updated to least recently updated.
Note: With pagination, you can fetch up to 3000 gists. For example, you can fetch 100 pages with 30 gists per page or 30 pages with 100 gists per page.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`since`** (string)
  Only show results that were last updated after the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gists/public
```

**Response schema (Status: 200):**

Same response schema as [List gists for the authenticated user](#list-gists-for-the-authenticated-user).

## List starred gists

```
GET /gists/starred
```

List the authenticated user's starred gists:

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`since`** (string)
  Only show results that were last updated after the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gists/starred
```

**Response schema (Status: 200):**

Same response schema as [List gists for the authenticated user](#list-gists-for-the-authenticated-user).

## Get a gist

```
GET /gists/{gist_id}
```

Gets a specified gist.
This endpoint supports the following custom media types. For more information, see "Media types."

application/vnd.github.raw+json: Returns the raw markdown. This is the default if you do not pass any specific media type.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden Gist

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gists/GIST_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a gist](#create-a-gist).

## Update a gist

```
PATCH /gists/{gist_id}
```

Allows you to update a gist's description and to update, delete, or rename gist files. Files
from the previous version of the gist that aren't explicitly changed during an edit
are unchanged.
At least one of description or files is required.
This endpoint supports the following custom media types. For more information, see "Media types."

application/vnd.github.raw+json: Returns the raw markdown. This is the default if you do not pass any specific media type.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

#### Body parameters

* **`description`** (string)
  The description of the gist.

* **`files`** (object)
  The gist files to be updated, renamed, or deleted. Each key must match the current filename
  (including extension) of the targeted gist file. For example: hello.py.
  To delete a file, set the whole file to null. For example: hello.py : null. The file will also be
  deleted if the specified object does not contain at least one of content or filename.
  * **`key`** (object)
    A user-defined key to represent an item in files.
    * **`content`** (string)
      The new content of the file.
    * **`filename`** (string or null)
      The new filename for the file.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Updating a gist

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/gists/GIST_ID \
  -d '{
  "description": "An updated gist description",
  "files": {
    "README.md": {
      "content": "Hello World from GitHub"
    }
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a gist](#create-a-gist).

#### Deleting a gist file

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/gists/GIST_ID \
  -d '{
  "files": {
    "hello.py": null
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a gist](#create-a-gist).

#### Renaming a gist file

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/gists/GIST_ID \
  -d '{
  "files": {
    "hello.py": {
      "filename": "goodbye.py"
    }
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a gist](#create-a-gist).

## Delete a gist

```
DELETE /gists/{gist_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/gists/GIST_ID
```

**Response schema (Status: 204):**

## List gist commits

```
GET /gists/{gist_id}/commits
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gists/GIST_ID/commits
```

**Response schema (Status: 200):**

Array of `Gist Commit`:

* `url`: required, string, format: uri
* `version`: required, string
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
* `change_status`: required, object:
  * `total`: integer
  * `additions`: integer
  * `deletions`: integer
* `committed_at`: required, string, format: date-time

## List gist forks

```
GET /gists/{gist_id}/forks
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gists/GIST_ID/forks
```

**Response schema (Status: 200):**

Array of `Gist Simple`:

* `fork_of`: `Gist`:
  * `url`: required, string, format: uri
  * `forks_url`: required, string, format: uri
  * `commits_url`: required, string, format: uri
  * `id`: required, string
  * `node_id`: required, string
  * `git_pull_url`: required, string, format: uri
  * `git_push_url`: required, string, format: uri
  * `html_url`: required, string, format: uri
  * `files`: required, object, additional properties: object
  * `public`: required, boolean
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `description`: required, string or null
  * `comments`: required, integer
  * `comments_enabled`: boolean
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
  * `comments_url`: required, string, format: uri
  * `owner`: any of:
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
  * `truncated`: boolean
  * `forks`: array of object
  * `history`: array of object
* `url`: string
* `forks_url`: string
* `commits_url`: string
* `id`: string
* `node_id`: string
* `git_pull_url`: string
* `git_push_url`: string
* `html_url`: string
* `files`: object, additional properties: object or null
* `public`: boolean
* `created_at`: string
* `updated_at`: string
* `description`: string or null
* `comments`: integer
* `comments_enabled`: boolean
* `user`: string or null
* `comments_url`: string
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
* `truncated`: boolean

## Fork a gist

```
POST /gists/{gist_id}/forks
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

### HTTP response status codes

* **201** - Created

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/gists/GIST_ID/forks
```

**Response schema (Status: 201):**

* `url`: required, string, format: uri
* `forks_url`: required, string, format: uri
* `commits_url`: required, string, format: uri
* `id`: required, string
* `node_id`: required, string
* `git_pull_url`: required, string, format: uri
* `git_push_url`: required, string, format: uri
* `html_url`: required, string, format: uri
* `files`: required, object, additional properties: object
* `public`: required, boolean
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `description`: required, string or null
* `comments`: required, integer
* `comments_enabled`: boolean
* `comments_url`: required, string, format: uri
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
* `truncated`: boolean

## Check if a gist is starred

```
GET /gists/{gist_id}/star
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

### HTTP response status codes

* **204** - Response if gist is starred

* **304** - Not modified

* **403** - Forbidden

* **404** - Not Found if gist is not starred

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gists/GIST_ID/star
```

**Response schema (Status: 204):**

## Star a gist

```
PUT /gists/{gist_id}/star
```

Note that you'll need to set Content-Length to zero when calling out to this endpoint. For more information, see "HTTP method."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/gists/GIST_ID/star
```

**Response schema (Status: 204):**

## Unstar a gist

```
DELETE /gists/{gist_id}/star
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/gists/GIST_ID/star
```

**Response schema (Status: 204):**

## Get a gist revision

```
GET /gists/{gist_id}/{sha}
```

Gets a specified gist revision.
This endpoint supports the following custom media types. For more information, see "Media types."

application/vnd.github.raw+json: Returns the raw markdown. This is the default if you do not pass any specific media type.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

* **`sha`** (string) (required)

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gists/GIST_ID/SHA
```

**Response schema (Status: 200):**

Same response schema as [Create a gist](#create-a-gist).

## List gists for a user

```
GET /users/{username}/gists
```

Lists public gists for the specified user:

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`since`** (string)
  Only show results that were last updated after the given time. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

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
  https://api.github.com/users/USERNAME/gists
```

**Response schema (Status: 200):**

Same response schema as [List gists for the authenticated user](#list-gists-for-the-authenticated-user).