# Configurations

Use the REST API to create and manage security configurations for your organization.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get code security configurations for an enterprise

```
GET /enterprises/{enterprise}/code-security/configurations
```

Lists all code security configurations available in an enterprise.
The authenticated user must be an administrator of the enterprise in order to use this endpoint.
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

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations
```

**Response schema (Status: 200):**

Array of objects:
  * `id`: integer
  * `name`: string
  * `target_type`: string, enum: `global`, `organization`, `enterprise`
  * `description`: string
  * `advanced_security`: string, enum: `enabled`, `disabled`, `code_security`, `secret_protection`
  * `dependency_graph`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependency_graph_autosubmit_action`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependency_graph_autosubmit_action_options`: object:
    * `labeled_runners`: boolean
  * `dependabot_alerts`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependabot_security_updates`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependabot_delegated_alert_dismissal`: string or null, enum: `enabled`, `disabled`, `not_set`, `null`
  * `code_scanning_options`: object or null:
    * `allow_advanced`: boolean or null
  * `code_scanning_default_setup`: string, enum: `enabled`, `disabled`, `not_set`
  * `code_scanning_default_setup_options`: object or null:
    * `runner_type`: string or null, enum: `standard`, `labeled`, `not_set`, `null`
    * `runner_label`: string or null
  * `code_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_push_protection`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_bypass`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_bypass_options`: object:
    * `reviewers`: array of objects:
      * `reviewer_id`: required, integer
      * `reviewer_type`: required, string, enum: `TEAM`, `ROLE`
      * `mode`: string, enum: `ALWAYS`, `EXEMPT`, default: `"ALWAYS"`
      * `security_configuration_id`: integer
  * `secret_scanning_validity_checks`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_non_provider_patterns`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_generic_secrets`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_extended_metadata`: string, enum: `enabled`, `disabled`, `not_set`
  * `private_vulnerability_reporting`: string, enum: `enabled`, `disabled`, `not_set`
  * `enforcement`: string, enum: `enforced`, `unenforced`
  * `url`: string, format: uri
  * `html_url`: string, format: uri
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time





## Create a code security configuration for an enterprise

```
POST /enterprises/{enterprise}/code-security/configurations
```

Creates a code security configuration in an enterprise.
The authenticated user must be an administrator of the enterprise in order to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`name`** (string) (required)
  The name of the code security configuration. Must be unique within the enterprise.

- **`description`** (string) (required)
  A description of the code security configuration

- **`advanced_security`** (string)
  The enablement status of GitHub Advanced Security features. enabled will enable both Code Security and Secret Protection features.
Warning

code_security and secret_protection are deprecated values for this field. Prefer the individual code_security and secret_protection fields to set the status of these features.
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `code_security`, `secret_protection`

- **`code_security`** (string)
  The enablement status of GitHub Code Security features.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph`** (string)
  The enablement status of Dependency Graph
  Default: `enabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph_autosubmit_action`** (string)
  The enablement status of Automatic dependency submission
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph_autosubmit_action_options`** (object)
  Feature options for Automatic dependency submission
  - **`labeled_runners`** (boolean)
    Whether to use runners labeled with 'dependency-submission' or standard GitHub runners.
    Default: `false`

- **`dependabot_alerts`** (string)
  The enablement status of Dependabot alerts
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependabot_security_updates`** (string)
  The enablement status of Dependabot security updates
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`code_scanning_options`** (object or null)
  Security Configuration feature options for code scanning
  - **`allow_advanced`** (boolean or null)
    Whether to allow repos which use advanced setup

- **`code_scanning_default_setup`** (string)
  The enablement status of code scanning default setup
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`code_scanning_default_setup_options`** (object or null)
  Feature options for code scanning default setup
  - **`runner_type`** (string)
    Whether to use labeled runners or standard GitHub runners.
    Can be one of: `standard`, `labeled`, `not_set`
  - **`runner_label`** (string or null)
    The label of the runner to use for code scanning default setup when runner_type is 'labeled'.

- **`code_scanning_delegated_alert_dismissal`** (string)
  The enablement status of code scanning delegated alert dismissal
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_protection`** (string)
  The enablement status of GitHub Secret Protection features.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning`** (string)
  The enablement status of secret scanning
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_push_protection`** (string)
  The enablement status of secret scanning push protection
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_validity_checks`** (string)
  The enablement status of secret scanning validity checks
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_non_provider_patterns`** (string)
  The enablement status of secret scanning non provider patterns
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_generic_secrets`** (string)
  The enablement status of Copilot secret scanning
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_delegated_alert_dismissal`** (string)
  The enablement status of secret scanning delegated alert dismissal
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_extended_metadata`** (string)
  The enablement status of secret scanning extended metadata
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`private_vulnerability_reporting`** (string)
  The enablement status of private vulnerability reporting
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`enforcement`** (string)
  The enforcement status for a security configuration
  Default: `enforced`
  Can be one of: `enforced`, `unenforced`





### HTTP response status codes


- **201** - Successfully created code security configuration


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example for a code security configuration

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations \
  -d '{
  "name": "High rish settings",
  "description": "This is a code security configuration for octo-enterprise",
  "advanced_security": "enabled",
  "dependabot_alerts": "enabled",
  "dependabot_security_updates": "not_set",
  "secret_scanning": "enabled"
}'
```

