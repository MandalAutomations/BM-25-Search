# REST API endpoints for {% data variables.product.prodname\_marketplace %}

Use the REST API to interact with GitHub Marketplace

## About GitHub Marketplace

For more information about GitHub Marketplace, see [GitHub Marketplace](/en/apps/publishing-apps-to-github-marketplace).

These endpoints allow you to see which customers are using a pricing plan, see a customer's purchases, and see if an account has an active subscription.

### Testing with stubbed endpoints

You can [test your GitHub App](/en/apps/publishing-apps-to-github-marketplace/using-the-github-marketplace-api-in-your-app/testing-your-app) with **stubbed data**. Stubbed data is hard-coded, fake data that will not change based on actual subscriptions.

To test with stubbed data, use a stubbed endpoint in place of its production counterpart. This allows you to test whether the API logic succeeds before listing GitHub Apps on GitHub Marketplace.

Make sure to replace stubbed endpoints with production endpoints before deploying your GitHub App.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get a subscription plan for an account

```
GET /marketplace_listing/accounts/{account_id}
```

Shows whether the user or organization account actively subscribes to a plan listed by the authenticated GitHub App. When someone submits a plan change that won't be processed until the end of their billing cycle, you will also see the upcoming pending change.
GitHub Apps must use a JWT to access this endpoint. OAuth apps must use basic authentication with their client ID and client secret to access this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`account_id`** (integer) (required)
  account\_id parameter

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **404** - Not Found when the account has not purchased the listing

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/marketplace_listing/accounts/ACCOUNT_ID
```

**Response schema (Status: 200):**

* `url`: required, string
* `type`: required, string
* `id`: required, integer
* `login`: required, string
* `organization_billing_email`: string
* `email`: string or null
* `marketplace_pending_change`: object or null:
  * `is_installed`: boolean
  * `effective_date`: string
  * `unit_count`: integer or null
  * `id`: integer
  * `plan`: `Marketplace Listing Plan`:
    * `url`: required, string, format: uri
    * `accounts_url`: required, string, format: uri
    * `id`: required, integer
    * `number`: required, integer
    * `name`: required, string
    * `description`: required, string
    * `monthly_price_in_cents`: required, integer
    * `yearly_price_in_cents`: required, integer
    * `price_model`: required, string, enum: `FREE`, `FLAT_RATE`, `PER_UNIT`
    * `has_free_trial`: required, boolean
    * `unit_name`: required, string or null
    * `state`: required, string
    * `bullets`: required, array of string
* `marketplace_purchase`: required, object:
  * `billing_cycle`: string
  * `next_billing_date`: string or null
  * `is_installed`: boolean
  * `unit_count`: integer or null
  * `on_free_trial`: boolean
  * `free_trial_ends_on`: string or null
  * `updated_at`: string
  * `plan`: `Marketplace Listing Plan`:
    * `url`: required, string, format: uri
    * `accounts_url`: required, string, format: uri
    * `id`: required, integer
    * `number`: required, integer
    * `name`: required, string
    * `description`: required, string
    * `monthly_price_in_cents`: required, integer
    * `yearly_price_in_cents`: required, integer
    * `price_model`: required, string, enum: `FREE`, `FLAT_RATE`, `PER_UNIT`
    * `has_free_trial`: required, boolean
    * `unit_name`: required, string or null
    * `state`: required, string
    * `bullets`: required, array of string

## List plans

```
GET /marketplace_listing/plans
```

Lists all plans that are part of your GitHub Marketplace listing.
GitHub Apps must use a JWT to access this endpoint. OAuth apps must use basic authentication with their client ID and client secret to access this endpoint.

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

* **401** - Requires authentication

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/marketplace_listing/plans
```

**Response schema (Status: 200):**

Array of `Marketplace Listing Plan`:

* `url`: required, string, format: uri
* `accounts_url`: required, string, format: uri
* `id`: required, integer
* `number`: required, integer
* `name`: required, string
* `description`: required, string
* `monthly_price_in_cents`: required, integer
* `yearly_price_in_cents`: required, integer
* `price_model`: required, string, enum: `FREE`, `FLAT_RATE`, `PER_UNIT`
* `has_free_trial`: required, boolean
* `unit_name`: required, string or null
* `state`: required, string
* `bullets`: required, array of string

## List accounts for a plan

```
GET /marketplace_listing/plans/{plan_id}/accounts
```

Returns user and organization accounts associated with the specified plan, including free plans. For per-seat pricing, you see the list of accounts that have purchased the plan, including the number of seats purchased. When someone submits a plan change that won't be processed until the end of their billing cycle, you will also see the upcoming pending change.
GitHub Apps must use a JWT to access this endpoint. OAuth apps must use basic authentication with their client ID and client secret to access this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`plan_id`** (integer) (required)
  The unique identifier of the plan.

* **`sort`** (string)
  The property to sort the results by.
  Default: `created`
  Can be one of: `created`, `updated`

* **`direction`** (string)
  To return the oldest accounts first, set to asc. Ignored without the sort parameter.
  Can be one of: `asc`, `desc`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/marketplace_listing/plans/PLAN_ID/accounts
