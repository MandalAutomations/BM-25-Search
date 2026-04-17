# REST API endpoints for Management Console

Use the REST API to manage your GitHub Enterprise Server installation.

## About the Management Console endpoints

The full functionality of the Management Console endpoints was added to the [Manage GHES](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes) endpoints in GitHub Enterprise Server version 3.12. With feature parity achieved, the Management Console API endpoints were removed in version 3.15.

To help you migrate, the mapping table below shows the equivalent Manage GHES operation for each Management Console operation. Please migrate to the Manage GHES API endpoints as soon as possible.

| Purpose                            | Management Console API operation             | Manage GHES API operation                                                                                                                           |
| ---------------------------------- | -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Get the configuration status       | `GET /setup/api/configcheck`                 | [`GET /manage/v1/config/apply`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#get-the-status-of-a-ghe-config-apply-run)              |
| Start a configuration process      | `POST /setup/api/configure`                  | [`POST /manage/v1/config/apply`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#trigger-a-ghe-config-apply-run)                       |
| Get the maintenance status         | `GET /setup/api/maintenance`                 | [`GET /manage/v1/maintenance`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#get-the-status-of-maintenance-mode)                     |
| Enable or disable maintenance mode | `POST /setup/api/maintenance`                | [`POST /manage/v1/maintenance`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#set-the-status-of-maintenance-mode)                    |
| Get settings                       | `GET /setup/api/settings`                    | [`GET /manage/v1/config/settings`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#get-the-ghes-settings)                              |
| Set settings                       | `PUT /setup/api/settings`                    | [`PUT /manage/v1/config/settings`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#set-settings)                                       |
| Get all authorized SSH keys        | `GET /setup/api/settings/authorized-keys`    | [`GET /manage/v1/access/ssh`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#get-the-configured-ssh-keys)                             |
| Add an authorized SSH key          | `POST /setup/api/settings/authorized-keys`   | [`POST /manage/v1/access/ssh`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#set-a-new-ssh-key)                                      |
| Remove an authorized SSH key       | `DELETE /setup/api/settings/authorized-keys` | [`DELETE /manage/v1/access/ssh`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#delete-a-ssh-key)                                     |
| Create a GitHub license            | `POST /setup/api/start`                      | [`POST /manage/v1/config/init`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#initialize-instance-configuration-with-license-upload) |
| Upgrade a license                  | `POST /setup/api/upgrade`                    | [`PUT /manage/v1/config/license`](/en/enterprise-server@3.14/rest/enterprise-admin/manage-ghes#upload-an-enterprise-license)                        |

## About the Management Console

You should explicitly set the port number when making API calls to the Management Console. If TLS is enabled on your enterprise, the port number is `8443`. Otherwise, the port number is `8080`.

If you cannot provide a port number, you'll need to configure your tool to automatically follow redirects.

You may also need to add the [`-k` flag](http://curl.haxx.se/docs/manpage.html#-k) when using `curl`, since GitHub uses a self-signed certificate before you [add your own TLS certificate](/en/enterprise-server@3.14/admin/configuration/configuring-network-settings/configuring-tls).

### Authentication as the root site administrator

You need to pass your [root site administrator password](/en/enterprise-server@3.14/admin/configuration/administering-your-instance-from-the-management-console/managing-access-to-the-management-console) as an authentication token to every endpoint in this category except [Create a GitHub license](#create-a-github-license).

Use the `api_key` parameter to send this token with each request. For example:

```shell
curl -L 'https://HOSTNAME:ADMIN-PORT/setup/api?api_key=YOUR_PASSWORD'
```

You can also use standard HTTP authentication to send this token. For example:

```shell
curl -L -u "api_key:YOUR_PASSWORD" 'https://HOSTNAME:ADMIN-PORT/setup/api'
```

### Authentication as a Management Console user

[Management Console user accounts](/en/enterprise-server@3.14/admin/configuration/administering-your-instance-from-the-management-console/managing-access-to-the-management-console#management-console-user) can also authenticate to access this endpoint.

To authenticate with the password for a Management Console user account, use standard HTTP authentication. In the following example, replace YOUR\_USER\_NAME and YOUR\_PASSWORD with the account's user name and password.

```shell
curl -L -u "YOUR_USER_NAME:YOUR_PASSWORD" 'https://HOSTNAME:ADMIN-PORT/setup/api'
```

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## Get the configuration status

```
GET /setup/api/configcheck
```

This endpoint allows you to check the status of the most recent configuration process:
Note that you may need to wait several seconds after you start a process before you can check its status.
The different statuses are:

StatusDescriptionPENDINGThe job has not started yetCONFIGURINGThe job is runningDONEThe job has finished correctlyFAILEDThe job has finished unexpectedly

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/setup/api/configcheck
```

**Response schema (Status: 200):**

* `status`: string
* `progress`: array of objects:
  * `status`: required, string
  * `key`: required, string

## Start a configuration process

```
POST /setup/api/configure
```

This endpoint allows you to start a configuration process at any time for your updated settings to take effect:

### HTTP response status codes

* **202** - Accepted

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/setup/api/configure
```

**Response schema (Status: 202):**

## Get the maintenance status

```
GET /setup/api/maintenance
```

Check your installation's maintenance status:

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/setup/api/maintenance
```

**Response schema (Status: 200):**

* `status`: string
* `scheduled_time`: string
* `connection_services`: array of objects:
  * `name`: required, string
  * `number`: required, integer

## Enable or disable maintenance mode

```
POST /setup/api/maintenance
```

Note

The request body for this operation must be submitted as application/x-www-form-urlencoded data. You can submit a parameter value as a string, or you can use a tool such as curl to submit a parameter value as the contents of a text file. For more information, see the curl documentation.

### Parameters

#### Body parameters

* **`maintenance`** (string) (required)
  A JSON string with the attributes enabled and when.
  The possible values for enabled are true and false. When it's false, the attribute when is ignored and the maintenance mode is turned off. when defines the time period when the maintenance was enabled.
  The possible values for when are now or any date parseable by mojombo/chronic.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/setup/api/maintenance \
  -d '{
  "maintenance": "{\"enabled\":true, \"when\":\"now\"}"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get the maintenance status](#get-the-maintenance-status).

## Get settings

```
GET /setup/api/settings
```

Gets the settings for your instance. To change settings, see the Set settings endpoint.
Note

You cannot retrieve the management console password with the Enterprise administration API.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/setup/api/settings
```

**Response schema (Status: 200):**

* `enterprise`: object:
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
    * `base`: array of object
    * `uid`: string or null
    * `bind_dn`: string or null
    * `password`: string or null
    * `method`: string
    * `search_strategy`: string
    * `user_groups`: array of object
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
* `run_list`: array of string

## Set settings

```
PUT /setup/api/settings
```

Applies settings on your instance. For a list of the available settings, see the Get settings endpoint.
Notes:

The request body for this operation must be submitted as application/x-www-form-urlencoded data. You can submit a parameter value as a string, or you can use a tool such as curl to submit a parameter value as the contents of a text file. For more information, see the curl documentation.
You cannot set the management console password with the Enterprise administration API. Use the ghe-set-password utility to change the management console password. For more information, see "Command-line utilities."

### Parameters

#### Body parameters

* **`settings`** (string) (required)
  A JSON string with the new settings. Note that you only need to pass the specific settings you want to modify. For a list of the available settings, see the Get settings endpoint.

### HTTP response status codes

* **204** - No Content

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  http(s)://HOSTNAME/setup/api/settings \
  -d '{
  "settings": "{ \"enterprise\": { \"public_pages\": true }}"
}'
```

**Response schema (Status: 204):**

## Get all authorized SSH keys

```
GET /setup/api/settings/authorized-keys
```

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/setup/api/settings/authorized-keys
```

**Response schema (Status: 200):**

Array of objects:

* `key`: string
* `pretty-print`: string

## Add an authorized SSH key

```
POST /setup/api/settings/authorized-keys
```

Note: The request body for this operation must be submitted as application/x-www-form-urlencoded data. You can submit a parameter value as a string, or you can use a tool such as curl to submit a parameter value as the contents of a text file. For more information, see the curl documentation.

### Parameters

#### Body parameters

* **`authorized_key`** (string) (required)
  The public SSH key.

### HTTP response status codes

* **201** - Created

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/setup/api/settings/authorized-keys \
  -d '{
  "authorized_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQCssTL/Vtu/ODLTj0VtZoRAbvf7uiv5997GyDq0MoAZUjb5jmA5wYe2/wF6sFuhiZTnZoF1ZtCHunPp0hM/GHrn6VySBhNncx14YO8FPt1CIhEeRMSEjUK9cY3xAbS365oXY8vnUHJsS9+1tr/2bx/+4NJfcUt/Ezf1OR/0LStQXw=="
}'
```

**Response schema (Status: 201):**

Same response schema as [Get all authorized SSH keys](#get-all-authorized-ssh-keys).

## Remove an authorized SSH key

```
DELETE /setup/api/settings/authorized-keys
```

Note: The request body for this operation must be submitted as application/x-www-form-urlencoded data. You can submit a parameter value as a string, or you can use a tool such as curl to submit a parameter value as the contents of a text file. For more information, see the curl documentation.

### Parameters

#### Body parameters

* **`authorized_key`** (string) (required)
  The public SSH key.

### HTTP response status codes

* **200** - OK

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/setup/api/settings/authorized-keys \
  -d '{
  "authorized_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQCssTL/Vtu/ODLTj0VtZoRAbvf7uiv5997GyDq0MoAZUjb5jmA5wYe2/wF6sFuhiZTnZoF1ZtCHunPp0hM/GHrn6VySBhNncx14YO8FPt1CIhEeRMSEjUK9cY3xAbS365oXY8vnUHJsS9+1tr/2bx/+4NJfcUt/Ezf1OR/0LStQXw=="
}'
```

**Response schema (Status: 200):**

Same response schema as [Get all authorized SSH keys](#get-all-authorized-ssh-keys).

## Create a GitHub license

```
POST /setup/api/start
```

When you boot a GitHub instance for the first time, you can use the following endpoint to upload a license.
Note that you need to POST to /setup/api/configure to start the actual configuration process.
When using this endpoint, your GitHub instance must have a password set. This can be accomplished two ways:

If you're working directly with the API before accessing the web interface, you must pass in the password parameter to set your password.
If you set up your instance via the web interface before accessing the API, your calls to this endpoint do not need the password parameter.

Note

The request body for this operation must be submitted as multipart/form-data data. You can can reference the license file by prefixing the filename with the @ symbol using curl. For more information, see the curl documentation.

### Parameters

#### Body parameters

* **`license`** (string) (required)
  The content of your .ghl license file.

* **`password`** (string)
  You must provide a password only if you are uploading your license for the first time. If you previously set a password through the web interface, you don't need this parameter.

* **`settings`** (string)
  An optional JSON string containing the installation settings. For a list of the available settings, see the Get settings endpoint.

### HTTP response status codes

* **202** - Accepted

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/setup/api/start \
  -d '{
  "license": "@enterprise.ghl",
  "password": "secret"
}'
```

**Response schema (Status: 202):**

## Upgrade a license

```
POST /setup/api/upgrade
```

This API upgrades your license and also triggers the configuration process.
Note

The request body for this operation must be submitted as multipart/form-data data. You can can reference the license file by prefixing the filename with the @ symbol using curl. For more information, see the curl documentation.

### Parameters

#### Body parameters

* **`license`** (string)
  The content of your new .ghl license file.

### HTTP response status codes

* **202** - Accepted

* **401** - Unauthorized

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/setup/api/upgrade \
  -d '{
  "license": "@enterprise.ghl"
}'
```

**Response schema (Status: 202):**