**Response schema (Status: 201):**

* `id`: integer
* `name`: string
* `target_type`: string, enum: `global`, `organization`, `enterprise`
* `description`: string
* `advanced_security`: string, enum: `enabled`, `disabled`, `code_security`, `secret_protection`
* `dependency_graph`: string, enum: `enabled`, `disabled`, `not_set`
* `dependency_graph_autosubmit_action`: string, enum: `enabled`, `disabled`, `not_set`
* `dependency_graph_autosubmit_action_options`: object:
  * `labeled_runners`: boolean
* `dependabot_alerts`: string, enum: `enabled`, `disabled`, `not_set`
* `dependabot_security_updates`: string, enum: `enabled`, `disabled`, `not_set`
* `dependabot_delegated_alert_dismissal`: string or null, enum: `enabled`, `disabled`, `not_set`, `null`
* `code_scanning_options`: object or null:
  * `allow_advanced`: boolean or null
* `code_scanning_default_setup`: string, enum: `enabled`, `disabled`, `not_set`
* `code_scanning_default_setup_options`: object or null:
  * `runner_type`: string or null, enum: `standard`, `labeled`, `not_set`, `null`
  * `runner_label`: string or null
* `code_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
* `secret_scanning`: string, enum: `enabled`, `disabled`, `not_set`
* `secret_scanning_push_protection`: string, enum: `enabled`, `disabled`, `not_set`
* `secret_scanning_delegated_bypass`: string, enum: `enabled`, `disabled`, `not_set`
* `secret_scanning_delegated_bypass_options`: object:
  * `reviewers`: array of objects:
    * `reviewer_id`: required, integer
    * `reviewer_type`: required, string, enum: `TEAM`, `ROLE`
    * `mode`: string, enum: `ALWAYS`, `EXEMPT`, default: `"ALWAYS"`
    * `security_configuration_id`: integer
* `secret_scanning_validity_checks`: string, enum: `enabled`, `disabled`, `not_set`
* `secret_scanning_non_provider_patterns`: string, enum: `enabled`, `disabled`, `not_set`
* `secret_scanning_generic_secrets`: string, enum: `enabled`, `disabled`, `not_set`
* `secret_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
* `secret_scanning_extended_metadata`: string, enum: `enabled`, `disabled`, `not_set`
* `private_vulnerability_reporting`: string, enum: `enabled`, `disabled`, `not_set`
* `enforcement`: string, enum: `enforced`, `unenforced`
* `url`: string, format: uri
* `html_url`: string, format: uri
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time





## Get default code security configurations for an enterprise

```
GET /enterprises/{enterprise}/code-security/configurations/defaults
```

