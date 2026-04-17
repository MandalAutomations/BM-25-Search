# REST API for organization custom properties in an enterprise

Use the REST API to manage custom properties for organizations belonging to an enterprise


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get organization custom properties schema for an enterprise

```
GET /enterprises/{enterprise}/org-properties/schema
```

Gets all organization custom property definitions that are defined on an enterprise.
Access requirements:

Enterprise admins
OAuth tokens and personal access tokens (classic) with the read:enterprise scope
Actors with the enterprise-level "read enterprise custom properties for organizations" fine-grained permission or above


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
  https://api.github.com/enterprises/ENTERPRISE/org-properties/schema
```

**Response schema (Status: 200):**

Array of `Custom Property for Organization` objects: all of:
  * **object**
    * `property_name`: string
    * `url`: string, format: uri
    * `source_type`: string, enum: `organization`, `enterprise`
    * `value_type`: string, enum: `string`, `single_select`, `multi_select`, `true_false`, `url`
    * `required`: boolean
    * `default_value`: one of:
      * **string**
      * **array**
    * `description`: string or null
    * `allowed_values`: array of string or null
  * **object**
    * `values_editable_by`: string or null, enum: `enterprise_actors`, `enterprise_and_org_actors`, `null`





## Create or update organization custom property definitions on an enterprise

```
PATCH /enterprises/{enterprise}/org-properties/schema
```

Creates new or updates existing organization custom properties defined on an enterprise in a batch.
If the property already exists, the existing property will be replaced with the new values.
Missing optional values will fall back to default values, previous values will be overwritten.
Access requirements:

Enterprise admins
OAuth tokens and personal access tokens (classic) with the admin:enterprise scope
Actors with the enterprise-level "manage enterprise custom properties for organizations" fine-grained permission


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`properties`** (array of objects) (required)
  The array of organization custom properties to create or update.
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
    Can be one of: `enterprise_actors`, `enterprise_and_org_actors`, `null`





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
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/org-properties/schema \
  -d '{
  "properties": [
    {
      "property_name": "environment",
      "source_type": "enterprise",
      "value_type": "single_select",
      "required": true,
      "default_value": "production",
      "description": "Prod or dev environment",
      "allowed_values": [
        "production",
        "development"
      ],
      "values_editable_by": "enterprise_actors"
    },
    {
      "property_name": "service",
      "source_type": "enterprise",
      "value_type": "string"
    },
    {
      "property_name": "team",
      "source_type": "enterprise",
      "value_type": "string",
      "description": "Team owning the organization"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get organization custom properties schema for an enterprise](#get-organization-custom-properties-schema-for-an-enterprise).





## Get an organization custom property definition from an enterprise

```
GET /enterprises/{enterprise}/org-properties/schema/{custom_property_name}
```

Gets an organization custom property definition that is defined on an enterprise.
Access requirements:

Enterprise admins
OAuth tokens and personal access tokens (classic) with the read:enterprise scope
Actors with the enterprise-level "read enterprise custom properties for organizations" fine-grained permission or above


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
  https://api.github.com/enterprises/ENTERPRISE/org-properties/schema/CUSTOM_PROPERTY_NAME
```

**Response schema (Status: 200):**

* all of:
  * **object**
    * `property_name`: string
    * `url`: string, format: uri
    * `source_type`: string, enum: `organization`, `enterprise`
    * `value_type`: string, enum: `string`, `single_select`, `multi_select`, `true_false`, `url`
    * `required`: boolean
    * `default_value`: one of:
      * **string**
      * **array**
    * `description`: string or null
    * `allowed_values`: array of string or null
  * **object**
    * `values_editable_by`: string or null, enum: `enterprise_actors`, `enterprise_and_org_actors`, `null`





## Create or update an organization custom property definition on an enterprise

```
PUT /enterprises/{enterprise}/org-properties/schema/{custom_property_name}
```

Creates a new or updates an existing organization custom property definition that is defined on an enterprise.
Access requirements:

Enterprise admins
OAuth tokens and personal access tokens (classic) with the admin:enterprise scope
Actors with the enterprise-level "manage enterprise custom properties for organizations" fine-grained permission


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
  The type of the value for the property.
  Can be one of: `string`, `single_select`, `multi_select`, `true_false`, `url`

- **`required`** (boolean)
  Whether the property is required.

- **`default_value`** (null or string or array)
  Default value of the property.

- **`description`** (string or null)
  Short description of the property.

- **`allowed_values`** (array of strings or null)
  An ordered list of the allowed values of the property.
The property can have up to 200 allowed values.

- **`values_editable_by`** (string or null)
  Who can edit the values of the property.
  Can be one of: `enterprise_actors`, `enterprise_and_org_actors`, `null`





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
  https://api.github.com/enterprises/ENTERPRISE/org-properties/schema/CUSTOM_PROPERTY_NAME \
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

Same response schema as [Get an organization custom property definition from an enterprise](#get-an-organization-custom-property-definition-from-an-enterprise).





## Remove an organization custom property definition from an enterprise

```
DELETE /enterprises/{enterprise}/org-properties/schema/{custom_property_name}
```

Removes an organization custom property definition that is defined on an enterprise.
Access requirements:

Enterprise admins
OAuth tokens and personal access tokens (classic) with the admin:enterprise scope
Actors with the enterprise-level "manage enterprise custom properties for organizations" fine-grained permission


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


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/org-properties/schema/CUSTOM_PROPERTY_NAME
```

**Response schema (Status: 204):**





## List custom property values for organizations in an enterprise

```
GET /enterprises/{enterprise}/org-properties/values
```

Lists enterprise organizations with all of their custom property values.
Access requirements:

Enterprise admins
OAuth tokens and personal access tokens (classic) with the read:enterprise scope
Actors with the enterprise-level "read enterprise custom properties for organizations" fine-grained permission or above


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






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
  https://api.github.com/enterprises/ENTERPRISE/org-properties/values
```

**Response schema (Status: 200):**

Array of `Enterprise Organization Custom Property Values`:
  * `organization_id`: required, integer
  * `organization_login`: required, string
  * `properties`: required, array of `Custom Property Value`:
    * `property_name`: required, string
    * `value`: required, one of:
      * **string**
      * **array**





## Create or update custom property values for organizations in an enterprise

```
PATCH /enterprises/{enterprise}/org-properties/values
```

Create or update custom property values for organizations in an enterprise.
To remove a custom property value from an organization, set the property value to null.
Access requirements:

Enterprise admins
OAuth tokens and personal access tokens (classic) with the admin:enterprise scope
Actors with the enterprise-level "edit enterprise custom properties for organizations" fine-grained permission or above


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`organization_logins`** (array of strings) (required)
  The names of organizations that the custom property values will be applied to.

- **`properties`** (array of objects) (required)
  List of custom property names and associated values to apply to the organizations.
  - **`property_name`** (string) (required)
    The name of the property
  - **`value`** (null or string or array) (required)
    The value assigned to the property





### HTTP response status codes


- **204** - No Content when custom property values are successfully created or updated


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/org-properties/values \
  -d '{
  "organization_logins": [
    "acme",
    "github"
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