# REST API endpoints for global webhooks

Use the REST API to manage global webhooks for your enterprise.

## About global webhooks

These endpoints are only available to [authenticated](/en/enterprise-server@3.20/rest/overview/authenticating-to-the-rest-api) site administrators Normal users will receive a `404` response. To learn how to configure global webhooks, see [About global webhooks](/en/enterprise-server@3.20/admin/monitoring-activity-in-your-enterprise/exploring-user-activity/managing-global-webhooks).

Global webhooks are automatically installed on your enterprise. You can use global webhooks to automatically monitor, respond to, or enforce rules for users, organizations, teams, and repositories on your enterprise.

Global webhooks can subscribe to the [organization](/en/enterprise-server@3.20/webhooks-and-events/webhooks/webhook-events-and-payloads#organization), [user](/en/enterprise-server@3.20/webhooks-and-events/webhooks/webhook-events-and-payloads#user), [repository](/en/enterprise-server@3.20/webhooks-and-events/webhooks/webhook-events-and-payloads#repository), [team](/en/enterprise-server@3.20/webhooks-and-events/webhooks/webhook-events-and-payloads#team), [member](/en/enterprise-server@3.20/webhooks-and-events/webhooks/webhook-events-and-payloads#member), [membership](/en/enterprise-server@3.20/webhooks-and-events/webhooks/webhook-events-and-payloads#membership), [fork](/en/enterprise-server@3.20/webhooks-and-events/webhooks/webhook-events-and-payloads#fork), and [ping](/en/enterprise-server@3.20/webhooks-and-events/webhooks/about-webhooks#ping-event) event types.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## List global webhooks

```
GET /admin/hooks
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

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/admin/hooks
```

**Response schema (Status: 200):**

Array of objects:

* `type`: string
* `id`: integer
* `name`: string
* `active`: boolean
* `events`: array of string
* `config`: object:
  * `url`: string
  * `content_type`: string
  * `insecure_ssl`: string
  * `secret`: string
* `updated_at`: string
* `created_at`: string
* `url`: string
* `ping_url`: string

## Create a global webhook

```
POST /admin/hooks
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

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
    If provided, the secret will be used as the key to generate the HMAC hex digest value in the X-Hub-Signature header.
  * **`insecure_ssl`** (string)
    Determines whether the SSL certificate of the host for url will be verified when delivering payloads. Supported values include 0 (verification is performed) and 1 (verification is not performed). The default is 0. We strongly recommend not setting this to 1 as you are subject to man-in-the-middle and other attacks.

* **`events`** (array of strings)
  The events that trigger this webhook. A global webhook can be triggered by user and organization events. Default: user and organization.

* **`active`** (boolean)
  Determines if notifications are sent when the webhook is triggered. Set to true to send notifications.
  Default: `true`

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/hooks \
  -d '{
  "name": "web",
  "events": [
    "organization",
    "user"
  ],
  "config": {
    "url": "https://example.com/webhook",
    "content_type": "json",
    "secret": "secret"
  }
}'
```

**Response schema (Status: 201):**

* `type`: string
* `id`: integer
* `name`: string
* `active`: boolean
* `events`: array of string
* `config`: object:
  * `url`: string
  * `content_type`: string
  * `insecure_ssl`: string
  * `secret`: string
* `updated_at`: string
* `created_at`: string
* `url`: string
* `ping_url`: string

## Get a global webhook

```
GET /admin/hooks/{hook_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

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
  http(s)://HOSTNAME/api/v3/admin/hooks/HOOK_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a global webhook](#create-a-global-webhook).

## Update a global webhook

```
PATCH /admin/hooks/{hook_id}
```

Parameters that are not provided will be overwritten with the default value or removed if no default exists.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

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
    If provided, the secret will be used as the key to generate the HMAC hex digest value in the X-Hub-Signature header.
  * **`insecure_ssl`** (string)
    Determines whether the SSL certificate of the host for url will be verified when delivering payloads. Supported values include 0 (verification is performed) and 1 (verification is not performed). The default is 0. We strongly recommend not setting this to 1 as you are subject to man-in-the-middle and other attacks.

* **`events`** (array of strings)
  The events that trigger this webhook. A global webhook can be triggered by user and organization events. Default: user and organization.

* **`active`** (boolean)
  Determines if notifications are sent when the webhook is triggered. Set to true to send notifications.
  Default: `true`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/admin/hooks/HOOK_ID \
  -d '{
  "events": [
    "organization"
  ],
  "config": {
    "url": "https://example.com/webhook"
  }
}'
```

**Response schema (Status: 200):**

* `type`: string
* `id`: integer
* `name`: string
* `active`: boolean
* `events`: array of string
* `config`: object:
  * `url`: string
  * `content_type`: string
  * `insecure_ssl`: string
* `updated_at`: string
* `created_at`: string
* `url`: string
* `ping_url`: string

## Delete a global webhook

```
DELETE /admin/hooks/{hook_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/admin/hooks/HOOK_ID
```

**Response schema (Status: 204):**

## Ping a global webhook

```
POST /admin/hooks/{hook_id}/pings
```

This will trigger a ping event to be sent to the webhook.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`hook_id`** (integer) (required)
  The unique identifier of the hook. You can find this value in the X-GitHub-Hook-ID header of a webhook delivery.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/hooks/HOOK_ID/pings
```

**Response schema (Status: 204):**