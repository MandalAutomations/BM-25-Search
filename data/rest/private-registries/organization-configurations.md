# Organization configurations

Use the REST API to manage private registry configurations for organizations.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List private registries for an organization

```
GET /orgs/{org}/private-registries
```

Lists all private registry configurations available at the organization-level without revealing their encrypted
values.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **400** - Bad Request


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/private-registries
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `configurations`: required, array of `Organization private registry`:
  * `name`: required, string
  * `registry_type`: required, string, enum: `maven_repository`, `nuget_feed`, `goproxy_server`, `npm_registry`, `rubygems_server`, `cargo_registry`, `composer_repository`, `docker_registry`, `git_source`, `helm_registry`, `hex_organization`, `hex_repository`, `pub_repository`, `python_index`, `terraform_registry`
  * `auth_type`: string, enum: `token`, `username_password`, `oidc_azure`, `oidc_aws`, `oidc_jfrog`
  * `url`: string, format: uri
  * `username`: string or null
  * `replaces_base`: boolean, default: `false`
  * `visibility`: required, string, enum: `all`, `private`, `selected`
  * `tenant_id`: string
  * `client_id`: string
  * `aws_region`: string
  * `account_id`: string
  * `role_name`: string
  * `domain`: string
  * `domain_owner`: string
  * `jfrog_oidc_provider_name`: string
  * `audience`: string
  * `identity_mapping_name`: string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time





## Create a private registry for an organization

```
POST /orgs/{org}/private-registries
```

Creates a private registry configuration with an encrypted value for an organization. Encrypt your secret using LibSodium. For more information, see "Encrypting secrets for the REST API."
For OIDC-based registries (oidc_azure, oidc_aws, or oidc_jfrog), the encrypted_value and key_id fields should be omitted.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`registry_type`** (string) (required)
  The registry type.
  Can be one of: `maven_repository`, `nuget_feed`, `goproxy_server`, `npm_registry`, `rubygems_server`, `cargo_registry`, `composer_repository`, `docker_registry`, `git_source`, `helm_registry`, `hex_organization`, `hex_repository`, `pub_repository`, `python_index`, `terraform_registry`

- **`url`** (string) (required)
  The URL of the private registry.

- **`username`** (string or null)
  The username to use when authenticating with the private registry. This field should be omitted if the private registry does not require a username for authentication.

- **`replaces_base`** (boolean)
  Whether this private registry should replace the base registry (e.g., npmjs.org for npm, rubygems.org for rubygems). When set to true, Dependabot will only use this registry and will not fall back to the public registry. When set to false (default), Dependabot will use this registry for scoped packages but may fall back to the public registry for other packages.
  Default: `false`

- **`encrypted_value`** (string)
  The value for your secret, encrypted with LibSodium using the public key retrieved from the Get private registries public key for an organization endpoint. Required when auth_type is token or username_password. Should be omitted for OIDC auth types.

- **`key_id`** (string)
  The ID of the key you used to encrypt the secret. Required when auth_type is token or username_password. Should be omitted for OIDC auth types.

- **`visibility`** (string) (required)
  Which type of organization repositories have access to the private registry. selected means only the repositories specified by selected_repository_ids can access the private registry.
  Can be one of: `all`, `private`, `selected`

- **`selected_repository_ids`** (array of integers)
  An array of repository IDs that can access the organization private registry. You can only provide a list of repository IDs when visibility is set to selected. You can manage the list of selected repositories using the Update a private registry for an organization endpoint. This field should be omitted if visibility is set to all or private.

- **`auth_type`** (string)
  The authentication type for the private registry. Defaults to token if not specified. Use oidc_azure, oidc_aws, or oidc_jfrog for OIDC authentication.
  Can be one of: `token`, `username_password`, `oidc_azure`, `oidc_aws`, `oidc_jfrog`

- **`tenant_id`** (string)
  The tenant ID of the Azure AD application. Required when auth_type is oidc_azure.

- **`client_id`** (string)
  The client ID of the Azure AD application. Required when auth_type is oidc_azure.

- **`aws_region`** (string)
  The AWS region. Required when auth_type is oidc_aws.

- **`account_id`** (string)
  The AWS account ID. Required when auth_type is oidc_aws.

- **`role_name`** (string)
  The AWS IAM role name. Required when auth_type is oidc_aws.

- **`domain`** (string)
  The CodeArtifact domain. Required when auth_type is oidc_aws.

