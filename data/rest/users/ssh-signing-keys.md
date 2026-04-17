# REST API endpoints for SSH signing keys

Use the REST API to manage SSH signing keys of authenticated users.

## About SSH signing key administration

If a request URL does not include a `{username}` parameter then the response will be for the signed-in user (and you must pass [authentication information](/en/rest/overview/authenticating-to-the-rest-api) with your request). Additional private information, such as whether a user has two-factor authentication enabled, is included when authenticated through OAuth with the `user` scope.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List SSH signing keys for the authenticated user

```
GET /user/ssh_signing_keys
```

Lists the SSH signing keys for the authenticated user's GitHub account.
OAuth app tokens and personal access tokens (classic) need the read:ssh\_signing\_key scope to use this endpoint.

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
  https://api.github.com/user/ssh_signing_keys
```

**Response schema (Status: 200):**

Array of `SSH Signing Key`:

* `key`: required, string
* `id`: required, integer
* `title`: required, string
* `created_at`: required, string, format: date-time

## Create a SSH signing key for the authenticated user

```
POST /user/ssh_signing_keys
```

Creates an SSH signing key for the authenticated user's GitHub account.
OAuth app tokens and personal access tokens (classic) need the write:ssh\_signing\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`title`** (string)
  A descriptive name for the new key.

* **`key`** (string) (required)
  The public SSH key to add to your GitHub account. For more information, see "Checking for existing SSH keys."

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
  https://api.github.com/user/ssh_signing_keys \
  -d '{
  "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234",
  "title": "ssh-rsa AAAAB3NzaC1yc2EAAA"
}'
```

**Response schema (Status: 201):**

* `key`: required, string
* `id`: required, integer
* `title`: required, string
* `created_at`: required, string, format: date-time

## Get an SSH signing key for the authenticated user

```
GET /user/ssh_signing_keys/{ssh_signing_key_id}
```

Gets extended details for an SSH signing key.
OAuth app tokens and personal access tokens (classic) need the read:ssh\_signing\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`ssh_signing_key_id`** (integer) (required)
  The unique identifier of the SSH signing key.

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
  https://api.github.com/user/ssh_signing_keys/SSH_SIGNING_KEY_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a SSH signing key for the authenticated user](#create-a-ssh-signing-key-for-the-authenticated-user).

## Delete an SSH signing key for the authenticated user

```
DELETE /user/ssh_signing_keys/{ssh_signing_key_id}
```

Deletes an SSH signing key from the authenticated user's GitHub account.
OAuth app tokens and personal access tokens (classic) need the admin:ssh\_signing\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`ssh_signing_key_id`** (integer) (required)
  The unique identifier of the SSH signing key.

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
  https://api.github.com/user/ssh_signing_keys/SSH_SIGNING_KEY_ID
```

**Response schema (Status: 204):**

## List SSH signing keys for a user

```
GET /users/{username}/ssh_signing_keys
```

Lists the SSH signing keys for a user. This operation is accessible by anyone.

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
  https://api.github.com/users/USERNAME/ssh_signing_keys
```

**Response schema (Status: 200):**

Same response schema as [List SSH signing keys for the authenticated user](#list-ssh-signing-keys-for-the-authenticated-user).