Lists the default code security configurations for an enterprise.
The authenticated user must be an administrator of the enterprise in order to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations/defaults
```

**Response schema (Status: 200):**

Array of objects:
  * `default_for_new_repos`: enum: `public`, `private_and_internal`, `all`
  * `configuration`: object:
    * `id`: integer
    * `name`: string
    * `target_type`: string, enum: `global`, `organization`, `enterprise`
    * `description`: string
    * `advanced_security`: string, enum: `enabled`, `disabled`, `code_security`, `secret_protection`
    * `dependency_graph`: string, enum: `enabled`, `disabled`, `not_set`
    * `dependency_graph_autosubmit_action`: string, enum: `enabled`, `disabled`, `not_set`
    * `dependency_graph_autosubmit_action_options`: object:
      * `labeled_runners`: boolean
    * `dependabot_alerts`: string, enum: `enabled`, `disabled`, `not_set`
    * `dependabot_security_updates`: string, enum: `enabled`, `disabled`, `not_set`
    * `dependabot_delegated_alert_dismissal`: string or null, enum: `enabled`, `disabled`, `not_set`, `null`
    * `code_scanning_options`: object or null:
      * `allow_advanced`: boolean or null
    * `code_scanning_default_setup`: string, enum: `enabled`, `disabled`, `not_set`
    * `code_scanning_default_setup_options`: object or null:
      * `runner_type`: string or null, enum: `standard`, `labeled`, `not_set`, `null`
      * `runner_label`: string or null
    * `code_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
    * `secret_scanning`: string, enum: `enabled`, `disabled`, `not_set`
    * `secret_scanning_push_protection`: string, enum: `enabled`, `disabled`, `not_set`
    * `secret_scanning_delegated_bypass`: string, enum: `enabled`, `disabled`, `not_set`
    * `secret_scanning_delegated_bypass_options`: object:
      * `reviewers`: array of objects:
        * `reviewer_id`: required, integer
        * `reviewer_type`: required, string, enum: `TEAM`, `ROLE`
        * `mode`: string, enum: `ALWAYS`, `EXEMPT`, default: `"ALWAYS"`
        * `security_configuration_id`: integer
    * `secret_scanning_validity_checks`: string, enum: `enabled`, `disabled`, `not_set`
    * `secret_scanning_non_provider_patterns`: string, enum: `enabled`, `disabled`, `not_set`
    * `secret_scanning_generic_secrets`: string, enum: `enabled`, `disabled`, `not_set`
    * `secret_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
    * `secret_scanning_extended_metadata`: string, enum: `enabled`, `disabled`, `not_set`
    * `private_vulnerability_reporting`: string, enum: `enabled`, `disabled`, `not_set`
    * `enforcement`: string, enum: `enforced`, `unenforced`
    * `url`: string, format: uri
    * `html_url`: string, format: uri
    * `created_at`: string, format: date-time
    * `updated_at`: string, format: date-time





## Retrieve a code security configuration of an enterprise

```
GET /enterprises/{enterprise}/code-security/configurations/{configuration_id}
```

Gets a code security configuration available in an enterprise.
The authenticated user must be an administrator of the enterprise in order to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations/CONFIGURATION_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a code security configuration for an enterprise](#create-a-code-security-configuration-for-an-enterprise).





## Update a custom code security configuration for an enterprise

```
PATCH /enterprises/{enterprise}/code-security/configurations/{configuration_id}
```

Updates a code security configuration in an enterprise.
The authenticated user must be an administrator of the enterprise in order to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.




#### Body parameters

- **`name`** (string)
  The name of the code security configuration. Must be unique across the enterprise.

- **`description`** (string)
  A description of the code security configuration

- **`advanced_security`** (string)
  The enablement status of GitHub Advanced Security features. enabled will enable both Code Security and Secret Protection features.
Warning

code_security and secret_protection are deprecated values for this field. Prefer the individual code_security and secret_protection fields to set the status of these features.
  Can be one of: `enabled`, `disabled`, `code_security`, `secret_protection`

- **`code_security`** (string)
  The enablement status of GitHub Code Security features.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph`** (string)
  The enablement status of Dependency Graph
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph_autosubmit_action`** (string)
  The enablement status of Automatic dependency submission
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph_autosubmit_action_options`** (object)
  Feature options for Automatic dependency submission
  - **`labeled_runners`** (boolean)
    Whether to use runners labeled with 'dependency-submission' or standard GitHub runners.

- **`dependabot_alerts`** (string)
  The enablement status of Dependabot alerts
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependabot_security_updates`** (string)
  The enablement status of Dependabot security updates
  Can be one of: `enabled`, `disabled`, `not_set`

- **`code_scanning_default_setup`** (string)
  The enablement status of code scanning default setup
  Can be one of: `enabled`, `disabled`, `not_set`

- **`code_scanning_default_setup_options`** (object or null)
  Feature options for code scanning default setup
  - **`runner_type`** (string)
    Whether to use labeled runners or standard GitHub runners.
    Can be one of: `standard`, `labeled`, `not_set`
  - **`runner_label`** (string or null)
    The label of the runner to use for code scanning default setup when runner_type is 'labeled'.

- **`code_scanning_options`** (object or null)
  Security Configuration feature options for code scanning
  - **`allow_advanced`** (boolean or null)
    Whether to allow repos which use advanced setup

- **`code_scanning_delegated_alert_dismissal`** (string)
  The enablement status of code scanning delegated alert dismissal
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_protection`** (string)
  The enablement status of GitHub Secret Protection features.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning`** (string)
  The enablement status of secret scanning
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_push_protection`** (string)
  The enablement status of secret scanning push protection
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_validity_checks`** (string)
  The enablement status of secret scanning validity checks
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_non_provider_patterns`** (string)
  The enablement status of secret scanning non-provider patterns
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_generic_secrets`** (string)
  The enablement status of Copilot secret scanning
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_delegated_alert_dismissal`** (string)
  The enablement status of secret scanning delegated alert dismissal
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_extended_metadata`** (string)
  The enablement status of secret scanning extended metadata
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`private_vulnerability_reporting`** (string)
  The enablement status of private vulnerability reporting
  Can be one of: `enabled`, `disabled`, `not_set`

- **`enforcement`** (string)
  The enforcement status for a security configuration
  Can be one of: `enforced`, `unenforced`





### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict




### Code examples



#### Example for updating a code security configuration

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations/CONFIGURATION_ID \
  -d '{
  "name": "octo-enterprise recommended settings v2",
  "secret_scanning": "disabled",
  "code_scanning_default_setup": "enabled"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a code security configuration for an enterprise](#create-a-code-security-configuration-for-an-enterprise).





## Delete a code security configuration for an enterprise

```
DELETE /enterprises/{enterprise}/code-security/configurations/{configuration_id}
```

Deletes a code security configuration from an enterprise.
Repositories attached to the configuration will retain their settings but will no longer be associated with
the configuration.
The authenticated user must be an administrator for the enterprise to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.






### HTTP response status codes


- **204** - A header with no content is returned.


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations/CONFIGURATION_ID
```

