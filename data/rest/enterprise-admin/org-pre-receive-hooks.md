# REST API endpoints for organization pre-receive hooks

Use the REST API to view and modify enforcement of the pre-receive hooks that are available to an organization.

## About organization pre-receive hooks

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

### Object attributes

| Name                             | Type      | Description                                               |
| -------------------------------- | --------- | --------------------------------------------------------- |
| `name`                           | `string`  | The name of the hook.                                     |
| `enforcement`                    | `string`  | The state of enforcement for the hook on this repository. |
| `allow_downstream_configuration` | `boolean` | Whether repositories can override enforcement.            |
| `configuration_url`              | `string`  | URL for the endpoint where enforcement is set.            |

Possible values for `enforcement` are `enabled`, `disabled` and`testing`. `disabled` indicates the pre-receive hook will not run. `enabled` indicates it will run and reject any pushes that result in a non-zero status. `testing` means the script will run but will not cause any pushes to be rejected.

`configuration_url` may be a link to this endpoint or this hook's global configuration. Only site admins are able to access the global configuration.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## List pre-receive hooks for an organization

```
GET /orgs/{org}/pre-receive-hooks
```

List all pre-receive hooks that are enabled or testing for this organization as well as any disabled hooks that can be configured at the organization level. Globally disabled pre-receive hooks that do not allow downstream configuration are not listed.

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

* **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

* **`sort`** (string)
  The sort order for the response collection.
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
  http(s)://HOSTNAME/api/v3/orgs/ORG/pre-receive-hooks
```

**Response schema (Status: 200):**

Array of objects:

* `id`: integer
* `name`: string
* `enforcement`: string
* `configuration_url`: string
* `allow_downstream_configuration`: boolean

## Get a pre-receive hook for an organization

```
GET /orgs/{org}/pre-receive-hooks/{pre_receive_hook_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  http(s)://HOSTNAME/api/v3/orgs/ORG/pre-receive-hooks/PRE_RECEIVE_HOOK_ID
```

**Response schema (Status: 200):**

* `id`: integer
* `name`: string
* `enforcement`: string
* `configuration_url`: string
* `allow_downstream_configuration`: boolean

## Update pre-receive hook enforcement for an organization

```
PATCH /orgs/{org}/pre-receive-hooks/{pre_receive_hook_id}
```

For pre-receive hooks which are allowed to be configured at the org level, you can set enforcement and allow\_downstream\_configuration

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`pre_receive_hook_id`** (integer) (required)
  The unique identifier of the pre-receive hook.

#### Body parameters

* **`enforcement`** (string)
  The state of enforcement for the hook on this repository.

* **`allow_downstream_configuration`** (boolean)
  Whether repositories can override enforcement.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/orgs/ORG/pre-receive-hooks/PRE_RECEIVE_HOOK_ID \
  -d '{
  "enforcement": "enabled",
  "allow_downstream_configuration": false
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a pre-receive hook for an organization](#get-a-pre-receive-hook-for-an-organization).

## Remove pre-receive hook enforcement for an organization

```
DELETE /orgs/{org}/pre-receive-hooks/{pre_receive_hook_id}
```

Removes any overrides for this hook at the org level for this org.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`pre_receive_hook_id`** (integer) (required)
  The unique identifier of the pre-receive hook.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/orgs/ORG/pre-receive-hooks/PRE_RECEIVE_HOOK_ID
```

**Response schema (Status: 200):**

Same response schema as [Get a pre-receive hook for an organization](#get-a-pre-receive-hook-for-an-organization).