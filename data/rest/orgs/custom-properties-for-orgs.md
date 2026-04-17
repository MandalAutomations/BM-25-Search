# REST API endpoints for an organization's custom property values

Use the REST API to manage custom property values for an organization


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get all custom property values for an organization

```
GET /organizations/{org}/org-properties/values
```

Gets all custom property values that are set for an organization.
The organization must belong to an enterprise.
Access requirements:

Organization admins
OAuth tokens and personal access tokens (classic) with the read:org scope
Actors with the organization-level "read custom properties for an organization" fine-grained permission or above


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






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
  https://api.github.com/organizations/ORG/org-properties/values
```

**Response schema (Status: 200):**

Array of `Custom Property Value`:
  * `property_name`: required, string
  * `value`: required, one of:
    * **string**
    * **array**





## Create or update custom property values for an organization

```
PATCH /organizations/{org}/org-properties/values
```

Create new or update existing custom property values for an organization.
To remove a custom property value from an organization, set the property value to null.
The organization must belong to an enterprise.
Access requirements:

Organization admins
OAuth tokens and personal access tokens (classic) with the admin:org scope
Actors with the organization-level "edit custom properties for an organization" fine-grained permission


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`properties`** (array of objects) (required)
  A list of custom property names and associated values to apply to the organization.
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
  https://api.github.com/organizations/ORG/org-properties/values \
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