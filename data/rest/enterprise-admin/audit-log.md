# REST API endpoints for enterprise audit logs

Use the REST API to retrieve audit logs for an enterprise.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get the audit log for an enterprise

```
GET /enterprises/{enterprise}/audit-log
```

Gets the audit log for an enterprise.
This endpoint has a rate limit of 1,750 queries per hour per user and IP address. If your integration receives a rate limit error (typically a 403 or 429 response), it should wait before making another request to the GitHub API. For more information, see "Rate limits for the REST API" and "Best practices for integrators."
The authenticated user must be an enterprise admin to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:audit\_log scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`phrase`** (string)
  A search phrase. For more information, see Searching the audit log.

* **`include`** (string)
  The event types to include:

web - returns web (non-Git) events.
git - returns Git events.
all - returns both web and Git events.

The default is web.
Can be one of: `web`, `git`, `all`

* **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for events after this cursor.

* **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for events before this cursor.

* **`order`** (string)
  The order of audit log events. To list newest events first, specify desc. To list oldest events first, specify asc.
  The default is desc.
  Can be one of: `desc`, `asc`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/audit-log
```

**Response schema (Status: 200):**

Array of objects:

* `@timestamp`: integer
* `action`: string
* `active`: boolean
* `active_was`: boolean
* `actor`: string
* `actor_id`: integer
* `actor_location`: object:
  * `country_name`: string
* `data`: object, additional properties allowed
* `org_id`: integer
* `user_id`: integer
* `business_id`: integer
* `blocked_user`: string
* `business`: string
* `config`: array of object
* `config_was`: array of object
* `content_type`: string
* `operation_type`: string
* `created_at`: integer
* `deploy_key_fingerprint`: string
* `_document_id`: string
* `emoji`: string
* `events`: array of object
* `events_were`: array of object
* `explanation`: string
* `fingerprint`: string
* `hook_id`: integer
* `limited_availability`: boolean
* `message`: string
* `name`: string
* `old_user`: string
* `openssh_public_key`: string
* `org`: string
* `previous_visibility`: string
* `read_only`: boolean
* `repo`: string
* `repository`: string
* `repository_public`: boolean
* `target_login`: string
* `team`: string
* `transport_protocol`: integer
* `transport_protocol_name`: string
* `user`: string
* `visibility`: string

## Get the audit log stream key for encrypting secrets

```
GET /enterprises/{enterprise}/audit-log/stream-key
```

Retrieves the audit log streaming public key for encrypting secrets.
When using this endpoint, you must encrypt the credentials following the same encryption steps as outlined in the guide on encrypting secrets. See "Encrypting secrets for the REST API."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - The stream key for the audit log streaming configuration was retrieved successfully.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/audit-log/stream-key
```

**Response schema (Status: 200):**

* `key_id`: required, string
* `key`: required, string

## List audit log stream configurations for an enterprise

```
GET /enterprises/{enterprise}/audit-log/streams
```

