# REST API endpoints for billing

Use the REST API to get billing information.

## About billing

You can get billing information for an enterprise. For more information, see [REST API endpoints for billing](/en/enterprise-cloud@latest/rest/enterprise-admin/billing).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get GitHub Advanced Security active committers for an organization

```
GET /orgs/{org}/settings/billing/advanced-security
```

Gets the GitHub Advanced Security active committers for an organization per repository.
Each distinct user login across all repositories is counted as a single Advanced Security seat, so the total\_advanced\_security\_committers is not the sum of advanced\_security\_committers for each repository.
If this organization defers to an enterprise for billing, the total\_advanced\_security\_committers returned from the organization API may include some users that are in more than one organization, so they will only consume a single Advanced Security seat at the enterprise level.
The total number of repositories with committer information is tracked by the total\_count field.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`advanced_security_product`** (string)
  The security product to get GitHub Advanced Security active committers for.
  For standalone Code Scanning or Secret Protection products, this parameter is required to specify which product you want committer information for. For other plans this parameter cannot be used.
  Can be one of: `code_security`, `secret_protection`

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - Success

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/settings/billing/advanced-security
```

**Response schema (Status: 200):**

* `total_advanced_security_committers`: integer
* `total_count`: integer
* `maximum_advanced_security_committers`: integer
* `purchased_advanced_security_committers`: integer
* `repositories`: required, array of objects:
  * `name`: required, string
  * `advanced_security_committers`: required, integer
  * `advanced_security_committers_breakdown`: required, array of objects:
    * `user_login`: required, string
    * `last_pushed_date`: required, string
    * `last_pushed_email`: required, string