**Response schema (Status: 204):**





## Attach an enterprise configuration to repositories

```
POST /enterprises/{enterprise}/code-security/configurations/{configuration_id}/attach
```

Attaches an enterprise code security configuration to repositories. If the repositories specified are already attached to a configuration, they will be re-attached to the provided configuration.
If insufficient GHAS licenses are available to attach the configuration to a repository, only free features will be enabled.
The authenticated user must be an administrator for the enterprise to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.




#### Body parameters

- **`scope`** (string) (required)
  The type of repositories to attach the configuration to.
  Can be one of: `all`, `all_without_configurations`





### HTTP response status codes


- **202** - Accepted


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict




### Code examples



#### Example for attaching a configuration to some repositories

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations/CONFIGURATION_ID/attach \
  -d '{
  "scope": "all"
}'
```

**Response schema (Status: 202):**

object





## Set a code security configuration as a default for an enterprise

```
PUT /enterprises/{enterprise}/code-security/configurations/{configuration_id}/defaults
```

Sets a code security configuration as a default to be applied to new repositories in your enterprise.
This configuration will be applied by default to the matching repository type when created, but only for organizations within the enterprise that do not already have a default code security configuration set.
The authenticated user must be an administrator for the enterprise to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.




#### Body parameters

- **`default_for_new_repos`** (string)
  Specify which types of repository this security configuration should be applied to by default.
  Can be one of: `all`, `none`, `private_and_internal`, `public`





### HTTP response status codes


- **200** - Default successfully changed.


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Set this configuration to be enabled by default on all new repositories.

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations/CONFIGURATION_ID/defaults \
  -d '{
  "default_for_new_repos": "all"
}'
```

**Response schema (Status: 200):**

* `default_for_new_repos`: string, enum: `all`, `none`, `private_and_internal`, `public`
* `configuration`: object:
  * `id`: integer
  * `name`: string
  * `target_type`: string, enum: `global`, `organization`, `enterprise`
  * `description`: string
  * `advanced_security`: string, enum: `enabled`, `disabled`, `code_security`, `secret_protection`
  * `dependency_graph`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependency_graph_autosubmit_action`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependency_graph_autosubmit_action_options`: object:
    * `labeled_runners`: boolean
  * `dependabot_alerts`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependabot_security_updates`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependabot_delegated_alert_dismissal`: string or null, enum: `enabled`, `disabled`, `not_set`, `null`
  * `code_scanning_options`: object or null:
    * `allow_advanced`: boolean or null
  * `code_scanning_default_setup`: string, enum: `enabled`, `disabled`, `not_set`
  * `code_scanning_default_setup_options`: object or null:
    * `runner_type`: string or null, enum: `standard`, `labeled`, `not_set`, `null`
    * `runner_label`: string or null
  * `code_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_push_protection`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_bypass`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_bypass_options`: object:
    * `reviewers`: array of objects:
      * `reviewer_id`: required, integer
      * `reviewer_type`: required, string, enum: `TEAM`, `ROLE`
      * `mode`: string, enum: `ALWAYS`, `EXEMPT`, default: `"ALWAYS"`
      * `security_configuration_id`: integer
  * `secret_scanning_validity_checks`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_non_provider_patterns`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_generic_secrets`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_extended_metadata`: string, enum: `enabled`, `disabled`, `not_set`
  * `private_vulnerability_reporting`: string, enum: `enabled`, `disabled`, `not_set`
  * `enforcement`: string, enum: `enforced`, `unenforced`
  * `url`: string, format: uri
  * `html_url`: string, format: uri
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time





## Get repositories associated with an enterprise code security configuration

```
GET /enterprises/{enterprise}/code-security/configurations/{configuration_id}/repositories
```

Lists the repositories associated with an enterprise code security configuration in an organization.
The authenticated user must be an administrator of the enterprise in order to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

- **`status`** (string)
  A comma-separated list of statuses. If specified, only repositories with these attachment statuses will be returned.
Can be: all, attached, attaching, removed, enforced, failed, updating, removed_by_enterprise
  Default: `all`






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/code-security/configurations/CONFIGURATION_ID/repositories
```

