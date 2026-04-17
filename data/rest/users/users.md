# REST API endpoints for users

Use the REST API to get public and private information about authenticated users.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get the authenticated user

```
GET /user
```

OAuth app tokens and personal access tokens (classic) need the user scope in order for the response to include private profile information.



### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user
```

**Response schema (Status: 200):**

* one of:
  * **Private User**
    * `login`: required, string
    * `id`: required, integer, format: int64
    * `user_view_type`: string
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
    * `name`: required, string or null
    * `company`: required, string or null
    * `blog`: required, string or null
    * `location`: required, string or null
    * `email`: required, string or null, format: email
    * `notification_email`: string or null, format: email
    * `hireable`: required, boolean or null
    * `bio`: required, string or null
    * `twitter_username`: string or null
    * `public_repos`: required, integer
    * `public_gists`: required, integer
    * `followers`: required, integer
    * `following`: required, integer
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `private_gists`: required, integer
    * `total_private_repos`: required, integer
    * `owned_private_repos`: required, integer
    * `disk_usage`: required, integer
    * `collaborators`: required, integer
    * `two_factor_authentication`: required, boolean
    * `plan`: object:
      * `collaborators`: required, integer
      * `name`: required, string
      * `space`: required, integer
      * `private_repos`: required, integer
    * `business_plus`: boolean
    * `ldap_dn`: string
  * **Public User**
    * `login`: required, string
    * `id`: required, integer, format: int64
    * `user_view_type`: string
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
    * `name`: required, string or null
    * `company`: required, string or null
    * `blog`: required, string or null
    * `location`: required, string or null
    * `email`: required, string or null, format: email
    * `notification_email`: string or null, format: email
    * `hireable`: required, boolean or null
    * `bio`: required, string or null
    * `twitter_username`: string or null
    * `public_repos`: required, integer
    * `public_gists`: required, integer
    * `followers`: required, integer
    * `following`: required, integer
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `plan`: object:
      * `collaborators`: required, integer
      * `name`: required, string
      * `space`: required, integer
      * `private_repos`: required, integer
    * `private_gists`: integer
    * `total_private_repos`: integer
    * `owned_private_repos`: integer
    * `disk_usage`: integer
    * `collaborators`: integer



#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user
```

**Response schema (Status: 200):**

* one of:
  * **Private User**
    * `login`: required, string
    * `id`: required, integer, format: int64
    * `user_view_type`: string
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
    * `name`: required, string or null
    * `company`: required, string or null
    * `blog`: required, string or null
    * `location`: required, string or null
    * `email`: required, string or null, format: email
    * `notification_email`: string or null, format: email
    * `hireable`: required, boolean or null
    * `bio`: required, string or null
    * `twitter_username`: string or null
    * `public_repos`: required, integer
    * `public_gists`: required, integer
    * `followers`: required, integer
    * `following`: required, integer
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `private_gists`: required, integer
    * `total_private_repos`: required, integer
    * `owned_private_repos`: required, integer
    * `disk_usage`: required, integer
    * `collaborators`: required, integer
    * `two_factor_authentication`: required, boolean
    * `plan`: object:
      * `collaborators`: required, integer
      * `name`: required, string
      * `space`: required, integer
      * `private_repos`: required, integer
    * `business_plus`: boolean
    * `ldap_dn`: string
  * **Public User**
    * `login`: required, string
    * `id`: required, integer, format: int64
    * `user_view_type`: string
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
    * `name`: required, string or null
    * `company`: required, string or null
    * `blog`: required, string or null
    * `location`: required, string or null
    * `email`: required, string or null, format: email
    * `notification_email`: string or null, format: email
    * `hireable`: required, boolean or null
    * `bio`: required, string or null
    * `twitter_username`: string or null
    * `public_repos`: required, integer
    * `public_gists`: required, integer
    * `followers`: required, integer
    * `following`: required, integer
    * `created_at`: required, string, format: date-time
    * `updated_at`: required, string, format: date-time
    * `plan`: object:
      * `collaborators`: required, integer
      * `name`: required, string
      * `space`: required, integer
      * `private_repos`: required, integer
    * `private_gists`: integer
    * `total_private_repos`: integer
    * `owned_private_repos`: integer
    * `disk_usage`: integer
    * `collaborators`: integer





## Update the authenticated user

```
PATCH /user
```

Note: If your email is set to private and you send an email parameter as part of this request to update your profile, your privacy settings are still enforced: the email address will not be displayed on your public profile or via the API.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.





#### Body parameters

- **`name`** (string)
  The new name of the user.

- **`email`** (string)
  The publicly visible email address of the user.

- **`blog`** (string)
  The new blog URL of the user.

- **`twitter_username`** (string or null)
  The new Twitter username of the user.

- **`company`** (string)
  The new company of the user.

- **`location`** (string)
  The new location of the user.

