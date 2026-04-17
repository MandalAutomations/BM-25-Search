# REST API endpoints for Git SSH keys

Use the REST API to manage Git SSH keys of authenticated users.

## About Git SSH key administration

If a request URL does not include a `{username}` parameter then the response will be for the signed-in user (and you must pass [authentication information](/en/rest/overview/authenticating-to-the-rest-api) with your request). Additional private information, such as whether a user has two-factor authentication enabled, is included when authenticated through OAuth with the `user` scope.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List public SSH keys for the authenticated user

```
GET /user/keys
```

Lists the public SSH keys for the authenticated user's GitHub account.
OAuth app tokens and personal access tokens (classic) need the read:public\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

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

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/keys
```

**Response schema (Status: 200):**

Array of `Key`:

* `key`: required, string
* `id`: required, integer, format: int64
* `url`: required, string
* `title`: required, string
* `created_at`: required, string, format: date-time
* `verified`: required, boolean
* `read_only`: required, boolean
* `last_used`: string or null, format: date-time

## Create a public SSH key for the authenticated user

```
POST /user/keys
```

Adds a public SSH key to the authenticated user's GitHub account.
OAuth app tokens and personal access tokens (classic) need the write:public\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`title`** (string)
  A descriptive name for the new key.

* **`key`** (string) (required)
  The public SSH key to add to your GitHub account.

### HTTP response status codes

* **201** - Created

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/keys \
  -d '{
  "title": "ssh-rsa AAAAB3NzaC1yc2EAAA",
  "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234"
}'
```

**Response schema (Status: 201):**

* `key`: required, string
* `id`: required, integer, format: int64
* `url`: required, string
* `title`: required, string
* `created_at`: required, string, format: date-time
* `verified`: required, boolean
* `read_only`: required, boolean
* `last_used`: string or null, format: date-time

## Get a public SSH key for the authenticated user

```
GET /user/keys/{key_id}
```

View extended details for a single public SSH key.
OAuth app tokens and personal access tokens (classic) need the read:public\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`key_id`** (integer) (required)
  The unique identifier of the key.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/keys/KEY_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a public SSH key for the authenticated user](#create-a-public-ssh-key-for-the-authenticated-user).

## Delete a public SSH key for the authenticated user

```
DELETE /user/keys/{key_id}
```

Removes a public SSH key from the authenticated user's GitHub account.
OAuth app tokens and personal access tokens (classic) need the admin:public\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`key_id`** (integer) (required)
  The unique identifier of the key.

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/keys/KEY_ID
```

**Response schema (Status: 204):**

## List public keys for a user

```
GET /users/{username}/keys
```

Lists the verified public SSH keys for a user. This is accessible by anyone.

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
  https://api.github.com/users/USERNAME/keys
```

**Response schema (Status: 200):**

Array of `Key Simple`:

* `id`: required, integer
* `key`: required, string
* `created_at`: string, format: date-time
* `last_used`: string or null, format: date-time