**Response schema (Status: 200):**

Array of objects:
  * `status`: string, enum: `attached`, `attaching`, `detached`, `removed`, `enforced`, `failed`, `updating`, `removed_by_enterprise`
  * `repository`: `Simple Repository`:
    * `id`: required, integer, format: int64
    * `node_id`: required, string
    * `name`: required, string
    * `full_name`: required, string
    * `owner`: required, `Simple User`:
      * `name`: string or null
      * `email`: string or null
      * `login`: required, string
      * `id`: required, integer, format: int64
      * `node_id`: required, string
      * `avatar_url`: required, string, format: uri
      * `gravatar_id`: required, string or null
      * `url`: required, string, format: uri
      * `html_url`: required, string, format: uri
      * `followers_url`: required, string, format: uri
      * `following_url`: required, string
      * `gists_url`: required, string
      * `starred_url`: required, string
      * `subscriptions_url`: required, string, format: uri
      * `organizations_url`: required, string, format: uri
      * `repos_url`: required, string, format: uri
      * `events_url`: required, string
      * `received_events_url`: required, string, format: uri
      * `type`: required, string
      * `site_admin`: required, boolean
      * `starred_at`: string
      * `user_view_type`: string
    * `private`: required, boolean
    * `html_url`: required, string, format: uri
    * `description`: required, string or null
    * `fork`: required, boolean
    * `url`: required, string, format: uri
    * `archive_url`: required, string
    * `assignees_url`: required, string
    * `blobs_url`: required, string
    * `branches_url`: required, string
    * `collaborators_url`: required, string
    * `comments_url`: required, string
    * `commits_url`: required, string
    * `compare_url`: required, string
    * `contents_url`: required, string
    * `contributors_url`: required, string, format: uri
    * `deployments_url`: required, string, format: uri
    * `downloads_url`: required, string, format: uri
    * `events_url`: required, string, format: uri
    * `forks_url`: required, string, format: uri
    * `git_commits_url`: required, string
    * `git_refs_url`: required, string
    * `git_tags_url`: required, string
    * `issue_comment_url`: required, string
    * `issue_events_url`: required, string
    * `issues_url`: required, string
    * `keys_url`: required, string
    * `labels_url`: required, string
    * `languages_url`: required, string, format: uri
    * `merges_url`: required, string, format: uri
    * `milestones_url`: required, string
    * `notifications_url`: required, string
    * `pulls_url`: required, string
    * `releases_url`: required, string
    * `stargazers_url`: required, string, format: uri
    * `statuses_url`: required, string
    * `subscribers_url`: required, string, format: uri
    * `subscription_url`: required, string, format: uri
    * `tags_url`: required, string, format: uri
    * `teams_url`: required, string, format: uri
    * `trees_url`: required, string
    * `hooks_url`: required, string, format: uri





## Get code security configurations for an organization

```
GET /orgs/{org}/code-security/configurations
```

Lists all code security configurations available in an organization.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`target_type`** (string)
  The target type of the code security configuration
  Default: `all`
  Can be one of: `global`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/code-security/configurations
