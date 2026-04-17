# Custom properties

Use the REST API to manage custom properties for your enterprise.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get custom properties for an enterprise

```
GET /enterprises/{enterprise}/properties/schema
```

Gets all custom properties defined for an enterprise.
Enterprise members can read these properties.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






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
  https://api.github.com/enterprises/ENTERPRISE/properties/schema
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





## Create or update custom properties for an enterprise

```
PATCH /enterprises/{enterprise}/properties/schema
```

Creates new or updates existing custom properties defined for an enterprise in a batch.
If the property already exists, the existing property will be replaced with the new values.
Missing optional values will fall back to default values, previous values will be overwritten.
E.g. if a property exists with values_editable_by: org_and_repo_actors and it's updated without specifying values_editable_by, it will be updated to default value org_actors.
To use this endpoint, the authenticated user must be an administrator for the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`properties`** (array of objects) (required)
  The array of custom properties to create or update.
  - **`property_name`** (string) (required)
    The name of the property
  - **`url`** (string)
    The URL that can be used to fetch, update, or delete info about this property via the API.
  - **`source_type`** (string)
    The source type of the property
    Can be one of: `organization`, `enterprise`
  - **`value_type`** (string) (required)
    The type of the value for the property
    Can be one of: `string`, `single_select`, `multi_select`, `true_false`, `url`
  - **`required`** (boolean)
    Whether the property is required.
  - **`default_value`** (null or string or array)
    Default value of the property
  - **`description`** (string or null)
    Short description of the property
  - **`allowed_values`** (array of strings or null)
    An ordered list of the allowed values of the property.
The property can have up to 200 allowed values.
  - **`values_editable_by`** (string or null)
    Who can edit the values of the property
    Can be one of: `org_actors`, `org_and_repo_actors`, `null`
  - **`require_explicit_values`** (boolean)
    Whether setting properties values is mandatory





### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/properties/schema \
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

Same response schema as [Get custom properties for an enterprise](#get-custom-properties-for-an-enterprise).





## Promote a custom property to an enterprise

```
PUT /enterprises/{enterprise}/properties/schema/organizations/{org}/{custom_property_name}/promote
```

Promotes an existing organization custom property to an enterprise.
To use this endpoint, the authenticated user must be an administrator for the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`custom_property_name`** (string) (required)
  The custom property name






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/properties/schema/organizations/ORG/CUSTOM_PROPERTY_NAME/promote
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





## Get a custom property for an enterprise

```
GET /enterprises/{enterprise}/properties/schema/{custom_property_name}
```

Gets a custom property that is defined for an enterprise.
Enterprise members can read these properties.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`custom_property_name`** (string) (required)
  The custom property name






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
  https://api.github.com/enterprises/ENTERPRISE/properties/schema/CUSTOM_PROPERTY_NAME
```

**Response schema (Status: 200):**

Same response schema as [Promote a custom property to an enterprise](#promote-a-custom-property-to-an-enterprise).





## Create or update a custom property for an enterprise

```
PUT /enterprises/{enterprise}/properties/schema/{custom_property_name}
```

Creates a new or updates an existing custom property that is defined for an enterprise.
To use this endpoint, the authenticated user must be an administrator for the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`custom_property_name`** (string) (required)
  The custom property name




#### Body parameters

- **`value_type`** (string) (required)
  The type of the value for the property
  Can be one of: `string`, `single_select`, `multi_select`, `true_false`, `url`

- **`required`** (boolean)
  Whether the property is required.

- **`default_value`** (null or string or array)
  Default value of the property

- **`description`** (string or null)
  Short description of the property

- **`allowed_values`** (array of strings or null)
  An ordered list of the allowed values of the property.
The property can have up to 200 allowed values.

- **`values_editable_by`** (string or null)
  Who can edit the values of the property
  Can be one of: `org_actors`, `org_and_repo_actors`, `null`

- **`require_explicit_values`** (boolean)
  Whether setting properties values is mandatory





### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/properties/schema/CUSTOM_PROPERTY_NAME \
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

Same response schema as [Promote a custom property to an enterprise](#promote-a-custom-property-to-an-enterprise).





## Remove a custom property for an enterprise

```
DELETE /enterprises/{enterprise}/properties/schema/{custom_property_name}
```

Remove a custom property that is defined for an enterprise.
To use this endpoint, the authenticated user must be an administrator for the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`custom_property_name`** (string) (required)
  The custom property name






### HTTP response status codes


- **204** - A header with no content is returned.


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/properties/schema/CUSTOM_PROPERTY_NAME
```

**Response schema (Status: 204):**