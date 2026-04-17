# REST API endpoints for managing GitHub Enterprise Server

Use the REST API to manage your GitHub Enterprise Server instance.

## About the Manage GitHub Enterprise Server API

You can manage your GitHub Enterprise Server instance using the Manage GitHub Enterprise Server API. For example, you can retrieve information about the version of the GitHub Enterprise Server software running on the instance, or on instances with multiple nodes, view the status of replication.

> \[!TIP] You can use this API to replace the functionality of the **Management Console API**, which was removed in GitHub Enterprise Server version 3.15. For a mapping between the endpoints, see [REST API endpoints for Management Console](/en/enterprise-server@3.20/rest/enterprise-admin/management-console) in version 3.14 of the documentation.

Specify the port number when making API calls to endpoints for the Manage GitHub Enterprise Server API. If your instance uses TLS, the port number is 8443. Otherwise, the port number is 8080. If you cannot provide a port number, you'll need to configure your client to automatically follow redirects. For more information, see [Configuring TLS](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/configuring-tls).

You can also use the GitHub Enterprise Server extension of the GitHub CLI to invoke endpoints in the Manage GitHub Enterprise Server API. For more information, see the [`github/gh-es`](https://github.com/github/gh-es/blob/main/README.md) repository.

### Authentication

To authenticate requests to endpoints for the Manage GitHub Enterprise Server API, specify the password for the instance's root site administrator account as an authentication token. Use standard HTTP authentication to send the password. The `api_key` user identifies the root site administrator. The following example demonstrates authentication for this API. Replace ROOT-SITE-ADMINISTRATOR-PASSWORD with the password, and ADMINISTRATION-PORT with either 8443 or 8080.

```shell
curl -L -u "api_key:ROOT-SITE-ADMINISTRATOR-PASSWORD" 'http(s)://HOSTNAME:ADMINISTRATION-PORT/manage'
```

### Authentication as a Management Console user

Management Console user accounts can also authenticate to access these endpoints. For more information, see [Managing access to the Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console/managing-access-to-the-management-console#management-console-user).

To authenticate with the password for a Management Console user account, use standard HTTP authentication. In the following example, replace YOUR\_USER\_NAME and YOUR\_PASSWORD with the account's user name and password.

```shell
curl -L -u "YOUR_USER_NAME:YOUR_PASSWORD" 'http(s)://HOSTNAME:ADMINISTRATION-PORT/manage'
```

### Query parameters

By default, the response includes information from about all configured nodes for the instance. On an instance with multiple nodes, the details originate from `/data/user/common/cluster.conf`. You can use the following query parameters to filter the response for information about specific nodes.

| Query parameter | Description                                                                                                                                                                                                   |
| :-------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `uuid`          | Unique identifier for the node.                                                                                                                                                                               |
| `cluster_role`  | For nodes in a cluster, the roles that apply to the node. For more information, see [About cluster nodes](/en/enterprise-server@3.20/admin/enterprise-management/configuring-clustering/about-cluster-nodes). |

You can specify multiple values for the query parameter by delimiting the values with a comma. For example, the following request uses curl to return any nodes with the `web-server` or `storage-server` role.

```shell
curl -L -u "api_key:ROOT-SITE-ADMINISTRATOR-PASSWORD" 'http(s)://HOSTNAME:ADMINISTRATION-PORT/manage/v1/config/nodes?cluster_role=WebServer,StorageServer'
```

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## Get the configured SSH keys

```
GET /manage/v1/access/ssh
```

Gets the configured SSH keys on all available nodes. For more information, see "Accessing the administrative shell (SSH)."

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/access/ssh
```

**Response schema (Status: 200):**

Array of objects:

* `key`: string, format: ssh-key
* `fingerprint`: string, format: ssh-key fingerprint

## Set a new SSH key

```
POST /manage/v1/access/ssh
```

Adds a SSH key to the authorized\_keys file for your GitHub Enterprise Server instance. This will grant access via SSH to your instance. For more information, see "Accessing the administrative shell (SSH)."

### Parameters

#### Body parameters

* **`key`** (string) (required)
  The public SSH key to add to the authorized\_keys file.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/manage/v1/access/ssh \
  -d '{
  "key": "ssh-rsa AAAAB3NzaC1yc2EAAAADCIABAAAAgQCY/ZiDDOFWcZnYXPwMbvwQDofXPdHxLfxPK+HWGVPd1DLcDncYBUSB0bmCU2g9Sc+oHKLoHhXp0ivau9h+EpmQJ7V8vqsRdD9pc4aL/WAnUyF4o3Y7xL94rlRpVbVo/tNjzcvqxxyzBiYyy3GciCMpYQh/uKt56B94/5PNyIGEEw=="
}'
```

**Response schema (Status: 200):**

Array of objects:

* `hostname`: string, format: hostname
* `uuid`: string, format: uuid
* `message`: string
* `error`: string
* `modified`: boolean

## Delete a SSH key

```
DELETE /manage/v1/access/ssh
```

Deletes a SSH key from the authorized\_keys file for your GitHub Enterprise Server instance. This will remove access via SSH to your instance. For more information, see "Accessing the administrative shell (SSH)."

### Parameters

#### Body parameters

* **`key`** (string) (required)
  The public SSH key to remove from the authorized\_keys file.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/manage/v1/access/ssh \
  -d '{
  "key": "ssh-rsa AAAAB3NzaC1yc2EAAAADCIABAAAAgQCY/ZiDDOFWcZnYXPwMbvwQDofXPdHxLfxPK+HWGVPd1DLcDncYBUSB0bmCU2g9Sc+oHKLoHhXp0ivau9h+EpmQJ7V8vqsRdD9pc4aL/WAnUyF4o3Y7xL94rlRpVbVo/tNjzcvqxxyzBiYyy3GciCMpYQh/uKt56B94/5PNyIGEEw=="
}'
```

**Response schema (Status: 200):**

Array of objects:

* `hostname`: string, format: hostname
* `uuid`: string, format: uuid
* `message`: string
* `error`: string

## Get the system requirement check results for configured cluster nodes

```
GET /manage/v1/checks/system-requirements
```

Checks if the minimum requirements for system hardware resources are met on each configured cluster node.
This endpoint may take several seconds to reply.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/checks/system-requirements
```

**Response schema (Status: 200):**

* `status`: string, enum: `OK`, `FAILED`
* `nodes`: array of objects:
  * `hostname`: string
  * `status`: string, enum: `OK`, `FAILED`
  * `roles_status`: array of objects:
    * `status`: string, enum: `OK`, `FAILED`
    * `role`: string

## Get the status of services running on all cluster nodes

```
GET /manage/v1/cluster/status
```

Gets the status of all services running on each cluster node.
This endpoint may take several seconds to reply.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/cluster/status
```

**Response schema (Status: 200):**

* `status`: string, enum: `UNKNOWN`, `OK`, `WARNING`, `CRITICAL`
* `nodes`: array of objects:
  * `hostname`: string
  * `status`: string, enum: `UNKNOWN`, `OK`, `WARNING`, `CRITICAL`
  * `services`: array of objects:
    * `status`: string, enum: `UNKNOWN`, `OK`, `WARNING`, `CRITICAL`
    * `name`: string
    * `details`: string

## Get the status of a ghe-config-apply run

```
GET /manage/v1/config/apply
```

Displays the current status of ghe-config-apply in the environment or the status of a historical run by ID.

### Parameters

#### Path and query parameters

* **`run_id`** (string)
  The unique run ID of the ghe-config-apply run.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/config/apply
```

**Response schema (Status: 200):**

* `running`: boolean
* `successful`: boolean
* `nodes`: array of objects:
  * `run_id`: string
  * `hostname`: string
  * `running`: boolean
  * `successful`: boolean

## Trigger a ghe-config-apply run

```
POST /manage/v1/config/apply
```

Triggers a run of ghe-config-apply from the ghes-manage agent on your Nomad Delegate instance.
You can provide a run ID or allow one to be generated randomly.

### Parameters

#### Body parameters

* **`run_id`** (string)
  The run ID to execute ghe-config-apply with. If not provided, a run ID will be generated randomly.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/manage/v1/config/apply \
  -d '{
  "run_id": "d34db33f"
}'
```

**Response schema (Status: 200):**

* `run_id`: string

## List events from ghe-config-apply

```
GET /manage/v1/config/apply/events
```

Lists events from an in-process ghe-config-apply run on your Github Enterprise Server instance.

### Parameters

#### Path and query parameters

* **`last_request_id`** (string)
  The unique ID of the last response from a host, used for pagination.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/config/apply/events
```

