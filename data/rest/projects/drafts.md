# REST API endpoints for draft Project items

Use the REST API to manage draft items in Projects.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Create draft item for organization owned project

```
POST /orgs/{org}/projectsV2/{project_number}/drafts
```

Create draft issue item for the specified organization owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`project_number`** (integer) (required)
  The project's number.




#### Body parameters

- **`title`** (string) (required)
  The title of the draft issue item to create in the project.

- **`body`** (string)
  The body content of the draft issue item to create in the project.





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden





## Create draft item for user owned project

```
POST /user/{user_id}/projectsV2/{project_number}/drafts
```

Create draft issue item for the specified user owned project.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`user_id`** (string) (required)
  The unique identifier of the user.

- **`project_number`** (integer) (required)
  The project's number.




#### Body parameters

- **`title`** (string) (required)
  The title of the draft issue item to create in the project.

- **`body`** (string)
  The body content of the draft issue item to create in the project.





### HTTP response status codes


- **201** - Created


- **304** - Not modified


- **401** - Requires authentication


- **403** - Forbidden