# REST API endpoints for GitHub Actions OIDC

Use the REST API to interact with JWTs for OIDC subject claims in GitHub Actions.

## About GitHub Actions OIDC

You can use the REST API to query and manage a customization template for an OpenID Connect (OIDC) subject claim. For more information, see [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List OIDC custom property inclusions for an enterprise

```
GET /enterprises/{enterprise}/actions/oidc/customization/properties/repo
```

Lists the repository custom properties that are included in the OIDC token for repository actions in an enterprise.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - A JSON array of OIDC custom property inclusions

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/actions/oidc/customization/properties/repo
```

**Response schema (Status: 200):**

Array of `Actions OIDC Custom Property Inclusion`:

* `custom_property_name`: required, string
* `inclusion_source`: required, string, enum: `organization`, `enterprise`

## Create an OIDC custom property inclusion for an enterprise

```
POST /enterprises/{enterprise}/actions/oidc/customization/properties/repo
```

Adds a repository custom property to be included in the OIDC token for repository actions in an enterprise.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`custom_property_name`** (string) (required)
  The name of the custom property to include in the OIDC token

### HTTP response status codes

* **201** - OIDC custom property inclusion created

* **400** - Invalid input

* **403** - Forbidden

* **422** - Property inclusion already exists

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/actions/oidc/customization/properties/repo \
  -d '{
  "custom_property_name": "environment"
}'
```

**Response schema (Status: 201):**

* `custom_property_name`: required, string
* `inclusion_source`: required, string, enum: `organization`, `enterprise`

## Delete an OIDC custom property inclusion for an enterprise

```
DELETE /enterprises/{enterprise}/actions/oidc/customization/properties/repo/{custom_property_name}
```

Removes a repository custom property from being included in the OIDC token for repository actions in an enterprise.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`custom_property_name`** (string) (required)
  The name of the custom property to remove from OIDC token inclusion

### HTTP response status codes

* **204** - OIDC custom property inclusion deleted

* **400** - Invalid input

* **403** - Forbidden

* **404** - Property inclusion not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/actions/oidc/customization/properties/repo/CUSTOM_PROPERTY_NAME
```

**Response schema (Status: 204):**

## List OIDC custom property inclusions for an organization

```
GET /orgs/{org}/actions/oidc/customization/properties/repo
```

Lists the repository custom properties that are included in the OIDC token for repository actions in an organization.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - A JSON array of OIDC custom property inclusions

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/oidc/customization/properties/repo
```

**Response schema (Status: 200):**

Same response schema as [List OIDC custom property inclusions for an enterprise](#list-oidc-custom-property-inclusions-for-an-enterprise).

## Create an OIDC custom property inclusion for an organization

```
POST /orgs/{org}/actions/oidc/customization/properties/repo
```

Adds a repository custom property to be included in the OIDC token for repository actions in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`custom_property_name`** (string) (required)
  The name of the custom property to include in the OIDC token

### HTTP response status codes

* **201** - OIDC custom property inclusion created

* **400** - Invalid input

* **403** - Forbidden

* **422** - Property inclusion already exists

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/actions/oidc/customization/properties/repo \
  -d '{
  "custom_property_name": "environment"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create an OIDC custom property inclusion for an enterprise](#create-an-oidc-custom-property-inclusion-for-an-enterprise).

## Delete an OIDC custom property inclusion for an organization

```
DELETE /orgs/{org}/actions/oidc/customization/properties/repo/{custom_property_name}
```

Removes a repository custom property from being included in the OIDC token for repository actions in an organization.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`custom_property_name`** (string) (required)
  The name of the custom property to remove from OIDC token inclusion

### HTTP response status codes

* **204** - OIDC custom property inclusion deleted

* **400** - Invalid input

* **403** - Forbidden

* **404** - Property inclusion not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/oidc/customization/properties/repo/CUSTOM_PROPERTY_NAME
```

**Response schema (Status: 204):**

## Get the customization template for an OIDC subject claim for an organization

```
GET /orgs/{org}/actions/oidc/customization/sub
```

Gets the customization template for an OpenID Connect (OIDC) subject claim.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - A JSON serialized template for OIDC subject claim customization

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/oidc/customization/sub
```

**Response schema (Status: 200):**

* `include_claim_keys`: required, array of string

## Set the customization template for an OIDC subject claim for an organization

```
PUT /orgs/{org}/actions/oidc/customization/sub
```

Creates or updates the customization template for an OpenID Connect (OIDC) subject claim.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`include_claim_keys`** (array of strings)
  Array of unique strings. Each claim key can only contain alphanumeric characters and underscores.

### HTTP response status codes

* **201** - Empty response

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/oidc/customization/sub \
  -d '{
  "include_claim_keys": [
    "repo",
    "context"
  ]
}'
```

**Response schema (Status: 201):**

## Get the customization template for an OIDC subject claim for a repository

```
GET /repos/{owner}/{repo}/actions/oidc/customization/sub
```

Gets the customization template for an OpenID Connect (OIDC) subject claim.
OAuth tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - Status response

* **400** - Bad Request

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/oidc/customization/sub
```

**Response schema (Status: 200):**

* `use_default`: required, boolean
* `include_claim_keys`: array of string

## Set the customization template for an OIDC subject claim for a repository

```
PUT /repos/{owner}/{repo}/actions/oidc/customization/sub
```

Sets the customization template and opt-in or opt-out flag for an OpenID Connect (OIDC) subject claim for a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`use_default`** (boolean) (required)
  Whether to use the default template or not. If true, the include\_claim\_keys field is ignored.

* **`include_claim_keys`** (array of strings)
  Array of unique strings. Each claim key can only contain alphanumeric characters and underscores.

### HTTP response status codes

* **201** - Empty response

* **400** - Bad Request

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/oidc/customization/sub \
  -d '{
  "use_default": false,
  "include_claim_keys": [
    "repo",
    "context"
  ]
}'
```

**Response schema (Status: 201):**