**Response schema (Status: 200):**

* `nodes`: array of objects:
  * `node`: string
  * `last_request_id`: string
  * `events`: array of objects:
    * `timestamp`: string
    * `severity_text`: string
    * `body`: string
    * `event_name`: string
    * `topology`: string
    * `hostname`: string
    * `config_run_id`: string
    * `trace_id`: string
    * `span_id`: string
    * `span_parent_id`: string
    * `span_depth`: integer

## Initialize instance configuration with license and password

```
POST /manage/v1/config/init
```

When you boot and set up a GitHub instance for the first time, you can use this endpoint to upload a license and set the initial root site administrator password.
Important

To start the configuration process and apply the license, you need to POST to /manage/v1/config/apply

The root site administrator password provided when calling this endpoint is used to authenticate for all other endpoints in the GHES Manage API and the Management Console UI.
Note

The request body for this operation must be submitted as multipart/form-data data. You can can reference the license file by prefixing the filename with the @ symbol using curl. For more information, see the curl documentation.

### Parameters

#### Body parameters

* **`license`** (string) (required)
  The content of your .ghl license file.

* **`password`** (string) (required)
  The root site administrator password.

### HTTP response status codes

* **202** - Accepted

* **400** - Bad request

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/manage/v1/config/init \
  -d '{
  "license": "@enterprise.ghl",
  "password": "provide-password-here!"
}'
```

**Response schema (Status: 202):**

## Get the enterprise license information

```
GET /manage/v1/config/license
```

Gets information about the license that is currently set for the enterprise.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/config/license
```

