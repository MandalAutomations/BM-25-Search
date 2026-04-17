# REST API endpoints for pre-receive hooks

Use the REST API to create, list, update and delete pre-receive hooks.

## About pre-receive hooks

These endpoints are only available to [authenticated](/en/enterprise-server@3.20/rest/overview/authenticating-to-the-rest-api) site administrators. Normal users will receive a `404` response.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

### Object attributes

#### Pre-receive Hook

| Name                             | Type      | Description                                                     |
| -------------------------------- | --------- | --------------------------------------------------------------- |
| `name`                           | `string`  | The name of the hook.                                           |
| `script`                         | `string`  | The script that the hook runs.                                  |
| `script_repository`              | `object`  | The GitHub repository where the script is kept.                 |
| `environment`                    | `object`  | The pre-receive environment where the script is executed.       |
| `enforcement`                    | `string`  | The state of enforcement for this hook.                         |
| `allow_downstream_configuration` | `boolean` | Whether enforcement can be overridden at the org or repo level. |

Possible values for *enforcement* are `enabled`, `disabled` and`testing`. `disabled` indicates the pre-receive hook will not run. `enabled` indicates it will run and reject
any pushes that result in a non-zero status. `testing` means the script will run but will not cause any pushes to be rejected.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## List pre-receive hooks

```
GET /admin/pre-receive-hooks
```

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

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`sort`** (string)
  The property to sort the results by.
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
  http(s)://HOSTNAME/api/v3/admin/pre-receive-hooks
```

**Response schema (Status: 200):**

Array of objects:

* `id`: integer
* `name`: string
* `enforcement`: string
* `script`: string
* `script_repository`: object:
  * `id`: integer
  * `full_name`: string
  * `url`: string
  * `html_url`: string
* `environment`: object:
  * `id`: integer, format: int64
  * `name`: string
  * `image_url`: string
  * `url`: string
  * `html_url`: string
  * `default_environment`: boolean
  * `created_at`: string
  * `hooks_count`: integer
  * `download`: object:
    * `url`: string
    * `state`: string
    * `downloaded_at`: string or null
    * `message`: string or null
* `allow_downstream_configuration`: boolean

## Create a pre-receive hook

```
POST /admin/pre-receive-hooks
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`name`** (string) (required)
  The name of the hook.

* **`script`** (string) (required)
  The script that the hook runs.

* **`script_repository`** (object) (required)
  The GitHub repository where the script is kept.

* **`environment`** (object) (required)
  The pre-receive environment where the script is executed.

* **`enforcement`** (string)
  The state of enforcement for this hook. default: disabled

* **`allow_downstream_configuration`** (boolean)
  Whether enforcement can be overridden at the org or repo level. default: false

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-hooks \
  -d '{
  "name": "Check Commits",
  "script": "scripts/commit_check.sh",
  "enforcement": "disabled",
  "allow_downstream_configuration": false,
  "script_repository": {
    "full_name": "DevIT/hooks"
  },
  "environment": {
    "id": 2
  }
}'
```

**Response schema (Status: 201):**

* `id`: integer
* `name`: string
* `enforcement`: string
* `script`: string
* `script_repository`: object:
  * `id`: integer
  * `full_name`: string
  * `url`: string
  * `html_url`: string
* `environment`: object:
  * `id`: integer, format: int64
  * `name`: string
  * `image_url`: string
  * `url`: string
  * `html_url`: string
  * `default_environment`: boolean
  * `created_at`: string
  * `hooks_count`: integer
  * `download`: object:
    * `url`: string
    * `state`: string
    * `downloaded_at`: string or null
    * `message`: string or null
* `allow_downstream_configuration`: boolean

## Get a pre-receive hook

```
GET /admin/pre-receive-hooks/{pre_receive_hook_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

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
  http(s)://HOSTNAME/api/v3/admin/pre-receive-hooks/PRE_RECEIVE_HOOK_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a pre-receive hook](#create-a-pre-receive-hook).

## Update a pre-receive hook

```
PATCH /admin/pre-receive-hooks/{pre_receive_hook_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`pre_receive_hook_id`** (integer) (required)
  The unique identifier of the pre-receive hook.

#### Body parameters

* **`name`** (string)
  The name of the hook.

* **`script`** (string)
  The script that the hook runs.

* **`script_repository`** (object)
  The GitHub repository where the script is kept.

* **`environment`** (object)
  The pre-receive environment where the script is executed.

* **`enforcement`** (string)
  The state of enforcement for this hook.

* **`allow_downstream_configuration`** (boolean)
  Whether enforcement can be overridden at the org or repo level.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-hooks/PRE_RECEIVE_HOOK_ID \
  -d '{
  "name": "Check Commits",
  "environment": {
    "id": 1
  },
  "allow_downstream_configuration": true
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a pre-receive hook](#create-a-pre-receive-hook).

## Delete a pre-receive hook

```
DELETE /admin/pre-receive-hooks/{pre_receive_hook_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`pre_receive_hook_id`** (integer) (required)
  The unique identifier of the pre-receive hook.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-hooks/PRE_RECEIVE_HOOK_ID
```

**Response schema (Status: 204):**