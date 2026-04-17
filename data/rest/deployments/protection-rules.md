# REST API endpoints for protection rules

Use the REST API to create, configure, and delete deployment protection rules.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get all deployment protection rules for an environment

```
GET /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules
```

Gets all custom deployment protection rules that are enabled for an environment. Anyone with read access to the repository can use this endpoint. For more information about environments, see "Using environments for deployment."
For more information about the app that is providing this custom deployment rule, see the documentation for the GET /apps/{app_slug} endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with a private repository.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.






### HTTP response status codes


- **200** - List of deployment protection rules




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment_protection_rules
```

**Response schema (Status: 200):**

* `total_count`: integer
* `custom_deployment_protection_rules`: array of `Deployment protection rule`:
  * `id`: required, integer
  * `node_id`: required, string
  * `enabled`: required, boolean
  * `app`: required, `Custom deployment protection rule app`:
    * `id`: required, integer
    * `slug`: required, string
    * `integration_url`: required, string
    * `node_id`: required, string





## Create a custom deployment protection rule on an environment

```
POST /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules
```

Enable a custom deployment protection rule for an environment.
The authenticated user must have admin or owner permissions to the repository to use this endpoint.
For more information about the app that is providing this custom deployment rule, see the documentation for the GET /apps/{app_slug} endpoint, as well as the guide to creating custom deployment protection rules.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.




#### Body parameters

- **`integration_id`** (integer)
  The ID of the custom app that will be enabled on the environment.





### HTTP response status codes


- **201** - The enabled custom deployment protection rule




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment_protection_rules \
  -d '{
  "integration_id": 5
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `node_id`: required, string
* `enabled`: required, boolean
* `app`: required, `Custom deployment protection rule app`:
  * `id`: required, integer
  * `slug`: required, string
  * `integration_url`: required, string
  * `node_id`: required, string





## List custom deployment rule integrations available for an environment

```
GET /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules/apps
```

Gets all custom deployment protection rule integrations that are available for an environment.
The authenticated user must have admin or owner permissions to the repository to use this endpoint.
For more information about environments, see "Using environments for deployment."
For more information about the app that is providing this custom deployment rule, see "GET an app".
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with a private repository.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






### HTTP response status codes


- **200** - A list of custom deployment rule integrations available for this environment.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment_protection_rules/apps
```

**Response schema (Status: 200):**

* `total_count`: integer
* `available_custom_deployment_protection_rule_integrations`: array of `Custom deployment protection rule app`:
  * `id`: required, integer
  * `slug`: required, string
  * `integration_url`: required, string
  * `node_id`: required, string





## Get a custom deployment protection rule

```
GET /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules/{protection_rule_id}
```

Gets an enabled custom deployment protection rule for an environment. Anyone with read access to the repository can use this endpoint. For more information about environments, see "Using environments for deployment."
For more information about the app that is providing this custom deployment rule, see GET /apps/{app_slug}.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with a private repository.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

- **`protection_rule_id`** (integer) (required)
  The unique identifier of the protection rule.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment_protection_rules/PROTECTION_RULE_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a custom deployment protection rule on an environment](#create-a-custom-deployment-protection-rule-on-an-environment).





## Disable a custom protection rule for an environment

```
DELETE /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules/{protection_rule_id}
```

Disables a custom deployment protection rule for an environment.
The authenticated user must have admin or owner permissions to the repository to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`protection_rule_id`** (integer) (required)
  The unique identifier of the protection rule.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment_protection_rules/PROTECTION_RULE_ID
```

**Response schema (Status: 204):**