# REST API endpoints for repository traffic

Use the REST API to retrieve information provided in your repository graph.

## About repository traffic

You can use these endpoints to retrieve information provided in your repository graph, for repositories that you have write access to. For more information, see [Viewing traffic to a repository](/en/repositories/viewing-activity-and-data-for-your-repository/viewing-traffic-to-a-repository).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get repository clones

```
GET /repos/{owner}/{repo}/traffic/clones
```

Get the total number of clones and breakdown per day or week for the last 14 days. Timestamps are aligned to UTC midnight of the beginning of the day or week. Week begins on Monday.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`per`** (string)
  The time frame to display results for.
  Default: `day`
  Can be one of: `day`, `week`

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/traffic/clones
```

**Response schema (Status: 200):**

* `count`: required, integer
* `uniques`: required, integer
* `clones`: required, array of `Traffic`:
  * `timestamp`: required, string, format: date-time
  * `uniques`: required, integer
  * `count`: required, integer

## Get top referral paths

```
GET /repos/{owner}/{repo}/traffic/popular/paths
```

Get the top 10 popular contents over the last 14 days.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/traffic/popular/paths
```

**Response schema (Status: 200):**

Array of `Content Traffic`:

* `path`: required, string
* `title`: required, string
* `count`: required, integer
* `uniques`: required, integer

## Get top referral sources

```
GET /repos/{owner}/{repo}/traffic/popular/referrers
```

Get the top 10 referrers over the last 14 days.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/traffic/popular/referrers
```

**Response schema (Status: 200):**

Array of `Referrer Traffic`:

* `referrer`: required, string
* `count`: required, integer
* `uniques`: required, integer

## Get page views

```
GET /repos/{owner}/{repo}/traffic/views
```

Get the total number of views and breakdown per day or week for the last 14 days. Timestamps are aligned to UTC midnight of the beginning of the day or week. Week begins on Monday.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`per`** (string)
  The time frame to display results for.
  Default: `day`
  Can be one of: `day`, `week`

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/traffic/views
```

**Response schema (Status: 200):**

* `count`: required, integer
* `uniques`: required, integer
* `views`: required, array of `Traffic`:
  * `timestamp`: required, string, format: date-time
  * `uniques`: required, integer
  * `count`: required, integer