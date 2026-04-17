# REST API endpoints for enterprise security features for code

Use the REST API to manage use of security features for your enterprise.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get code security and analysis features for an enterprise

```
GET /enterprises/{enterprise}/code_security_and_analysis
```

Warning

Closing down notice: The ability to fetch code security and analysis settings for an enterprise is closing down. Please use code security configurations instead. For more information, see the changelog.

Gets code security and analysis settings for the specified enterprise.
The authenticated user must be an administrator of the enterprise in order to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/code_security_and_analysis
```

**Response schema (Status: 200):**

* `advanced_security_enabled_for_new_repositories`: required, boolean
* `advanced_security_enabled_for_new_user_namespace_repositories`: boolean
* `dependabot_alerts_enabled_for_new_repositories`: required, boolean
* `secret_scanning_enabled_for_new_repositories`: required, boolean
* `secret_scanning_push_protection_enabled_for_new_repositories`: required, boolean
* `secret_scanning_push_protection_custom_link`: string or null
* `secret_scanning_non_provider_patterns_enabled_for_new_repositories`: boolean
* `secret_scanning_validity_checks_enabled`: boolean

## Update code security and analysis features for an enterprise

```
PATCH /enterprises/{enterprise}/code_security_and_analysis
```

Warning

Closing down notice: The ability to update code security and analysis settings for an enterprise is closing down. Please use code security configurations instead. For more information, see the changelog.

Updates the settings for advanced security, Dependabot alerts, secret scanning, and push protection for new repositories in an enterprise.
The authenticated user must be an administrator of the enterprise to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`advanced_security_enabled_for_new_repositories`** (boolean)
  Whether GitHub Advanced Security is automatically enabled for new repositories. For more information, see "About GitHub Advanced Security."

* **`advanced_security_enabled_new_user_namespace_repos`** (boolean)
  Whether GitHub Advanced Security is automatically enabled for new user namespace repositories. For more information, see "About GitHub Advanced Security."

* **`dependabot_alerts_enabled_for_new_repositories`** (boolean)
  Whether Dependabot alerts are automatically enabled for new repositories. For more information, see "About Dependabot alerts."

* **`secret_scanning_enabled_for_new_repositories`** (boolean)
  Whether secret scanning is automatically enabled for new repositories. For more information, see "About secret scanning."

* **`secret_scanning_push_protection_enabled_for_new_repositories`** (boolean)
  Whether secret scanning push protection is automatically enabled for new repositories. For more information, see "Protecting pushes with secret scanning."

* **`secret_scanning_push_protection_custom_link`** (string or null)
  The URL that will be displayed to contributors who are blocked from pushing a secret. For more information, see "Protecting pushes with secret scanning."
  To disable this functionality, set this field to null.

* **`secret_scanning_non_provider_patterns_enabled_for_new_repositories`** (boolean or null)
  Whether secret scanning of non-provider patterns is enabled for new repositories under this enterprise.

### HTTP response status codes

* **204** - Action started

* **404** - Resource not found

* **422** - The action could not be taken due to an in progress enablement, or a policy is preventing enablement

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/code_security_and_analysis \
  -d '{
  "advanced_security_enabled_for_new_repositories": true,
  "advanced_security_enabled_new_user_namespace_repos": true,
  "dependabot_alerts_enabled_for_new_repositories": true,
  "secret_scanning_enabled_for_new_repositories": true,
  "secret_scanning_push_protection_enabled_for_new_repositories": true,
  "secret_scanning_push_protection_custom_link": "https://github.com/test-org/test-repo/blob/main/README.md",
  "secret_scanning_non_provider_patterns_enabled_for_new_repositories": true
}'
```

**Response schema (Status: 204):**

## Enable or disable a security feature

```
POST /enterprises/{enterprise}/{security_product}/{enablement}
```

Warning

Closing down notice: The ability to enable or disable a security feature for an enterprise is closing down. Please use code security configurations instead. For more information, see the changelog.

Enables or disables the specified security feature for all repositories in an enterprise.
The authenticated user must be an administrator of the enterprise to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`security_product`** (string) (required)
  The security feature to enable or disable.
  Can be one of: `advanced_security`, `advanced_security_user_namespace`, `dependabot_alerts`, `secret_scanning`, `secret_scanning_push_protection`, `secret_scanning_non_provider_patterns`

* **`enablement`** (string) (required)
  The action to take.
  enable\_all means to enable the specified security feature for all repositories in the enterprise.
  disable\_all means to disable the specified security feature for all repositories in the enterprise.
  Can be one of: `enable_all`, `disable_all`

### HTTP response status codes

* **204** - Action started

* **404** - Resource not found

* **422** - The action could not be taken due to an in progress enablement, or a policy is preventing enablement

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/SECURITY_PRODUCT/ENABLEMENT
```

**Response schema (Status: 204):**