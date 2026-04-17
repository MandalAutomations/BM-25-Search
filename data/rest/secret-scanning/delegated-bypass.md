# REST API endpoints for push protection bypass requests

Use the REST API to manage push protection bypass requests for secret scanning.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List bypass requests for secret scanning for an enterprise

```
GET /enterprises/{enterprise}/bypass-requests/secret-scanning
```

List requests to bypass secret scanning push protection in an enterprise.
Delegated bypass must be enabled on repositories in the enterprise and the user must be a bypass reviewer to access this endpoint.
Personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`organization_name`** (string)
  The name of the organization to filter on.

- **`reviewer`** (string)
  Filter bypass requests by the handle of the GitHub user who reviewed the bypass request.

- **`requester`** (string)
  Filter bypass requests by the handle of the GitHub user who requested the bypass.

- **`time_period`** (string)
  The time period to filter by.
For example, day will filter for rule suites that occurred in the past 24 hours, and week will filter for rule suites that occurred in the past 7 days (168 hours).
  Default: `day`
  Can be one of: `hour`, `day`, `week`, `month`

- **`request_status`** (string)
  The status of the bypass request to filter on. When specified, only requests with this status will be returned.
  Default: `all`
  Can be one of: `completed`, `cancelled`, `approved`, `expired`, `deleted`, `denied`, `open`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/bypass-requests/secret-scanning
```

**Response schema (Status: 200):**

Array of `Secret scanning bypass request`:
  * `id`: integer
  * `number`: integer
  * `repository`: object:
    * `id`: integer
    * `name`: string
    * `full_name`: string
  * `organization`: object:
    * `id`: integer
    * `name`: string
  * `requester`: object:
    * `actor_id`: integer
    * `actor_name`: string
  * `request_type`: string
  * `data`: array of objects or null:
    * `secret_type`: string
    * `bypass_reason`: string, enum: `used_in_tests`, `false_positive`, `fix_later`
    * `path`: string
    * `branch`: string
  * `resource_identifier`: string
  * `status`: string, enum: `pending`, `denied`, `approved`, `cancelled`, `completed`, `expired`, `open`
  * `requester_comment`: string or null
  * `expires_at`: string, format: date-time
  * `created_at`: string, format: date-time
  * `responses`: array of `Bypass response` or null:
    * `id`: integer
    * `reviewer`: object:
      * `actor_id`: integer
      * `actor_name`: string
    * `status`: string, enum: `approved`, `denied`, `dismissed`
    * `created_at`: string, format: date-time
  * `url`: string, format: uri
  * `html_url`: string, format: uri





## List bypass requests for secret scanning for an org

```
GET /orgs/{org}/bypass-requests/secret-scanning
```

List requests to bypass secret scanning push protection in an org.
Delegated bypass must be enabled on repositories in the org and the user must be a bypass reviewer to access this endpoint.
Personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`repository_name`** (string)
  The name of the repository to filter on.

- **`reviewer`** (string)
  Filter bypass requests by the handle of the GitHub user who reviewed the bypass request.

- **`requester`** (string)
  Filter bypass requests by the handle of the GitHub user who requested the bypass.

- **`time_period`** (string)
  The time period to filter by.
For example, day will filter for rule suites that occurred in the past 24 hours, and week will filter for rule suites that occurred in the past 7 days (168 hours).
  Default: `day`
  Can be one of: `hour`, `day`, `week`, `month`

- **`request_status`** (string)
  The status of the bypass request to filter on. When specified, only requests with this status will be returned.
  Default: `all`
  Can be one of: `completed`, `cancelled`, `approved`, `expired`, `deleted`, `denied`, `open`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/bypass-requests/secret-scanning
```

**Response schema (Status: 200):**

