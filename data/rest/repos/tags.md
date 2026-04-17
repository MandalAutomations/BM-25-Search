# REST API endpoints for repository tags

Use the REST API to manage tags for a repository.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.


## Closing down - List tag protection states for a repository

```
GET /repos/{owner}/{repo}/tags/protection
```

Warning

Closing down notice: This operation is closing down and will be removed after August 30, 2024. Use the "Repository Rulesets" endpoint instead.

This returns the tag protection states of a repository.
This information is only available to repository administrators.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.






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
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/tags/protection
```

**Response schema (Status: 200):**

Array of `Tag protection`:
  * `id`: integer
  * `created_at`: string
  * `updated_at`: string
  * `enabled`: boolean
  * `pattern`: required, string





## Closing down - Create a tag protection state for a repository

```
POST /repos/{owner}/{repo}/tags/protection
```

Warning

Closing down notice: This operation is closing down and will be removed after August 30, 2024. Use the "Repository Rulesets" endpoint instead.

This creates a tag protection state for a repository.
This endpoint is only available to repository administrators.


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

- **`pattern`** (string) (required)
  An optional glob pattern to match against when enforcing tag protection.





### HTTP response status codes


- **201** - Created


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/tags/protection \
  -d '{
  "pattern": "v1.*"
}'
```

**Response schema (Status: 201):**

* `id`: integer
* `created_at`: string
* `updated_at`: string
* `enabled`: boolean
* `pattern`: required, string





## Closing down - Delete a tag protection state for a repository

```
DELETE /repos/{owner}/{repo}/tags/protection/{tag_protection_id}
```

Warning

Closing down notice: This operation is closing down and will be removed after August 30, 2024. Use the "Repository Rulesets" endpoint instead.

This deletes a tag protection state for a repository.
This endpoint is only available to repository administrators.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`tag_protection_id`** (integer) (required)
  The unique identifier of the tag protection.






### HTTP response status codes


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/repos/OWNER/REPO/tags/protection/TAG_PROTECTION_ID
```

**Response schema (Status: 204):**