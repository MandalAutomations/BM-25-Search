# REST API endpoints for deployment environments

Use the REST API to create, configure, and delete deployment environments.

## About deployment environments

For more information about environments, see [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment). To manage environment secrets, see [REST API endpoints for GitHub Actions Secrets](/en/rest/actions/secrets).

Environments, environment secrets, and deployment protection rules are available in public repositories for all current GitHub plans. They are not available on legacy plans, such as Bronze, Silver, or Gold. For access to environments, environment secrets, and deployment branches in private or internal repositories, you must use GitHub Pro, GitHub Team, or GitHub Enterprise. If you are on a GitHub Free, GitHub Pro, or GitHub Team plan, other deployment protection rules, such as a wait timer or required reviewers, are only available for public repositories.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List environments

```
GET /repos/{owner}/{repo}/environments
```

Lists the environments for a repository.
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
  https://api.github.com/repos/OWNER/REPO/environments
```

**Response schema (Status: 200):**

* `total_count`: integer
* `environments`: array of `Environment`:
  * `id`: required, integer, format: int64
  * `node_id`: required, string
  * `name`: required, string
  * `url`: required, string
  * `html_url`: required, string
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `protection_rules`: array of object
  * `deployment_branch_policy`: object or null:
    * `protected_branches`: required, boolean
    * `custom_branch_policies`: required, boolean

## Get an environment

```
GET /repos/{owner}/{repo}/environments/{environment_name}
```

Note

To get information about name patterns that branches must match in order to deploy to this environment, see "Get a deployment branch policy."

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

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME
```

**Response schema (Status: 200):**

* `id`: required, integer, format: int64
* `node_id`: required, string
* `name`: required, string
* `url`: required, string
* `html_url`: required, string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `protection_rules`: array of object
* `deployment_branch_policy`: object or null:
  * `protected_branches`: required, boolean
  * `custom_branch_policies`: required, boolean

## Create or update an environment

```
PUT /repos/{owner}/{repo}/environments/{environment_name}
```

Create or update an environment with protection rules, such as required reviewers. For more information about environment protection rules, see "Environments."
Note

To create or update name patterns that branches must match in order to deploy to this environment, see "Deployment branch policies."

Note

To create or update secrets for an environment, see "GitHub Actions secrets."

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

* **`wait_timer`** (integer)
  The amount of time to delay a job after the job is initially triggered. The time (in minutes) must be an integer between 0 and 43,200 (30 days).

* **`prevent_self_review`** (boolean)
  Whether or not a user who created the job is prevented from approving their own job.

* **`reviewers`** (array of objects or null)
  The people or teams that may review jobs that reference the environment. You can list up to six users or teams as reviewers. The reviewers must have at least read access to the repository. Only one of the required reviewers needs to approve the job for it to proceed.
  * **`type`** (string)
    The type of reviewer.
    Can be one of: `User`, `Team`
  * **`id`** (integer)
    The id of the user or team who can review the deployment

* **`deployment_branch_policy`** (object or null)
  The type of deployment branch policy for this environment. To allow all branches to deploy, set to null.
  * **`protected_branches`** (boolean) (required)
    Whether only branches with branch protection rules can deploy to this environment. If protected\_branches is true, custom\_branch\_policies must be false; if protected\_branches is false, custom\_branch\_policies must be true.
  * **`custom_branch_policies`** (boolean) (required)
    Whether only branches that match the specified name patterns can deploy to this environment.  If custom\_branch\_policies is true, protected\_branches must be false; if custom\_branch\_policies is false, protected\_branches must be true.

### HTTP response status codes

* **200** - OK

* **422** - Validation error when the environment name is invalid or when protected\_branches and custom\_branch\_policies in deployment\_branch\_policy are set to the same value

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME \
  -d '{
  "wait_timer": 30,
  "prevent_self_review": false,
  "reviewers": [
    {
      "type": "User",
      "id": 1
    },
    {
      "type": "Team",
      "id": 1
    }
  ],
  "deployment_branch_policy": {
    "protected_branches": false,
    "custom_branch_policies": true
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an environment](#get-an-environment).

## Delete an environment

```
DELETE /repos/{owner}/{repo}/environments/{environment_name}
```

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

### HTTP response status codes

* **204** - Default response

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/environments/ENVIRONMENT_NAME
```

**Response schema (Status: 204):**