Lists the configured audit log streaming configurations for an enterprise.
This only lists configured streams for supported providers.
When using this endpoint, you must encrypt the credentials following the same encryption steps as outlined in the guide on encrypting secrets. See "Encrypting secrets for the REST API."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/audit-log/streams
```

**Response schema (Status: 200):**

Array of objects:

* `id`: integer
* `stream_type`: string
* `stream_details`: string
* `enabled`: boolean
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time
* `paused_at`: string or null, format: date-time

## Create an audit log streaming configuration for an enterprise

```
POST /enterprises/{enterprise}/audit-log/streams
```

Creates an audit log streaming configuration for any of the supported streaming endpoints: Azure Blob Storage, Azure Event Hubs, Amazon S3, Splunk, Google Cloud Storage, Datadog.
When using this endpoint, you must encrypt the credentials following the same encryption steps as outlined in the guide on encrypting secrets. See "Encrypting secrets for the REST API."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`enabled`** (boolean) (required)
  This setting pauses or resumes a stream.

* **`stream_type`** (string) (required)
  The audit log streaming provider. The name is case sensitive.
  Can be one of: `Azure Blob Storage`, `Azure Event Hubs`, `Amazon S3`, `Splunk`, `HTTPS Event Collector`, `Google Cloud Storage`, `Datadog`

* **`vendor_specific`** (object) (required)
  * **`AzureBlobConfig`** (object)
    Azure Blob Config for audit log streaming configuration.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`encrypted_sas_url`** (string) (required)
    * **`container`** (string) (required)
      The name of the Azure Blob Storage container to which the audit logs will be sent.
  * **`AzureHubConfig`** (object)
    Azure Event Hubs Config for audit log streaming configuration.
    * **`name`** (string) (required)
      Instance name of Azure Event Hubs
    * **`encrypted_connstring`** (string) (required)
      Encrypted Connection String for Azure Event Hubs
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
  * **`AmazonS3OIDCConfig`** (object)
    Amazon S3 OIDC Config for audit log streaming configuration.
    * **`bucket`** (string) (required)
      Amazon S3 Bucket Name.
    * **`region`** (string) (required)
      AWS S3 Bucket Region.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`authentication_type`** (string) (required)
      Authentication Type for Amazon S3.
      Can be one of: `oidc`
    * **`arn_role`** (string) (required)
  * **`AmazonS3AccessKeysConfig`** (object)
    Amazon S3 Access Keys Config for audit log streaming configuration.
    * **`bucket`** (string) (required)
      Amazon S3 Bucket Name.
    * **`region`** (string) (required)
      Amazon S3 Bucket Name.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`authentication_type`** (string) (required)
      Authentication Type for Amazon S3.
      Can be one of: `access_keys`
    * **`encrypted_secret_key`** (string) (required)
      Encrypted AWS Secret Key.
    * **`encrypted_access_key_id`** (string) (required)
      Encrypted AWS Access Key ID.
  * **`SplunkConfig`** (object)
    Splunk Config for Audit Log Stream Configuration
    * **`domain`** (string) (required)
      Domain of Splunk instance.
    * **`port`** (integer) (required)
      The port number for connecting to Splunk.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`encrypted_token`** (string) (required)
      Encrypted Token.
    * **`ssl_verify`** (boolean) (required)
      SSL verification helps ensure your events are sent to your Splunk endpoint securely.
  * **`HecConfig`** (object)
    Hec Config for Audit Log Stream Configuration
    * **`domain`** (string) (required)
      Domain of Hec instance.
    * **`port`** (integer) (required)
      The port number for connecting to HEC.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`encrypted_token`** (string) (required)
      Encrypted Token.
    * **`path`** (string) (required)
      Path to send events to.
    * **`ssl_verify`** (boolean) (required)
      SSL verification helps ensure your events are sent to your HEC endpoint securely.
  * **`GoogleCloudConfig`** (object)
    Google Cloud Config for audit log streaming configuration.
    * **`bucket`** (string) (required)
      Google Cloud Bucket Name
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`encrypted_json_credentials`** (string) (required)
  * **`DatadogConfig`** (object)
    Datadog Config for audit log streaming configuration.
    * **`encrypted_token`** (string) (required)
      Encrypted Splunk token.
    * **`site`** (string) (required)
      Datadog Site to use.
      Can be one of: `US`, `US3`, `US5`, `EU1`, `US1-FED`, `AP1`
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.

### HTTP response status codes

* **200** - The audit log stream configuration was created successfully.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/audit-log/streams \
  -d '{
  "enabled": false,
  "stream_type": "Azure Event Hubs",
  "vendor_specific": {
    "namespace": "newnamespace",
    "shared_access_key_name": "newaccesskeyname",
    "shared_access_key": "newaccesskey",
    "event_hub_name": "neweventhub"
  }
}'
```

**Response schema (Status: 200):**

* `id`: required, integer
* `stream_type`: required, string
* `stream_details`: required, string
* `enabled`: required, boolean
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `paused_at`: string or null, format: date-time

## List one audit log streaming configuration via a stream ID

```
GET /enterprises/{enterprise}/audit-log/streams/{stream_id}
```

Lists one audit log stream configuration via a stream ID.
When using this endpoint, you must encrypt the credentials following the same encryption steps as outlined in the guide on encrypting secrets. See "Encrypting secrets for the REST API."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`stream_id`** (integer) (required)
  The ID of the audit log stream configuration.

### HTTP response status codes