```

**Response schema (Status: 200):**

Same response schema as [Get code security configurations for an enterprise](#get-code-security-configurations-for-an-enterprise).





## Create a code security configuration

```
POST /orgs/{org}/code-security/configurations
```

Creates a code security configuration in an organization.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  The name of the code security configuration. Must be unique within the organization.

- **`description`** (string) (required)
  A description of the code security configuration

- **`advanced_security`** (string)
  The enablement status of GitHub Advanced Security features. enabled will enable both Code Security and Secret Protection features.
Warning

code_security and secret_protection are deprecated values for this field. Prefer the individual code_security and secret_protection fields to set the status of these features.
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `code_security`, `secret_protection`

- **`code_security`** (string)
  The enablement status of GitHub Code Security features.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph`** (string)
  The enablement status of Dependency Graph
  Default: `enabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph_autosubmit_action`** (string)
  The enablement status of Automatic dependency submission
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph_autosubmit_action_options`** (object)
  Feature options for Automatic dependency submission
  - **`labeled_runners`** (boolean)
    Whether to use runners labeled with 'dependency-submission' or standard GitHub runners.
    Default: `false`

- **`dependabot_alerts`** (string)
  The enablement status of Dependabot alerts
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependabot_security_updates`** (string)
  The enablement status of Dependabot security updates
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependabot_delegated_alert_dismissal`** (string)
  The enablement status of Dependabot delegated alert dismissal. Requires Dependabot alerts to be enabled.
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`code_scanning_options`** (object or null)
  Security Configuration feature options for code scanning
  - **`allow_advanced`** (boolean or null)
    Whether to allow repos which use advanced setup

- **`code_scanning_default_setup`** (string)
  The enablement status of code scanning default setup
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`code_scanning_default_setup_options`** (object or null)
  Feature options for code scanning default setup
  - **`runner_type`** (string)
    Whether to use labeled runners or standard GitHub runners.
    Can be one of: `standard`, `labeled`, `not_set`
  - **`runner_label`** (string or null)
    The label of the runner to use for code scanning default setup when runner_type is 'labeled'.

- **`code_scanning_delegated_alert_dismissal`** (string)
  The enablement status of code scanning delegated alert dismissal
  Default: `not_set`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_protection`** (string)
  The enablement status of GitHub Secret Protection features.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning`** (string)
  The enablement status of secret scanning
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_push_protection`** (string)
  The enablement status of secret scanning push protection
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_delegated_bypass`** (string)
  The enablement status of secret scanning delegated bypass
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_delegated_bypass_options`** (object)
  Feature options for secret scanning delegated bypass
  - **`reviewers`** (array of objects)
    The bypass reviewers for secret scanning delegated bypass
    - **`reviewer_id`** (integer) (required)
      The ID of the team or role selected as a bypass reviewer
    - **`reviewer_type`** (string) (required)
      The type of the bypass reviewer
      Can be one of: `TEAM`, `ROLE`
    - **`mode`** (string)
      The bypass mode for the reviewer
      Default: `ALWAYS`
      Can be one of: `ALWAYS`, `EXEMPT`

- **`secret_scanning_validity_checks`** (string)
  The enablement status of secret scanning validity checks
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_non_provider_patterns`** (string)
  The enablement status of secret scanning non provider patterns
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_generic_secrets`** (string)
  The enablement status of Copilot secret scanning
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_delegated_alert_dismissal`** (string)
  The enablement status of secret scanning delegated alert dismissal
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_extended_metadata`** (string)
  The enablement status of secret scanning extended metadata
  Can be one of: `enabled`, `disabled`, `not_set`

- **`private_vulnerability_reporting`** (string)
  The enablement status of private vulnerability reporting
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`enforcement`** (string)
  The enforcement status for a security configuration
  Default: `enforced`
  Can be one of: `enforced`, `unenforced`





### HTTP response status codes


- **201** - Successfully created code security configuration




### Code examples



#### Example for a code security configuration

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/code-security/configurations \
  -d '{
  "name": "octo-org recommended settings",
  "description": "This is a code security configuration for octo-org",
  "advanced_security": "enabled",
  "dependabot_alerts": "enabled",
  "dependabot_security_updates": "not_set",
  "secret_scanning": "enabled"
}'
```

**Response schema (Status: 201):**

Same response schema as [Create a code security configuration for an enterprise](#create-a-code-security-configuration-for-an-enterprise).





## Get default code security configurations

```
GET /orgs/{org}/code-security/configurations/defaults
```

Lists the default code security configurations for an organization.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/code-security/configurations/defaults
```

**Response schema (Status: 200):**

Same response schema as [Get default code security configurations for an enterprise](#get-default-code-security-configurations-for-an-enterprise).





## Detach configurations from repositories

```
DELETE /orgs/{org}/code-security/configurations/detach
```

Detach code security configuration(s) from a set of repositories.
Repositories will retain their settings but will no longer be associated with the configuration.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`selected_repository_ids`** (array of integers)
  An array of repository IDs to detach from configurations. Up to 250 IDs can be provided.





### HTTP response status codes


- **204** - A header with no content is returned.


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict




### Code examples



#### Example for detaching repositories from configurations.

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/code-security/configurations/detach \
  -d '{
  "selected_repository_ids": [
    32,
    91
  ]
}'
```

**Response schema (Status: 204):**





## Get a code security configuration

```
GET /orgs/{org}/code-security/configurations/{configuration_id}
```

Gets a code security configuration available in an organization.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/code-security/configurations/CONFIGURATION_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a code security configuration for an enterprise](#create-a-code-security-configuration-for-an-enterprise).





## Update a code security configuration

```
PATCH /orgs/{org}/code-security/configurations/{configuration_id}
```

Updates a code security configuration in an organization.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.




#### Body parameters

- **`name`** (string)
  The name of the code security configuration. Must be unique within the organization.

- **`description`** (string)
  A description of the code security configuration

- **`advanced_security`** (string)
  The enablement status of GitHub Advanced Security features. enabled will enable both Code Security and Secret Protection features.
Warning

code_security and secret_protection are deprecated values for this field. Prefer the individual code_security and secret_protection fields to set the status of these features.
  Can be one of: `enabled`, `disabled`, `code_security`, `secret_protection`

- **`code_security`** (string)
  The enablement status of GitHub Code Security features.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph`** (string)
  The enablement status of Dependency Graph
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph_autosubmit_action`** (string)
  The enablement status of Automatic dependency submission
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependency_graph_autosubmit_action_options`** (object)
  Feature options for Automatic dependency submission
  - **`labeled_runners`** (boolean)
    Whether to use runners labeled with 'dependency-submission' or standard GitHub runners.

