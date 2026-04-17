# REST API endpoints for network configurations

REST API endpoints for network configurations


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List hosted compute network configurations for an organization

```
GET /orgs/{org}/settings/network-configurations
```

Lists all hosted compute network configurations configured in an organization.
OAuth app tokens and personal access tokens (classic) need the read:network_configurations scope to use this endpoint.


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




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/settings/network-configurations
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `network_configurations`: required, array of `Hosted compute network configuration`:
  * `id`: required, string
  * `name`: required, string
  * `compute_service`: string, enum: `none`, `actions`, `codespaces`
  * `network_settings_ids`: array of string
  * `failover_network_settings_ids`: array of string
  * `failover_network_enabled`: boolean
  * `created_on`: required, string or null, format: date-time





## Create a hosted compute network configuration for an organization

```
POST /orgs/{org}/settings/network-configurations
```

Creates a hosted compute network configuration for an organization.
OAuth app tokens and personal access tokens (classic) need the write:network_configurations scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  Name of the network configuration. Must be between 1 and 100 characters and may only contain upper and lowercase letters a-z, numbers 0-9, '.', '-', and '_'.

- **`compute_service`** (string)
  The hosted compute service to use for the network configuration.
  Can be one of: `none`, `actions`

- **`network_settings_ids`** (array of strings) (required)
  A list of identifiers of the network settings resources to use for the network configuration. Exactly one resource identifier must be specified in the list.

- **`failover_network_settings_ids`** (array of strings)
  A list of identifiers of the failover network settings resources to use for the network configuration. Exactly one resource identifier must be specified in the list.

- **`failover_network_enabled`** (boolean)
  Indicates whether the failover network resource is enabled.





### HTTP response status codes


- **201** - Created




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/settings/network-configurations \
  -d '{
  "name": "my-network-configuration",
  "network_settings_ids": [
    "23456789ABDCEF1"
  ],
  "compute_service": "actions"
}'
```

**Response schema (Status: 201):**

* `id`: required, string
* `name`: required, string
* `compute_service`: string, enum: `none`, `actions`, `codespaces`
* `network_settings_ids`: array of string
* `failover_network_settings_ids`: array of string
* `failover_network_enabled`: boolean
* `created_on`: required, string or null, format: date-time





## Get a hosted compute network configuration for an organization

```
GET /orgs/{org}/settings/network-configurations/{network_configuration_id}
```

Gets a hosted compute network configuration configured in an organization.
OAuth app tokens and personal access tokens (classic) need the read:network_configurations scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`network_configuration_id`** (string) (required)
  Unique identifier of the hosted compute network configuration.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/settings/network-configurations/NETWORK_CONFIGURATION_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a hosted compute network configuration for an organization](#create-a-hosted-compute-network-configuration-for-an-organization).





## Update a hosted compute network configuration for an organization

```
PATCH /orgs/{org}/settings/network-configurations/{network_configuration_id}
```

Updates a hosted compute network configuration for an organization.
OAuth app tokens and personal access tokens (classic) need the write:network_configurations scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`network_configuration_id`** (string) (required)
  Unique identifier of the hosted compute network configuration.




#### Body parameters

- **`name`** (string)
  Name of the network configuration. Must be between 1 and 100 characters and may only contain upper and lowercase letters a-z, numbers 0-9, '.', '-', and '_'.

- **`compute_service`** (string)
  The hosted compute service to use for the network configuration.
  Can be one of: `none`, `actions`

- **`network_settings_ids`** (array of strings)
  A list of identifiers of the network settings resources to use for the network configuration. Exactly one resource identifier must be specified in the list.

- **`failover_network_settings_ids`** (array of strings)
  A list of identifiers of the failover network settings resources to use for the network configuration. Exactly one resource identifier must be specified in the list.

- **`failover_network_enabled`** (boolean)
  Indicates whether the failover network resource is enabled.





### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/settings/network-configurations/NETWORK_CONFIGURATION_ID \
  -d '{
  "name": "my-network-configuration",
  "network_settings_ids": [
    "23456789ABDCEF1"
  ],
  "compute_service": "actions"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a hosted compute network configuration for an organization](#create-a-hosted-compute-network-configuration-for-an-organization).





## Delete a hosted compute network configuration from an organization

```
DELETE /orgs/{org}/settings/network-configurations/{network_configuration_id}
```

Deletes a hosted compute network configuration from an organization.
OAuth app tokens and personal access tokens (classic) need the write:network_configurations scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`network_configuration_id`** (string) (required)
  Unique identifier of the hosted compute network configuration.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/settings/network-configurations/NETWORK_CONFIGURATION_ID
```

**Response schema (Status: 204):**





## Get a hosted compute network settings resource for an organization

```
GET /orgs/{org}/settings/network-settings/{network_settings_id}
```

Gets a hosted compute network settings resource configured for an organization.
OAuth app tokens and personal access tokens (classic) need the read:network_configurations scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`network_settings_id`** (string) (required)
  Unique identifier of the hosted compute network settings.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/settings/network-settings/NETWORK_SETTINGS_ID
```

**Response schema (Status: 200):**

* `id`: required, string
* `network_configuration_id`: string
* `name`: required, string
* `subnet_id`: required, string
* `region`: required, string