# REST API endpoints for Enterprise Live Migrations

Use the REST API to manage Enterprise Live Migrations on your GitHub Enterprise Server instance.

>[!NOTE] Enterprise Live Migrations is in public preview and subject to change.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List Enterprise Live Migrations

```
GET /enterprise/live-migrations
```

List Enterprise Live Migrations (ELM) for the current GHES appliance.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`page_size`** (integer)
  Number of results per page.

- **`after`** (string)
  Cursor for pagination. Use the value from next_cursor of a previous response.

- **`status`** (string)
  Optional filter by migration status.
  Can be one of: `created`, `queued`, `in_progress`, `paused`, `completed`, `failed`, `terminated`, `all`

### HTTP response status codes

- **200** - OK

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **422** - The migration service is missing the source or target credentials required to service this request. An organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

- **501** - Not implemented.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations
```

**Response schema (Status: 200):**

## Create an Enterprise Live Migration

```
POST /enterprise/live-migrations
```

Create an Enterprise Live Migration (ELM) for a single repository on the current GHES appliance. The migration is created in a created state and is not started; run the start endpoint to launch backfill and live updates. Credentials are referenced by name (pat_name) rather than submitted inline, and are not echoed back in the response.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

- **`source_organization_login`** (string) (required)
  Source organization login on the GHES appliance.

- **`source_repository_name`** (string) (required)
  Source repository name.

- **`target_organization_login`** (string) (required)
  Target organization login on the destination GitHub environment.

- **`target_repository_name`** (string) (required)
  Target repository name.

- **`target_api_endpoint`** (string) (required)
  Migration target API endpoint URL. Must be a valid HTTPS URL.

- **`pat_name`** (string) (required)
  Name of the organization-scoped migration credential set to use. The raw token is never submitted inline and is never returned in the response.

- **`target_visibility`** (string)
  Target repository visibility. Defaults to internal when omitted. A source repository with public visibility must set this explicitly.
  Can be one of: `private`, `internal`

### HTTP response status codes

- **201** - The migration was created. The response contains the new migration identifier and its expiration. No credentials are returned.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict. The request conflicts with the current state of the migration.

- **422** - The migration service is missing the source or target credentials required to service this request. An organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations
```

**Response schema (Status: 201):**

## Get an Enterprise Live Migration

```
GET /enterprise/live-migrations/{migration_id}
```

Retrieve combined status, progress, cutover readiness, expiration, and timing for an Enterprise Live Migration (ELM) on the current GHES appliance.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`migration_id`** (string) (required)
  The ID of the migration.

### HTTP response status codes

- **200** - OK

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **422** - The migration service is missing the source or target credentials required to service this request. An organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations/MIGRATION_ID
```

**Response schema (Status: 200):**

## Cancel an Enterprise Live Migration

```
POST /enterprise/live-migrations/{migration_id}/cancel
```

Cancel an Enterprise Live Migration (ELM) in progress. This terminates the migration: it is cancelled locally, aborted on the migration backend, and its work items are removed. This is a terminal action with no recovery — a subsequent status request reflects the terminated state.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`migration_id`** (string) (required)
  The ID of the migration.

### HTTP response status codes

- **204** - The migration was cancelled. No content is returned; query the migration status to observe the terminal state.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict. The migration is not in a state that can be cancelled (for example, it has already completed or been terminated).

- **422** - The migration service is missing the source or target credentials required to service this request. An organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations/MIGRATION_ID/cancel
```

**Response schema (Status: 204):**

## Cutover an Enterprise Live Migration

```
POST /enterprise/live-migrations/{migration_id}/cutover
```

Initiate cutover for an Enterprise Live Migration (ELM), archiving the source repository and draining remaining changes. Cutover is asynchronous; the migration transitions through cutover_pending and cutover_finalizing to completed. No content is returned — query the migration status to observe progress.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`migration_id`** (string) (required)
  The ID of the migration.

#### Body parameters

- **`force`** (boolean)
  Bypass the cutover readiness checks and initiate cutover even when the migration is not reported as ready. Defaults to false.
  Default: `false`

### HTTP response status codes

- **204** - Cutover was initiated. No content is returned; query the migration status to observe the cutover progress.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict. The migration is not ready for cutover (for example, backfill is still in progress, or the migration has already completed, been cancelled, or failed).

- **422** - The migration service is missing the source or target credentials required to service this request. An organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations/MIGRATION_ID/cutover
```

**Response schema (Status: 204):**

## Pause an Enterprise Live Migration

```
POST /enterprise/live-migrations/{migration_id}/pause
```

Pause source-load work for an active Enterprise Live Migration (ELM). Backfill and Git synchronization are paused while live event collection and delivery continue. The operation is idempotent for a migration that is already paused. No content is returned; query the migration status to observe the durable state.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`migration_id`** (string) (required)
  The unique identifier of the Enterprise Live Migration.

### HTTP response status codes

- **204** - The migration was paused. No content is returned; query the migration status to confirm its current state.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict. The migration is not in a state that can be paused, such as when it has not been started or has already completed.

- **422** - The pause request was accepted by the migration service, but the migration did not complete the transition to paused. Query the migration status and retry. This status is also returned when the migration service is missing the source or target credentials required to service the request; an organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations/MIGRATION_ID/pause
```

**Response schema (Status: 204):**

## Resume an Enterprise Live Migration

```
POST /enterprise/live-migrations/{migration_id}/resume
```

Resume a paused Enterprise Live Migration (ELM). The migration is re-queued and resumes backfill and live updates. A subsequent status request reflects the resumed state.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`migration_id`** (string) (required)
  The ID of the migration.

### HTTP response status codes

- **204** - The migration was resumed. No content is returned; query the migration status to observe the resumed state.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict. The migration is not in a state that can be resumed (for example, it is not paused, or has completed or terminated).

- **422** - The migration service is missing the source or target credentials required to service this request. An organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations/MIGRATION_ID/resume
```

**Response schema (Status: 204):**

## Revert cutover for an Enterprise Live Migration

```
POST /enterprise/live-migrations/{migration_id}/revert-cutover
```

Revert cutover for an Enterprise Live Migration (ELM). This unarchives the source repository and terminates any cutover or migration still in progress so the source repository can be migrated again.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`migration_id`** (string) (required)
  The ID of the migration.

### HTTP response status codes

- **200** - The cutover was reverted.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict. The migration is not in a state where cutover can be reverted.

- **422** - The migration service is missing the source or target credentials required to service this request. An organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

- **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations/MIGRATION_ID/revert-cutover
```

**Response schema (Status: 200):**

## Start an Enterprise Live Migration

```
POST /enterprise/live-migrations/{migration_id}/start
```

Start a created Enterprise Live Migration (ELM), launching backfill and enabling live updates. The migration must be in a startable state (for example, created, paused, or failed); preflight validation runs before the migration is queued unless it has been skipped.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`migration_id`** (string) (required)
  The ID of the migration.

### HTTP response status codes

- **204** - The migration was started (queued for execution). No content is returned; query the migration status to observe progress.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict. The migration is not in a state that can be started (for example, it has already been started or has completed).

- **422** - The migration could not be started because preflight validation did not pass. Query the migration status for details. This status is also returned when the migration service is missing the source or target credentials required to service the request; an organization administrator must configure the required secrets before retrying.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/enterprise/live-migrations/MIGRATION_ID/start
```

**Response schema (Status: 204):**