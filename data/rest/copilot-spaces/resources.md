# REST API endpoints for Copilot Spaces

Use the REST API to interact with Copilot Spaces resources.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List resources for an organization Copilot Space

```
GET /orgs/{org}/copilot-spaces/{space_number}/resources
```

Lists all resources attached to a specific Copilot Space owned by an organization.
The authenticated user must have appropriate permissions to view the space.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.






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
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/resources
```

**Response schema (Status: 200):**

* `resources`: required, array of `Copilot Space Resource`:
  * `id`: required, integer
  * `resource_type`: required, string, enum: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`, `media_content`, `uploaded_text_file`
  * `copilot_chat_attachment_id`: integer or null
  * `metadata`: required, object, additional properties allowed
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time





## Create a resource for an organization Copilot Space

```
POST /orgs/{org}/copilot-spaces/{space_number}/resources
```

Creates a new resource in a specific Copilot Space owned by an organization.
The authenticated user must have write permissions on the space.
The following resource types are supported: repository, github_file, free_text, github_issue, github_pull_request.
The uploaded_text_file and media_content types are not supported via this endpoint.
For github_file resources, if a resource with the same repository, file path, and SHA already exists, the existing resource is returned with a 200 status.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.




#### Body parameters

- **`resource_type`** (string) (required)
  The type of resource to create.
  Can be one of: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`

- **`metadata`** (object) (required)
  Resource-specific metadata.





### HTTP response status codes


- **200** - Duplicate github_file resource already exists


- **201** - Resource created


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.





## Get a resource for an organization Copilot Space

```
GET /orgs/{org}/copilot-spaces/{space_number}/resources/{space_resource_id}
```

Gets a specific resource attached to a Copilot Space owned by an organization.
The authenticated user must have appropriate permissions to view the space.
OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.

- **`space_resource_id`** (integer) (required)
  The unique identifier of the resource.






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
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/resources/SPACE_RESOURCE_ID
```

**Response schema (Status: 200):**

* `id`: required, integer
* `resource_type`: required, string, enum: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`, `media_content`, `uploaded_text_file`
* `copilot_chat_attachment_id`: integer or null
* `metadata`: required, object, additional properties allowed
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time





## Set a resource for an organization Copilot Space

```
PUT /orgs/{org}/copilot-spaces/{space_number}/resources/{space_resource_id}
```

Updates the metadata of a resource in a specific Copilot Space owned by an organization.
The authenticated user must have write permissions on the space.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.

- **`space_resource_id`** (integer) (required)
  The unique identifier of the resource.




#### Body parameters

- **`metadata`** (object)
  Updated resource-specific metadata.





### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/resources/SPACE_RESOURCE_ID \
  -d '{
  "metadata": {
    "name": "updated-notes.txt",
    "text": "Updated content"
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a resource for an organization Copilot Space](#get-a-resource-for-an-organization-copilot-space).





## Delete a resource from an organization Copilot Space

```
DELETE /orgs/{org}/copilot-spaces/{space_number}/resources/{space_resource_id}
```

Deletes a resource from a specific Copilot Space owned by an organization.
The authenticated user must have write permissions on the space.
OAuth app tokens and personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.

- **`space_resource_id`** (integer) (required)
  The unique identifier of the resource.






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
  https://api.github.com/orgs/ORG/copilot-spaces/SPACE_NUMBER/resources/SPACE_RESOURCE_ID
```

**Response schema (Status: 204):**





## List resources for a Copilot Space for a user

```
GET /users/{username}/copilot-spaces/{space_number}/resources
```

Lists all resources attached to a specific Copilot Space owned by a user.
The authenticated user must have appropriate permissions to view the space.
OAuth app tokens and personal access tokens (classic) need the read:user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.






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
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER/resources
```

**Response schema (Status: 200):**

Same response schema as [List resources for an organization Copilot Space](#list-resources-for-an-organization-copilot-space).





## Create a resource for a Copilot Space for a user

```
POST /users/{username}/copilot-spaces/{space_number}/resources
```

Creates a new resource in a specific Copilot Space owned by a user.
The authenticated user must have write permissions on the space.
The following resource types are supported: repository, github_file, free_text, github_issue, github_pull_request.
The uploaded_text_file and media_content types are not supported via this endpoint.
For github_file resources, if a resource with the same repository, file path, and SHA already exists, the existing resource is returned with a 200 status.
OAuth app tokens and personal access tokens (classic) need the write:user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.




#### Body parameters

- **`resource_type`** (string) (required)
  The type of resource to create.
  Can be one of: `repository`, `github_file`, `free_text`, `github_issue`, `github_pull_request`

- **`metadata`** (object) (required)
  Resource-specific metadata.





### HTTP response status codes


- **200** - Duplicate github_file resource already exists


- **201** - Resource created


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.





## Get a resource for a Copilot Space for a user

```
GET /users/{username}/copilot-spaces/{space_number}/resources/{space_resource_id}
```

Gets a specific resource attached to a Copilot Space owned by a user.
The authenticated user must have appropriate permissions to view the space.
OAuth app tokens and personal access tokens (classic) need the read:user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.

- **`space_resource_id`** (integer) (required)
  The unique identifier of the resource.






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
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER/resources/SPACE_RESOURCE_ID
```

**Response schema (Status: 200):**

Same response schema as [Get a resource for an organization Copilot Space](#get-a-resource-for-an-organization-copilot-space).





## Set a resource for a Copilot Space for a user

```
PUT /users/{username}/copilot-spaces/{space_number}/resources/{space_resource_id}
```

Updates the metadata of a resource in a specific Copilot Space owned by a user.
The authenticated user must have write permissions on the space.
OAuth app tokens and personal access tokens (classic) need the write:user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.

- **`space_resource_id`** (integer) (required)
  The unique identifier of the resource.




#### Body parameters

- **`metadata`** (object)
  Updated resource-specific metadata.





### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER/resources/SPACE_RESOURCE_ID \
  -d '{
  "metadata": {
    "name": "updated-notes.txt",
    "text": "Updated content"
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a resource for an organization Copilot Space](#get-a-resource-for-an-organization-copilot-space).





## Delete a resource from a Copilot Space for a user

```
DELETE /users/{username}/copilot-spaces/{space_number}/resources/{space_resource_id}
```

Deletes a resource from a specific Copilot Space owned by a user.
The authenticated user must have write permissions on the space.
OAuth app tokens and personal access tokens (classic) need the write:user scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`space_number`** (integer) (required)
  The unique identifier of the Copilot Space.

- **`space_resource_id`** (integer) (required)
  The unique identifier of the resource.






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
  https://api.github.com/users/USERNAME/copilot-spaces/SPACE_NUMBER/resources/SPACE_RESOURCE_ID
```

**Response schema (Status: 204):**