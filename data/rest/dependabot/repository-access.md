# REST API endpoints for {% data variables.product.prodname_dependabot %} repository access

Use the REST API to manage which repositories Dependabot can access within an organization.

## About Dependabot repository access

You can list repositories that Dependabot already has access to and set a default repository access level for Dependabot.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Lists the repositories Dependabot can access in an organization

```
GET /orgs/{org}/dependabot/repository-access
```

Lists repositories that organization admins have allowed Dependabot to access when updating dependencies.
Note

This operation supports both server-to-server and user-to-server access.
Unauthorized users will not see the existence of this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`page`** (integer)
  The page number of results to fetch.
  Default: `1`

- **`per_page`** (integer)
  Number of results per page.
  Default: `30`






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/dependabot/repository-access
```

**Response schema (Status: 200):**

* `default_level`: string or null, enum: `public`, `internal`, `null`
* `accessible_repositories`: array of object





## Updates Dependabot's repository access list for an organization

```
PATCH /orgs/{org}/dependabot/repository-access
```

Updates repositories according to the list of repositories that organization admins have given Dependabot access to when they've updated dependencies.
Note

This operation supports both server-to-server and user-to-server access.
Unauthorized users will not see the existence of this endpoint.

Example request body:
{
  "repository_ids_to_add": [123, 456],
  "repository_ids_to_remove": [789]
}


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`repository_ids_to_add`** (array of integers)
  List of repository IDs to add.

- **`repository_ids_to_remove`** (array of integers)
  List of repository IDs to remove.





### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example with a 'succeeded' status.

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/dependabot/repository-access
```

**Response schema (Status: 204):**





## Set the default repository access level for Dependabot

```
PUT /orgs/{org}/dependabot/repository-access/default-level
```

Sets the default level of repository access Dependabot will have while performing an update.  Available values are:

'public' - Dependabot will only have access to public repositories, unless access is explicitly granted to non-public repositories.
'internal' - Dependabot will only have access to public and internal repositories, unless access is explicitly granted to private repositories.

Unauthorized users will not see the existence of this endpoint.
This operation supports both server-to-server and user-to-server access.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`default_level`** (string) (required)
  The default repository access level for Dependabot updates.
  Can be one of: `public`, `internal`





### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example with a 'succeeded' status.

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/dependabot/repository-access/default-level \
  -d '{
  "default_level": "public"
}'
```

**Response schema (Status: 204):**