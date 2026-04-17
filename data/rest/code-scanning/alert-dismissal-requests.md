# REST API endpoints for {% data variables.product.prodname_code_scanning %} alert dismissal requests

Use the REST API to interact with code scanning alert dismissal requests from a repository.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List dismissal requests for code scanning alerts for an organization

```
GET /orgs/{org}/dismissal-requests/code-scanning
```

Lists dismissal requests for code scanning alerts for all repositories in an organization.
The user must be authorized to review dismissal requests for the organization.
Personal access tokens (classic) need the security_events scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`reviewer`** (string)
  Filter alert dismissal requests by the handle of the GitHub user who reviewed the dismissal request.

- **`requester`** (string)
  Filter alert dismissal requests by the handle of the GitHub user who requested the dismissal.

- **`time_period`** (string)
  The time period to filter by.
For example, day will filter for rule suites that occurred in the past 24 hours, and week will filter for insights that occurred in the past 7 days (168 hours).
  Default: `month`
  Can be one of: `hour`, `day`, `week`, `month`

- **`request_status`** (string)
  Filter alert dismissal requests by status. When specified, only requests with this status will be returned.
  Default: `all`
  Can be one of: `open`, `approved`, `expired`, `denied`, `all`

- **`repository_name`** (string)
  The name of the repository to filter on.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of alert dismissal requests.


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/dismissal-requests/code-scanning
```

**Response schema (Status: 200):**

Array of `Code scanning alert dismissal request`:
  * `id`: integer, format: int64
  * `number`: integer, format: int64
  * `repository`: object:
    * `id`: integer, format: int64
    * `name`: string
    * `full_name`: string
  * `organization`: object:
    * `id`: integer, format: int64
    * `name`: string
  * `requester`: object:
    * `actor_id`: integer, format: int64
    * `actor_name`: string
  * `request_type`: string
  * `data`: array of objects or null:
    * `reason`: string
    * `alert_number`: string
    * `pr_review_thread_id`: string
  * `resource_identifier`: string
  * `status`: string, enum: `pending`, `denied`, `approved`, `expired`
  * `requester_comment`: string or null
  * `expires_at`: string, format: date-time
  * `created_at`: string, format: date-time
  * `responses`: array of `Dismissal request response` or null:
    * `id`: integer, format: int64
    * `reviewer`: object:
      * `actor_id`: integer, format: int64
      * `actor_name`: string
    * `message`: string or null
    * `status`: string, enum: `approved`, `denied`, `dismissed`
    * `created_at`: string, format: date-time
  * `url`: string, format: uri
  * `html_url`: string, format: uri





## List dismissal requests for code scanning alerts for a repository

```
GET /repos/{owner}/{repo}/dismissal-requests/code-scanning
```

Lists dismissal requests for code scanning alerts for a repository.
Delegated alert dismissal must be enabled on the repository.
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
  Filter alert dismissal requests by the handle of the GitHub user who reviewed the dismissal request.

- **`requester`** (string)
  Filter alert dismissal requests by the handle of the GitHub user who requested the dismissal.

- **`time_period`** (string)
  The time period to filter by.
For example, day will filter for rule suites that occurred in the past 24 hours, and week will filter for insights that occurred in the past 7 days (168 hours).
  Default: `month`
  Can be one of: `hour`, `day`, `week`, `month`

- **`request_status`** (string)
  Filter alert dismissal requests by status. When specified, only requests with this status will be returned.
  Default: `all`
  Can be one of: `open`, `approved`, `expired`, `denied`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of alert dismissal requests.


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dismissal-requests/code-scanning
```

**Response schema (Status: 200):**

Same response schema as [List dismissal requests for code scanning alerts for an organization](#list-dismissal-requests-for-code-scanning-alerts-for-an-organization).





## Get a dismissal request for a code scanning alert for a repository

```
GET /repos/{owner}/{repo}/dismissal-requests/code-scanning/{alert_number}
```

Gets a dismissal request to dismiss a code scanning alert in a repository.
Delegated alert dismissal must be enabled on the repository.
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

- **`alert_number`** (integer) (required)
  The number that identifies the code scanning alert.






### HTTP response status codes


- **200** - A single dismissal request.


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dismissal-requests/code-scanning/ALERT_NUMBER
```

**Response schema (Status: 200):**

* `id`: integer, format: int64
* `number`: integer, format: int64
* `repository`: object:
  * `id`: integer, format: int64
  * `name`: string
  * `full_name`: string
* `organization`: object:
  * `id`: integer, format: int64
  * `name`: string
* `requester`: object:
  * `actor_id`: integer, format: int64
  * `actor_name`: string
* `request_type`: string
* `data`: array of objects or null:
  * `reason`: string
  * `alert_number`: string
  * `pr_review_thread_id`: string
* `resource_identifier`: string
* `status`: string, enum: `pending`, `denied`, `approved`, `expired`
* `requester_comment`: string or null
* `expires_at`: string, format: date-time
* `created_at`: string, format: date-time
* `responses`: array of `Dismissal request response` or null:
  * `id`: integer, format: int64
  * `reviewer`: object:
    * `actor_id`: integer, format: int64
    * `actor_name`: string
  * `message`: string or null
  * `status`: string, enum: `approved`, `denied`, `dismissed`
  * `created_at`: string, format: date-time
* `url`: string, format: uri
* `html_url`: string, format: uri





## Review a dismissal request for a code scanning alert for a repository

```
PATCH /repos/{owner}/{repo}/dismissal-requests/code-scanning/{alert_number}
```

Approve or deny a dismissal request to dismiss a code scanning alert in a repository.
Delegated alert dismissal must be enabled on the repository and the user must be a dismissal reviewer to access this endpoint.
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

- **`alert_number`** (integer) (required)
  The number that identifies the code scanning alert.




#### Body parameters

- **`status`** (string) (required)
  The review action to perform on the bypass request.
  Can be one of: `approve`, `deny`

- **`message`** (string) (required)
  A message to include with the review. Has a maximum character length of 2048.





### HTTP response status codes


- **204** - Successful update


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
  https://api.github.com/repos/OWNER/REPO/dismissal-requests/code-scanning/ALERT_NUMBER \
  -d '{
  "status": "approve",
  "message": "Used in tests."
}'
```

**Response schema (Status: 204):**