- **`domain_owner`** (string)
  The CodeArtifact domain owner (AWS account ID). Required when auth_type is oidc_aws.

- **`jfrog_oidc_provider_name`** (string)
  The JFrog OIDC provider name. Required when auth_type is oidc_jfrog.

- **`audience`** (string)
  The OIDC audience. Optional for oidc_aws and oidc_jfrog auth types.

- **`identity_mapping_name`** (string)
  The JFrog identity mapping name. Optional for oidc_jfrog auth type.





### HTTP response status codes


- **201** - The organization private registry configuration


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example of a private registry configuration with private visibility

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/private-registries \
  -d '{
  "registry_type": "maven_repository",
  "url": "https://maven.pkg.github.com/organization/",
  "username": "monalisa",
  "replaces_base": true,
  "encrypted_value": "c2VjcmV0",
  "key_id": "012345678912345678",
  "visibility": "private"
}'
```

**Response schema (Status: 201):**

* `name`: required, string
* `registry_type`: required, string, enum: `maven_repository`, `nuget_feed`, `goproxy_server`, `npm_registry`, `rubygems_server`, `cargo_registry`, `composer_repository`, `docker_registry`, `git_source`, `helm_registry`, `hex_organization`, `hex_repository`, `pub_repository`, `python_index`, `terraform_registry`
* `auth_type`: string, enum: `token`, `username_password`, `oidc_azure`, `oidc_aws`, `oidc_jfrog`
* `url`: string, format: uri
* `username`: string
* `replaces_base`: boolean, default: `false`
* `visibility`: required, string, enum: `all`, `private`, `selected`
* `selected_repository_ids`: array of integer
* `tenant_id`: string
* `client_id`: string
* `aws_region`: string
* `account_id`: string
* `role_name`: string
* `domain`: string
* `domain_owner`: string
* `jfrog_oidc_provider_name`: string
* `audience`: string
* `identity_mapping_name`: string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time



#### Example of a private registry configuration with selected visibility

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/private-registries \
  -d '{
  "registry_type": "maven_repository",
  "url": "https://maven.pkg.github.com/organization/",
  "username": "monalisa",
  "encrypted_value": "c2VjcmV0",
  "key_id": "012345678912345678",
  "visibility": "selected",
  "selected_repository_ids": [
    1296269,
    1296280
  ]
}'
```

**Response schema (Status: 201):**

* `name`: required, string
* `registry_type`: required, string, enum: `maven_repository`, `nuget_feed`, `goproxy_server`, `npm_registry`, `rubygems_server`, `cargo_registry`, `composer_repository`, `docker_registry`, `git_source`, `helm_registry`, `hex_organization`, `hex_repository`, `pub_repository`, `python_index`, `terraform_registry`
* `auth_type`: string, enum: `token`, `username_password`, `oidc_azure`, `oidc_aws`, `oidc_jfrog`
* `url`: string, format: uri
* `username`: string
* `replaces_base`: boolean, default: `false`
* `visibility`: required, string, enum: `all`, `private`, `selected`
* `selected_repository_ids`: array of integer
* `tenant_id`: string
* `client_id`: string
* `aws_region`: string
* `account_id`: string
* `role_name`: string
* `domain`: string
* `domain_owner`: string
* `jfrog_oidc_provider_name`: string
* `audience`: string
* `identity_mapping_name`: string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time





## Get private registries public key for an organization

```
GET /orgs/{org}/private-registries/public-key
```

Gets the org public key, which is needed to encrypt private registry secrets. You need to encrypt a secret before you can create or update secrets.
OAuth tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/private-registries/public-key
```

**Response schema (Status: 200):**

* `key_id`: required, string
* `key`: required, string





## Get a private registry for an organization

```
GET /orgs/{org}/private-registries/{secret_name}
```

Get the configuration of a single private registry defined for an organization, omitting its encrypted value.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`secret_name`** (string) (required)
  The name of the secret.






### HTTP response status codes


- **200** - The specified private registry configuration for the organization


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/private-registries/SECRET_NAME
```

**Response schema (Status: 200):**

