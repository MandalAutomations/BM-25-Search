# REST API endpoints for GitHub Actions cache

Use the REST API to interact with the cache for repositories in GitHub Actions.

## About the cache in GitHub Actions

You can use the REST API to query and manage the cache for repositories in GitHub Actions. You can also install a GitHub CLI extension to manage your caches from the command line. For more information, see [Dependency caching reference](/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows#managing-caches).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get GitHub Actions cache retention limit for an enterprise

```
GET /enterprises/{enterprise}/actions/cache/retention-limit
```

Gets GitHub Actions cache retention limit for an enterprise. All organizations and repositories under this
enterprise may not set a higher cache retention limit.
OAuth tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/actions/cache/retention-limit
```

**Response schema (Status: 200):**

* `max_cache_retention_days`: integer

## Set GitHub Actions cache retention limit for an enterprise

```
PUT /enterprises/{enterprise}/actions/cache/retention-limit
```

Sets GitHub Actions cache retention limit for an enterprise. All organizations and repositories under this
enterprise may not set a higher cache retention limit.
OAuth tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`max_cache_retention_days`** (integer)
  For repositories & organizations in an enterprise, the maximum duration, in days, for which caches in a repository may be retained.

### HTTP response status codes

* **204** - No Content

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/actions/cache/retention-limit \
  -d '{
  "max_cache_retention_days": 80
}'
```

**Response schema (Status: 204):**

## Get GitHub Actions cache storage limit for an enterprise

```
GET /enterprises/{enterprise}/actions/cache/storage-limit
```

Gets GitHub Actions cache storage limit for an enterprise. All organizations and repositories under this
enterprise may not set a higher cache storage limit.
OAuth tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/actions/cache/storage-limit
```

**Response schema (Status: 200):**

* `max_cache_size_gb`: integer

## Set GitHub Actions cache storage limit for an enterprise

```
PUT /enterprises/{enterprise}/actions/cache/storage-limit
```

Sets GitHub Actions cache storage limit for an enterprise. All organizations and repositories under this
enterprise may not set a higher cache storage limit.
OAuth tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`max_cache_size_gb`** (integer)
  For repositories & organizations in an enterprise, the maximum size limit for the sum of all caches in a repository, in gigabytes.

### HTTP response status codes

* **204** - No Content

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/actions/cache/storage-limit \
  -d '{
  "max_cache_size_gb": 150
}'
```

**Response schema (Status: 204):**

## Get GitHub Actions cache retention limit for an organization

```
GET /organizations/{org}/actions/cache/retention-limit
```

Gets GitHub Actions cache retention limit for an organization. All repositories under this
organization may not set a higher cache retention limit.
OAuth tokens and personal access tokens (classic) need the admin:organization scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/organizations/ORG/actions/cache/retention-limit
```

**Response schema (Status: 200):**

Same response schema as [Get GitHub Actions cache retention limit for an enterprise](#get-github-actions-cache-retention-limit-for-an-enterprise).

## Set GitHub Actions cache retention limit for an organization

```
PUT /organizations/{org}/actions/cache/retention-limit
```

Sets GitHub Actions cache retention limit for an organization. All repositories under this
organization may not set a higher cache retention limit.
OAuth tokens and personal access tokens (classic) need the admin:organization scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`max_cache_retention_days`** (integer)
  For repositories in this organization, the maximum duration, in days, for which caches in a repository may be retained.

### HTTP response status codes

* **204** - No Content

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/organizations/ORG/actions/cache/retention-limit \
  -d '{
  "max_cache_retention_days": 80
}'
```

**Response schema (Status: 204):**

## Get GitHub Actions cache storage limit for an organization

```
GET /organizations/{org}/actions/cache/storage-limit
```

Gets GitHub Actions cache storage limit for an organization. All repositories under this
organization may not set a higher cache storage limit.
OAuth tokens and personal access tokens (classic) need the admin:organization scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/organizations/ORG/actions/cache/storage-limit
```

**Response schema (Status: 200):**

Same response schema as [Get GitHub Actions cache storage limit for an enterprise](#get-github-actions-cache-storage-limit-for-an-enterprise).

## Set GitHub Actions cache storage limit for an organization

```
PUT /organizations/{org}/actions/cache/storage-limit
```

Sets GitHub Actions cache storage limit for an organization. All organizations and repositories under this
organization may not set a higher cache storage limit.
OAuth tokens and personal access tokens (classic) need the admin:organization scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`max_cache_size_gb`** (integer)
  For repositories in the organization, the maximum size limit for the sum of all caches in a repository, in gigabytes.

### HTTP response status codes

* **204** - No Content

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/organizations/ORG/actions/cache/storage-limit \
  -d '{
  "max_cache_size_gb": 150
}'
```

**Response schema (Status: 204):**

## Get GitHub Actions cache usage for an organization

```
GET /orgs/{org}/actions/cache/usage
```

Gets the total GitHub Actions cache usage for an organization.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.
OAuth tokens and personal access tokens (classic) need the read:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/cache/usage
```

**Response schema (Status: 200):**

* `total_active_caches_count`: required, integer
* `total_active_caches_size_in_bytes`: required, integer

## List repositories with GitHub Actions cache usage for an organization

```
GET /orgs/{org}/actions/cache/usage-by-repository
```

Lists repositories and their GitHub Actions cache usage for an organization.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.
OAuth tokens and personal access tokens (classic) need the read:org scope to use this endpoint.

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
  https://api.github.com/orgs/ORG/actions/cache/usage-by-repository
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `repository_cache_usages`: required, array of `Actions Cache Usage by repository`:
  * `full_name`: required, string
  * `active_caches_size_in_bytes`: required, integer
  * `active_caches_count`: required, integer

## Get GitHub Actions cache retention limit for a repository

```
GET /repos/{owner}/{repo}/actions/cache/retention-limit
```

Gets GitHub Actions cache retention limit for a repository. This determines how long caches will be retained for, if
not manually removed or evicted due to size constraints.
OAuth tokens and personal access tokens (classic) need the admin:repository scope to use this endpoint.

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

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/cache/retention-limit
```

**Response schema (Status: 200):**

Same response schema as [Get GitHub Actions cache retention limit for an enterprise](#get-github-actions-cache-retention-limit-for-an-enterprise).

## Set GitHub Actions cache retention limit for a repository

```
PUT /repos/{owner}/{repo}/actions/cache/retention-limit
```

Sets GitHub Actions cache retention limit for a repository. This determines how long caches will be retained for, if
not manually removed or evicted due to size constraints.
OAuth tokens and personal access tokens (classic) need the admin:repository scope to use this endpoint.

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

* **`max_cache_retention_days`** (integer)
  The maximum number of days to keep caches in this repository.

### HTTP response status codes

* **204** - No Content

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/cache/retention-limit \
  -d '{
  "max_cache_retention_days": 80
}'
```

**Response schema (Status: 204):**

## Get GitHub Actions cache storage limit for a repository

```
GET /repos/{owner}/{repo}/actions/cache/storage-limit
```

Gets GitHub Actions cache storage limit for a repository. This determines the maximum size of caches that can be
stored before eviction occurs.
OAuth tokens and personal access tokens (classic) need the admin:repository scope to use this endpoint.

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

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/cache/storage-limit
```

**Response schema (Status: 200):**

Same response schema as [Get GitHub Actions cache storage limit for an enterprise](#get-github-actions-cache-storage-limit-for-an-enterprise).

## Set GitHub Actions cache storage limit for a repository

```
PUT /repos/{owner}/{repo}/actions/cache/storage-limit
```

Sets GitHub Actions cache storage limit for a repository. This determines the maximum size of caches that can be
stored before eviction occurs.
OAuth tokens and personal access tokens (classic) need the admin:repository scope to use this endpoint.

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

* **`max_cache_size_gb`** (integer)
  The maximum total cache size for this repository, in gigabytes.

### HTTP response status codes

* **204** - No Content

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/cache/storage-limit \
  -d '{
  "max_cache_size_gb": 150
}'
```

**Response schema (Status: 204):**

## Get GitHub Actions cache usage for a repository

```
GET /repos/{owner}/{repo}/actions/cache/usage
```

Gets GitHub Actions cache usage for a repository.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.
Anyone with read access to the repository can use this endpoint.
If the repository is private, OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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
  https://api.github.com/repos/OWNER/REPO/actions/cache/usage
```

**Response schema (Status: 200):**

* `full_name`: required, string
* `active_caches_size_in_bytes`: required, integer
* `active_caches_count`: required, integer

## List GitHub Actions caches for a repository

```
GET /repos/{owner}/{repo}/actions/caches
```

Lists the GitHub Actions caches for a repository.
OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`ref`** (string)
  The full Git reference for narrowing down the cache. The ref for a branch should be formatted as refs/heads/<branch name>. To reference a pull request use refs/pull/<number>/merge.

* **`key`** (string)
  An explicit key or prefix for identifying the cache

* **`sort`** (string)
  The property to sort the results by. created\_at means when the cache was created. last\_accessed\_at means when the cache was last accessed. size\_in\_bytes is the size of the cache in bytes.
  Default: `last_accessed_at`
  Can be one of: `created_at`, `last_accessed_at`, `size_in_bytes`

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/caches
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `actions_caches`: required, array of objects:
  * `id`: integer
  * `ref`: string
  * `key`: string
  * `version`: string
  * `last_accessed_at`: string, format: date-time
  * `created_at`: string, format: date-time
  * `size_in_bytes`: integer

## Delete GitHub Actions caches for a repository (using a cache key)

```
DELETE /repos/{owner}/{repo}/actions/caches
```

Deletes one or more GitHub Actions caches for a repository, using a complete cache key. By default, all caches that match the provided key are deleted, but you can optionally provide a Git ref to restrict deletions to caches that match both the provided key and the Git ref.
OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`key`** (string) (required)
  A key for identifying the cache.

* **`ref`** (string)
  The full Git reference for narrowing down the cache. The ref for a branch should be formatted as refs/heads/<branch name>. To reference a pull request use refs/pull/<number>/merge.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/actions/caches
```

**Response schema (Status: 200):**

Same response schema as [List GitHub Actions caches for a repository](#list-github-actions-caches-for-a-repository).

## Delete a GitHub Actions cache for a repository (using a cache ID)

```
DELETE /repos/{owner}/{repo}/actions/caches/{cache_id}
```

Deletes a GitHub Actions cache for a repository, using a cache ID.
OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`cache_id`** (integer) (required)
  The unique identifier of the GitHub Actions cache.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/actions/caches/CACHE_ID
```

**Response schema (Status: 204):**