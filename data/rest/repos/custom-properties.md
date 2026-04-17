# REST API endpoints for custom properties

Use the REST API to list the custom properties assigned to a repository by the organization.

## About custom properties

You can use the REST API to view the custom properties that were assigned to a repository by the organization that owns the repository. For more information, see [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization). For more information about the REST API endpoints to manage custom properties, see [REST API endpoints for custom properties](/en/rest/orgs/properties).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get all custom property values for a repository

```
GET /repos/{owner}/{repo}/properties/values
```

Gets all custom property values that are set for a repository.
Users with read access to the repository can use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/properties/values
```

**Response schema (Status: 200):**

Array of `Custom Property Value`:

* `property_name`: required, string
* `value`: required, one of:
  * **string**
  * **array**

## Create or update custom property values for a repository

```
PATCH /repos/{owner}/{repo}/properties/values
```

Create new or update existing custom property values for a repository.
Using a value of null for a custom property will remove or 'unset' the property value from the repository.
Repository admins and other users with the repository-level "edit custom property values" fine-grained permission can use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`properties`** (array of objects) (required)
  A list of custom property names and associated values to apply to the repositories.
  * **`property_name`** (string) (required)
    The name of the property
  * **`value`** (null or string or array) (required)
    The value assigned to the property

### HTTP response status codes

* **204** - No Content when custom property values are successfully created or updated

* **403** - Forbidden

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/properties/values \
  -d '{
  "properties": [
    {
      "property_name": "environment",
      "value": "production"
    },
    {
      "property_name": "service",
      "value": "web"
    },
    {
      "property_name": "team",
      "value": "octocat"
    }
  ]
}'
```

**Response schema (Status: 204):**