**Response schema (Status: 200):**

* `advancedSecurityEnabled`: boolean
* `advancedSecuritySeats`: integer
* `clusterSupport`: boolean
* `company`: string
* `croquetSupport`: boolean
* `customTerms`: boolean
* `evaluation`: boolean
* `expireAt`: string, format: date-time
* `insightsEnabled`: boolean
* `insightsExpireAt`: string, format: date-time
* `learningLabEvaluationExpires`: string, format: date-time
* `learningLabSeats`: integer
* `perpetual`: boolean
* `referenceNumber`: string
* `seats`: integer
* `sshAllowed`: boolean
* `supportKey`: string
* `unlimitedSeating`: boolean

## Upload an enterprise license

```
PUT /manage/v1/config/license
```

Uploads a new enterprise license. In order to apply it right away, use the apply query parameter.
Note

The request body for this operation must be submitted as multipart/form-data data. You can can reference the license file by prefixing the filename with the @ symbol using curl. For more information, see the curl documentation.

### Parameters

#### Path and query parameters

* **`apply`** (boolean)
  Whether to instantly apply changes from the license. Otherwise the new license can be applied using the /manage/v1/config/apply endpoint.

#### Body parameters

* **`license`** (string) (required)
  The content of your .ghl license file.

### HTTP response status codes

* **201** - Created

* **202** - Accepted

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example 1: Status Code 201

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/manage/v1/config/license \
  -d '{
  "license": "@enterprise.ghl"
}'
```

**Response schema (Status: 201):**

#### Example 2: Status Code 202

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/manage/v1/config/license \
  -d '{
  "license": "@enterprise.ghl"
}'
```

**Response schema (Status: 202):**

## Check a license

```
GET /manage/v1/config/license/check
```

Check the status of the license that is currently set for the enterprise.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/config/license/check
```

**Response schema (Status: 200):**

* `status`: string, enum: `valid`, `invalid`, `expired`, `cluster mode not supported`

## Get GHES node metadata for all nodes

```
GET /manage/v1/config/nodes
```

Get node metadata for all configured nodes in the current cluster. For more information, see "About clustering."

### Parameters

#### Path and query parameters

* **`uuid`** (string)
  The UUID which identifies a node.

* **`cluster_roles`** (string)
  The cluster roles from the cluster configuration file.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/config/nodes
```

