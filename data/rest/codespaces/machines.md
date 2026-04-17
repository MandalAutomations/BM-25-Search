# REST API endpoints for Codespaces machines

Use the REST API to manage availability of machine types for a codespace.

## About Codespaces machines

You can determine which machine types are available to create a codespace, either on a given repository or as an authenticated user. For more information, see [Changing the machine type for your codespace](/en/codespaces/customizing-your-codespace/changing-the-machine-type-for-your-codespace#about-machine-types).

You can also use this information when changing the machine of an existing codespace by updating its `machine` property. The machine update will take place the next time the codespace is restarted. For more information, see [Changing the machine type for your codespace](/en/codespaces/customizing-your-codespace/changing-the-machine-type-for-your-codespace).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List available machine types for a repository

```
GET /repos/{owner}/{repo}/codespaces/machines
```

List the machine types available for a given repository based on its configuration.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`location`** (string)
  The location to check for available machines. Assigned by IP if not provided.

* **`client_ip`** (string)
  IP for location auto-detection when proxying a request

* **`ref`** (string)
  The branch or commit to check for prebuild availability and devcontainer restrictions.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/codespaces/machines
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `machines`: required, array of `Codespace machine`:
  * `name`: required, string
  * `display_name`: required, string
  * `operating_system`: required, string
  * `storage_in_bytes`: required, integer
  * `memory_in_bytes`: required, integer
  * `cpus`: required, integer
  * `prebuild_availability`: required, string or null, enum: `none`, `ready`, `in_progress`, `null`

## List machine types for a codespace

```
GET /user/codespaces/{codespace_name}/machines
```

List the machine types a codespace can transition to use.
OAuth app tokens and personal access tokens (classic) need the codespace scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`codespace_name`** (string) (required)
  The name of the codespace.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/codespaces/CODESPACE_NAME/machines
```

**Response schema (Status: 200):**

Same response schema as [List available machine types for a repository](#list-available-machine-types-for-a-repository).