* **200** - Lists one audit log stream configuration via stream ID.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/audit-log/streams/STREAM_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an audit log streaming configuration for an enterprise](#create-an-audit-log-streaming-configuration-for-an-enterprise).

## Update an existing audit log stream configuration

```
PUT /enterprises/{enterprise}/audit-log/streams/{stream_id}
```

Updates an existing audit log stream configuration for an enterprise.
When using this endpoint, you must encrypt the credentials following the same encryption steps as outlined in the guide on encrypting secrets. See "Encrypting secrets for the REST API."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`stream_id`** (integer) (required)
  The ID of the audit log stream configuration.

#### Body parameters

* **`enabled`** (boolean) (required)
  This setting pauses or resumes a stream.

* **`stream_type`** (string) (required)
  The audit log streaming provider. The name is case sensitive.
  Can be one of: `Azure Blob Storage`, `Azure Event Hubs`, `Amazon S3`, `Splunk`, `HTTPS Event Collector`, `Google Cloud Storage`, `Datadog`

* **`vendor_specific`** (object) (required)
  * **`AzureBlobConfig`** (object)
    Azure Blob Config for audit log streaming configuration.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`encrypted_sas_url`** (string) (required)
    * **`container`** (string) (required)
      The name of the Azure Blob Storage container to which the audit logs will be sent.
  * **`AzureHubConfig`** (object)
    Azure Event Hubs Config for audit log streaming configuration.
    * **`name`** (string) (required)
      Instance name of Azure Event Hubs
    * **`encrypted_connstring`** (string) (required)
      Encrypted Connection String for Azure Event Hubs
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
  * **`AmazonS3OIDCConfig`** (object)
    Amazon S3 OIDC Config for audit log streaming configuration.
    * **`bucket`** (string) (required)
      Amazon S3 Bucket Name.
    * **`region`** (string) (required)
      AWS S3 Bucket Region.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`authentication_type`** (string) (required)
      Authentication Type for Amazon S3.
      Can be one of: `oidc`
    * **`arn_role`** (string) (required)
  * **`AmazonS3AccessKeysConfig`** (object)
    Amazon S3 Access Keys Config for audit log streaming configuration.
    * **`bucket`** (string) (required)
      Amazon S3 Bucket Name.
    * **`region`** (string) (required)
      Amazon S3 Bucket Name.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`authentication_type`** (string) (required)
      Authentication Type for Amazon S3.
      Can be one of: `access_keys`
    * **`encrypted_secret_key`** (string) (required)
      Encrypted AWS Secret Key.
    * **`encrypted_access_key_id`** (string) (required)
      Encrypted AWS Access Key ID.
  * **`SplunkConfig`** (object)
    Splunk Config for Audit Log Stream Configuration
    * **`domain`** (string) (required)
      Domain of Splunk instance.
    * **`port`** (integer) (required)
      The port number for connecting to Splunk.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`encrypted_token`** (string) (required)
      Encrypted Token.
    * **`ssl_verify`** (boolean) (required)
      SSL verification helps ensure your events are sent to your Splunk endpoint securely.
  * **`HecConfig`** (object)
    Hec Config for Audit Log Stream Configuration
    * **`domain`** (string) (required)
      Domain of Hec instance.
    * **`port`** (integer) (required)
      The port number for connecting to HEC.
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`encrypted_token`** (string) (required)
      Encrypted Token.
    * **`path`** (string) (required)
      Path to send events to.
    * **`ssl_verify`** (boolean) (required)
      SSL verification helps ensure your events are sent to your HEC endpoint securely.
  * **`GoogleCloudConfig`** (object)
    Google Cloud Config for audit log streaming configuration.
    * **`bucket`** (string) (required)
      Google Cloud Bucket Name
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.
    * **`encrypted_json_credentials`** (string) (required)
  * **`DatadogConfig`** (object)
    Datadog Config for audit log streaming configuration.
    * **`encrypted_token`** (string) (required)
      Encrypted Splunk token.
    * **`site`** (string) (required)
      Datadog Site to use.
      Can be one of: `US`, `US3`, `US5`, `EU1`, `US1-FED`, `AP1`
    * **`key_id`** (string) (required)
      Key ID obtained from the audit log stream key endpoint used to encrypt secrets.

### HTTP response status codes

* **200** - Successful update

* **422** - Validation error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/audit-log/streams/STREAM_ID \
  -d '{
  "enabled": false,
  "stream_type": "Azure Event Hubs",
  "vendor_specific": {
    "namespace": "newnamespace",
    "shared_access_key_name": "newaccesskeyname",
    "shared_access_key": "newaccesskey",
    "event_hub_name": "neweventhub"
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an audit log streaming configuration for an enterprise](#create-an-audit-log-streaming-configuration-for-an-enterprise).

## Delete an audit log streaming configuration for an enterprise

```
DELETE /enterprises/{enterprise}/audit-log/streams/{stream_id}
```

Deletes an existing audit log stream configuration for an enterprise.
When using this endpoint, you must encrypt the credentials following the same encryption steps as outlined in the guide on encrypting secrets. See "Encrypting secrets for the REST API."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`stream_id`** (integer) (required)
  The ID of the audit log stream configuration.

### HTTP response status codes

* **204** - The audit log stream configuration was deleted successfully.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/audit-log/streams/STREAM_ID
```

**Response schema (Status: 204):**