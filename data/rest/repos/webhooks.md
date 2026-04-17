# REST API endpoints for repository webhooks

Use the REST API to create and manage webhooks for your repositories.

## About repository webhooks

Repository webhooks allow your server to receive HTTP `POST` payloads whenever certain events happen in a repository. For more information, see [Webhooks documentation](/en/webhooks).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List repository webhooks

```
GET /repos/{owner}/{repo}/hooks
```

Lists webhooks for a repository. last response may return null if there have not been any deliveries within 30 days.

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

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/hooks
```

**Response schema (Status: 200):**

Array of `Webhook`:

* `type`: required, string
* `id`: required, integer
* `name`: required, string
* `active`: required, boolean
* `events`: required, array of string
* `config`: required, `Webhook Configuration`:
  * `url`: string, format: uri
  * `content_type`: string
  * `secret`: string
  * `insecure_ssl`: one of:
    * **string**
    * **number**
* `updated_at`: required, string, format: date-time
* `created_at`: required, string, format: date-time
* `url`: required, string, format: uri
* `test_url`: required, string, format: uri
* `ping_url`: required, string, format: uri
* `deliveries_url`: string, format: uri
* `last_response`: required, `Hook Response`:
  * `code`: required, integer or null
  * `status`: required, string or null
  * `message`: required, string or null

## Create a repository webhook

```
POST /repos/{owner}/{repo}/hooks
```

Repositories can have multiple webhooks installed. Each webhook should have a unique config. Multiple webhooks can
share the same config as long as those webhooks do not have any events that overlap.

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

* **`name`** (string)
  Use web to create a webhook. Default: web. This parameter only accepts the value web.

* **`config`** (object)
  Key/value pairs to provide settings for this webhook.
  * **`url`** (string)
    The URL to which the payloads will be delivered.
  * **`content_type`** (string)
    The media type used to serialize the payloads. Supported values include json and form. The default is form.
  * **`secret`** (string)
    If provided, the secret will be used as the key to generate the HMAC hex digest value for delivery signature headers.
  * **`insecure_ssl`** (string or number)
    Determines whether the SSL certificate of the host for url will be verified when delivering payloads. Supported values include 0 (verification is performed) and 1 (verification is not performed). The default is 0. We strongly recommend not setting this to 1 as you are subject to man-in-the-middle and other attacks.

* **`events`** (array of strings)
  Determines what events the hook is triggered for.
  Default: `push`

* **`active`** (boolean)
  Determines if notifications are sent when the webhook is triggered. Set to true to send notifications.
  Default: `true`

### HTTP response status codes

* **201** - Created

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/hooks \
  -d '{
  "name": "web",
  "active": true,
  "events": [
    "push",
    "pull_request"
  ],
  "config": {
    "url": "https://example.com/webhook",
    "content_type": "json",
    "insecure_ssl": "0"
  }
}'
```

**Response schema (Status: 201):**

* `type`: required, string
* `id`: required, integer
* `name`: required, string
* `active`: required, boolean
* `events`: required, array of string
* `config`: required, `Webhook Configuration`:
  * `url`: string, format: uri
  * `content_type`: string
  * `secret`: string
  * `insecure_ssl`: one of:
    * **string**
    * **number**
* `updated_at`: required, string, format: date-time
* `created_at`: required, string, format: date-time
* `url`: required, string, format: uri
* `test_url`: required, string, format: uri
* `ping_url`: required, string, format: uri
* `deliveries_url`: string, format: uri
* `last_response`: required, `Hook Response`:
  * `code`: required, integer or null
  * `status`: required, string or null
  * `message`: required, string or null

## Get a repository webhook

```
GET /repos/{owner}/{repo}/hooks/{hook_id}
```

