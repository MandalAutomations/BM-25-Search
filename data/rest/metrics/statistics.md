# REST API endpoints for repository statistics

Use the REST API to fetch the data that GitHub uses for visualizing different types of repository activity.

## About repository statistics

You can use the REST API to fetch the data that GitHub uses for visualizing different types of repository activity.

### Best practices for caching

Computing repository statistics is an expensive operation, so we try to return cached
data whenever possible. If the data hasn't been cached when you query a repository's
statistics, you'll receive a `202` response; a background job is also fired to
start compiling these statistics. You should allow the job a short time to complete, and
then submit the request again. If the job has completed, that request will receive a
`200` response with the statistics in the response body.

Repository statistics are cached by the SHA of the repository's default branch; pushing to the default branch resets the statistics cache.

### Statistics exclude some types of commits

The statistics exposed by the API match the statistics shown by [different repository graphs](/en/repositories/viewing-activity-and-data-for-your-repository/about-repository-graphs).

To summarize this:

* All statistics exclude merge commits.
* Contributor statistics also exclude empty commits.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get the weekly commit activity

```
GET /repos/{owner}/{repo}/stats/code_frequency
```

Returns a weekly aggregate of the number of additions and deletions pushed to a repository.
Note

This endpoint can only be used for repositories with fewer than 10,000 commits. If the repository contains 10,000 or more commits, a 422 status code will be returned.

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

* **200** - Returns a weekly aggregate of the number of additions and deletions pushed to a repository.

* **202** - Accepted

* **204** - A header with no content is returned.

* **422** - Repository contains more than 10,000 commits

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/stats/code_frequency
```

**Response schema (Status: 200):**

Array of array

## Get the last year of commit activity

```
GET /repos/{owner}/{repo}/stats/commit_activity
```

Returns the last year of commit activity grouped by week. The days array is a group of commits per day, starting on Sunday.

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

* **202** - Accepted

* **204** - A header with no content is returned.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/stats/commit_activity
```

**Response schema (Status: 200):**

Array of `Commit Activity`:

* `days`: required, array of integer
* `total`: required, integer
* `week`: required, integer

## Get all contributor commit activity

```
GET /repos/{owner}/{repo}/stats/contributors
```

Returns the total number of commits authored by the contributor. In addition, the response includes a Weekly Hash (weeks array) with the following information:

w - Start of the week, given as a Unix timestamp.
a - Number of additions
d - Number of deletions
c - Number of commits

Note

This endpoint will return 0 values for all addition and deletion counts in repositories with 10,000 or more commits.

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

* **202** - Accepted

* **204** - A header with no content is returned.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/stats/contributors
```

**Response schema (Status: 200):**

Array of `Contributor Activity`:

* `author`: required, any of:
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
* `total`: required, integer
* `weeks`: required, array of objects:
  * `w`: integer
  * `a`: integer
  * `d`: integer
  * `c`: integer

## Get the weekly commit count

```
GET /repos/{owner}/{repo}/stats/participation
```

Returns the total commit counts for the owner and total commit counts in all. all is everyone combined, including the owner in the last 52 weeks. If you'd like to get the commit counts for non-owners, you can subtract owner from all.
The array order is oldest week (index 0) to most recent week.
The most recent week is seven days ago at UTC midnight to today at UTC midnight.

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

* **200** - The array order is oldest week (index 0) to most recent week.

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/stats/participation
```

**Response schema (Status: 200):**

* `all`: required, array of integer
* `owner`: required, array of integer

## Get the hourly commit count for each day

```
GET /repos/{owner}/{repo}/stats/punch_card
```

Each array contains the day number, hour number, and number of commits:

0-6: Sunday - Saturday
0-23: Hour of day
Number of commits

For example, \[2, 14, 25] indicates that there were 25 total commits, during the 2:00pm hour on Tuesdays. All times are based on the time zone of individual commits.

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

* **200** - For example, \[2, 14, 25] indicates that there were 25 total commits, during the 2:00pm hour on Tuesdays. All times are based on the time zone of individual commits.

* **204** - A header with no content is returned.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/stats/punch_card
```

**Response schema (Status: 200):**

Same response schema as [Get the weekly commit activity](#get-the-weekly-commit-activity).