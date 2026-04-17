# REST API endpoints for API Insights

Use the REST API to view statistics for API usage in an organization.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get route stats by actor

```
GET /orgs/{org}/insights/api/route-stats/{actor_type}/{actor_id}
```

Get API request count statistics for an actor broken down by route within a specified time frame.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`actor_type`** (string) (required)
  The type of the actor
  Can be one of: `installation`, `classic_pat`, `fine_grained_pat`, `oauth_app`, `github_app_user_to_server`

- **`actor_id`** (integer) (required)
  The ID of the actor

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`sort`** (array)
  The property to sort the results by.

- **`api_route_substring`** (string)
  Providing a substring will filter results where the API route contains the substring. This is a case-insensitive search.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/route-stats/ACTOR_TYPE/ACTOR_ID
```

**Response schema (Status: 200):**

Array of objects:
  * `http_method`: string
  * `api_route`: string
  * `total_request_count`: integer, format: int64
  * `rate_limited_request_count`: integer, format: int64
  * `last_rate_limited_timestamp`: string or null
  * `last_request_timestamp`: string





## Get subject stats

```
GET /orgs/{org}/insights/api/subject-stats
```

Get API request statistics for all subjects within an organization within a specified time frame. Subjects can be users or GitHub Apps.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`sort`** (array)
  The property to sort the results by.

- **`subject_name_substring`** (string)
  Providing a substring will filter results where the subject name contains the substring. This is a case-insensitive search.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/subject-stats
```

**Response schema (Status: 200):**

Array of objects:
  * `subject_type`: string
  * `subject_name`: string
  * `subject_id`: integer, format: int64
  * `total_request_count`: integer
  * `rate_limited_request_count`: integer
  * `last_rate_limited_timestamp`: string or null
  * `last_request_timestamp`: string





## Get summary stats

```
GET /orgs/{org}/insights/api/summary-stats
```

Get overall statistics of API requests made within an organization by all users and apps within a specified time frame.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/summary-stats
```

**Response schema (Status: 200):**

* `total_request_count`: integer, format: int64
* `rate_limited_request_count`: integer, format: int64





## Get summary stats by user

```
GET /orgs/{org}/insights/api/summary-stats/users/{user_id}
```

Get overall statistics of API requests within the organization for a user.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`user_id`** (string) (required)
  The ID of the user to query for stats

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/summary-stats/users/USER_ID
```

**Response schema (Status: 200):**

Same response schema as [Get summary stats](#get-summary-stats).





## Get summary stats by actor

```
GET /orgs/{org}/insights/api/summary-stats/{actor_type}/{actor_id}
```

Get overall statistics of API requests within the organization made by a specific actor. Actors can be GitHub App installations, OAuth apps or other tokens on behalf of a user.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`actor_type`** (string) (required)
  The type of the actor
  Can be one of: `installation`, `classic_pat`, `fine_grained_pat`, `oauth_app`, `github_app_user_to_server`

- **`actor_id`** (integer) (required)
  The ID of the actor






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/summary-stats/ACTOR_TYPE/ACTOR_ID
```

**Response schema (Status: 200):**

Same response schema as [Get summary stats](#get-summary-stats).





## Get time stats

```
GET /orgs/{org}/insights/api/time-stats
```

Get the number of API requests and rate-limited requests made within an organization over a specified time period.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`timestamp_increment`** (string) (required)
  The increment of time used to breakdown the query results (5m, 10m, 1h, etc.)






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/time-stats
```

**Response schema (Status: 200):**

Array of objects:
  * `timestamp`: string
  * `total_request_count`: integer, format: int64
  * `rate_limited_request_count`: integer, format: int64





## Get time stats by user

```
GET /orgs/{org}/insights/api/time-stats/users/{user_id}
```

Get the number of API requests and rate-limited requests made within an organization by a specific user over a specified time period.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`user_id`** (string) (required)
  The ID of the user to query for stats

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`timestamp_increment`** (string) (required)
  The increment of time used to breakdown the query results (5m, 10m, 1h, etc.)






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/time-stats/users/USER_ID
```

**Response schema (Status: 200):**

Same response schema as [Get time stats](#get-time-stats).





## Get time stats by actor

```
GET /orgs/{org}/insights/api/time-stats/{actor_type}/{actor_id}
```

Get the number of API requests and rate-limited requests made within an organization by a specific actor within a specified time period.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`actor_type`** (string) (required)
  The type of the actor
  Can be one of: `installation`, `classic_pat`, `fine_grained_pat`, `oauth_app`, `github_app_user_to_server`

- **`actor_id`** (integer) (required)
  The ID of the actor

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`timestamp_increment`** (string) (required)
  The increment of time used to breakdown the query results (5m, 10m, 1h, etc.)






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/time-stats/ACTOR_TYPE/ACTOR_ID
```

**Response schema (Status: 200):**

Same response schema as [Get time stats](#get-time-stats).





## Get user stats

```
GET /orgs/{org}/insights/api/user-stats/{user_id}
```

Get API usage statistics within an organization for a user broken down by the type of access.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`user_id`** (string) (required)
  The ID of the user to query for stats

- **`min_timestamp`** (string) (required)
  The minimum timestamp to query for stats. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`max_timestamp`** (string)
  The maximum timestamp to query for stats. Defaults to the time 30 days ago. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`sort`** (array)
  The property to sort the results by.

- **`actor_name_substring`** (string)
  Providing a substring will filter results where the actor name contains the substring. This is a case-insensitive search.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/insights/api/user-stats/USER_ID
```

**Response schema (Status: 200):**

Array of objects:
  * `actor_type`: string
  * `actor_name`: string
  * `actor_id`: integer, format: int64
  * `integration_id`: integer or null, format: int64
  * `oauth_application_id`: integer or null, format: int64
  * `total_request_count`: integer
  * `rate_limited_request_count`: integer
  * `last_rate_limited_timestamp`: string or null
  * `last_request_timestamp`: string