# REST API endpoints for repository push rule bypass requests

Use the REST API to manage repository push rule bypass requests.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List repository push rule bypass requests

```
GET /repos/{owner}/{repo}/bypass-requests/push-rules
```

Lists the requests made by users of a repository to bypass push protection rules


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


- **200** - OK


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/bypass-requests/push-rules
```

**Response schema (Status: 200):**

Array of `Push rule bypass request`:
  * `id`: integer
  * `number`: integer
  * `repository`: object:
    * `id`: integer or null
    * `name`: string or null
    * `full_name`: string or null
  * `organization`: object:
    * `id`: integer or null
    * `name`: string or null
  * `requester`: object:
    * `actor_id`: integer
    * `actor_name`: string
  * `request_type`: string
  * `data`: array of objects or null:
    * `ruleset_id`: integer
    * `ruleset_name`: string
    * `total_violations`: integer
    * `rule_type`: string
  * `resource_identifier`: string
  * `status`: string, enum: `pending`, `denied`, `approved`, `cancelled`, `completed`, `expired`, `deleted`, `open`
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





## Get a repository push bypass request

```
GET /repos/{owner}/{repo}/bypass-requests/push-rules/{bypass_request_number}
```

Get information about a request to bypass push protection rules for a repository.


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
  The number that identifies the bypass request within the context of the given repository.






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
  https://api.github.com/repos/OWNER/REPO/bypass-requests/push-rules/BYPASS_REQUEST_NUMBER
```

**Response schema (Status: 200):**

* `id`: integer
* `number`: integer
* `repository`: object:
  * `id`: integer or null
  * `name`: string or null
  * `full_name`: string or null
* `organization`: object:
  * `id`: integer or null
  * `name`: string or null
* `requester`: object:
  * `actor_id`: integer
  * `actor_name`: string
* `request_type`: string
* `data`: array of objects or null:
  * `ruleset_id`: integer
  * `ruleset_name`: string
  * `total_violations`: integer
  * `rule_type`: string
* `resource_identifier`: string
* `status`: string, enum: `pending`, `denied`, `approved`, `cancelled`, `completed`, `expired`, `deleted`, `open`
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