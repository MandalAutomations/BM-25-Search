# Billing usage

Use the REST API to get billing usage information.

The endpoints on this page return usage that is billed to the account associated with the endpoint. For help deciding which level of usage to report on, see [Automating usage reporting with the REST API](/en/billing/tutorials/automate-usage-reporting#step-1-decide-what-level-to-report-on).

* User endpoints return Copilot usage that is billed directly to an individual user’s personal account. These endpoints are only applicable if the user has purchased their own Copilot plan.
* If a user’s Copilot license is managed and billed through an organization or enterprise, their usage is not included in user-level endpoints. In that case, you must use the organization- or enterprise-level endpoints instead.

To view enterprise-level endpoints, select the dropdown menu at the top of the page and switch from Free, Pro, & Team to GitHub Enterprise Cloud.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get billing premium request usage report for an organization

```
GET /organizations/{org}/settings/billing/premium_request/usage
```

Gets a report of premium request usage for an organization. To use this endpoint, you must be an administrator of an organization within an enterprise or an organization account.
Note: Only data from the past 24 months is accessible via this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`year`** (integer)
  If specified, only return results for a single year. The value of year is an integer with four digits representing a year. For example, 2025. Default value is the current year.

* **`month`** (integer)
  If specified, only return results for a single month. The value of month is an integer between 1 and 12. Default value is the current month. If no year is specified the default year is used.

* **`day`** (integer)
  If specified, only return results for a single day. The value of day is an integer between 1 and 31. If no year or month is specified, the default year and month are used.

* **`user`** (string)
  The user name to query usage for. The name is not case sensitive.

* **`model`** (string)
  The model name to query usage for. The name is not case sensitive.

* **`product`** (string)
  The product name to query usage for. The name is not case sensitive.

### HTTP response status codes

* **200** - Response when getting a billing premium request usage report

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/organizations/ORG/settings/billing/premium_request/usage
```

**Response schema (Status: 200):**

* `timePeriod`: required, object:
  * `year`: required, integer
  * `month`: integer
  * `day`: integer
* `organization`: required, string
* `user`: string
* `product`: string
* `model`: string
* `usageItems`: required, array of objects:
  * `product`: required, string
  * `sku`: required, string
  * `model`: required, string
  * `unitType`: required, string
  * `pricePerUnit`: required, number
  * `grossQuantity`: required, number
  * `grossAmount`: required, number
  * `discountQuantity`: required, number
  * `discountAmount`: required, number
  * `netQuantity`: required, number
  * `netAmount`: required, number

## Get billing usage report for an organization

```
GET /organizations/{org}/settings/billing/usage
```

Gets a report of the total usage for an organization. To use this endpoint, you must be an administrator of an organization within an enterprise or an organization account.
Note: This endpoint is only available to organizations with access to the enhanced billing platform. For more information, see "About the enhanced billing platform."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`year`** (integer)
  If specified, only return results for a single year. The value of year is an integer with four digits representing a year. For example, 2025. Default value is the current year.

* **`month`** (integer)
  If specified, only return results for a single month. The value of month is an integer between 1 and 12. If no year is specified the default year is used.

* **`day`** (integer)
  If specified, only return results for a single day. The value of day is an integer between 1 and 31. If no year or month is specified, the default year and month are used.

### HTTP response status codes

* **200** - Billing usage report response for an organization

* **400** - Bad Request

* **403** - Forbidden

* **500** - Internal Error

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/organizations/ORG/settings/billing/usage
```

**Response schema (Status: 200):**

* `usageItems`: array of objects:
  * `date`: required, string
  * `product`: required, string
  * `sku`: required, string
  * `quantity`: required, integer
  * `unitType`: required, string
  * `pricePerUnit`: required, number
  * `grossAmount`: required, number
  * `discountAmount`: required, number
  * `netAmount`: required, number
  * `organizationName`: required, string
  * `repositoryName`: string

## Get billing usage summary for an organization

```
GET /organizations/{org}/settings/billing/usage/summary
```

Note

This endpoint is in public preview and is subject to change.

Gets a summary report of usage for an organization. To use this endpoint, you must be an administrator of an organization within an enterprise or an organization account.
Note: Only data from the past 24 months is accessible via this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`year`** (integer)
  If specified, only return results for a single year. The value of year is an integer with four digits representing a year. For example, 2025. Default value is the current year.

* **`month`** (integer)
  If specified, only return results for a single month. The value of month is an integer between 1 and 12. Default value is the current month. If no year is specified the default year is used.

* **`day`** (integer)
  If specified, only return results for a single day. The value of day is an integer between 1 and 31. If no year or month is specified, the default year and month are used.

* **`repository`** (string)
  The repository name to query for usage in the format owner/repository.

* **`product`** (string)
  The product name to query usage for. The name is not case sensitive.

* **`sku`** (string)
  The SKU to query for usage.

### HTTP response status codes

* **200** - Response when getting a billing usage summary

* **400** - Bad Request

* **403** - Forbidden

* **500** - Internal Error

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/organizations/ORG/settings/billing/usage/summary
```

**Response schema (Status: 200):**

* `timePeriod`: required, object:
  * `year`: required, integer
  * `month`: integer
  * `day`: integer
* `organization`: required, string
* `repository`: string
* `product`: string
* `sku`: string
* `usageItems`: required, array of objects:
  * `product`: required, string
  * `sku`: required, string
  * `unitType`: required, string
  * `pricePerUnit`: required, number
  * `grossQuantity`: required, number
  * `grossAmount`: required, number
  * `discountQuantity`: required, number
  * `discountAmount`: required, number
  * `netQuantity`: required, number
  * `netAmount`: required, number

## Get billing premium request usage report for a user

```
GET /users/{username}/settings/billing/premium_request/usage
```

Gets a report of premium request usage for a user.
Note: Only data from the past 24 months is accessible via this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`year`** (integer)
  If specified, only return results for a single year. The value of year is an integer with four digits representing a year. For example, 2025. Default value is the current year.

* **`month`** (integer)
  If specified, only return results for a single month. The value of month is an integer between 1 and 12. Default value is the current month. If no year is specified the default year is used.

* **`day`** (integer)
  If specified, only return results for a single day. The value of day is an integer between 1 and 31. If no year or month is specified, the default year and month are used.

* **`model`** (string)
  The model name to query usage for. The name is not case sensitive.

* **`product`** (string)
  The product name to query usage for. The name is not case sensitive.

### HTTP response status codes

* **200** - Response when getting a billing premium request usage report

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/settings/billing/premium_request/usage
```

**Response schema (Status: 200):**

* `timePeriod`: required, object:
  * `year`: required, integer
  * `month`: integer
  * `day`: integer
* `user`: required, string
* `product`: string
* `model`: string
* `usageItems`: required, array of objects:
  * `product`: required, string
  * `sku`: required, string
  * `model`: required, string
  * `unitType`: required, string
  * `pricePerUnit`: required, number
  * `grossQuantity`: required, number
  * `grossAmount`: required, number
  * `discountQuantity`: required, number
  * `discountAmount`: required, number
  * `netQuantity`: required, number
  * `netAmount`: required, number

## Get billing usage report for a user

```
GET /users/{username}/settings/billing/usage
```

Gets a report of the total usage for a user.
Note: This endpoint is only available to users with access to the enhanced billing platform.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`year`** (integer)
  If specified, only return results for a single year. The value of year is an integer with four digits representing a year. For example, 2025. Default value is the current year.

* **`month`** (integer)
  If specified, only return results for a single month. The value of month is an integer between 1 and 12. If no year is specified the default year is used.

* **`day`** (integer)
  If specified, only return results for a single day. The value of day is an integer between 1 and 31. If no year or month is specified, the default year and month are used.

### HTTP response status codes

* **200** - Response when getting a billing usage report

* **400** - Bad Request

* **403** - Forbidden

* **500** - Internal Error

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/settings/billing/usage
```

**Response schema (Status: 200):**

* `usageItems`: array of objects:
  * `date`: required, string
  * `product`: required, string
  * `sku`: required, string
  * `quantity`: required, integer
  * `unitType`: required, string
  * `pricePerUnit`: required, number
  * `grossAmount`: required, number
  * `discountAmount`: required, number
  * `netAmount`: required, number
  * `repositoryName`: string

## Get billing usage summary for a user

```
GET /users/{username}/settings/billing/usage/summary
```

Note

This endpoint is in public preview and is subject to change.

Gets a summary report of usage for a user.
Note: Only data from the past 24 months is accessible via this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`year`** (integer)
  If specified, only return results for a single year. The value of year is an integer with four digits representing a year. For example, 2025. Default value is the current year.

* **`month`** (integer)
  If specified, only return results for a single month. The value of month is an integer between 1 and 12. Default value is the current month. If no year is specified the default year is used.

* **`day`** (integer)
  If specified, only return results for a single day. The value of day is an integer between 1 and 31. If no year or month is specified, the default year and month are used.

* **`repository`** (string)
  The repository name to query for usage in the format owner/repository.

* **`product`** (string)
  The product name to query usage for. The name is not case sensitive.

* **`sku`** (string)
  The SKU to query for usage.

### HTTP response status codes

* **200** - Response when getting a billing usage summary

* **400** - Bad Request

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

* **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/settings/billing/usage/summary
```

**Response schema (Status: 200):**

* `timePeriod`: required, object:
  * `year`: required, integer
  * `month`: integer
  * `day`: integer
* `user`: required, string
* `repository`: string
* `product`: string
* `sku`: string
* `usageItems`: required, array of objects:
  * `product`: required, string
  * `sku`: required, string
  * `unitType`: required, string
  * `pricePerUnit`: required, number
  * `grossQuantity`: required, number
  * `grossAmount`: required, number
  * `discountQuantity`: required, number
  * `discountAmount`: required, number
  * `netQuantity`: required, number
  * `netAmount`: required, number