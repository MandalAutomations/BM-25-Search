# REST API endpoints for GPG keys

Use the REST API to manage GPG keys of authenticated users.

## About user GPG key administration

The data returned in the `public_key` response field is not a GPG formatted key. When a user uploads a GPG key, it is parsed and the cryptographic public key is extracted and stored. This cryptographic key is what the endpoints in this category will return. This key is not suitable for direct use in programs such as GPG.

If a request URL does not include a `{username}` parameter then the response will be for the signed-in user (and you must pass [authentication information](/en/rest/overview/authenticating-to-the-rest-api) with your request). Additional private information, such as whether a user has two-factor authentication enabled, is included when authenticated through OAuth with the `user` scope.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List GPG keys for the authenticated user

```
GET /user/gpg_keys
```

Lists the current user's GPG keys.
OAuth app tokens and personal access tokens (classic) need the read:gpg\_key scope to use this endpoint.

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
  https://api.github.com/user/gpg_keys
```

**Response schema (Status: 200):**

Array of `GPG Key`:

* `id`: required, integer, format: int64
* `name`: string or null
* `primary_key_id`: required, integer or null
* `key_id`: required, string
* `public_key`: required, string
* `emails`: required, array of objects:
  * `email`: string
  * `verified`: boolean
* `subkeys`: required, array of objects:
  * `id`: integer, format: int64
  * `primary_key_id`: integer
  * `key_id`: string
  * `public_key`: string
  * `emails`: array of objects:
    * `email`: string
    * `verified`: boolean
  * `subkeys`: array of object
  * `can_sign`: boolean
  * `can_encrypt_comms`: boolean
  * `can_encrypt_storage`: boolean
  * `can_certify`: boolean
  * `created_at`: string
  * `expires_at`: string or null
  * `raw_key`: string or null
  * `revoked`: boolean
* `can_sign`: required, boolean
* `can_encrypt_comms`: required, boolean
* `can_encrypt_storage`: required, boolean
* `can_certify`: required, boolean
* `created_at`: required, string, format: date-time
* `expires_at`: required, string or null, format: date-time
* `revoked`: required, boolean
* `raw_key`: required, string or null

## Create a GPG key for the authenticated user

```
POST /user/gpg_keys
```

Adds a GPG key to the authenticated user's GitHub account.
OAuth app tokens and personal access tokens (classic) need the write:gpg\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`name`** (string)
  A descriptive name for the new key.

* **`armored_public_key`** (string) (required)
  A GPG key in ASCII-armored format.

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
  https://api.github.com/user/gpg_keys \
  -d '{
  "name": "Octocat's GPG Key",
  "armored_public_key": "-----BEGIN PGP PUBLIC KEY BLOCK-----\nVersion: GnuPG v1\n\nmQINBFnZ2ZIBEADQ2Z7Z7\n-----END PGP PUBLIC KEY BLOCK-----"
}'
```

**Response schema (Status: 201):**

* `id`: required, integer, format: int64
* `name`: string or null
* `primary_key_id`: required, integer or null
* `key_id`: required, string
* `public_key`: required, string
* `emails`: required, array of objects:
  * `email`: string
  * `verified`: boolean
* `subkeys`: required, array of objects:
  * `id`: integer, format: int64
  * `primary_key_id`: integer
  * `key_id`: string
  * `public_key`: string
  * `emails`: array of objects:
    * `email`: string
    * `verified`: boolean
  * `subkeys`: array of object
  * `can_sign`: boolean
  * `can_encrypt_comms`: boolean
  * `can_encrypt_storage`: boolean
  * `can_certify`: boolean
  * `created_at`: string
  * `expires_at`: string or null
  * `raw_key`: string or null
  * `revoked`: boolean
* `can_sign`: required, boolean
* `can_encrypt_comms`: required, boolean
* `can_encrypt_storage`: required, boolean
* `can_certify`: required, boolean
* `created_at`: required, string, format: date-time
* `expires_at`: required, string or null, format: date-time
* `revoked`: required, boolean
* `raw_key`: required, string or null

## Get a GPG key for the authenticated user

```
GET /user/gpg_keys/{gpg_key_id}
```

View extended details for a single GPG key.
OAuth app tokens and personal access tokens (classic) need the read:gpg\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gpg_key_id`** (integer) (required)
  The unique identifier of the GPG key.

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
  https://api.github.com/user/gpg_keys/GPG_KEY_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a GPG key for the authenticated user](#create-a-gpg-key-for-the-authenticated-user).

## Delete a GPG key for the authenticated user

```
DELETE /user/gpg_keys/{gpg_key_id}
```

Removes a GPG key from the authenticated user's GitHub account.
OAuth app tokens and personal access tokens (classic) need the admin:gpg\_key scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`gpg_key_id`** (integer) (required)
  The unique identifier of the GPG key.

### HTTP response status codes

* **204** - No Content

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
  -X DELETE \
  https://api.github.com/user/gpg_keys/GPG_KEY_ID
```

**Response schema (Status: 204):**

## List GPG keys for a user

```
GET /users/{username}/gpg_keys
```

Lists the GPG keys for a user. This information is accessible by anyone.

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
  https://api.github.com/users/USERNAME/gpg_keys
```

**Response schema (Status: 200):**

Same response schema as [List GPG keys for the authenticated user](#list-gpg-keys-for-the-authenticated-user).