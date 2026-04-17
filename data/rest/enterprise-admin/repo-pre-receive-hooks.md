# REST API endpoints for repository pre-receive hooks

Use the REST API to view and modify enforcement of the pre-receive hooks that are available to a repository.

## About repository pre-receive hooks

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

| Name                | Type     | Description                                               |
| ------------------- | -------- | --------------------------------------------------------- |
| `name`              | `string` | The name of the hook.                                     |
| `enforcement`       | `string` | The state of enforcement for the hook on this repository. |
| `configuration_url` | `string` | URL for the endpoint where enforcement is set.            |

Possible values for *enforcement* are `enabled`, `disabled` and`testing`. `disabled` indicates the pre-receive hook will not run. `enabled` indicates it will run and reject any pushes that result in a non-zero status. `testing` means the script will run but will not cause any pushes to be rejected.

`configuration_url` may be a link to this repository, its organization owner or global configuration. Authorization to access the endpoint at `configuration_url` is determined at the owner or site admin level.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## List pre-receive hooks for a repository

```
GET /repos/{owner}/{repo}/pre-receive-hooks
```

List all pre-receive hooks that are enabled or testing for this repository as well as any disabled hooks that are allowed to be enabled at the repository level. Pre-receive hooks that are disabled at a higher level and are not configurable will not be listed.

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

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`sort`** (string)
  Default: `created`
  Can be one of: `created`, `updated`, `name`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/pre-receive-hooks
```

**Response schema (Status: 200):**

Array of objects:

* `id`: integer
* `name`: string
* `enforcement`: string
* `configuration_url`: string

## Get a pre-receive hook for a repository

```
GET /repos/{owner}/{repo}/pre-receive-hooks/{pre_receive_hook_id}
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

* **`pre_receive_hook_id`** (integer) (required)
  The unique identifier of the pre-receive hook.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/pre-receive-hooks/PRE_RECEIVE_HOOK_ID
```

**Response schema (Status: 200):**

* `id`: integer
* `name`: string
* `enforcement`: string
* `configuration_url`: string

## Update pre-receive hook enforcement for a repository

```
PATCH /repos/{owner}/{repo}/pre-receive-hooks/{pre_receive_hook_id}
```

For pre-receive hooks which are allowed to be configured at the repo level, you can set enforcement

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`pre_receive_hook_id`** (integer) (required)
  The unique identifier of the pre-receive hook.

#### Body parameters

* **`enforcement`** (string)
  The state of enforcement for the hook on this repository.
  Can be one of: `enabled`, `disabled`, `testing`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/pre-receive-hooks/PRE_RECEIVE_HOOK_ID \
  -d '{
  "enforcement": "enabled"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a pre-receive hook for a repository](#get-a-pre-receive-hook-for-a-repository).

## Remove pre-receive hook enforcement for a repository

```
DELETE /repos/{owner}/{repo}/pre-receive-hooks/{pre_receive_hook_id}
```

Deletes any overridden enforcement on this repository for the specified hook.
Responds with effective values inherited from owner and/or global level.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`pre_receive_hook_id`** (integer) (required)
  The unique identifier of the pre-receive hook.

### HTTP response status codes

* **200** - Responds with effective values inherited from owner and/or global level.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/pre-receive-hooks/PRE_RECEIVE_HOOK_ID
```

**Response schema (Status: 200):**

Same response schema as [Get a pre-receive hook for a repository](#get-a-pre-receive-hook-for-a-repository).