- **`hireable`** (boolean)
  The new hiring availability of the user.

- **`bio`** (string)
  The new short biography of the user.





### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example of updating blog and name

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/user \
  -d '{
  "blog": "https://github.com/blog",
  "name": "monalisa octocat"
}'
```

**Response schema (Status: 200):**

* `login`: required, string
* `id`: required, integer, format: int64
* `user_view_type`: string
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
* `name`: required, string or null
* `company`: required, string or null
* `blog`: required, string or null
* `location`: required, string or null
* `email`: required, string or null, format: email
* `notification_email`: string or null, format: email
* `hireable`: required, boolean or null
* `bio`: required, string or null
* `twitter_username`: string or null
* `public_repos`: required, integer
* `public_gists`: required, integer
* `followers`: required, integer
* `following`: required, integer
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `private_gists`: required, integer
* `total_private_repos`: required, integer
* `owned_private_repos`: required, integer
* `disk_usage`: required, integer
* `collaborators`: required, integer
* `two_factor_authentication`: required, boolean
* `plan`: object:
  * `collaborators`: required, integer
  * `name`: required, string
  * `space`: required, integer
  * `private_repos`: required, integer
* `business_plus`: boolean
* `ldap_dn`: string





## Get a user using their ID

```
GET /user/{account_id}
```

Provides publicly available information about someone with a GitHub account. This method takes their durable user ID instead of their login, which can change over time.
If you are requesting information about an Enterprise Managed User, or a GitHub App bot that is installed in an organization that uses Enterprise Managed Users, your requests must be authenticated as a user or GitHub App that has access to the organization to view that account's information. If you are not authorized, the request will return a 404 Not Found status.
The email key in the following response is the publicly visible email address from your GitHub profile page. When setting up your profile, you can select a primary email address to be public which provides an email entry for this endpoint. If you do not set a public email address for email, then it will have a value of null. You only see publicly visible email addresses when authenticated with GitHub. For more information, see Authentication.
The Emails API enables you to list all of your email addresses, and toggle a primary email to be visible publicly. For more information, see Emails API.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`account_id`** (integer) (required)
  account_id parameter






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/ACCOUNT_ID
```

**Response schema (Status: 200):**

Same response schema as [Get the authenticated user](#get-the-authenticated-user).



#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/ACCOUNT_ID
```

**Response schema (Status: 200):**

Same response schema as [Get the authenticated user](#get-the-authenticated-user).





## List users

```
GET /users
```

Lists all users, in the order that they signed up on GitHub. This list includes personal user accounts and organization accounts.
Note: Pagination is powered exclusively by the since parameter. Use the Link header to get the URL for the next page of users.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`since`** (integer)
  A user ID. Only return users with an ID greater than this ID.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`






### HTTP response status codes


- **200** - OK


- **304** - Not modified




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users
```

**Response schema (Status: 200):**

Array of `Simple User`:
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





## Get a user

```
GET /users/{username}
```

Provides publicly available information about someone with a GitHub account.
If you are requesting information about an Enterprise Managed User, or a GitHub App bot that is installed in an organization that uses Enterprise Managed Users, your requests must be authenticated as a user or GitHub App that has access to the organization to view that account's information. If you are not authorized, the request will return a 404 Not Found status.
The email key in the following response is the publicly visible email address from your GitHub profile page. When setting up your profile, you can select a primary email address to be public which provides an email entry for this endpoint. If you do not set a public email address for email, then it will have a value of null. You only see publicly visible email addresses when authenticated with GitHub. For more information, see Authentication.
The Emails API enables you to list all of your email addresses, and toggle a primary email to be visible publicly. For more information, see Emails API.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME
```

**Response schema (Status: 200):**

Same response schema as [Get the authenticated user](#get-the-authenticated-user).



#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME
```

**Response schema (Status: 200):**

Same response schema as [Get the authenticated user](#get-the-authenticated-user).





## Get contextual information for a user

```
GET /users/{username}/hovercard
```

Provides hovercard information. You can find out more about someone in relation to their pull requests, issues, repositories, and organizations.
The subject_type and subject_id parameters provide context for the person's hovercard, which returns more information than without the parameters. For example, if you wanted to find out more about octocat who owns the Spoon-Knife repository, you would use a subject_type value of repository and a subject_id value of 1300192 (the ID of the Spoon-Knife repository).
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`subject_type`** (string)
  Identifies which additional information you'd like to receive about the person's hovercard. Can be organization, repository, issue, pull_request. Required when using subject_id.
  Can be one of: `organization`, `repository`, `issue`, `pull_request`

- **`subject_id`** (string)
  Uses the ID for the subject_type you specified. Required when using subject_type.






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
  https://api.github.com/users/USERNAME/hovercard
```

**Response schema (Status: 200):**

* `contexts`: required, array of objects:
  * `message`: required, string
  * `octicon`: required, string