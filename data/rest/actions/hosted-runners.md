# GitHub-hosted runners

Use the REST API to interact with GitHub-hosted runners in GitHub Actions.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List GitHub-hosted runners for an organization

```
GET /orgs/{org}/actions/hosted-runners
```

Lists all GitHub-hosted runners configured in an organization.
OAuth app tokens and personal access tokens (classic) need the manage_runner:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/actions/hosted-runners
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `runners`: required, array of `GitHub-hosted hosted runner`:
  * `id`: required, integer
  * `name`: required, string
  * `runner_group_id`: integer
  * `image_details`: required, any of:
    * **null**
    * **GitHub-hosted runner image details.**
      * `id`: required, string
      * `size_gb`: required, integer
      * `display_name`: required, string
      * `source`: required, string, enum: `github`, `partner`, `custom`
      * `version`: string
  * `machine_size_details`: required, `Github-owned VM details.`:
    * `id`: required, string
    * `cpu_cores`: required, integer
    * `memory_gb`: required, integer
    * `storage_gb`: required, integer
  * `status`: required, string, enum: `Ready`, `Provisioning`, `Shutdown`, `Deleting`, `Stuck`
  * `platform`: required, string
  * `maximum_runners`: integer, default: `10`
  * `public_ip_enabled`: required, boolean
  * `public_ips`: array of `Public IP for a GitHub-hosted larger runners.`:
    * `enabled`: boolean
    * `prefix`: string
    * `length`: integer
  * `last_active_on`: string or null, format: date-time
  * `image_gen`: boolean





## Create a GitHub-hosted runner for an organization

```
POST /orgs/{org}/actions/hosted-runners
```

Creates a GitHub-hosted runner for an organization.
OAuth tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`name`** (string) (required)
  Name of the runner. Must be between 1 and 64 characters and may only contain upper and lowercase letters a-z, numbers 0-9, '.', '-', and '_'.

- **`image`** (object) (required)
  The image of runner. To list all available images, use GET /actions/hosted-runners/images/github-owned or GET /actions/hosted-runners/images/partner.
  - **`id`** (string)
    The unique identifier of the runner image.
  - **`source`** (string)
    The source of the runner image.
    Can be one of: `github`, `partner`, `custom`
  - **`version`** (string or null)
    The version of the runner image to deploy. This is relevant only for runners using custom images.

- **`size`** (string) (required)
  The machine size of the runner. To list available sizes, use GET actions/hosted-runners/machine-sizes

- **`runner_group_id`** (integer) (required)
  The existing runner group to add this runner to.

- **`maximum_runners`** (integer)
  The maximum amount of runners to scale up to. Runners will not auto-scale above this number. Use this setting to limit your cost.

- **`enable_static_ip`** (boolean)
  Whether this runner should be created with a static public IP. Note limit on account. To list limits on account, use GET actions/hosted-runners/limits

- **`image_gen`** (boolean)
  Whether this runner should be used to generate custom images.
  Default: `false`





### HTTP response status codes


- **201** - Created




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/actions/hosted-runners \
  -d '{
  "name": "My Hosted runner",
  "image": {
    "id": "ubuntu-latest",
    "source": "github"
  },
  "runner_group_id": 1,
  "size": "4-core",
  "maximum_runners": 50,
  "enable_static_ip": false
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `name`: required, string
* `runner_group_id`: integer
* `image_details`: required, any of:
  * **null**
  * **GitHub-hosted runner image details.**
    * `id`: required, string
    * `size_gb`: required, integer
    * `display_name`: required, string
    * `source`: required, string, enum: `github`, `partner`, `custom`
    * `version`: string
* `machine_size_details`: required, `Github-owned VM details.`:
  * `id`: required, string
  * `cpu_cores`: required, integer
  * `memory_gb`: required, integer
  * `storage_gb`: required, integer
* `status`: required, string, enum: `Ready`, `Provisioning`, `Shutdown`, `Deleting`, `Stuck`
* `platform`: required, string
* `maximum_runners`: integer, default: `10`
* `public_ip_enabled`: required, boolean
* `public_ips`: array of `Public IP for a GitHub-hosted larger runners.`:
  * `enabled`: boolean
  * `prefix`: string
  * `length`: integer
