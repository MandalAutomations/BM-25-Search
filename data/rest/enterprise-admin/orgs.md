# REST API endpoints for enterprise organizations

Use the REST API to create organizations on your enterprise.

## About organization administration

These endpoints are only available to [authenticated](/en/enterprise-server@3.20/rest/overview/authenticating-to-the-rest-api) site administrators. Normal users will receive a `404` response.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## Create an organization

```
POST /admin/organizations
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`login`** (string) (required)
  The organization's username.

* **`admin`** (string) (required)
  The login of the user who will manage this organization.

* **`profile_name`** (string)
  The organization's display name.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/admin/organizations \
  -d '{
  "login": "github",
  "profile_name": "GitHub, Inc.",
  "admin": "monalisaoctocat"
}'
```

**Response schema (Status: 201):**

* `login`: required, string
* `id`: required, integer
* `node_id`: required, string
* `url`: required, string, format: uri
* `repos_url`: required, string, format: uri
* `events_url`: required, string, format: uri
* `hooks_url`: required, string
* `issues_url`: required, string
* `members_url`: required, string
* `public_members_url`: required, string
* `avatar_url`: required, string
* `description`: required, string or null

## Update an organization name

```
PATCH /admin/organizations/{org}
```

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`login`** (string) (required)
  The organization's new name.

### HTTP response status codes

* **202** - Accepted

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/admin/organizations/ORG \
  -d '{
  "login": "the-new-octocats"
}'
```

**Response schema (Status: 202):**

* `message`: string
* `url`: string