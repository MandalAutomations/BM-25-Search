# REST API endpoints for emails

Use the REST API to manage email addresses of authenticated users.

## About email administration

If a request URL does not include a `{username}` parameter then the response will be for the signed-in user (and you must pass [authentication information](/en/rest/overview/authenticating-to-the-rest-api) with your request). Additional private information, such as whether a user has two-factor authentication enabled, is included when authenticated through OAuth with the `user` scope.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Set primary email visibility for the authenticated user

```
PATCH /user/email/visibility
```

Sets the visibility for your primary email addresses.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`visibility`** (string) (required)
  Denotes whether an email is publicly visible.
  Can be one of: `public`, `private`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example setting the primary email address to private

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/user/email/visibility \
  -d '{
  "visibility": "private"
}'
```

**Response schema (Status: 200):**

Array of `Email`:

* `email`: required, string, format: email
* `primary`: required, boolean
* `verified`: required, boolean
* `visibility`: required, string or null

## List email addresses for the authenticated user

```
GET /user/emails
```

Lists all of your email addresses, and specifies which one is visible
to the public.
OAuth app tokens and personal access tokens (classic) need the user:email scope to use this endpoint.

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
  https://api.github.com/user/emails
```

**Response schema (Status: 200):**

Same response schema as [Set primary email visibility for the authenticated user](#set-primary-email-visibility-for-the-authenticated-user).

## Add an email address for the authenticated user

```
POST /user/emails
```

OAuth app tokens and personal access tokens (classic) need the user scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`emails`** (array of strings) (required)
  Adds one or more email addresses to your GitHub account. Must contain at least one email address. Note: Alternatively, you can pass a single email address or an array of emails addresses directly, but we recommend that you pass an object using the emails key.

### HTTP response status codes

* **201** - Created

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example adding multiple email addresses

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/emails \
  -d '{
  "emails": [
    "octocat@github.com",
    "mona@github.com",
    "octocat@octocat.org"
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Set primary email visibility for the authenticated user](#set-primary-email-visibility-for-the-authenticated-user).

## Delete an email address for the authenticated user

```
DELETE /user/emails
```

OAuth app tokens and personal access tokens (classic) need the user scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`emails`** (array of strings) (required)
  Email addresses associated with the GitHub user account.

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **401** - Requires authentication

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example deleting multiple email accounts

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/emails \
  -d '{
  "emails": [
    "octocat@github.com",
    "mona@github.com"
  ]
}'
```

**Response schema (Status: 204):**

## List public email addresses for the authenticated user

```
GET /user/public_emails
```

Lists your publicly visible email address, which you can set with the
Set primary email visibility for the authenticated user
endpoint.
OAuth app tokens and personal access tokens (classic) need the user:email scope to use this endpoint.

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
  https://api.github.com/user/public_emails
```

**Response schema (Status: 200):**

Same response schema as [Set primary email visibility for the authenticated user](#set-primary-email-visibility-for-the-authenticated-user).