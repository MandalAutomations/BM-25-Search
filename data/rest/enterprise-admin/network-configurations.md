# REST API endpoints for enterprise network configurations

Use the REST API to interact with enterprise network configurations.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List hosted compute network configurations for an enterprise

```
GET /enterprises/{enterprise}/network-configurations
```

Lists all hosted compute network configurations configured in an enterprise.


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


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/network-configurations
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





## Create a hosted compute network configuration for an enterprise

```
POST /enterprises/{enterprise}/network-configurations
```

Creates a hosted compute network configuration for an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`name`** (string) (required)
  Name of the network configuration. Must be between 1 and 100 characters and may only contain upper and lowercase letters a-z, numbers 0-9, ., -, and _.

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
  https://api.github.com/enterprises/ENTERPRISE/network-configurations \
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





## Get a hosted compute network configuration for an enterprise

```
GET /enterprises/{enterprise}/network-configurations/{network_configuration_id}
```

Gets a hosted compute network configuration configured in an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

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
  https://api.github.com/enterprises/ENTERPRISE/network-configurations/NETWORK_CONFIGURATION_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a hosted compute network configuration for an enterprise](#create-a-hosted-compute-network-configuration-for-an-enterprise).





## Update a hosted compute network configuration for an enterprise

```
PATCH /enterprises/{enterprise}/network-configurations/{network_configuration_id}
```

Updates a hosted compute network configuration for an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`network_configuration_id`** (string) (required)
  Unique identifier of the hosted compute network configuration.




#### Body parameters

- **`name`** (string)
  Name of the network configuration. Must be between 1 and 100 characters and may only contain upper and lowercase letters a-z, numbers 0-9, ., -, and _.

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
  https://api.github.com/enterprises/ENTERPRISE/network-configurations/NETWORK_CONFIGURATION_ID \
  -d '{
  "name": "my-network-configuration",
  "network_settings_ids": [
    "23456789ABDCEF1"
  ],
  "compute_service": "actions"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a hosted compute network configuration for an enterprise](#create-a-hosted-compute-network-configuration-for-an-enterprise).





## Delete a hosted compute network configuration from an enterprise

```
DELETE /enterprises/{enterprise}/network-configurations/{network_configuration_id}
```

Deletes a hosted compute network configuration from an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

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
  https://api.github.com/enterprises/ENTERPRISE/network-configurations/NETWORK_CONFIGURATION_ID
```

**Response schema (Status: 204):**





## Get a hosted compute network settings resource for an enterprise

```
GET /enterprises/{enterprise}/network-settings/{network_settings_id}
```

Gets a hosted compute network settings resource configured for an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

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
  https://api.github.com/enterprises/ENTERPRISE/network-settings/NETWORK_SETTINGS_ID
```

**Response schema (Status: 200):**

* `id`: required, string
* `network_configuration_id`: string
* `name`: required, string
* `subnet_id`: required, string
* `region`: required, string