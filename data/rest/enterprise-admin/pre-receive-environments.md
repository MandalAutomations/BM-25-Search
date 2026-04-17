# REST API endpoints for pre-receive environments

Use the REST API to create, list, update and delete environments for pre-receive hooks.

## About pre-receive environments

These endpoints are only available to [authenticated](/en/enterprise-server@3.20/rest/overview/authenticating-to-the-rest-api) site administrators. Normal users will receive a `404` response.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

### Object attributes

#### Pre-receive Environment

| Name                  | Type      | Description                                                     |
| --------------------- | --------- | --------------------------------------------------------------- |
| `name`                | `string`  | The name of the environment as displayed in the UI.             |
| `image_url`           | `string`  | URL to the tarball that will be downloaded and extracted.       |
| `default_environment` | `boolean` | Whether this is the default environment that ships with GitHub. |
| `download`            | `object`  | This environment's download status.                             |
| `hooks_count`         | `integer` | The number of pre-receive hooks that use this environment.      |

#### Pre-receive Environment Download

| Name            | Type     | Description                                             |
| --------------- | -------- | ------------------------------------------------------- |
| `state`         | `string` | The state of the most recent download.                  |
| `downloaded_at` | `string` | The time when the most recent download started.         |
| `message`       | `string` | On failure, this will have any error messages produced. |

Possible values for `state` are `not_started`, `in_progress`, `success`, `failed`.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## List pre-receive environments

```
GET /admin/pre-receive-environments
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
  http(s)://HOSTNAME/api/v3/admin/pre-receive-environments
```

**Response schema (Status: 200):**

Array of objects:

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

## Create a pre-receive environment

```
POST /admin/pre-receive-environments
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`name`** (string) (required)
  The new pre-receive environment's name.

* **`image_url`** (string) (required)
  URL from which to download a tarball of this environment.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-environments \
  -d '{
  "name": "DevTools Hook Env",
  "image_url": "https://my_file_server/path/to/devtools_env.tar.gz"
}'
```

**Response schema (Status: 201):**

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

## Get a pre-receive environment

```
GET /admin/pre-receive-environments/{pre_receive_environment_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`pre_receive_environment_id`** (integer) (required)
  The unique identifier of the pre-receive environment.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-environments/PRE_RECEIVE_ENVIRONMENT_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a pre-receive environment](#create-a-pre-receive-environment).

## Update a pre-receive environment

```
PATCH /admin/pre-receive-environments/{pre_receive_environment_id}
```

You cannot modify the default environment. If you attempt to modify the default environment, you will receive a 422 Unprocessable Entity response.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`pre_receive_environment_id`** (integer) (required)
  The unique identifier of the pre-receive environment.

#### Body parameters

* **`name`** (string)
  This pre-receive environment's new name.

* **`image_url`** (string)
  URL from which to download a tarball of this environment.

### HTTP response status codes

* **200** - OK

* **422** - Client Errors

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-environments/PRE_RECEIVE_ENVIRONMENT_ID \
  -d '{
  "name": "DevTools Hook Env",
  "image_url": "https://my_file_server/path/to/devtools_env.tar.gz"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a pre-receive environment](#create-a-pre-receive-environment).

## Delete a pre-receive environment

```
DELETE /admin/pre-receive-environments/{pre_receive_environment_id}
```

If you attempt to delete an environment that cannot be deleted, you will receive a 422 Unprocessable Entity response.
The possible error messages are:

Cannot modify or delete the default environment
Cannot delete environment that has hooks
Cannot delete environment when download is in progress

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`pre_receive_environment_id`** (integer) (required)
  The unique identifier of the pre-receive environment.

### HTTP response status codes

* **204** - No Content

* **422** - Client Errors

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-environments/PRE_RECEIVE_ENVIRONMENT_ID
```

**Response schema (Status: 204):**

## Start a pre-receive environment download

```
POST /admin/pre-receive-environments/{pre_receive_environment_id}/downloads
```

Triggers a new download of the environment tarball from the environment's image\_url. When the download is finished, the newly downloaded tarball will overwrite the existing environment.
If a download cannot be triggered, you will receive a 422 Unprocessable Entity response.
The possible error messages are:

Cannot modify or delete the default environment
Can not start a new download when a download is in progress

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`pre_receive_environment_id`** (integer) (required)
  The unique identifier of the pre-receive environment.

### HTTP response status codes

* **202** - Accepted

* **422** - Client Errors

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-environments/PRE_RECEIVE_ENVIRONMENT_ID/downloads
```

**Response schema (Status: 202):**

* `url`: string
* `state`: string
* `downloaded_at`: string or null
* `message`: string or null

## Get the download status for a pre-receive environment

```
GET /admin/pre-receive-environments/{pre_receive_environment_id}/downloads/latest
```

In addition to seeing the download status at the "Get a pre-receive environment" endpoint, there is also this separate endpoint for just the download status.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`pre_receive_environment_id`** (integer) (required)
  The unique identifier of the pre-receive environment.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/admin/pre-receive-environments/PRE_RECEIVE_ENVIRONMENT_ID/downloads/latest
```

**Response schema (Status: 200):**

Same response schema as [Start a pre-receive environment download](#start-a-pre-receive-environment-download).