# REST API endpoints for outside collaborators

Use the REST API to manage outside collaborators.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List outside collaborators for an organization

```
GET /orgs/{org}/outside_collaborators
```

List all users who are outside collaborators of an organization.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`filter`** (string)
  Filter the list of outside collaborators. 2fa_disabled means that only outside collaborators without two-factor authentication enabled will be returned. 2fa_insecure means that only outside collaborators with insecure 2FA methods will be returned.
  Default: `all`
  Can be one of: `2fa_disabled`, `2fa_insecure`, `all`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/outside_collaborators
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





## Convert an organization member to outside collaborator

```
PUT /orgs/{org}/outside_collaborators/{username}
```

When an organization member is converted to an outside collaborator, they'll only have access to the repositories that their current team membership allows. The user will no longer be a member of the organization. For more information, see "Converting an organization member to an outside collaborator". Converting an organization member to an outside collaborator may be restricted by enterprise administrators. For more information, see "Enforcing repository management policies in your enterprise."


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`username`** (string) (required)
  The handle for the GitHub user account.




#### Body parameters

- **`async`** (boolean)
  When set to true, the request will be performed asynchronously. Returns a 202 status code when the job is successfully queued.
  Default: `false`





### HTTP response status codes


- **202** - User is getting converted asynchronously


- **204** - User was converted


- **403** - Forbidden if user is the last owner of the organization, not a member of the organization, or if the enterprise enforces a policy for inviting outside collaborators. For more information, see "Enforcing repository management policies in your enterprise."


- **404** - Resource not found




### Code examples



#### Status code 202, asynchronous request

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/outside_collaborators/USERNAME \
  -d '{
  "async": true
}'
```

**Response schema (Status: 202):**





#### Status code 204, synchronous request

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/outside_collaborators/USERNAME
```

**Response schema (Status: 204):**





## Remove outside collaborator from an organization

```
DELETE /orgs/{org}/outside_collaborators/{username}
```

Removing a user from this list will remove them from all the organization's repositories.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`username`** (string) (required)
  The handle for the GitHub user account.






### HTTP response status codes


- **204** - No Content


- **422** - Unprocessable Entity if user is a member of the organization




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/outside_collaborators/USERNAME
```

**Response schema (Status: 204):**