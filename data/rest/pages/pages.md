# REST API endpoints for {% data variables.product.prodname_pages %}

Use the REST API to interact with GitHub Pages sites and builds.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get a GitHub Pages site

```
GET /repos/{owner}/{repo}/pages
```

Gets information about a GitHub Pages site.
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


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/pages
```

**Response schema (Status: 200):**

* `url`: required, string, format: uri
* `status`: required, string or null, enum: `built`, `building`, `errored`, `null`
* `cname`: required, string or null
* `protected_domain_state`: string or null, enum: `pending`, `verified`, `unverified`, `null`
* `pending_domain_unverified_at`: string or null, format: date-time
* `custom_404`: required, boolean, default: `false`
* `html_url`: string, format: uri
* `build_type`: string or null, enum: `legacy`, `workflow`, `null`
* `source`: `Pages Source Hash`:
  * `branch`: required, string
  * `path`: required, string
* `public`: required, boolean
* `https_certificate`: `Pages Https Certificate`:
  * `state`: required, string, enum: `new`, `authorization_created`, `authorization_pending`, `authorized`, `authorization_revoked`, `issued`, `uploaded`, `approved`, `errored`, `bad_authz`, `destroy_pending`, `dns_changed`
  * `description`: required, string
  * `domains`: required, array of string
  * `expires_at`: string, format: date
* `https_enforced`: boolean





## Create a GitHub Pages site

```
POST /repos/{owner}/{repo}/pages
```

Configures a GitHub Pages site. For more information, see "About GitHub Pages."
The authenticated user must be a repository administrator, maintainer, or have the 'manage GitHub Pages settings' permission.
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




#### Body parameters

- **`build_type`** (string)
  The process in which the Page will be built. Possible values are "legacy" and "workflow".
  Can be one of: `legacy`, `workflow`

- **`source`** (object)
  The source branch and directory used to publish your Pages site.
  - **`branch`** (string) (required)
    The repository branch used to publish your site's source files.
  - **`path`** (string)
    The repository directory that includes the source files for the Pages site. Allowed paths are / or /docs. Default: /
    Default: `/`
    Can be one of: `/`, `/docs`





### HTTP response status codes


- **201** - Created


- **409** - Conflict


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pages \
  -d '{
  "source": {
    "branch": "main",
    "path": "/docs"
  }
}'
```

**Response schema (Status: 201):**

Same response schema as [Get a GitHub Pages site](#get-a-github-pages-site).





## Update information about a GitHub Pages site

```
PUT /repos/{owner}/{repo}/pages
```

Updates information for a GitHub Pages site. For more information, see "About GitHub Pages.
The authenticated user must be a repository administrator, maintainer, or have the 'manage GitHub Pages settings' permission.
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




#### Body parameters

- **`cname`** (string or null)
  Specify a custom domain for the repository. Sending a null value will remove the custom domain. For more about custom domains, see "Using a custom domain with GitHub Pages."

- **`https_enforced`** (boolean)
  Specify whether HTTPS should be enforced for the repository.

- **`build_type`** (string)
  The process by which the GitHub Pages site will be built. workflow means that the site is built by a custom GitHub Actions workflow. legacy means that the site is built by GitHub when changes are pushed to a specific branch.
  Can be one of: `legacy`, `workflow`

- **`source`** (object)
  Update the source for the repository. Must include the branch name and path.
  - **`branch`** (string) (required)
    The repository branch used to publish your site's source files.
  - **`path`** (string) (required)
    The repository directory that includes the source files for the Pages site. Allowed paths are / or /docs.
    Can be one of: `/`, `/docs`





### HTTP response status codes


- **204** - No Content


- **400** - Bad Request


- **409** - Conflict


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/pages \
  -d '{
  "cname": "octocatblog.com",
  "source": {
    "branch": "main",
    "path": "/"
  }
}'
```

**Response schema (Status: 204):**





## Delete a GitHub Pages site

```
DELETE /repos/{owner}/{repo}/pages
```

Deletes a GitHub Pages site. For more information, see "About GitHub Pages.
The authenticated user must be a repository administrator, maintainer, or have the 'manage GitHub Pages settings' permission.
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


- **204** - No Content


- **404** - Resource not found


- **409** - Conflict


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/pages
```

**Response schema (Status: 204):**





## List GitHub Pages builds

```
GET /repos/{owner}/{repo}/pages/builds
```

Lists builts of a GitHub Pages site.
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
  https://api.github.com/repos/OWNER/REPO/pages/builds
```

**Response schema (Status: 200):**

Array of `Page Build`:
  * `url`: required, string, format: uri
  * `status`: required, string
  * `error`: required, object:
    * `message`: required, string or null
  * `pusher`: required, any of:
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
  * `commit`: required, string
  * `duration`: required, integer
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time





## Request a GitHub Pages build

```
POST /repos/{owner}/{repo}/pages/builds
```

You can request that your site be built from the latest revision on the default branch. This has the same effect as pushing a commit to your default branch, but does not require an additional commit. Manually triggering page builds can be helpful when diagnosing build warnings and failures.
Build requests are limited to one concurrent build per repository and one concurrent build per requester. If you request a build while another is still in progress, the second request will be queued until the first completes.


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


- **201** - Created




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pages/builds
```

