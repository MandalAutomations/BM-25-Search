# REST API endpoints for Codespaces repository secrets

Use the REST API to manage secrets for repositories that the user has access to in a codespace.

## About Codespaces repository secrets

You can create, list, and delete secrets (such as access tokens for cloud services) for repositories that the user has access to. These secrets are made available to the codespace at runtime. For more information, see [Managing your account-specific secrets for GitHub Codespaces](/en/codespaces/managing-your-codespaces/managing-your-account-specific-secrets-for-github-codespaces).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List repository secrets

```
GET /repos/{owner}/{repo}/codespaces/secrets
```

Lists all development environment secrets available in a repository without revealing their encrypted
values.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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
  https://api.github.com/repos/OWNER/REPO/codespaces/secrets
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `secrets`: required, array of `Codespaces Secret`:
  * `name`: required, string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time

## Get a repository public key

```
GET /repos/{owner}/{repo}/codespaces/secrets/public-key
```

Gets your public key, which you need to encrypt secrets. You need to
encrypt a secret before you can create or update secrets.
If the repository is private, OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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
  https://api.github.com/repos/OWNER/REPO/codespaces/secrets/public-key
```

**Response schema (Status: 200):**

* `key_id`: required, string
* `key`: required, string
* `id`: integer
* `url`: string
* `title`: string
* `created_at`: string

## Get a repository secret

```
GET /repos/{owner}/{repo}/codespaces/secrets/{secret_name}
```

Gets a single repository development environment secret without revealing its encrypted value.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`secret_name`** (string) (required)
  The name of the secret.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/codespaces/secrets/SECRET_NAME
```

**Response schema (Status: 200):**

* `name`: required, string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time

## Create or update a repository secret

```
PUT /repos/{owner}/{repo}/codespaces/secrets/{secret_name}
```

Creates or updates a repository development environment secret with an encrypted value. Encrypt your secret using
LibSodium. For more information, see "Encrypting secrets for the REST API."
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint. The associated user must be a repository admin.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`secret_name`** (string) (required)
  The name of the secret.

#### Body parameters

* **`encrypted_value`** (string)
  Value for your secret, encrypted with LibSodium using the public key retrieved from the Get a repository public key endpoint.

* **`key_id`** (string)
  ID of the key you used to encrypt the secret.

### HTTP response status codes

* **201** - Response when creating a secret

* **204** - Response when updating a secret

### Code examples

#### Example 1: Status Code 201

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/codespaces/secrets/SECRET_NAME \
  -d '{
  "encrypted_value": "c2VjcmV0",
  "key_id": "012345678912345678"
}'
```

**Response schema (Status: 201):**

#### Example 2: Status Code 204

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/codespaces/secrets/SECRET_NAME \
  -d '{
  "encrypted_value": "c2VjcmV0",
  "key_id": "012345678912345678"
}'
```

**Response schema (Status: 204):**

## Delete a repository secret

```
DELETE /repos/{owner}/{repo}/codespaces/secrets/{secret_name}
```

Deletes a development environment secret in a repository using the secret name.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint. The associated user must be a repository admin.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`secret_name`** (string) (required)
  The name of the secret.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/codespaces/secrets/SECRET_NAME
```

**Response schema (Status: 204):**