- **`dependabot_alerts`** (string)
  The enablement status of Dependabot alerts
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependabot_security_updates`** (string)
  The enablement status of Dependabot security updates
  Can be one of: `enabled`, `disabled`, `not_set`

- **`dependabot_delegated_alert_dismissal`** (string)
  The enablement status of Dependabot delegated alert dismissal. Requires Dependabot alerts to be enabled.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`code_scanning_default_setup`** (string)
  The enablement status of code scanning default setup
  Can be one of: `enabled`, `disabled`, `not_set`

- **`code_scanning_default_setup_options`** (object or null)
  Feature options for code scanning default setup
  - **`runner_type`** (string)
    Whether to use labeled runners or standard GitHub runners.
    Can be one of: `standard`, `labeled`, `not_set`
  - **`runner_label`** (string or null)
    The label of the runner to use for code scanning default setup when runner_type is 'labeled'.

- **`code_scanning_options`** (object or null)
  Security Configuration feature options for code scanning
  - **`allow_advanced`** (boolean or null)
    Whether to allow repos which use advanced setup

- **`code_scanning_delegated_alert_dismissal`** (string)
  The enablement status of code scanning delegated alert dismissal
  Default: `disabled`
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_protection`** (string)
  The enablement status of GitHub Secret Protection features.
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning`** (string)
  The enablement status of secret scanning
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_push_protection`** (string)
  The enablement status of secret scanning push protection
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_delegated_bypass`** (string)
  The enablement status of secret scanning delegated bypass
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_delegated_bypass_options`** (object)
  Feature options for secret scanning delegated bypass
  - **`reviewers`** (array of objects)
    The bypass reviewers for secret scanning delegated bypass
    - **`reviewer_id`** (integer) (required)
      The ID of the team or role selected as a bypass reviewer
    - **`reviewer_type`** (string) (required)
      The type of the bypass reviewer
      Can be one of: `TEAM`, `ROLE`
    - **`mode`** (string)
      The bypass mode for the reviewer
      Default: `ALWAYS`
      Can be one of: `ALWAYS`, `EXEMPT`

- **`secret_scanning_validity_checks`** (string)
  The enablement status of secret scanning validity checks
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_non_provider_patterns`** (string)
  The enablement status of secret scanning non-provider patterns
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_generic_secrets`** (string)
  The enablement status of Copilot secret scanning
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_delegated_alert_dismissal`** (string)
  The enablement status of secret scanning delegated alert dismissal
  Can be one of: `enabled`, `disabled`, `not_set`

- **`secret_scanning_extended_metadata`** (string)
  The enablement status of secret scanning extended metadata
  Can be one of: `enabled`, `disabled`, `not_set`

- **`private_vulnerability_reporting`** (string)
  The enablement status of private vulnerability reporting
  Can be one of: `enabled`, `disabled`, `not_set`

- **`enforcement`** (string)
  The enforcement status for a security configuration
  Can be one of: `enforced`, `unenforced`





### HTTP response status codes


- **200** - Response when a configuration is updated


- **204** - Response when no new updates are made




### Code examples



#### Example for updating a code security configuration

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/code-security/configurations/CONFIGURATION_ID \
  -d '{
  "name": "octo-org recommended settings v2",
  "secret_scanning": "disabled",
  "code_scanning_default_setup": "enabled"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a code security configuration for an enterprise](#create-a-code-security-configuration-for-an-enterprise).





## Delete a code security configuration

```
DELETE /orgs/{org}/code-security/configurations/{configuration_id}
```

Deletes the desired code security configuration from an organization.
Repositories attached to the configuration will retain their settings but will no longer be associated with
the configuration.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.






### HTTP response status codes


- **204** - A header with no content is returned.


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/code-security/configurations/CONFIGURATION_ID
```

**Response schema (Status: 204):**





## Attach a configuration to repositories

```
POST /orgs/{org}/code-security/configurations/{configuration_id}/attach
```

Attach a code security configuration to a set of repositories. If the repositories specified are already attached to a configuration, they will be re-attached to the provided configuration.
If insufficient GHAS licenses are available to attach the configuration to a repository, only free features will be enabled.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.




#### Body parameters

- **`scope`** (string) (required)
  The type of repositories to attach the configuration to. selected means the configuration will be attached to only the repositories specified by selected_repository_ids
  Can be one of: `all`, `all_without_configurations`, `public`, `private_or_internal`, `selected`

