# REST API endpoints for stacked pull requests

Use the REST API to interact with stacked pull requests.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List pull request stacks

```
GET /repos/{owner}/{repo}/stacks
```

Lists pull request stacks in a repository.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`pull_request`** (integer)
  Filter to the stack containing this repository pull request number.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/stacks
```

**Response schema (Status: 200):**

Array of `Pull Request Stack Minimal`:
  * `id`: required, integer
  * `number`: required, integer
  * `node_id`: required, string
  * `url`: required, string, format: uri
  * `base`: required, object:
    * `ref`: required, string
  * `open`: required, boolean
  * `created_at`: required, string, format: date-time
  * `pull_requests`: required, array of objects:
    * `number`: required, integer
    * `state`: required, string, enum: `open`, `closed`
    * `draft`: required, boolean
    * `merged_at`: required, string or null, format: date-time
    * `head`: required, object:
      * `ref`: required, string
      * `sha`: required, string

## Create a pull request stack

```
POST /repos/{owner}/{repo}/stacks
```

Creates a stack from an ordered list of pull request numbers. Provide the pull
request numbers from the bottom of the stack to the top. Each pull request's
base ref must match the previous pull request's head ref.

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

- **`pull_requests`** (array of integers) (required)
  An ordered list of pull request numbers forming the stack from bottom to top.

### HTTP response status codes

- **201** - Created

- **404** - Resource not found

- **422** - Validation failed. Returned when the request references pull requests that
don't exist in the repository, or when the pull requests can't form a
valid stack.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/stacks \
  -d '{
  "pull_requests": [
    101,
    102,
    103
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `number`: required, integer
* `node_id`: required, string
* `url`: required, string, format: uri
* `base`: required, object:
  * `ref`: required, string
* `open`: required, boolean
* `created_at`: required, string, format: date-time
* `pull_requests`: required, array of object

## Get a pull request stack

```
GET /repos/{owner}/{repo}/stacks/{stack_number}
```

Gets a pull request stack by providing its stack number.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`stack_number`** (integer) (required)
  The number that identifies the pull request stack.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/stacks/STACK_NUMBER
```

**Response schema (Status: 200):**

Same response schema as [Create a pull request stack](#create-a-pull-request-stack).

## Add pull requests to a pull request stack

```
POST /repos/{owner}/{repo}/stacks/{stack_number}/add
```

Appends an ordered list of pull request numbers onto the top of an existing
stack. Provide only the pull requests you want to add, from the current top of
the stack upward. The first new pull request's base ref must match the current
top pull request's head ref.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`stack_number`** (integer) (required)
  The number that identifies the pull request stack.

#### Body parameters

- **`pull_requests`** (array of integers) (required)
  An ordered list of pull request numbers to append to the stack, from the current top upward.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **409** - Conflict. Returned when the stack is being modified by another request.

- **422** - Validation failed. Returned when the request references pull requests that
don't exist in the repository, or when the pull requests can't be appended
to the stack.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/stacks/STACK_NUMBER/add \
  -d '{
  "pull_requests": [
    104,
    102
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create a pull request stack](#create-a-pull-request-stack).

## Remove pull requests from a pull request stack

```
POST /repos/{owner}/{repo}/stacks/{stack_number}/unstack
```

Removes the unmerged pull requests from a stack. Pull requests that cannot be
unstacked (for example, those that are queued for merge) are left in place. When pull requests remain in the stack, the updated
stack is returned with a 200. When no pull requests remain, the stack is
dissolved and a 204 is returned.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`stack_number`** (integer) (required)
  The number that identifies the pull request stack.

### HTTP response status codes

- **200** - OK

- **204** - A header with no content is returned.

- **404** - Resource not found

- **409** - Conflict. Returned when the stack is being modified by another request.

- **422** - Validation failed. Returned when the stack can't be unstacked because every
pull request in it is locked and cannot be removed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/stacks/STACK_NUMBER/unstack
```

**Response schema (Status: 200):**

Same response schema as [Create a pull request stack](#create-a-pull-request-stack).