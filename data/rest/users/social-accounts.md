# REST API endpoints for social accounts

Use the REST API to manage social accounts of authenticated users.

## About social account administration

If a request URL does not include a `{username}` parameter then the response will be for the signed-in user (and you must pass [authentication information](/en/rest/overview/authenticating-to-the-rest-api) with your request). Additional private information, such as whether a user has two-factor authentication enabled, is included when authenticated through OAuth with the `user` scope.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List social accounts for the authenticated user

```
GET /user/social_accounts
```

Lists all of your social accounts.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/social_accounts
```

**Response schema (Status: 200):**

Array of `Social account`:

* `provider`: required, string
* `url`: required, string

## Add social accounts for the authenticated user

```
POST /user/social_accounts
```

Add one or more social accounts to the authenticated user's profile.
OAuth app tokens and personal access tokens (classic) need the user scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`account_urls`** (array of strings) (required)
  Full URLs for the social media profiles to add.

### HTTP response status codes

* **201** - Created

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Adding multiple social accounts

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/social_accounts \
  -d '{
  "account_urls": [
    "https://facebook.com/GitHub",
    "https://www.youtube.com/@GitHub"
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [List social accounts for the authenticated user](#list-social-accounts-for-the-authenticated-user).

## Delete social accounts for the authenticated user

```
DELETE /user/social_accounts
```

Deletes one or more social accounts from the authenticated user's profile.
OAuth app tokens and personal access tokens (classic) need the user scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`account_urls`** (array of strings) (required)
  Full URLs for the social media profiles to delete.

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Deleting multiple social accounts

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/social_accounts \
  -d '{
  "account_urls": [
    "https://facebook.com/GitHub",
    "https://www.youtube.com/@GitHub"
  ]
}'
```

**Response schema (Status: 204):**

## List social accounts for a user

```
GET /users/{username}/social_accounts
```

Lists social media accounts for a user. This endpoint is accessible by anyone.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`username`** (string) (required)
  The handle for the GitHub user account.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/social_accounts
```

**Response schema (Status: 200):**

Same response schema as [List social accounts for the authenticated user](#list-social-accounts-for-the-authenticated-user).