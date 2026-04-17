# REST API endpoints for gist comments

Use the REST API to view and modify comments on a gist.

## About gist comments

You can use the REST API to view and modify comments on a gist. For more information about gists, see [Editing and sharing content with gists](/en/get-started/writing-on-github/editing-and-sharing-content-with-gists).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List gist comments

```
GET /gists/{gist_id}/comments
```

Lists the comments on a gist.
This endpoint supports the following custom media types. For more information, see "Media types."

application/vnd.github.raw+json: Returns the raw markdown. This is the default if you do not pass any specific media type.

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
  https://api.github.com/gists/GIST_ID/comments
```

**Response schema (Status: 200):**

Array of `Gist Comment`:

* `id`: required, integer
* `node_id`: required, string
* `url`: required, string, format: uri
* `body`: required, string, maxLength: 65535
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
* `author_association`: required, string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`

## Create a gist comment

```
POST /gists/{gist_id}/comments
```

Creates a comment on a gist.
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

* **`body`** (string) (required)
  The comment text.

### HTTP response status codes

* **201** - Created

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Creating a comment in a gist

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/gists/GIST_ID/comments \
  -d '{
  "body": "This is a comment to a gist"
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `node_id`: required, string
* `url`: required, string, format: uri
* `body`: required, string, maxLength: 65535
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
* `author_association`: required, string, enum: `COLLABORATOR`, `CONTRIBUTOR`, `FIRST_TIMER`, `FIRST_TIME_CONTRIBUTOR`, `MANNEQUIN`, `MEMBER`, `NONE`, `OWNER`

## Get a gist comment

```
GET /gists/{gist_id}/comments/{comment_id}
```

Gets a comment on a gist.
This endpoint supports the following custom media types. For more information, see "Media types."

application/vnd.github.raw+json: Returns the raw markdown. This is the default if you do not pass any specific media type.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

* **`comment_id`** (integer) (required)
  The unique identifier of the comment.

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
  https://api.github.com/gists/GIST_ID/comments/COMMENT_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a gist comment](#create-a-gist-comment).

## Update a gist comment

```
PATCH /gists/{gist_id}/comments/{comment_id}
```

Updates a comment on a gist.
This endpoint supports the following custom media types. For more information, see "Media types."

application/vnd.github.raw+json: Returns the raw markdown. This is the default if you do not pass any specific media type.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

* **`comment_id`** (integer) (required)
  The unique identifier of the comment.

#### Body parameters

* **`body`** (string) (required)
  The comment text.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Updating a comment in a gist

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/gists/GIST_ID/comments/COMMENT_ID \
  -d '{
  "body": "This is an update to a comment in a gist"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a gist comment](#create-a-gist-comment).

## Delete a gist comment

```
DELETE /gists/{gist_id}/comments/{comment_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gist_id`** (string) (required)
  The unique identifier of the gist.

* **`comment_id`** (integer) (required)
  The unique identifier of the comment.

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
  https://api.github.com/gists/GIST_ID/comments/COMMENT_ID
```

**Response schema (Status: 204):**