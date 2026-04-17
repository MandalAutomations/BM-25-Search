# Alert dismissal requests

Use the REST API to manage alert dismissal requests for secret scanning.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List alert dismissal requests for secret scanning for an enterprise

```
GET /enterprises/{enterprise}/dismissal-requests/secret-scanning
```

Lists requests to dismiss secret scanning alerts in an enterprise.
The authenticated user must be an enterprise owner or an enterprise security manager to access this endpoint.
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
  The status of the dismissal request to filter on. When specified, only requests with this status will be returned.
  Default: `all`
  Can be one of: `completed`, `cancelled`, `approved`, `expired`, `denied`, `open`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of the alert dismissal requests.


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/dismissal-requests/secret-scanning
```

**Response schema (Status: 200):**

Array of `Secret scanning alert dismissal request`:
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
    * `alert_number`: string
    * `reason`: string, enum: `fixed_later`, `false_positive`, `tests`, `revoked`
  * `resource_identifier`: string
  * `status`: string, enum: `pending`, `denied`, `approved`, `cancelled`, `expired`
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





## List alert dismissal requests for secret scanning for an org

```
GET /orgs/{org}/dismissal-requests/secret-scanning
```

Lists requests to dismiss secret scanning alerts in an org.
Delegated alert dismissal must be enabled on repositories in the org and the user must be an org admin, security manager,
or have the "Review and manage secret scanning alert dismissal requests" permission to access this endpoint.


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
  The status of the dismissal request to filter on. When specified, only requests with this status will be returned.
  Default: `all`
  Can be one of: `completed`, `cancelled`, `approved`, `expired`, `denied`, `open`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of the alert dismissal requests.


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/dismissal-requests/secret-scanning
```

**Response schema (Status: 200):**

Same response schema as [List alert dismissal requests for secret scanning for an enterprise](#list-alert-dismissal-requests-for-secret-scanning-for-an-enterprise).





## List alert dismissal requests for secret scanning for a repository

```
GET /repos/{owner}/{repo}/dismissal-requests/secret-scanning
```

Lists requests to dismiss secret scanning alerts in a repository.
Delegated alert dismissal must be enabled on the repository and the user must be an org admin, security manager,
or have the "Review and manage secret scanning alert dismissal requests" permission to access this endpoint.


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
  The status of the dismissal request to filter on. When specified, only requests with this status will be returned.
  Default: `all`
  Can be one of: `completed`, `cancelled`, `approved`, `expired`, `denied`, `open`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - A list of the alert dismissal requests.


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dismissal-requests/secret-scanning
```

**Response schema (Status: 200):**

Same response schema as [List alert dismissal requests for secret scanning for an enterprise](#list-alert-dismissal-requests-for-secret-scanning-for-an-enterprise).





## Get an alert dismissal request for secret scanning

```
GET /repos/{owner}/{repo}/dismissal-requests/secret-scanning/{alert_number}
```

Gets a specific request to dismiss a secret scanning alert in a repository.
Delegated alert dismissal must be enabled on the repository and the user must be an org admin, security manager,
or have the "Review and manage secret scanning alert dismissal requests" permission to access this endpoint.
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
  The number that identifies the secret scanning alert in a repository.






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
  https://api.github.com/repos/OWNER/REPO/dismissal-requests/secret-scanning/ALERT_NUMBER
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
  * `alert_number`: string
  * `reason`: string, enum: `fixed_later`, `false_positive`, `tests`, `revoked`
* `resource_identifier`: string
* `status`: string, enum: `pending`, `denied`, `approved`, `cancelled`, `expired`
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





## Review an alert dismissal request for secret scanning

```
PATCH /repos/{owner}/{repo}/dismissal-requests/secret-scanning/{alert_number}
```

Approve or deny a request to dismiss a secret scanning alert in a repository.
Delegated alert dismissal must be enabled on the repository and the user must be an org admin, security manager,
or have the "Review and manage secret scanning alert dismissal requests" permission to access this endpoint.
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
  The number that identifies the secret scanning alert in a repository.




#### Body parameters

- **`status`** (string) (required)
  The review action to perform on the dismissal request.
  Can be one of: `approve`, `deny`

- **`message`** (string) (required)
  A message to include with the review. Has a maximum character length of 2048.





### HTTP response status codes


- **200** - The review of the dismissal request.


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
  https://api.github.com/repos/OWNER/REPO/dismissal-requests/secret-scanning/ALERT_NUMBER \
  -d '{
  "status": "deny",
  "message": "This secret has not been revoked."
}'
```

**Response schema (Status: 200):**

* `dismissal_review_id`: integer