* `last_active_on`: string or null, format: date-time
* `image_gen`: boolean





## List custom images for an organization

```
GET /orgs/{org}/actions/hosted-runners/images/custom
```

List custom images for an organization.
OAuth tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/images/custom
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `images`: required, array of `GitHub-hosted runner custom image details`:
  * `id`: required, integer
  * `platform`: required, string
  * `total_versions_size`: required, integer
  * `name`: required, string
  * `source`: required, string
  * `versions_count`: required, integer
  * `latest_version`: required, string
  * `state`: required, string





## Get a custom image definition for GitHub Actions Hosted Runners

```
GET /orgs/{org}/actions/hosted-runners/images/custom/{image_definition_id}
```

Get a custom image definition for GitHub Actions Hosted Runners.
OAuth tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`image_definition_id`** (integer) (required)
  Image definition ID of custom image






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/images/custom/IMAGE_DEFINITION_ID
```

**Response schema (Status: 200):**

* `id`: required, integer
* `platform`: required, string
* `total_versions_size`: required, integer
* `name`: required, string
* `source`: required, string
* `versions_count`: required, integer
* `latest_version`: required, string
* `state`: required, string





## Delete a custom image from the organization

```
DELETE /orgs/{org}/actions/hosted-runners/images/custom/{image_definition_id}
```

Delete a custom image from the organization.
OAuth tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`image_definition_id`** (integer) (required)
  Image definition ID of custom image






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/hosted-runners/images/custom/IMAGE_DEFINITION_ID
```

**Response schema (Status: 204):**





## List image versions of a custom image for an organization

```
GET /orgs/{org}/actions/hosted-runners/images/custom/{image_definition_id}/versions
```

List image versions of a custom image for an organization.
OAuth tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`image_definition_id`** (integer) (required)
  Image definition ID of custom image

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/images/custom/IMAGE_DEFINITION_ID/versions
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `image_versions`: required, array of `GitHub-hosted runner custom image version details.`:
  * `version`: required, string
  * `state`: required, string
  * `size_gb`: required, integer
  * `created_on`: required, string
  * `state_details`: required, string





## Get an image version of a custom image for GitHub Actions Hosted Runners

```
GET /orgs/{org}/actions/hosted-runners/images/custom/{image_definition_id}/versions/{version}
```

Get an image version of a custom image for GitHub Actions Hosted Runners.
OAuth tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`image_definition_id`** (integer) (required)
  Image definition ID of custom image

- **`version`** (string) (required)
  Version of a custom image






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/images/custom/IMAGE_DEFINITION_ID/versions/VERSION
```

**Response schema (Status: 200):**

* `version`: required, string
* `state`: required, string
* `size_gb`: required, integer
* `created_on`: required, string
* `state_details`: required, string





## Delete an image version of custom image from the organization

```
DELETE /orgs/{org}/actions/hosted-runners/images/custom/{image_definition_id}/versions/{version}
```

Delete an image version of custom image from the organization.
OAuth tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`image_definition_id`** (integer) (required)
  Image definition ID of custom image

- **`version`** (string) (required)
  Version of a custom image






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/hosted-runners/images/custom/IMAGE_DEFINITION_ID/versions/VERSION
```

**Response schema (Status: 204):**





## Get GitHub-owned images for GitHub-hosted runners in an organization

```
GET /orgs/{org}/actions/hosted-runners/images/github-owned
```

Get the list of GitHub-owned images available for GitHub-hosted runners for an organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/images/github-owned
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `images`: required, array of `GitHub-hosted runner image details.`:
  * `id`: required, string
  * `platform`: required, string
  * `size_gb`: required, integer
  * `display_name`: required, string
  * `source`: required, string, enum: `github`, `partner`, `custom`





## Get partner images for GitHub-hosted runners in an organization

```
GET /orgs/{org}/actions/hosted-runners/images/partner
```

