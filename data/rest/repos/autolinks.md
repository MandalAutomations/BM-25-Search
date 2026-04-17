# REST API endpoints for repository autolinks

Use the REST API to add autolinks to external resources.

## About repository autolinks

To help streamline your workflow, you can use the REST API to add autolinks to external resources like JIRA issues and Zendesk tickets. For more information, see [Configuring autolinks to reference external resources](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/configuring-autolinks-to-reference-external-resources).

GitHub Apps require repository administration permissions with read or write access to use these endpoints.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get all autolinks of a repository

```
GET /repos/{owner}/{repo}/autolinks
```

Gets all autolinks that are configured for a repository.
Information about autolinks are only available to repository administrators.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/autolinks
```

**Response schema (Status: 200):**

Array of `Autolink reference`:

* `id`: required, integer
* `key_prefix`: required, string
* `url_template`: required, string
* `is_alphanumeric`: required, boolean
* `updated_at`: string or null, format: date-time

## Create an autolink reference for a repository

```
POST /repos/{owner}/{repo}/autolinks
```

Users with admin access to the repository can create an autolink.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`key_prefix`** (string) (required)
  This prefix appended by certain characters will generate a link any time it is found in an issue, pull request, or commit.

* **`url_template`** (string) (required)
  The URL must contain <num> for the reference number. <num> matches different characters depending on the value of is\_alphanumeric.

* **`is_alphanumeric`** (boolean)
  Whether this autolink reference matches alphanumeric characters. If true, the <num> parameter of the url\_template matches alphanumeric characters A-Z (case insensitive), 0-9, and -. If false, this autolink reference only matches numeric characters.
  Default: `true`

### HTTP response status codes

* **201** - Created

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/autolinks \
  -d '{
  "key_prefix": "TICKET-",
  "url_template": "https://example.com/TICKET?query=<num>",
  "is_alphanumeric": true
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `key_prefix`: required, string
* `url_template`: required, string
* `is_alphanumeric`: required, boolean
* `updated_at`: string or null, format: date-time

## Get an autolink reference of a repository

```
GET /repos/{owner}/{repo}/autolinks/{autolink_id}
```

This returns a single autolink reference by ID that was configured for the given repository.
Information about autolinks are only available to repository administrators.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`autolink_id`** (integer) (required)
  The unique identifier of the autolink.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/autolinks/AUTOLINK_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an autolink reference for a repository](#create-an-autolink-reference-for-a-repository).

## Delete an autolink reference from a repository

```
DELETE /repos/{owner}/{repo}/autolinks/{autolink_id}
```

This deletes a single autolink reference by ID that was configured for the given repository.
Information about autolinks are only available to repository administrators.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`autolink_id`** (integer) (required)
  The unique identifier of the autolink.

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/autolinks/AUTOLINK_ID
```

**Response schema (Status: 204):**