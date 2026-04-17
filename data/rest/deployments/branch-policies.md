# REST API endpoints for deployment branch policies

Use the REST API to manage custom deployment branch policies.

## About deployment branch policies

You can use the REST API to specify custom name patterns that branches must match in order to deploy to an environment. The `deployment_branch_policy.custom_branch_policies` property for the environment must be set to `true` to use these endpoints. To update the `deployment_branch_policy` for an environment, see [REST API endpoints for deployment environments](/en/rest/deployments/environments#create-or-update-an-environment).

For more information about restricting environment deployments to certain branches, see [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#deployment-branches).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List deployment branch policies

```
GET /repos/{owner}/{repo}/environments/{environment_name}/deployment-branch-policies
```

Lists the deployment branch policies for an environment.
Anyone with read access to the repository can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with a private repository.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment-branch-policies
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `branch_policies`: required, array of `Deployment branch policy`:
  * `id`: integer
  * `node_id`: string
  * `name`: string
  * `type`: string, enum: `branch`, `tag`

## Create a deployment branch policy

```
POST /repos/{owner}/{repo}/environments/{environment_name}/deployment-branch-policies
```

Creates a deployment branch or tag policy for an environment.
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

* **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

#### Body parameters

* **`name`** (string) (required)
  The name pattern that branches or tags must match in order to deploy to the environment.
  Wildcard characters will not match /. For example, to match branches that begin with release/ and contain an additional single slash, use release/*/*.
  For more information about pattern matching syntax, see the Ruby File.fnmatch documentation.

* **`type`** (string)
  Whether this rule targets a branch or tag
  Can be one of: `branch`, `tag`

### HTTP response status codes

* **200** - OK

* **303** - Response if the same branch name pattern already exists

* **404** - Not Found or deployment\_branch\_policy.custom\_branch\_policies property for the environment is set to false

### Code examples

#### Example of a wildcard name pattern

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment-branch-policies \
  -d '{
  "name": "release/*"
}'
```

**Response schema (Status: 200):**

* `id`: integer
* `node_id`: string
* `name`: string
* `type`: string, enum: `branch`, `tag`

#### Example of a single branch name pattern

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment-branch-policies \
  -d '{
  "name": "main",
  "type": "branch"
}'
```

**Response schema (Status: 200):**

* `id`: integer
* `node_id`: string
* `name`: string
* `type`: string, enum: `branch`, `tag`

#### Example of a single tag name pattern

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment-branch-policies \
  -d '{
  "name": "v1",
  "type": "tag"
}'
```

**Response schema (Status: 200):**

* `id`: integer
* `node_id`: string
* `name`: string
* `type`: string, enum: `branch`, `tag`

## Get a deployment branch policy

```
GET /repos/{owner}/{repo}/environments/{environment_name}/deployment-branch-policies/{branch_policy_id}
```

Gets a deployment branch or tag policy for an environment.
Anyone with read access to the repository can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with a private repository.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

* **`branch_policy_id`** (integer) (required)
  The unique identifier of the branch policy.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment-branch-policies/BRANCH_POLICY_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a deployment branch policy](#create-a-deployment-branch-policy).

## Update a deployment branch policy

```
PUT /repos/{owner}/{repo}/environments/{environment_name}/deployment-branch-policies/{branch_policy_id}
```

Updates a deployment branch or tag policy for an environment.
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

* **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

* **`branch_policy_id`** (integer) (required)
  The unique identifier of the branch policy.

#### Body parameters

* **`name`** (string) (required)
  The name pattern that branches must match in order to deploy to the environment.
  Wildcard characters will not match /. For example, to match branches that begin with release/ and contain an additional single slash, use release/*/*.
  For more information about pattern matching syntax, see the Ruby File.fnmatch documentation.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment-branch-policies/BRANCH_POLICY_ID \
  -d '{
  "name": "release/*"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a deployment branch policy](#create-a-deployment-branch-policy).

## Delete a deployment branch policy

```
DELETE /repos/{owner}/{repo}/environments/{environment_name}/deployment-branch-policies/{branch_policy_id}
```

Deletes a deployment branch or tag policy for an environment.
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

* **`environment_name`** (string) (required)
  The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with %2F.

* **`branch_policy_id`** (integer) (required)
  The unique identifier of the branch policy.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME/deployment-branch-policies/BRANCH_POLICY_ID
```

**Response schema (Status: 204):**