* `name`: required, string
* `registry_type`: required, string, enum: `maven_repository`, `nuget_feed`, `goproxy_server`, `npm_registry`, `rubygems_server`, `cargo_registry`, `composer_repository`, `docker_registry`, `git_source`, `helm_registry`, `hex_organization`, `hex_repository`, `pub_repository`, `python_index`, `terraform_registry`
* `auth_type`: string, enum: `token`, `username_password`, `oidc_azure`, `oidc_aws`, `oidc_jfrog`
* `url`: string, format: uri
* `username`: string or null
* `replaces_base`: boolean, default: `false`
* `visibility`: required, string, enum: `all`, `private`, `selected`
* `tenant_id`: string
* `client_id`: string
* `aws_region`: string
* `account_id`: string
* `role_name`: string
* `domain`: string
* `domain_owner`: string
* `jfrog_oidc_provider_name`: string
* `audience`: string
* `identity_mapping_name`: string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time





## Update a private registry for an organization

```
PATCH /orgs/{org}/private-registries/{secret_name}
```

Updates a private registry configuration with an encrypted value for an organization. Encrypt your secret using LibSodium. For more information, see "Encrypting secrets for the REST API."
For OIDC-based registries (oidc_azure, oidc_aws, or oidc_jfrog), the encrypted_value and key_id fields should be omitted.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`secret_name`** (string) (required)
  The name of the secret.




#### Body parameters

- **`registry_type`** (string)
  The registry type.
  Can be one of: `maven_repository`, `nuget_feed`, `goproxy_server`, `npm_registry`, `rubygems_server`, `cargo_registry`, `composer_repository`, `docker_registry`, `git_source`, `helm_registry`, `hex_organization`, `hex_repository`, `pub_repository`, `python_index`, `terraform_registry`

- **`url`** (string)
  The URL of the private registry.

- **`username`** (string or null)
  The username to use when authenticating with the private registry. This field should be omitted if the private registry does not require a username for authentication.

- **`replaces_base`** (boolean)
  Whether this private registry should replace the base registry (e.g., npmjs.org for npm, rubygems.org for rubygems). When set to true, Dependabot will only use this registry and will not fall back to the public registry. When set to false (default), Dependabot will use this registry for scoped packages but may fall back to the public registry for other packages.
  Default: `false`

- **`encrypted_value`** (string)
  The value for your secret, encrypted with LibSodium using the public key retrieved from the Get private registries public key for an organization endpoint.

- **`key_id`** (string)
  The ID of the key you used to encrypt the secret.

- **`visibility`** (string)
  Which type of organization repositories have access to the private registry. selected means only the repositories specified by selected_repository_ids can access the private registry.
  Can be one of: `all`, `private`, `selected`

- **`selected_repository_ids`** (array of integers)
  An array of repository IDs that can access the organization private registry. You can only provide a list of repository IDs when visibility is set to selected. This field should be omitted if visibility is set to all or private.

- **`auth_type`** (string)
  The authentication type for the private registry. This field cannot be changed after creation. If provided, it must match the existing auth_type of the configuration. To change the authentication type, delete and recreate the configuration.
  Can be one of: `token`, `username_password`, `oidc_azure`, `oidc_aws`, `oidc_jfrog`

- **`tenant_id`** (string)
  The tenant ID of the Azure AD application. Required when auth_type is oidc_azure.

- **`client_id`** (string)
  The client ID of the Azure AD application. Required when auth_type is oidc_azure.

- **`aws_region`** (string)
  The AWS region. Required when auth_type is oidc_aws.

- **`account_id`** (string)
  The AWS account ID. Required when auth_type is oidc_aws.

- **`role_name`** (string)
  The AWS IAM role name. Required when auth_type is oidc_aws.

- **`domain`** (string)
  The CodeArtifact domain. Required when auth_type is oidc_aws.

- **`domain_owner`** (string)
  The CodeArtifact domain owner (AWS account ID). Required when auth_type is oidc_aws.

- **`jfrog_oidc_provider_name`** (string)
  The JFrog OIDC provider name. Required when auth_type is oidc_jfrog.

- **`audience`** (string)
  The OIDC audience. Optional for oidc_aws and oidc_jfrog auth types.

- **`identity_mapping_name`** (string)
  The JFrog identity mapping name. Optional for oidc_jfrog auth type.





### HTTP response status codes


- **204** - No Content


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.





## Delete a private registry for an organization

```
DELETE /orgs/{org}/private-registries/{secret_name}
```

Delete a private registry configuration at the organization-level.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`secret_name`** (string) (required)
  The name of the secret.






### HTTP response status codes


- **204** - No Content


- **400** - Bad Request


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/private-registries/SECRET_NAME
```

**Response schema (Status: 204):**