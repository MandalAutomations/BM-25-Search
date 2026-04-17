# REST API endpoints for deployment statuses

Use the REST API to manage deployment statuses.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List deployment statuses

```
GET /repos/{owner}/{repo}/deployments/{deployment_id}/statuses
```

Users with pull access can view deployment statuses for a deployment:


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`deployment_id`** (integer) (required)
  deployment_id parameter

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/deployments/DEPLOYMENT_ID/statuses
```

**Response schema (Status: 200):**

Array of `Deployment Status`:
  * `url`: required, string, format: uri
  * `id`: required, integer, format: int64
  * `node_id`: required, string
  * `state`: required, string, enum: `error`, `failure`, `inactive`, `pending`, `success`, `queued`, `in_progress`
  * `creator`: required, any of:
    * **null**
    * **Simple User**
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
  * `description`: required, string, default: `""`, maxLength: 140
  * `environment`: string, default: `""`
  * `target_url`: required, string, format: uri, default: `""`
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `deployment_url`: required, string, format: uri
  * `repository_url`: required, string, format: uri
  * `environment_url`: string, format: uri, default: `""`
  * `log_url`: string, format: uri, default: `""`
  * `performed_via_github_app`: any of:
    * **null**
    * **GitHub app**
      * `id`: required, integer
      * `slug`: string
      * `node_id`: required, string
      * `client_id`: string
      * `owner`: required, one of:
        * **Simple User**
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
        * **Enterprise**
          * `description`: string or null
          * `html_url`: required, string, format: uri
          * `website_url`: string or null, format: uri
          * `id`: required, integer
          * `node_id`: required, string
          * `name`: required, string
          * `slug`: required, string
          * `created_at`: required, string or null, format: date-time
          * `updated_at`: required, string or null, format: date-time
          * `avatar_url`: required, string, format: uri
      * `name`: required, string
      * `description`: required, string or null
      * `external_url`: required, string, format: uri
      * `html_url`: required, string, format: uri
      * `created_at`: required, string, format: date-time
      * `updated_at`: required, string, format: date-time
      * `permissions`: required, object, additional properties: string:
        * `issues`: string
        * `checks`: string
        * `metadata`: string
        * `contents`: string
        * `deployments`: string
      * `events`: required, array of string
      * `installations_count`: integer





## Create a deployment status

```
POST /repos/{owner}/{repo}/deployments/{deployment_id}/statuses
```

Users with push access can create deployment statuses for a given deployment.
OAuth app tokens and personal access tokens (classic) need the repo_deployment scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`deployment_id`** (integer) (required)
  deployment_id parameter




#### Body parameters

- **`state`** (string) (required)
  The state of the status. When you set a transient deployment to inactive, the deployment will be shown as destroyed in GitHub.
  Can be one of: `error`, `failure`, `inactive`, `in_progress`, `queued`, `pending`, `success`

- **`target_url`** (string)
  The target URL to associate with this status. This URL should contain output to keep the user updated while the task is running or serve as historical information for what happened in the deployment.
Note

It's recommended to use the log_url parameter, which replaces target_url.
  Default: ``

- **`log_url`** (string)
  The full URL of the deployment's output. This parameter replaces target_url. We will continue to accept target_url to support legacy uses, but we recommend replacing target_url with log_url. Setting log_url will automatically set target_url to the same value. Default: ""
  Default: ``

- **`description`** (string)
  A short description of the status. The maximum description length is 140 characters.
  Default: ``

- **`environment`** (string)
  Name for the target deployment environment, which can be changed when setting a deploy status. For example, production, staging, or qa. If not defined, the environment of the previous status on the deployment will be used, if it exists. Otherwise, the environment of the deployment will be used.

- **`environment_url`** (string)
  Sets the URL for accessing your environment. Default: ""
  Default: ``

- **`auto_inactive`** (boolean)
  Adds a new inactive status to all prior non-transient, non-production environment deployments with the same repository and environment name as the created status's deployment. An inactive status is only added to deployments that had a success state. Default: true





### HTTP response status codes


- **201** - Created


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/deployments/DEPLOYMENT_ID/statuses \
  -d '{
  "environment": "production",
  "state": "success",
  "log_url": "https://example.com/deployment/42/output",
  "description": "Deployment finished successfully."
}'
```

**Response schema (Status: 201):**

* `url`: required, string, format: uri
* `id`: required, integer, format: int64
* `node_id`: required, string
* `state`: required, string, enum: `error`, `failure`, `inactive`, `pending`, `success`, `queued`, `in_progress`
* `creator`: required, any of:
  * **null**
  * **Simple User**
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
* `description`: required, string, default: `""`, maxLength: 140
* `environment`: string, default: `""`
* `target_url`: required, string, format: uri, default: `""`
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `deployment_url`: required, string, format: uri
* `repository_url`: required, string, format: uri
* `environment_url`: string, format: uri, default: `""`
* `log_url`: string, format: uri, default: `""`
* `performed_via_github_app`: any of:
  * **null**
  * **GitHub app**
    * `id`: required, integer
    * `slug`: string
    * `node_id`: required, string
    * `client_id`: string
    * `owner`: required, one of:
      * **Simple User**
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
      * **Enterprise**
        * `description`: string or null
        * `html_url`: required, string, format: uri
        * `website_url`: string or null, format: uri
        * `id`: required, integer
        * `node_id`: required, string
        * `name`: required, string
        * `slug`: required, string
        * `created_at`: required, string or null, format: date-time
        * `updated_at`: required, string or null, format: date-time
        * `avatar_url`: required, string, format: uri
    * `name`: required, string
    * `description`: required, string or null
    * `external_url`: required, string, format: uri
    * `html_url`: required, string, format: uri
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `permissions`: required, object, additional properties: string:
      * `issues`: string
      * `checks`: string
      * `metadata`: string
      * `contents`: string
      * `deployments`: string
    * `events`: required, array of string
    * `installations_count`: integer





## Get a deployment status

```
GET /repos/{owner}/{repo}/deployments/{deployment_id}/statuses/{status_id}
```

Users with pull access can view a deployment status for a deployment:


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`deployment_id`** (integer) (required)
  deployment_id parameter

- **`status_id`** (integer) (required)






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/deployments/DEPLOYMENT_ID/statuses/STATUS_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a deployment status](#create-a-deployment-status).