**Response schema (Status: 201):**

* `url`: required, string, format: uri
* `status`: required, string





## Get latest Pages build

```
GET /repos/{owner}/{repo}/pages/builds/latest
```

Gets information about the single most recent build of a GitHub Pages site.
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




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/pages/builds/latest
```

**Response schema (Status: 200):**

* `url`: required, string, format: uri
* `status`: required, string
* `error`: required, object:
  * `message`: required, string or null
* `pusher`: required, any of:
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
* `commit`: required, string
* `duration`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time





## Get GitHub Pages build

```
GET /repos/{owner}/{repo}/pages/builds/{build_id}
```

Gets information about a GitHub Pages build.
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

- **`build_id`** (integer) (required)






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/pages/builds/BUILD_ID
```

**Response schema (Status: 200):**

Same response schema as [Get latest Pages build](#get-latest-pages-build).





## Create a GitHub Pages deployment

```
POST /repos/{owner}/{repo}/pages/deployments
```

Create a GitHub Pages deployment for a repository.
The authenticated user must have write permission to the repository.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.




#### Body parameters

- **`artifact_id`** (number)
  The ID of an artifact that contains the .zip or .tar of static assets to deploy. The artifact belongs to the repository. Either artifact_id or artifact_url are required.

- **`artifact_url`** (string)
  The URL of an artifact that contains the .zip or .tar of static assets to deploy. The artifact belongs to the repository. Either artifact_id or artifact_url are required.

- **`environment`** (string)
  The target environment for this GitHub Pages deployment.
  Default: `github-pages`

- **`pages_build_version`** (string) (required)
  A unique string that represents the version of the build for this deployment.
  Default: `GITHUB_SHA`

- **`oidc_token`** (string) (required)
  The OIDC token issued by GitHub Actions certifying the origin of the deployment.





### HTTP response status codes


- **200** - OK


- **400** - Bad Request


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pages/deployments \
  -d '{
  "artifact_url": "https://downloadcontent/",
  "environment": "github-pages",
  "pages_build_version": "4fd754f7e594640989b406850d0bc8f06a121251",
  "oidc_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6IlV2R1h4SUhlY0JFc1JCdEttemUxUEhfUERiVSIsImtpZCI6IjUyRjE5N0M0ODFERTcwMTEyQzQ0MUI0QTlCMzdCNTNDN0ZDRjBEQjUifQ.eyJqdGkiOiJhMWIwNGNjNy0zNzZiLTQ1N2QtOTMzNS05NTY5YmVjZDExYTIiLCJzdWIiOiJyZXBvOnBhcGVyLXNwYS9taW55aTplbnZpcm9ubWVudDpQcm9kdWN0aW9uIiwiYXVkIjoiaHR0cHM6Ly9naXRodWIuY29tL3BhcGVyLXNwYSIsInJlZiI6InJlZnMvaGVhZHMvbWFpbiIsInNoYSI6ImEyODU1MWJmODdiZDk3NTFiMzdiMmM0YjM3M2MxZjU3NjFmYWM2MjYiLCJyZXBvc2l0b3J5IjoicGFwZXItc3BhL21pbnlpIiwicmVwb3NpdG9yeV9vd25lciI6InBhcGVyLXNwYSIsInJ1bl9pZCI6IjE1NDY0NTkzNjQiLCJydW5fbnVtYmVyIjoiMzQiLCJydW5fYXR0ZW1wdCI6IjYiLCJhY3RvciI6IllpTXlzdHkiLCJ3b3JrZmxvdyI6IkNJIiwiaGVhZF9yZWYiOiIiLCJiYXNlX3JlZiI6IiIsImV2ZW50X25hbWUiOiJwdXNoIiwicmVmX3R5cGUiOiJicmFuY2giLCJlbnZpcm9ubWVudCI6IlByb2R1Y3Rpb24iLCJqb2Jfd29ya2Zsb3dfcmVmIjoicGFwZXItc3BhL21pbnlpLy5naXRodWIvd29ya2Zsb3dzL2JsYW5rLnltbEByZWZzL2hlYWRzL21haW4iLCJpc3MiOiJodHRwczovL3Rva2VuLmFjdGlvbnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwibmJmIjoxNjM5MDAwODU2LCJleHAiOjE2MzkwMDE3NTYsImlhdCI6MTYzOTAwMTQ1Nn0.VP8WictbQECKozE2SgvKb2FqJ9hisWsoMkYRTqfBrQfZTCXi5IcFEdgDMB2X7a99C2DeUuTvHh9RMKXLL2a0zg3-Sd7YrO7a2ll2kNlnvyIypcN6AeIc7BxHsTTnZN9Ud_xmEsTrSRGOEKmzCFkULQ6N4zlVD0sidypmXlMemmWEcv_ZHqhioEI_VMp5vwXQurketWH7qX4oDgG4okyYtPrv5RQHbfQcVo9izaPJ_jnsDd0CBA0QOx9InjPidtIkMYQLyUgJy33HLJy86EFNUnAf8UhBQuQi5mAsEpEzBBuKpG3PDiPtYCHOk64JZkZGd5mR888a5sbHRiaF8hm8YA"
}'
```

**Response schema (Status: 200):**

* `id`: required, one of:
  * **integer**
  * **string**
* `status_url`: required, string, format: uri
* `page_url`: required, string, format: uri
* `preview_url`: string, format: uri





## Get the status of a GitHub Pages deployment

```
GET /repos/{owner}/{repo}/pages/deployments/{pages_deployment_id}
```

Gets the current status of a GitHub Pages deployment.
The authenticated user must have read permission for the GitHub Pages site.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`pages_deployment_id`** (string) (required)
  The ID of the Pages deployment. You can also give the commit SHA of the deployment.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/pages/deployments/PAGES_DEPLOYMENT_ID
```