**Response schema (Status: 200):**

* `topology`: string, enum: `SingleNode`, `Ha`, `Cluster`
* `nodes`: array of objects:
  * `hostname`: string
  * `uuid`: string
  * `replica`: boolean
  * `cluster_roles`: array of string, enum: `Blank`, `ActionsServer`, `ConsulServer`, `ElasticsearchServer`, `GitServer`, `JobServer`, `LaunchServer`, `MemcacheServer`, `MetricsServer`, `MssqlServer`, `MysqlServer`, `PagesServer`, `RedisServer`, `StorageServer`, `WebServer`

## Get the GHES settings

```
GET /manage/v1/config/settings
```

Gets a list of settings for a GitHub Enterprise Server instance.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/config/settings
```

**Response schema (Status: 200):**

* `private_mode`: boolean
* `public_pages`: boolean
* `subdomain_isolation`: boolean
* `signup_enabled`: boolean
* `github_hostname`: string
* `identicons_host`: string
* `http_proxy`: string or null
* `auth_mode`: string
* `expire_sessions`: boolean
* `admin_password`: string or null
* `configuration_id`: integer
* `configuration_run_count`: integer
* `avatar`: object:
  * `enabled`: boolean
  * `uri`: string
* `customer`: object:
  * `name`: string
  * `email`: string
  * `uuid`: string
  * `secret_key_data`: string
  * `public_key_data`: string
* `license`: object:
  * `seats`: integer
  * `evaluation`: boolean
  * `perpetual`: boolean
  * `unlimited_seating`: boolean
  * `support_key`: string
  * `ssh_allowed`: boolean
  * `cluster_support`: boolean
  * `expire_at`: string
* `github_ssl`: object:
  * `enabled`: boolean
  * `cert`: string or null
  * `key`: string or null
* `ldap`: object:
  * `host`: string or null
  * `port`: integer
  * `base`: array of string
  * `uid`: string or null
  * `bind_dn`: string or null
  * `password`: string or null
  * `method`: string
  * `search_strategy`: string
  * `user_groups`: array of string
  * `admin_group`: string or null
  * `virtual_attribute_enabled`: boolean
  * `recursive_group_search`: boolean
  * `posix_support`: boolean
  * `user_sync_emails`: boolean
  * `user_sync_keys`: boolean
  * `user_sync_interval`: integer
  * `team_sync_interval`: integer
  * `sync_enabled`: boolean
  * `reconciliation`: object:
    * `user`: string or null
    * `org`: string or null
  * `profile`: object:
    * `uid`: string
    * `name`: string or null
    * `mail`: string or null
    * `key`: string or null
* `cas`: object:
  * `url`: string or null
* `saml`: object:
  * `sso_url`: string or null
  * `certificate`: string or null
  * `certificate_path`: string or null
  * `issuer`: string or null
  * `idp_initiated_sso`: boolean
  * `disable_admin_demote`: boolean
* `github_oauth`: object:
  * `client_id`: string
  * `client_secret`: string
  * `organization_name`: string
  * `organization_team`: string
* `smtp`: object:
  * `enabled`: boolean
  * `address`: string
  * `authentication`: string
  * `port`: string
  * `domain`: string
  * `username`: string
  * `user_name`: string
  * `enable_starttls_auto`: boolean
  * `password`: string
  * `discard-to-noreply-address`: boolean
  * `support_address`: string
  * `support_address_type`: string
  * `noreply_address`: string
* `ntp`: object:
  * `primary_server`: string
  * `secondary_server`: string
* `timezone`: string or null
* `snmp`: object:
  * `enabled`: boolean
  * `community`: string
* `syslog`: object:
  * `enabled`: boolean
  * `server`: string or null
  * `protocol_name`: string
* `assets`: string or null
* `pages`: object:
  * `enabled`: boolean
* `collectd`: object:
  * `enabled`: boolean
  * `server`: string or null
  * `port`: integer
  * `encryption`: string or null
  * `username`: string or null
  * `password`: string or null
* `mapping`: object:
  * `enabled`: boolean
  * `tileserver`: string or null
  * `basemap`: string
  * `token`: string or null
* `load_balancer`: string or null
* `prometheus`: object:
  * `enabled`: boolean
  * `trusted_ips`: string or null

## Set settings

```
PUT /manage/v1/config/settings
```

Updates the settings on your instance. For a list of the available settings, see the Get settings endpoint.
Notes:

The request body only requires the settings parameters that should be updated to be specified, all other parameters will be unmodified or populated from the default values.
You cannot set the Management Console root site administrator password with this API endpoint. Use the ghe-set-password utility to change the management console password. For more information, see "Command-line utilities."

### HTTP response status codes

* **204** - No Content

* **400** - Bad request

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/manage/v1/config/settings \
  -d '{
  "public_pages": true
}'
```

