# Licensing

Use the REST API to get licensing information.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List enterprise consumed licenses

```
GET /enterprises/{enterprise}/consumed-licenses
```

Lists the license consumption information for all users, including those from connected servers, associated with an enterprise.
The authenticated user must be an enterprise admin to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - Consumed Licenses Response




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/consumed-licenses
```

**Response schema (Status: 200):**

* `total_seats_consumed`: integer
* `total_seats_purchased`: integer
* `users`: array of objects:
  * `github_com_login`: string
  * `github_com_name`: string or null
  * `enterprise_server_user_ids`: array of string
  * `github_com_user`: boolean
  * `enterprise_server_user`: boolean or null
  * `visual_studio_subscription_user`: boolean
  * `license_type`: string
  * `github_com_profile`: string or null
  * `github_com_member_roles`: array of string
  * `github_com_enterprise_roles`: array of string
  * `github_com_verified_domain_emails`: array of string
  * `github_com_saml_name_id`: string or null
  * `github_com_orgs_with_pending_invites`: array of string
  * `github_com_two_factor_auth`: boolean or null
  * `enterprise_server_emails`: array of string
  * `visual_studio_license_status`: string or null
  * `visual_studio_subscription_email`: string or null
  * `total_user_accounts`: integer





## Get a license sync status

```
GET /enterprises/{enterprise}/license-sync-status
```

Gets information about the status of a license sync job for an enterprise.
The authenticated user must be an enterprise admin to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **200** - License Sync Status Response




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/license-sync-status
```

**Response schema (Status: 200):**

* `server_instances`: array of objects:
  * `server_id`: string
  * `hostname`: string
  * `last_sync`: object:
    * `date`: string
    * `status`: string
    * `error`: string





## Get GitHub Advanced Security active committers for an enterprise

```
GET /enterprises/{enterprise}/settings/billing/advanced-security
```

Gets the GitHub Advanced Security active committers for an enterprise per repository. The authenticated user must be an enterprise admin or billing manager.
Each distinct user login across all repositories is counted as a single Advanced Security seat, so the total_advanced_security_committers is not the sum of active_users for each repository.
The total number of repositories with committer information is tracked by the total_count field.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`advanced_security_product`** (string)
  The security product to get GitHub Advanced Security active committers for.
For standalone Code Scanning or Secret Protection products, this parameter is required to specify which product you want committer information for. For other plans this parameter cannot be used.
  Can be one of: `code_security`, `secret_protection`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - Success




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/settings/billing/advanced-security
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