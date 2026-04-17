# REST API endpoints for Copilot custom agents

Use the REST API to manage Copilot custom agents for your enterprise.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get custom agents for an enterprise

```
GET /enterprises/{enterprise}/copilot/custom-agents
```

Gets the list of all custom agents defined in the /agents/*.md files in the .github-private repository for the enterprise.
If no source repository has been configured, returns null for custom_agents.
Enterprise owners with read access to AI Controls can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


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


- **200** - Success


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Not found or source repository not found


- **500** - Internal Error




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/custom-agents
```

**Response schema (Status: 200):**

* `custom_agents`: array of objects or null:
  * `name`: string
  * `file_path`: string
  * `url`: string



#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/custom-agents
```

**Response schema (Status: 200):**

* `custom_agents`: array of objects or null:
  * `name`: string
  * `file_path`: string
  * `url`: string





## Get the source organization for custom agents in an enterprise

```
GET /enterprises/{enterprise}/copilot/custom-agents/source
```

Gets the organization and repository configured as the source for custom agent definitions in an enterprise.
Custom agents are enterprise-defined AI agents stored as markdown files in a special repository.
An enterprise admin configures one organization as the "source" and that org must have a repo named
.github-private containing agent definitions in /agents/*.md.
Enterprise owners with read access to AI Controls can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






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
  https://api.github.com/enterprises/ENTERPRISE/copilot/custom-agents/source
```

**Response schema (Status: 200):**

* `organization`: required, object or null:
  * `id`: required, integer
  * `login`: required, string
* `repository`: required, object or null:
  * `id`: required, integer
  * `name`: required, string
  * `full_name`: required, string





## Set the source organization for custom agents in an enterprise

```
PUT /enterprises/{enterprise}/copilot/custom-agents/source
```

Sets an organization as the source for custom agent definitions in the enterprise.
The organization must have a .github-private repository containing agent definitions.
By default, this endpoint also creates an enterprise-level ruleset to protect
agent definition files (agents/.md and .github/agents/.md). You can opt out
of ruleset creation by setting create_ruleset to false.
Enterprise owners with write access to AI Controls can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`organization_id`** (integer) (required)
  The ID of the organization to use as the custom agents source.

- **`create_ruleset`** (boolean)
  Whether to create a ruleset to protect agent definition files. Defaults to true.
  Default: `true`





### HTTP response status codes


- **200** - Success


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed


- **500** - Internal Error




### Code examples



#### Set source organization without creating a ruleset

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/copilot/custom-agents/source \
  -d '{
  "organization_id": 123,
  "create_ruleset": false
}'
```

**Response schema (Status: 200):**

* `organization`: object:
  * `id`: integer
  * `login`: string
  * `avatar_url`: string
* `repository`: object:
  * `id`: integer
  * `name`: string
  * `full_name`: string
* `ruleset`: object:
  * `id`: integer
  * `name`: string
  * `enforcement`: string





## Delete the custom agents source for an enterprise

```
DELETE /enterprises/{enterprise}/copilot/custom-agents/source
```

Removes the custom agents source configuration for the enterprise.
This effectively disables custom agents for the enterprise by removing
the reference to the source organization's .github-private repository.
Note: This does not delete the .github-private repository or any agent
definition files. It only removes the association between the enterprise
and the source repository.
Enterprise owners with write access to AI Controls can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **204** - No Content - The custom agents source was successfully removed.


- **403** - Forbidden - The user does not have enterprise admin access.


- **404** - Not found - Enterprise not found, feature not enabled, or no custom agents source is configured.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/copilot/custom-agents/source
```

**Response schema (Status: 204):**