**Response schema (Status: 204):**

## Get the status of maintenance mode

```
GET /manage/v1/maintenance
```

Gets the status and details of maintenance mode on all available nodes. For more information, see "Enabling and scheduling maintenance mode."

### Parameters

#### Path and query parameters

* **`uuid`** (string)
  The UUID which identifies a node.

* **`cluster_roles`** (string)
  The cluster roles from the cluster configuration file.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/maintenance
```

**Response schema (Status: 200):**

Array of objects:

* `hostname`: string, format: hostname
* `uuid`: string, format: uuid
* `status`: string, enum: `on`, `off`, `scheduled`
* `scheduled_time`: string, format: date
* `connection_services`: array of objects:
  * `name`: string
  * `number`: integer
* `can_unset_maintenance`: boolean
* `ip_exception_list`: array of string, format: ip/cidr
* `maintenance_mode_message`: string

## Set the status of maintenance mode

```
POST /manage/v1/maintenance
```

Sets or schedules the maintenance mode. For more information, see "Enabling and scheduling maintenance mode."

### Parameters

#### Body parameters

* **`enabled`** (boolean) (required)
  Whether to enable maintenance mode.

* **`uuid`** (string)
  The UUID of the node to target. This parameter is incompatible with maintenance mode scheduling. Only use uuid if the value of when is empty or now.

* **`when`** (string)
  The time to enable maintenance mode. If this parameter is empty or set to now, maintenance mode is enabled immediately. Otherwise, maintenance mode is enabled at the specified time. The format is ISO 8601.

* **`ip_exception_list`** (array of strings)
  The list of IP addresses to exclude from maintenance mode. IPv4, IPv6, and CIDR addresses are supported.

* **`maintenance_mode_message`** (string)
  The message to display to users when maintenance mode is enabled.

### HTTP response status codes

* **200** - OK

* **400** - Bad request

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/manage/v1/maintenance \
  -d '{
  "enabled": true,
  "when": "2006-01-02T15:04:05+00:00",
  "ip_exception_list": [
    "192.168.1.0/24",
    "1.1.1.1"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Delete a SSH key](#delete-a-ssh-key).

## Get the status of services running on all replica nodes

```
GET /manage/v1/replication/status
```

Gets the status of all services running on each replica node.
This endpoint may take several seconds to reply.

### Parameters

#### Path and query parameters

* **`uuid`** (string)
  The UUID which identifies a node.

* **`cluster_roles`** (string)
  The cluster roles from the cluster configuration file.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/replication/status
```

**Response schema (Status: 200):**

Same response schema as [Get the status of services running on all cluster nodes](#get-the-status-of-services-running-on-all-cluster-nodes).

## Get all GHES release versions for all nodes

```
GET /manage/v1/version
```

Gets the GitHub Enterprise Server release versions that are currently installed on all available nodes. For more information, see "GitHub Enterprise Server releases."

### Parameters

#### Path and query parameters

* **`uuid`** (string)
  The UUID which identifies a node.

* **`cluster_roles`** (string)
  The cluster roles from the cluster configuration file.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

* **500** - Internal error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/manage/v1/version
```

**Response schema (Status: 200):**

Array of objects:

* `hostname`: string, format: hostname
* `version`: object:
  * `version`: string, pattern: `[0-9]\.[0-9]{2}\.[0-9]`
  * `platform`: string, enum: `ami`, `azure`, `esx`, `gce`, `hyperv`, `kvm`
  * `build_id`: string, pattern: `[0-9a-f]{8}`
  * `build_date`: string, format: date