Get the list of partner images available for GitHub-hosted runners for an organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/images/partner
```

**Response schema (Status: 200):**

Same response schema as [Get GitHub-owned images for GitHub-hosted runners in an organization](#get-github-owned-images-for-github-hosted-runners-in-an-organization).





## Get limits on GitHub-hosted runners for an organization

```
GET /orgs/{org}/actions/hosted-runners/limits
```

Get the GitHub-hosted runners limits for an organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/limits
```

**Response schema (Status: 200):**

* `public_ips`: required, `Static public IP Limits for GitHub-hosted Hosted Runners.`:
  * `maximum`: required, integer
  * `current_usage`: required, integer





## Get GitHub-hosted runners machine specs for an organization

```
GET /orgs/{org}/actions/hosted-runners/machine-sizes
```

Get the list of machine specs available for GitHub-hosted runners for an organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/machine-sizes
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `machine_specs`: required, array of `Github-owned VM details.`:
  * `id`: required, string
  * `cpu_cores`: required, integer
  * `memory_gb`: required, integer
  * `storage_gb`: required, integer





## Get platforms for GitHub-hosted runners in an organization

```
GET /orgs/{org}/actions/hosted-runners/platforms
```

Get the list of platforms available for GitHub-hosted runners for an organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/platforms
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `platforms`: required, array of string





## Get a GitHub-hosted runner for an organization

```
GET /orgs/{org}/actions/hosted-runners/{hosted_runner_id}
```

Gets a GitHub-hosted runner configured in an organization.
OAuth app tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`hosted_runner_id`** (integer) (required)
  Unique identifier of the GitHub-hosted runner.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/hosted-runners/HOSTED_RUNNER_ID
```

**Response schema (Status: 200):**

Same response schema as [Create a GitHub-hosted runner for an organization](#create-a-github-hosted-runner-for-an-organization).





## Update a GitHub-hosted runner for an organization

```
PATCH /orgs/{org}/actions/hosted-runners/{hosted_runner_id}
```

Updates a GitHub-hosted runner for an organization.
OAuth app tokens and personal access tokens (classic) need the manage_runners:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`hosted_runner_id`** (integer) (required)
  Unique identifier of the GitHub-hosted runner.




#### Body parameters

- **`name`** (string)
  Name of the runner. Must be between 1 and 64 characters and may only contain upper and lowercase letters a-z, numbers 0-9, '.', '-', and '_'.

- **`runner_group_id`** (integer)
  The existing runner group to add this runner to.

- **`maximum_runners`** (integer)
  The maximum amount of runners to scale up to. Runners will not auto-scale above this number. Use this setting to limit your cost.

- **`enable_static_ip`** (boolean)
  Whether this runner should be updated with a static public IP. Note limit on account. To list limits on account, use GET actions/hosted-runners/limits

- **`size`** (string)
  The machine size of the runner. To list available sizes, use GET actions/hosted-runners/machine-sizes

- **`image_id`** (string)
  The unique identifier of the runner image. To list available images, use GET /actions/hosted-runners/images/github-owned, GET /actions/hosted-runners/images/partner, or GET /actions/hosted-runners/images/custom.

- **`image_version`** (string or null)
  The version of the runner image to deploy. This is relevant only for runners using custom images.





### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/actions/hosted-runners/HOSTED_RUNNER_ID \
  -d '{
  "name": "My larger runner",
  "runner_group_id": 1,
  "maximum_runners": 50,
  "enable_static_ip": false
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a GitHub-hosted runner for an organization](#create-a-github-hosted-runner-for-an-organization).





## Delete a GitHub-hosted runner for an organization

```
DELETE /orgs/{org}/actions/hosted-runners/{hosted_runner_id}
```

Deletes a GitHub-hosted runner for an organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`hosted_runner_id`** (integer) (required)
  Unique identifier of the GitHub-hosted runner.






### HTTP response status codes


- **202** - Accepted




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/hosted-runners/HOSTED_RUNNER_ID
```

**Response schema (Status: 202):**

Same response schema as [Create a GitHub-hosted runner for an organization](#create-a-github-hosted-runner-for-an-organization).