Same response schema as [List bypass requests for secret scanning for an enterprise](#list-bypass-requests-for-secret-scanning-for-an-enterprise).





## List bypass requests for secret scanning for a repository

```
GET /repos/{owner}/{repo}/bypass-requests/secret-scanning
```

Lists requests to bypass secret scanning push protection in a repository.
Delegated bypass must be enabled on the repository and the user must be a bypass reviewer to access this endpoint.
Personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`reviewer`** (string)
  Filter bypass requests by the handle of the GitHub user who reviewed the bypass request.

- **`requester`** (string)
  Filter bypass requests by the handle of the GitHub user who requested the bypass.

- **`time_period`** (string)
  The time period to filter by.
For example, day will filter for rule suites that occurred in the past 24 hours, and week will filter for rule suites that occurred in the past 7 days (168 hours).
  Default: `day`
  Can be one of: `hour`, `day`, `week`, `month`

- **`request_status`** (string)
  The status of the bypass request to filter on. When specified, only requests with this status will be returned.
  Default: `all`
  Can be one of: `completed`, `cancelled`, `approved`, `expired`, `deleted`, `denied`, `open`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of the bypass requests.


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/bypass-requests/secret-scanning
```

**Response schema (Status: 200):**

Same response schema as [List bypass requests for secret scanning for an enterprise](#list-bypass-requests-for-secret-scanning-for-an-enterprise).





## Get a bypass request for secret scanning

```
GET /repos/{owner}/{repo}/bypass-requests/secret-scanning/{bypass_request_number}
```

Gets a specific request to bypass secret scanning push protection in a repository.
Delegated bypass must be enabled on the repository and the user must be a bypass reviewer to access this endpoint.
Personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`bypass_request_number`** (integer) (required)
  The number that identifies the bypass request in a repository.






### HTTP response status codes


- **200** - A single bypass request.


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/bypass-requests/secret-scanning/BYPASS_REQUEST_NUMBER
```

**Response schema (Status: 200):**

* `id`: integer
* `number`: integer
* `repository`: object:
  * `id`: integer
  * `name`: string
  * `full_name`: string
* `organization`: object:
  * `id`: integer
  * `name`: string
* `requester`: object:
  * `actor_id`: integer
  * `actor_name`: string
* `request_type`: string
* `data`: array of objects or null:
  * `secret_type`: string
  * `bypass_reason`: string, enum: `used_in_tests`, `false_positive`, `fix_later`
  * `path`: string
  * `branch`: string
* `resource_identifier`: string
* `status`: string, enum: `pending`, `denied`, `approved`, `cancelled`, `completed`, `expired`, `open`
* `requester_comment`: string or null
* `expires_at`: string, format: date-time
* `created_at`: string, format: date-time
* `responses`: array of `Bypass response` or null:
  * `id`: integer
  * `reviewer`: object:
    * `actor_id`: integer
    * `actor_name`: string
  * `status`: string, enum: `approved`, `denied`, `dismissed`
  * `created_at`: string, format: date-time
* `url`: string, format: uri
* `html_url`: string, format: uri





## Review a bypass request for secret scanning

```
PATCH /repos/{owner}/{repo}/bypass-requests/secret-scanning/{bypass_request_number}
```

Approve or deny a request to bypass secret scanning push protection in a repository.
Delegated bypass must be enabled on the repository and the user must be a bypass reviewer to access this endpoint.
Personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`bypass_request_number`** (integer) (required)
  The number that identifies the bypass request in a repository.




#### Body parameters

- **`status`** (string) (required)
  The review action to perform on the bypass request.
  Can be one of: `approve`, `reject`

- **`message`** (string) (required)
  A message to include with the review. Has a maximum character length of 2048.





### HTTP response status codes


- **200** - The review of the bypass request.


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/bypass-requests/secret-scanning/BYPASS_REQUEST_NUMBER \
  -d '{
  "status": "reject",
  "message": "This secret has not been revoked."
}'
```

**Response schema (Status: 200):**

* `bypass_review_id`: integer





## Dismiss a response on a bypass request for secret scanning

```
DELETE /repos/{owner}/{repo}/bypass-responses/secret-scanning/{bypass_response_id}
```

Dissmiss a response given to a bypass request for secret scanning push protection in a repository.
Delegated bypass must be enabled on the repository and the user must be a bypass reviewer to access this endpoint.
Personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`bypass_response_id`** (integer) (required)
  ID of the bypass response.






### HTTP response status codes


- **204** - Review was successfully dismissed.


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/bypass-responses/secret-scanning/BYPASS_RESPONSE_ID
```

**Response schema (Status: 204):**