# REST API endpoints for deployments

Use the REST API to create and delete deployments and deployment environments.

## About deployments

Deployments are requests to deploy a specific ref (branch, SHA, tag). GitHub dispatches a [`deployment` event](/en/webhooks-and-events/webhooks/webhook-events-and-payloads#deployment) that external services can listen for and act on when new deployments are created. Deployments enable developers and organizations to build loosely coupled tooling around deployments, without having to worry about the implementation details of delivering different types of applications (e.g., web, native).

Deployment statuses allow external services to mark deployments with an `error`, `failure`, `pending`, `in_progress`, `queued`, or `success` state that systems listening to [`deployment_status` events](/en/webhooks-and-events/webhooks/webhook-events-and-payloads#deployment_status) can consume.

Deployment statuses can also include an optional `description` and `log_url`, which are highly recommended because they make deployment statuses more useful. The `log_url` is the full URL to the deployment output, and
the `description` is a high-level summary of what happened with the deployment.

GitHub dispatches `deployment` and `deployment_status` events when new deployments and deployment statuses are created. These events allow third-party integrations to receive and respond to deployment requests, and update the status of a deployment as progress is made.

Below is a simple sequence diagram for how these interactions would work.

```text
+---------+             +--------+            +-----------+        +-------------+
| Tooling |             | GitHub |            | 3rd Party |        | Your Server |
+---------+             +--------+            +-----------+        +-------------+
     |                      |                       |                     |
     |  Create Deployment   |                       |                     |
     |--------------------->|                       |                     |
     |                      |                       |                     |
     |  Deployment Created  |                       |                     |
     |<---------------------|                       |                     |
     |                      |                       |                     |
     |                      |   Deployment Event    |                     |
     |                      |---------------------->|                     |
     |                      |                       |     SSH+Deploys     |
     |                      |                       |-------------------->|
     |                      |                       |                     |
     |                      |   Deployment Status   |                     |
     |                      |<----------------------|                     |
     |                      |                       |                     |
     |                      |                       |   Deploy Completed  |
     |                      |                       |<--------------------|
     |                      |                       |                     |
     |                      |   Deployment Status   |                     |
     |                      |<----------------------|                     |
     |                      |                       |                     |
```

Keep in mind that GitHub is never actually accessing your servers. It's up to your third-party integration to interact with deployment events. Multiple systems can listen for deployment events, and it's up to each of those systems to decide whether they're responsible for pushing the code out to your servers, building native code, etc.

Note that the `repo_deployment` [OAuth scope](/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps) grants targeted access to deployments and deployment statuses **without** granting access to repository code, while the `public_repo` and `repo` scopes grant permission to code as well.

### Inactive deployments

When you set the state of a deployment to `success`, then all prior non-transient, non-production environment deployments in the same repository with the same environment name will become `inactive`. To avoid this, you can set `auto_inactive` to `false` when creating the deployment status.

You can communicate that a transient environment no longer exists by setting its `state` to `inactive`. Setting the `state` to `inactive` shows the deployment as `destroyed` in GitHub and removes access to it.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List deployments

```
GET /repos/{owner}/{repo}/deployments
```

Simple filtering of deployments is available via query parameters:

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`sha`** (string)
  The SHA recorded at creation time.
  Default: `none`

* **`ref`** (string)
  The name of the ref. This can be a branch, tag, or SHA.
  Default: `none`

* **`task`** (string)
  The name of the task for the deployment (e.g., deploy or deploy:migrations).
  Default: `none`

* **`environment`** (string,null)
  The name of the environment that was deployed to (e.g., staging or production).
  Default: `none`

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
  https://api.github.com/repos/OWNER/REPO/deployments
```

**Response schema (Status: 200):**

Array of `Deployment`:

* `url`: required, string, format: uri
* `id`: required, integer, format: int64
* `node_id`: required, string
* `sha`: required, string
* `ref`: required, string
* `task`: required, string
* `payload`: required, one of:
  * **object, additional properties allowed**
  * **string**
* `original_environment`: string
* `environment`: required, string
* `description`: required, string or null
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `statuses_url`: required, string, format: uri
* `repository_url`: required, string, format: uri
* `transient_environment`: boolean
* `production_environment`: boolean
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

## Create a deployment

```
POST /repos/{owner}/{repo}/deployments
```

Deployments offer a few configurable parameters with certain defaults.
The ref parameter can be any named branch, tag, or SHA. At GitHub we often deploy branches and verify them
before we merge a pull request.
The environment parameter allows deployments to be issued to different runtime environments. Teams often have
multiple environments for verifying their applications, such as production, staging, and qa. This parameter
makes it easier to track which environments have requested deployments. The default environment is production.
The auto\_merge parameter is used to ensure that the requested ref is not behind the repository's default branch. If
the ref is behind the default branch for the repository, we will attempt to merge it for you. If the merge succeeds,
the API will return a successful merge commit. If merge conflicts prevent the merge from succeeding, the API will
return a failure response.
By default, commit statuses for every submitted context must be in a success
state. The required\_contexts parameter allows you to specify a subset of contexts that must be success, or to
specify contexts that have not yet been submitted. You are not required to use commit statuses to deploy. If you do
not require any contexts or create any commit statuses, the deployment will always succeed.
The payload parameter is available for any extra information that a deployment system might need. It is a JSON text
field that will be passed on when a deployment event is dispatched.
The task parameter is used by the deployment system to allow different execution paths. In the web world this might
be deploy:migrations to run schema changes on the system. In the compiled world this could be a flag to compile an
application with debugging enabled.
Merged branch response:
You will see this response when GitHub automatically merges the base branch into the topic branch instead of creating
a deployment. This auto-merge happens when:

Auto-merge option is enabled in the repository
Topic branch does not include the latest changes on the base branch, which is master in the response example
There are no merge conflicts

If there are no new commits in the base branch, a new request to create a deployment should give a successful
response.
Merge conflict response:
This error happens when the auto\_merge option is enabled and when the default branch (in this case master), can't
be merged into the branch that's being deployed (in this case topic-branch), due to merge conflicts.
Failed commit status checks:
This error happens when the required\_contexts parameter indicates that one or more contexts need to have a success
status for the commit to be deployed, but one or more of the required contexts do not have a state of success.
OAuth app tokens and personal access tokens (classic) need the repo or repo\_deployment scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`ref`** (string) (required)
  The ref to deploy. This can be a branch, tag, or SHA.

* **`task`** (string)
  Specifies a task to execute (e.g., deploy or deploy:migrations).
  Default: `deploy`

* **`auto_merge`** (boolean)
  Attempts to automatically merge the default branch into the requested ref, if it's behind the default branch.
  Default: `true`

* **`required_contexts`** (array of strings)
  The status contexts to verify against commit status checks. If you omit this parameter, GitHub verifies all unique contexts before creating a deployment. To bypass checking entirely, pass an empty array. Defaults to all unique contexts.

* **`payload`** (object or string)
  JSON payload with extra information about the deployment.

* **`environment`** (string)
  Name for the target deployment environment (e.g., production, staging, qa).
  Default: `production`

* **`description`** (string or null)
  Short description of the deployment.
  Default: \`\`

* **`transient_environment`** (boolean)
  Specifies if the given environment is specific to the deployment and will no longer exist at some point in the future. Default: false
  Default: `false`

* **`production_environment`** (boolean)
  Specifies if the given environment is one that end-users directly interact with. Default: true when environment is production and false otherwise.

### HTTP response status codes

* **201** - Created

* **202** - Merged branch response

* **409** - Conflict when there is a merge conflict or the commit's status checks failed

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Simple example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/deployments \
  -d '{
  "ref": "topic-branch",
  "payload": "{ \"deploy\": \"migrate\" }",
  "description": "Deploy request from hubot"
}'
```

**Response schema (Status: 201):**

* `url`: required, string, format: uri
* `id`: required, integer, format: int64
* `node_id`: required, string
* `sha`: required, string
* `ref`: required, string
* `task`: required, string
* `payload`: required, one of:
  * **object, additional properties allowed**
  * **string**
* `original_environment`: string
* `environment`: required, string
* `description`: required, string or null
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
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `statuses_url`: required, string, format: uri
* `repository_url`: required, string, format: uri
* `transient_environment`: boolean
* `production_environment`: boolean
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

## Get a deployment

```
GET /repos/{owner}/{repo}/deployments/{deployment_id}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`deployment_id`** (integer) (required)
  deployment\_id parameter

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/deployments/DEPLOYMENT_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a deployment](#create-a-deployment).

## Delete a deployment

```
DELETE /repos/{owner}/{repo}/deployments/{deployment_id}
```

If the repository only has one deployment, you can delete the deployment regardless of its status. If the repository has more than one deployment, you can only delete inactive deployments. This ensures that repositories with multiple deployments will always have an active deployment.
To set a deployment as inactive, you must:

Create a new deployment that is active so that the system has a record of the current state, then delete the previously active deployment.
Mark the active deployment as inactive by adding any non-successful deployment status.

For more information, see "Create a deployment" and "Create a deployment status."
OAuth app tokens and personal access tokens (classic) need the repo or repo\_deployment scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`deployment_id`** (integer) (required)
  deployment\_id parameter

### HTTP response status codes

* **204** - No Content

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/deployments/DEPLOYMENT_ID
```

**Response schema (Status: 204):**