Returns a webhook configured in a repository. To get only the webhook config properties, see "Get a webhook configuration for a repository."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a repository webhook](#create-a-repository-webhook).

## Update a repository webhook

```
PATCH /repos/{owner}/{repo}/hooks/{hook_id}
```

Updates a webhook configured in a repository. If you previously had a secret set, you must provide the same secret or set a new secret or the secret will be removed. If you are only updating individual webhook config properties, use "Update a webhook configuration for a repository."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

#### Body parameters

* **`config`** (object)
  Configuration object of the webhook
  * **`url`** (string)
    The URL to which the payloads will be delivered.
  * **`content_type`** (string)
    The media type used to serialize the payloads. Supported values include json and form. The default is form.
  * **`secret`** (string)
    If provided, the secret will be used as the key to generate the HMAC hex digest value for delivery signature headers.
  * **`insecure_ssl`** (string or number)
    Determines whether the SSL certificate of the host for url will be verified when delivering payloads. Supported values include 0 (verification is performed) and 1 (verification is not performed). The default is 0. We strongly recommend not setting this to 1 as you are subject to man-in-the-middle and other attacks.

* **`events`** (array of strings)
  Determines what events the hook is triggered for. This replaces the entire array of events.
  Default: `push`

* **`add_events`** (array of strings)
  Determines a list of events to be added to the list of events that the Hook triggers for.

* **`remove_events`** (array of strings)
  Determines a list of events to be removed from the list of events that the Hook triggers for.

* **`active`** (boolean)
  Determines if notifications are sent when the webhook is triggered. Set to true to send notifications.
  Default: `true`

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID \
  -d '{
  "active": true,
  "add_events": [
    "pull_request"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a repository webhook](#create-a-repository-webhook).

## Delete a repository webhook

```
DELETE /repos/{owner}/{repo}/hooks/{hook_id}
```

Delete a webhook for an organization.
The authenticated user must be a repository owner, or have admin access in the repository, to delete the webhook.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID
```

**Response schema (Status: 204):**

## Get a webhook configuration for a repository

```
GET /repos/{owner}/{repo}/hooks/{hook_id}/config
```

Returns the webhook configuration for a repository. To get more information about the webhook, including the active state and events, use "Get a repository webhook."
OAuth app tokens and personal access tokens (classic) need the read:repo\_hook or repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID/config
```

**Response schema (Status: 200):**

* `url`: string, format: uri
* `content_type`: string
* `secret`: string
* `insecure_ssl`: one of:
  * **string**
  * **number**

## Update a webhook configuration for a repository

```
PATCH /repos/{owner}/{repo}/hooks/{hook_id}/config
```

Updates the webhook configuration for a repository. To update more information about the webhook, including the active state and events, use "Update a repository webhook."
OAuth app tokens and personal access tokens (classic) need the write:repo\_hook or repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

#### Body parameters

* **`url`** (string)
  The URL to which the payloads will be delivered.

* **`content_type`** (string)
  The media type used to serialize the payloads. Supported values include json and form. The default is form.

* **`secret`** (string)
  If provided, the secret will be used as the key to generate the HMAC hex digest value for delivery signature headers.

* **`insecure_ssl`** (string or number)
  Determines whether the SSL certificate of the host for url will be verified when delivering payloads. Supported values include 0 (verification is performed) and 1 (verification is not performed). The default is 0. We strongly recommend not setting this to 1 as you are subject to man-in-the-middle and other attacks.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example of updating content type and URL

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID/config \
  -d '{
  "content_type": "json",
  "url": "https://example.com/webhook"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a webhook configuration for a repository](#get-a-webhook-configuration-for-a-repository).

## List deliveries for a repository webhook

```
GET /repos/{owner}/{repo}/hooks/{hook_id}/deliveries
```

Returns a list of webhook deliveries for a webhook configured in a repository.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`cursor`** (string)
  Used for pagination: the starting delivery from which the page of deliveries is fetched. Refer to the link header for the next and previous page cursors.

* **`status`** (string)
  Returns webhook deliveries filtered by delivery outcome classification based on status\_code range. A status of success returns deliveries with a status\_code in the 200-399 range (inclusive). A status of failure returns deliveries with a status\_code in the 400-599 range (inclusive).
  Can be one of: `success`, `failure`

### HTTP response status codes

* **200** - OK

* **400** - Bad Request

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID/deliveries
```

**Response schema (Status: 200):**

Array of `Simple webhook delivery`:

* `id`: required, integer, format: int64
* `guid`: required, string
* `delivered_at`: required, string, format: date-time
* `redelivery`: required, boolean
* `duration`: required, number
* `status`: required, string
* `status_code`: required, integer
* `event`: required, string
* `action`: required, string or null
* `installation_id`: required, integer or null, format: int64
* `repository_id`: required, integer or null, format: int64
* `throttled_at`: string or null, format: date-time

## Get a delivery for a repository webhook

```
GET /repos/{owner}/{repo}/hooks/{hook_id}/deliveries/{delivery_id}
```

Returns a delivery for a webhook configured in a repository.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

* **`delivery_id`** (integer) (required)

### HTTP response status codes

* **200** - OK

* **400** - Bad Request

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID/deliveries/DELIVERY_ID
```

**Response schema (Status: 200):**

* `id`: required, integer
* `guid`: required, string
* `delivered_at`: required, string, format: date-time
* `redelivery`: required, boolean
* `duration`: required, number
* `status`: required, string
* `status_code`: required, integer
* `event`: required, string
* `action`: required, string or null
* `installation_id`: required, integer or null
* `repository_id`: required, integer or null
* `throttled_at`: string or null, format: date-time
* `url`: string
* `request`: required, object:
  * `headers`: required, object or null, additional properties allowed
  * `payload`: required, object or null, additional properties allowed
* `response`: required, object:
  * `headers`: required, object or null, additional properties allowed
  * `payload`: required, string or null, additional properties allowed

## Redeliver a delivery for a repository webhook

```
POST /repos/{owner}/{repo}/hooks/{hook_id}/deliveries/{delivery_id}/attempts
```

Redeliver a webhook delivery for a webhook configured in a repository.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

* **`delivery_id`** (integer) (required)

### HTTP response status codes

* **202** - Accepted

* **400** - Bad Request

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID/deliveries/DELIVERY_ID/attempts
```

**Response schema (Status: 202):**

object

## Ping a repository webhook

```
POST /repos/{owner}/{repo}/hooks/{hook_id}/pings
```

This will trigger a ping event to be sent to the hook.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID/pings
```

**Response schema (Status: 204):**

## Test the push repository webhook

```
POST /repos/{owner}/{repo}/hooks/{hook_id}/tests
```

This will trigger the hook with the latest push to the current repository if the hook is subscribed to push events. If the hook is not subscribed to push events, the server will respond with 204 but no test POST will be generated.
Note

Previously /repos/:owner/:repo/hooks/:hook\_id/test

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/hooks/HOOK_ID/tests
```

**Response schema (Status: 204):**