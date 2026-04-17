# REST API endpoints for deploy keys

Use the REST API to create and manage deploy keys.

## About deploy keys

You can launch projects from a repository on GitHub.com to your server by using a deploy key, which is an SSH key that grants access to a single repository. GitHub attaches the public part of the key directly to your repository instead of a personal account, and the private part of the key remains on your server. For more information, see [Delivering deployments](/en/rest/guides/delivering-deployments).

Deploy keys can either be set up using the following API endpoints, or by using the GitHub web interface. To learn how to set deploy keys up in the web interface, see [Managing deploy keys](/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys).

There are a few cases when a deploy key will be deleted by other activity:

* If the deploy key is created with a personal access token, deleting the personal access token will also delete the deploy key. Regenerating the personal access token will not delete the deploy key.
* If the deploy key is created with an OAuth app token, revoking the token will also delete the deploy key.

Conversely, these activities will not delete a deploy key:

* If the deploy key is created with a GitHub App user access token, revoking the token will not delete the deploy key.
* If the deploy key is created with a GitHub App installation access token, uninstalling or deleting the app will not delete the deploy key.
* If the deploy key is created with a personal access token, regenerating the personal access token will not delete the deploy key.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List deploy keys

```
GET /repos/{owner}/{repo}/keys
```

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
  https://api.github.com/repos/OWNER/REPO/keys
```

**Response schema (Status: 200):**

Array of `Deploy Key`:

* `id`: required, integer
* `key`: required, string
* `url`: required, string
* `title`: required, string
* `verified`: required, boolean
* `created_at`: required, string
* `read_only`: required, boolean
* `added_by`: string or null
* `last_used`: string or null, format: date-time
* `enabled`: boolean

## Create a deploy key

```
POST /repos/{owner}/{repo}/keys
```

You can create a read-only deploy key.

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

* **`title`** (string)
  A name for the key.

* **`key`** (string) (required)
  The contents of the key.

* **`read_only`** (boolean)
  If true, the key will only be able to read repository contents. Otherwise, the key will be able to read and write.
  Deploy keys with write access can perform the same actions as an organization member with admin access, or a collaborator on a personal repository. For more information, see "Repository permission levels for an organization" and "Permission levels for a user account repository."

### HTTP response status codes

* **201** - Created

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/keys \
  -d '{
  "title": "octocat@octomac",
  "key": "ssh-rsa AAA...",
  "read_only": true
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `key`: required, string
* `url`: required, string
* `title`: required, string
* `verified`: required, boolean
* `created_at`: required, string
* `read_only`: required, boolean
* `added_by`: string or null
* `last_used`: string or null, format: date-time
* `enabled`: boolean

## Get a deploy key

```
GET /repos/{owner}/{repo}/keys/{key_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`key_id`** (integer) (required)
  The unique identifier of the key.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/keys/KEY_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a deploy key](#create-a-deploy-key).

## Delete a deploy key

```
DELETE /repos/{owner}/{repo}/keys/{key_id}
```

Deploy keys are immutable. If you need to update a key, remove the key and create a new one instead.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`key_id`** (integer) (required)
  The unique identifier of the key.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/keys/KEY_ID
```

**Response schema (Status: 204):**