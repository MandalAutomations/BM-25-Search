# REST API endpoints for organization webhooks

Use the REST API to interact with webhooks in an organization.

## About organization webhooks

Organization webhooks allow your server to receive HTTP `POST` payloads whenever certain events happen in an organization. For more information, see [Webhooks documentation](/en/webhooks).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List organization webhooks

```
GET /orgs/{org}/hooks
```

List webhooks for an organization.
The authenticated user must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

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

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/hooks
```

**Response schema (Status: 200):**

Array of `Org Hook`:

* `id`: required, integer
* `url`: required, string, format: uri
* `ping_url`: required, string, format: uri
* `deliveries_url`: string, format: uri
* `name`: required, string
* `events`: required, array of string
* `active`: required, boolean
* `config`: required, object:
  * `url`: string
  * `insecure_ssl`: string
  * `content_type`: string
  * `secret`: string
* `updated_at`: required, string, format: date-time
* `created_at`: required, string, format: date-time
* `type`: required, string

## Create an organization webhook

```
POST /orgs/{org}/hooks
```

Create a hook that posts payloads in JSON format.
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or
edit webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`name`** (string) (required)
  Must be passed as "web".

* **`config`** (object) (required)
  Key/value pairs to provide settings for this webhook.
  * **`url`** (string) (required)
    The URL to which the payloads will be delivered.
  * **`content_type`** (string)
    The media type used to serialize the payloads. Supported values include json and form. The default is form.
  * **`secret`** (string)
    If provided, the secret will be used as the key to generate the HMAC hex digest value for delivery signature headers.
  * **`insecure_ssl`** (string or number)
    Determines whether the SSL certificate of the host for url will be verified when delivering payloads. Supported values include 0 (verification is performed) and 1 (verification is not performed). The default is 0. We strongly recommend not setting this to 1 as you are subject to man-in-the-middle and other attacks.
  * **`username`** (string)
  * **`password`** (string)

* **`events`** (array of strings)
  Determines what events the hook is triggered for. Set to \["\*"] to receive all possible events.
  Default: `push`

* **`active`** (boolean)
  Determines if notifications are sent when the webhook is triggered. Set to true to send notifications.
  Default: `true`

### HTTP response status codes

* **201** - Created

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/hooks \
  -d '{
  "name": "web",
  "active": true,
  "events": [
    "push",
    "pull_request"
  ],
  "config": {
    "url": "http://example.com/webhook",
    "content_type": "json"
  }
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `url`: required, string, format: uri
* `ping_url`: required, string, format: uri
* `deliveries_url`: string, format: uri
* `name`: required, string
* `events`: required, array of string
* `active`: required, boolean
* `config`: required, object:
  * `url`: string
  * `insecure_ssl`: string
  * `content_type`: string
  * `secret`: string
* `updated_at`: required, string, format: date-time
* `created_at`: required, string, format: date-time
* `type`: required, string

## Get an organization webhook

```
GET /orgs/{org}/hooks/{hook_id}
```

Returns a webhook configured in an organization. To get only the webhook
config properties, see "Get a webhook configuration for an organization.
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/hooks/HOOK_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an organization webhook](#create-an-organization-webhook).

## Update an organization webhook

```
PATCH /orgs/{org}/hooks/{hook_id}
```

Updates a webhook configured in an organization. When you update a webhook,
the secret will be overwritten. If you previously had a secret set, you must
provide the same secret or set a new secret or the secret will be removed. If
you are only updating individual webhook config properties, use "Update a webhook
configuration for an organization".
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

#### Body parameters

* **`config`** (object)
  Key/value pairs to provide settings for this webhook.
  * **`url`** (string) (required)
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

* **`name`** (string)

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
  https://api.github.com/orgs/ORG/hooks/HOOK_ID \
  -d '{
  "active": true,
  "events": [
    "pull_request"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an organization webhook](#create-an-organization-webhook).

## Delete an organization webhook

```
DELETE /orgs/{org}/hooks/{hook_id}
```

Delete a webhook for an organization.
The authenticated user must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/hooks/HOOK_ID
```

**Response schema (Status: 204):**

## Get a webhook configuration for an organization

```
GET /orgs/{org}/hooks/{hook_id}/config
```

Returns the webhook configuration for an organization. To get more information about the webhook, including the active state and events, use "Get an organization webhook ."
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/hooks/HOOK_ID/config
```

**Response schema (Status: 200):**

* `url`: string, format: uri
* `content_type`: string
* `secret`: string
* `insecure_ssl`: one of:
  * **string**
  * **number**

## Update a webhook configuration for an organization

```
PATCH /orgs/{org}/hooks/{hook_id}/config
```

Updates the webhook configuration for an organization. To update more information about the webhook, including the active state and events, use "Update an organization webhook ."
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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

#### Update an existing webhook

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/hooks/HOOK_ID/config \
  -d '{
  "url": "http://example.com/webhook",
  "content_type": "json",
  "insecure_ssl": "0",
  "secret": "********"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a webhook configuration for an organization](#get-a-webhook-configuration-for-an-organization).

## List deliveries for an organization webhook

```
GET /orgs/{org}/hooks/{hook_id}/deliveries
```

Returns a list of webhook deliveries for a webhook configured in an organization.
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/hooks/HOOK_ID/deliveries
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

## Get a webhook delivery for an organization webhook

```
GET /orgs/{org}/hooks/{hook_id}/deliveries/{delivery_id}
```

Returns a delivery for a webhook configured in an organization.
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/hooks/HOOK_ID/deliveries/DELIVERY_ID
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

## Redeliver a delivery for an organization webhook

```
POST /orgs/{org}/hooks/{hook_id}/deliveries/{delivery_id}/attempts
```

Redeliver a delivery for a webhook configured in an organization.
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/hooks/HOOK_ID/deliveries/DELIVERY_ID/attempts
```

**Response schema (Status: 202):**

object

## Ping an organization webhook

```
POST /orgs/{org}/hooks/{hook_id}/pings
```

This will trigger a ping event
to be sent to the hook.
You must be an organization owner to use this endpoint.
OAuth app tokens and personal access tokens (classic) need admin:org\_hook scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/hooks/HOOK_ID/pings
```

**Response schema (Status: 204):**