- **`selected_repository_ids`** (array of integers)
  An array of repository IDs to attach the configuration to. You can only provide a list of repository ids when the scope is set to selected.





### HTTP response status codes


- **202** - Accepted




### Code examples



#### Example for attaching a configuration to some repositories

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/code-security/configurations/CONFIGURATION_ID/attach \
  -d '{
  "scope": "selected",
  "selected_repository_ids": [
    32,
    91
  ]
}'
```

**Response schema (Status: 202):**

Same response schema as [Attach an enterprise configuration to repositories](#attach-an-enterprise-configuration-to-repositories).





## Set a code security configuration as a default for an organization

```
PUT /orgs/{org}/code-security/configurations/{configuration_id}/defaults
```

Sets a code security configuration as a default to be applied to new repositories in your organization.
This configuration will be applied to the matching repository type (all, none, public, private and internal) by default when they are created.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.




#### Body parameters

- **`default_for_new_repos`** (string)
  Specify which types of repository this security configuration should be applied to by default.
  Can be one of: `all`, `none`, `private_and_internal`, `public`





### HTTP response status codes


- **200** - Default successfully changed.


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Set this configuration to be enabled by default on all new repositories.

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/code-security/configurations/CONFIGURATION_ID/defaults \
  -d '{
  "default_for_new_repos": "all"
}'
```

**Response schema (Status: 200):**

Same response schema as [Set a code security configuration as a default for an enterprise](#set-a-code-security-configuration-as-a-default-for-an-enterprise).





## Get repositories associated with a code security configuration

```
GET /orgs/{org}/code-security/configurations/{configuration_id}/repositories
```

Lists the repositories associated with a code security configuration in an organization.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`configuration_id`** (integer) (required)
  The unique identifier of the code security configuration.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

- **`status`** (string)
  A comma-separated list of statuses. If specified, only repositories with these attachment statuses will be returned.
Can be: all, attached, attaching, detached, removed, enforced, failed, updating, removed_by_enterprise
  Default: `all`






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/code-security/configurations/CONFIGURATION_ID/repositories
```

**Response schema (Status: 200):**

Same response schema as [Get repositories associated with an enterprise code security configuration](#get-repositories-associated-with-an-enterprise-code-security-configuration).





## Get the code security configuration associated with a repository

```
GET /repos/{owner}/{repo}/code-security-configuration
```

Get the code security configuration that manages a repository's code security settings.
The authenticated user must be an administrator or security manager for the organization to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **204** - A header with no content is returned.


- **304** - Not modified


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-security-configuration
```

**Response schema (Status: 200):**

* `status`: string, enum: `attached`, `attaching`, `detached`, `removed`, `enforced`, `failed`, `updating`, `removed_by_enterprise`
* `configuration`: object:
  * `id`: integer
  * `name`: string
  * `target_type`: string, enum: `global`, `organization`, `enterprise`
  * `description`: string
  * `advanced_security`: string, enum: `enabled`, `disabled`, `code_security`, `secret_protection`
  * `dependency_graph`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependency_graph_autosubmit_action`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependency_graph_autosubmit_action_options`: object:
    * `labeled_runners`: boolean
  * `dependabot_alerts`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependabot_security_updates`: string, enum: `enabled`, `disabled`, `not_set`
  * `dependabot_delegated_alert_dismissal`: string or null, enum: `enabled`, `disabled`, `not_set`, `null`
  * `code_scanning_options`: object or null:
    * `allow_advanced`: boolean or null
  * `code_scanning_default_setup`: string, enum: `enabled`, `disabled`, `not_set`
  * `code_scanning_default_setup_options`: object or null:
    * `runner_type`: string or null, enum: `standard`, `labeled`, `not_set`, `null`
    * `runner_label`: string or null
  * `code_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_push_protection`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_bypass`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_bypass_options`: object:
    * `reviewers`: array of objects:
      * `reviewer_id`: required, integer
      * `reviewer_type`: required, string, enum: `TEAM`, `ROLE`
      * `mode`: string, enum: `ALWAYS`, `EXEMPT`, default: `"ALWAYS"`
      * `security_configuration_id`: integer
  * `secret_scanning_validity_checks`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_non_provider_patterns`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_generic_secrets`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_delegated_alert_dismissal`: string, enum: `enabled`, `disabled`, `not_set`
  * `secret_scanning_extended_metadata`: string, enum: `enabled`, `disabled`, `not_set`
  * `private_vulnerability_reporting`: string, enum: `enabled`, `disabled`, `not_set`
  * `enforcement`: string, enum: `enforced`, `unenforced`
  * `url`: string, format: uri
  * `html_url`: string, format: uri
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time