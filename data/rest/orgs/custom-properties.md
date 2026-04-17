# REST API endpoints for custom properties

Use the REST API to create and manage custom properties for an organization.

## About custom properties

You can use the REST API to create and manage custom properties for an organization. You can use custom properties to add metadata to repositories in your organization. For more information, see [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get all custom properties for an organization

```
GET /orgs/{org}/properties/schema
```

Gets all custom properties defined for an organization.
Organization members can read these properties.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

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
  https://api.github.com/orgs/ORG/properties/schema
```

**Response schema (Status: 200):**

Array of `Organization Custom Property`:

* `property_name`: required, string
* `url`: string, format: uri
* `source_type`: string, enum: `organization`, `enterprise`
* `value_type`: required, string, enum: `string`, `single_select`, `multi_select`, `true_false`, `url`
* `required`: boolean
* `default_value`: one of:
  * **string**
  * **array**
* `description`: string or null
* `allowed_values`: array of string or null
* `values_editable_by`: string or null, enum: `org_actors`, `org_and_repo_actors`, `null`
* `require_explicit_values`: boolean

## Create or update custom properties for an organization

```
PATCH /orgs/{org}/properties/schema
```

Creates new or updates existing custom properties defined for an organization in a batch.
If the property already exists, the existing property will be replaced with the new values.
Missing optional values will fall back to default values, previous values will be overwritten.
E.g. if a property exists with values\_editable\_by: org\_and\_repo\_actors and it's updated without specifying values\_editable\_by, it will be updated to default value org\_actors.
To use this endpoint, the authenticated user must be one of:

An administrator for the organization.
A user, or a user on a team, with the fine-grained permission of custom\_properties\_org\_definitions\_manager in the organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`properties`** (array of objects) (required)
  The array of custom properties to create or update.
  * **`property_name`** (string) (required)
    The name of the property
  * **`url`** (string)
    The URL that can be used to fetch, update, or delete info about this property via the API.
  * **`source_type`** (string)
    The source type of the property
    Can be one of: `organization`, `enterprise`
  * **`value_type`** (string) (required)
    The type of the value for the property
    Can be one of: `string`, `single_select`, `multi_select`, `true_false`, `url`
  * **`required`** (boolean)
    Whether the property is required.
  * **`default_value`** (null or string or array)
    Default value of the property
  * **`description`** (string or null)
    Short description of the property
  * **`allowed_values`** (array of strings or null)
    An ordered list of the allowed values of the property.
    The property can have up to 200 allowed values.
  * **`values_editable_by`** (string or null)
    Who can edit the values of the property
    Can be one of: `org_actors`, `org_and_repo_actors`, `null`
  * **`require_explicit_values`** (boolean)
    Whether setting properties values is mandatory

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/properties/schema \
  -d '{
  "properties": [
    {
      "property_name": "environment",
      "value_type": "single_select",
      "required": true,
      "default_value": "production",
      "description": "Prod or dev environment",
      "allowed_values": [
        "production",
        "development"
      ],
      "values_editable_by": "org_actors"
    },
    {
      "property_name": "service",
      "value_type": "string"
    },
    {
      "property_name": "team",
      "value_type": "string",
      "description": "Team owning the repository"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get all custom properties for an organization](#get-all-custom-properties-for-an-organization).

## Get a custom property for an organization

```
GET /orgs/{org}/properties/schema/{custom_property_name}
```

Gets a custom property that is defined for an organization.
Organization members can read these properties.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`custom_property_name`** (string) (required)
  The custom property name

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
  https://api.github.com/orgs/ORG/properties/schema/CUSTOM_PROPERTY_NAME
```

**Response schema (Status: 200):**

* `property_name`: required, string
* `url`: string, format: uri
* `source_type`: string, enum: `organization`, `enterprise`
* `value_type`: required, string, enum: `string`, `single_select`, `multi_select`, `true_false`, `url`
* `required`: boolean
* `default_value`: one of:
  * **string**
  * **array**
* `description`: string or null
* `allowed_values`: array of string or null
* `values_editable_by`: string or null, enum: `org_actors`, `org_and_repo_actors`, `null`
* `require_explicit_values`: boolean

## Create or update a custom property for an organization

```
PUT /orgs/{org}/properties/schema/{custom_property_name}
```

Creates a new or updates an existing custom property that is defined for an organization.
To use this endpoint, the authenticated user must be one of:

An administrator for the organization.
A user, or a user on a team, with the fine-grained permission of custom\_properties\_org\_definitions\_manager in the organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`custom_property_name`** (string) (required)
  The custom property name

#### Body parameters

* **`value_type`** (string) (required)
  The type of the value for the property
  Can be one of: `string`, `single_select`, `multi_select`, `true_false`, `url`

* **`required`** (boolean)
  Whether the property is required.

* **`default_value`** (null or string or array)
  Default value of the property

* **`description`** (string or null)
  Short description of the property

* **`allowed_values`** (array of strings or null)
  An ordered list of the allowed values of the property.
  The property can have up to 200 allowed values.

* **`values_editable_by`** (string or null)
  Who can edit the values of the property
  Can be one of: `org_actors`, `org_and_repo_actors`, `null`

* **`require_explicit_values`** (boolean)
  Whether setting properties values is mandatory

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/properties/schema/CUSTOM_PROPERTY_NAME \
  -d '{
  "value_type": "single_select",
  "required": true,
  "default_value": "production",
  "description": "Prod or dev environment",
  "allowed_values": [
    "production",
    "development"
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get a custom property for an organization](#get-a-custom-property-for-an-organization).

## Remove a custom property for an organization

```
DELETE /orgs/{org}/properties/schema/{custom_property_name}
```

Removes a custom property that is defined for an organization.
To use this endpoint, the authenticated user must be one of:

An administrator for the organization.
A user, or a user on a team, with the fine-grained permission of custom\_properties\_org\_definitions\_manager in the organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`custom_property_name`** (string) (required)
  The custom property name

### HTTP response status codes

* **204** - A header with no content is returned.

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/properties/schema/CUSTOM_PROPERTY_NAME
```

**Response schema (Status: 204):**

## List custom property values for organization repositories

```
GET /orgs/{org}/properties/values
```

Lists organization repositories with all of their custom property values.
Organization members can read these properties.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

* **`repository_query`** (string)
  Finds repositories in the organization with a query containing one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see Constructing a search query. See "Searching for repositories" for a detailed list of qualifiers.

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
  https://api.github.com/orgs/ORG/properties/values
```

**Response schema (Status: 200):**

Array of `Organization Repository Custom Property Values`:

* `repository_id`: required, integer
* `repository_name`: required, string
* `repository_full_name`: required, string
* `properties`: required, array of `Custom Property Value`:
  * `property_name`: required, string
  * `value`: required, one of:
    * **string**
    * **array**

## Create or update custom property values for organization repositories

```
PATCH /orgs/{org}/properties/values
```

Create new or update existing custom property values for repositories in a batch that belong to an organization.
Each target repository will have its custom property values updated to match the values provided in the request.
A maximum of 30 repositories can be updated in a single request.
Using a value of null for a custom property will remove or 'unset' the property value from the repository.
To use this endpoint, the authenticated user must be one of:

An administrator for the organization.
A user, or a user on a team, with the fine-grained permission of custom\_properties\_org\_values\_editor in the organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`repository_names`** (array of strings) (required)
  The names of repositories that the custom property values will be applied to.

* **`properties`** (array of objects) (required)
  List of custom property names and associated values to apply to the repositories.
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
  https://api.github.com/orgs/ORG/properties/values \
  -d '{
  "repository_names": [
    "Hello-World",
    "octo-repo"
  ],
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