**Response schema (Status: 200):**

* `status`: string, enum: `deployment_in_progress`, `syncing_files`, `finished_file_sync`, `updating_pages`, `purging_cdn`, `deployment_cancelled`, `deployment_failed`, `deployment_content_failed`, `deployment_attempt_error`, `deployment_lost`, `succeed`





## Cancel a GitHub Pages deployment

```
POST /repos/{owner}/{repo}/pages/deployments/{pages_deployment_id}/cancel
```

Cancels a GitHub Pages deployment.
The authenticated user must have write permissions for the GitHub Pages site.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`pages_deployment_id`** (string) (required)
  The ID of the Pages deployment. You can also give the commit SHA of the deployment.






### HTTP response status codes


- **204** - A header with no content is returned.


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pages/deployments/PAGES_DEPLOYMENT_ID/cancel
```

**Response schema (Status: 204):**





## Get a DNS health check for GitHub Pages

```
GET /repos/{owner}/{repo}/pages/health
```

Gets a health check of the DNS settings for the CNAME record configured for a repository's GitHub Pages.
The first request to this endpoint returns a 202 Accepted status and starts an asynchronous background task to get the results for the domain. After the background task completes, subsequent requests to this endpoint return a 200 OK status with the health check results in the response.
The authenticated user must be a repository administrator, maintainer, or have the 'manage GitHub Pages settings' permission to use this endpoint.
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


- **202** - Empty response


- **400** - Custom domains are not available for GitHub Pages


- **404** - Resource not found


- **422** - There isn't a CNAME for this page




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/pages/health
```

**Response schema (Status: 200):**

* `domain`: object:
  * `host`: string
  * `uri`: string
  * `nameservers`: string
  * `dns_resolves`: boolean
  * `is_proxied`: boolean or null
  * `is_cloudflare_ip`: boolean or null
  * `is_fastly_ip`: boolean or null
  * `is_old_ip_address`: boolean or null
  * `is_a_record`: boolean or null
  * `has_cname_record`: boolean or null
  * `has_mx_records_present`: boolean or null
  * `is_valid_domain`: boolean
  * `is_apex_domain`: boolean
  * `should_be_a_record`: boolean or null
  * `is_cname_to_github_user_domain`: boolean or null
  * `is_cname_to_pages_dot_github_dot_com`: boolean or null
  * `is_cname_to_fastly`: boolean or null
  * `is_pointed_to_github_pages_ip`: boolean or null
  * `is_non_github_pages_ip_present`: boolean or null
  * `is_pages_domain`: boolean
  * `is_served_by_pages`: boolean or null
  * `is_valid`: boolean
  * `reason`: string or null
  * `responds_to_https`: boolean
  * `enforces_https`: boolean
  * `https_error`: string or null
  * `is_https_eligible`: boolean or null
  * `caa_error`: string or null
* `alt_domain`: object or null:
  * `host`: string
  * `uri`: string
  * `nameservers`: string
  * `dns_resolves`: boolean
  * `is_proxied`: boolean or null
  * `is_cloudflare_ip`: boolean or null
  * `is_fastly_ip`: boolean or null
  * `is_old_ip_address`: boolean or null
  * `is_a_record`: boolean or null
  * `has_cname_record`: boolean or null
  * `has_mx_records_present`: boolean or null
  * `is_valid_domain`: boolean
  * `is_apex_domain`: boolean
  * `should_be_a_record`: boolean or null
  * `is_cname_to_github_user_domain`: boolean or null
  * `is_cname_to_pages_dot_github_dot_com`: boolean or null
  * `is_cname_to_fastly`: boolean or null
  * `is_pointed_to_github_pages_ip`: boolean or null
  * `is_non_github_pages_ip_present`: boolean or null
  * `is_pages_domain`: boolean
  * `is_served_by_pages`: boolean or null
  * `is_valid`: boolean
  * `reason`: string or null
  * `responds_to_https`: boolean
  * `enforces_https`: boolean
  * `https_error`: string or null
  * `is_https_eligible`: boolean or null
  * `caa_error`: string or null