```

**Response schema (Status: 200):**

Array of `Marketplace Purchase`:

* `url`: required, string
* `type`: required, string
* `id`: required, integer
* `login`: required, string
* `organization_billing_email`: string
* `email`: string or null
* `marketplace_pending_change`: object or null:
  * `is_installed`: boolean
  * `effective_date`: string
  * `unit_count`: integer or null
  * `id`: integer
  * `plan`: `Marketplace Listing Plan`:
    * `url`: required, string, format: uri
    * `accounts_url`: required, string, format: uri
    * `id`: required, integer
    * `number`: required, integer
    * `name`: required, string
    * `description`: required, string
    * `monthly_price_in_cents`: required, integer
    * `yearly_price_in_cents`: required, integer
    * `price_model`: required, string, enum: `FREE`, `FLAT_RATE`, `PER_UNIT`
    * `has_free_trial`: required, boolean
    * `unit_name`: required, string or null
    * `state`: required, string
    * `bullets`: required, array of string
* `marketplace_purchase`: required, object:
  * `billing_cycle`: string
  * `next_billing_date`: string or null
  * `is_installed`: boolean
  * `unit_count`: integer or null
  * `on_free_trial`: boolean
  * `free_trial_ends_on`: string or null
  * `updated_at`: string
  * `plan`: `Marketplace Listing Plan`:
    * `url`: required, string, format: uri
    * `accounts_url`: required, string, format: uri
    * `id`: required, integer
    * `number`: required, integer
    * `name`: required, string
    * `description`: required, string
    * `monthly_price_in_cents`: required, integer
    * `yearly_price_in_cents`: required, integer
    * `price_model`: required, string, enum: `FREE`, `FLAT_RATE`, `PER_UNIT`
    * `has_free_trial`: required, boolean
    * `unit_name`: required, string or null
    * `state`: required, string
    * `bullets`: required, array of string

## Get a subscription plan for an account (stubbed)

```
GET /marketplace_listing/stubbed/accounts/{account_id}
```

Shows whether the user or organization account actively subscribes to a plan listed by the authenticated GitHub App. When someone submits a plan change that won't be processed until the end of their billing cycle, you will also see the upcoming pending change.
GitHub Apps must use a JWT to access this endpoint. OAuth apps must use basic authentication with their client ID and client secret to access this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`account_id`** (integer) (required)
  account\_id parameter

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

* **404** - Not Found when the account has not purchased the listing

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/marketplace_listing/stubbed/accounts/ACCOUNT_ID
```

**Response schema (Status: 200):**

Same response schema as [Get a subscription plan for an account](#get-a-subscription-plan-for-an-account).

## List plans (stubbed)

```
GET /marketplace_listing/stubbed/plans
```

Lists all plans that are part of your GitHub Marketplace listing.
GitHub Apps must use a JWT to access this endpoint. OAuth apps must use basic authentication with their client ID and client secret to access this endpoint.

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

* **401** - Requires authentication

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/marketplace_listing/stubbed/plans
```

**Response schema (Status: 200):**

Same response schema as [List plans](#list-plans).

## List accounts for a plan (stubbed)

```
GET /marketplace_listing/stubbed/plans/{plan_id}/accounts
```

Returns repository and organization accounts associated with the specified plan, including free plans. For per-seat pricing, you see the list of accounts that have purchased the plan, including the number of seats purchased. When someone submits a plan change that won't be processed until the end of their billing cycle, you will also see the upcoming pending change.
GitHub Apps must use a JWT to access this endpoint. OAuth apps must use basic authentication with their client ID and client secret to access this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`plan_id`** (integer) (required)
  The unique identifier of the plan.

* **`sort`** (string)
  The property to sort the results by.
  Default: `created`
  Can be one of: `created`, `updated`

* **`direction`** (string)
  To return the oldest accounts first, set to asc. Ignored without the sort parameter.
  Can be one of: `asc`, `desc`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **401** - Requires authentication

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/marketplace_listing/stubbed/plans/PLAN_ID/accounts
```

**Response schema (Status: 200):**

Same response schema as [List accounts for a plan](#list-accounts-for-a-plan).

## List subscriptions for the authenticated user

```
GET /user/marketplace_purchases
```

Lists the active subscriptions for the authenticated user.

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

* **304** - Not modified

* **401** - Requires authentication

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/marketplace_purchases
```

**Response schema (Status: 200):**

Array of `User Marketplace Purchase`:

* `billing_cycle`: required, string
* `next_billing_date`: required, string or null, format: date-time
* `unit_count`: required, integer or null
* `on_free_trial`: required, boolean
* `free_trial_ends_on`: required, string or null, format: date-time
* `updated_at`: required, string or null, format: date-time
* `account`: required, `Marketplace Account`:
  * `url`: required, string, format: uri
  * `id`: required, integer
  * `type`: required, string
  * `node_id`: string
  * `login`: required, string
  * `email`: string or null, format: email
  * `organization_billing_email`: string or null, format: email
* `plan`: required, `Marketplace Listing Plan`:
  * `url`: required, string, format: uri
  * `accounts_url`: required, string, format: uri
  * `id`: required, integer
  * `number`: required, integer
  * `name`: required, string
  * `description`: required, string
  * `monthly_price_in_cents`: required, integer
  * `yearly_price_in_cents`: required, integer
  * `price_model`: required, string, enum: `FREE`, `FLAT_RATE`, `PER_UNIT`
  * `has_free_trial`: required, boolean
  * `unit_name`: required, string or null
  * `state`: required, string
  * `bullets`: required, array of string

## List subscriptions for the authenticated user (stubbed)

```
GET /user/marketplace_purchases/stubbed
```

Lists the active subscriptions for the authenticated user.

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

* **304** - Not modified

* **401** - Requires authentication

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/marketplace_purchases/stubbed
```

**Response schema (Status: 200):**

Same response schema as [List subscriptions for the authenticated user](#list-subscriptions-for-the-authenticated-user).