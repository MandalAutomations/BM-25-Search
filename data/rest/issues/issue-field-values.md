# REST API endpoints for issue field values

Use the REST API to view and manage issue field values for issues.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List issue field values for an issue

```
GET /repos/{owner}/{repo}/issues/{issue_number}/issue-field-values
```

Lists all issue field values for an issue.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`issue_number`** (integer) (required)
  The number that identifies the issue.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`






### HTTP response status codes


- **200** - OK


- **301** - Moved permanently


- **404** - Resource not found


- **410** - Gone




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/issues/ISSUE_NUMBER/issue-field-values
```

**Response schema (Status: 200):**

Array of `Issue Field Value`:
  * `issue_field_id`: required, integer, format: int64
  * `node_id`: required, string
  * `data_type`: required, string, enum: `text`, `single_select`, `number`, `date`
  * `value`: required, any of:
    * **string**
    * **number**
    * **integer**
  * `single_select_option`: object or null:
    * `id`: required, integer, format: int64
    * `name`: required, string
    * `color`: required, string





## Add issue field values to an issue

```
POST /repositories/{repository_id}/issues/{issue_number}/issue-field-values
```

Add custom field values to an issue. You can set values for organization-level issue fields that have been defined for the repository's organization.
Adding an empty array will clear all existing field values for the issue.
This endpoint supports the following field data types:

text: String values for text fields
single_select: Option names for single-select fields (must match an existing option name)
number: Numeric values for number fields
date: ISO 8601 date strings for date fields

Only users with push access to the repository can add issue field values. If you don't have the proper permissions, you'll receive a 403 Forbidden response.
This endpoint triggers notifications. Creating content too quickly using this endpoint may result in secondary rate limiting. For more information, see "Rate limits for the API"
and "Best practices for using the REST API."


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`repository_id`** (integer) (required)
  The unique identifier of the repository.

- **`issue_number`** (integer) (required)
  The number that identifies the issue.




#### Body parameters

- **`issue_field_values`** (array of objects)
  An array of issue field values to add to this issue. Each field value must include the field ID and the value to set.
  - **`field_id`** (integer) (required)
    The ID of the issue field to set
  - **`value`** (string or number) (required)
    The value to set for the field. The type depends on the field's data type:

For text fields: provide a string value
For single_select fields: provide the option name as a string (must match an existing option)
For number fields: provide a numeric value
For date fields: provide an ISO 8601 date string





### HTTP response status codes


- **200** - OK


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **503** - Service unavailable




### Code examples



#### Add multiple field values

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repositories/REPOSITORY_ID/issues/ISSUE_NUMBER/issue-field-values \
  -d '{
  "issue_field_values": [
    {
      "field_id": 123,
      "value": "Critical"
    },
    {
      "field_id": 456,
      "value": 5
    },
    {
      "field_id": 789,
      "value": "2024-12-31"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List issue field values for an issue](#list-issue-field-values-for-an-issue).





## Set issue field values for an issue

```
PUT /repositories/{repository_id}/issues/{issue_number}/issue-field-values
```

Set custom field values for an issue, replacing any existing values. You can set values for organization-level issue fields that have been defined for the repository's organization.
This endpoint supports the following field data types:

text: String values for text fields
single_select: Option names for single-select fields (must match an existing option name)
number: Numeric values for number fields
date: ISO 8601 date strings for date fields

This operation will replace all existing field values with the provided ones. If you want to add field values without replacing existing ones, use the POST endpoint instead.
Only users with push access to the repository can set issue field values. If you don't have the proper permissions, you'll receive a 403 Forbidden response.
This endpoint triggers notifications. Creating content too quickly using this endpoint may result in secondary rate limiting. For more information, see "Rate limits for the API"
and "Best practices for using the REST API."


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`repository_id`** (integer) (required)
  The unique identifier of the repository.

- **`issue_number`** (integer) (required)
  The number that identifies the issue.




#### Body parameters

- **`issue_field_values`** (array of objects)
  An array of issue field values to set for this issue. Each field value must include the field ID and the value to set. All existing field values will be replaced.
  - **`field_id`** (integer) (required)
    The ID of the issue field to set
  - **`value`** (string or number) (required)
    The value to set for the field. The type depends on the field's data type:

For text fields: provide a string value
For single_select fields: provide the option name as a string (must match an existing option)
For number fields: provide a numeric value
For date fields: provide an ISO 8601 date string





### HTTP response status codes


- **200** - OK


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **503** - Service unavailable




### Code examples



#### Set multiple field values

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repositories/REPOSITORY_ID/issues/ISSUE_NUMBER/issue-field-values \
  -d '{
  "issue_field_values": [
    {
      "field_id": 123,
      "value": "Critical"
    },
    {
      "field_id": 456,
      "value": 5
    },
    {
      "field_id": 789,
      "value": "2024-12-31"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [List issue field values for an issue](#list-issue-field-values-for-an-issue).





## Delete an issue field value from an issue

```
DELETE /repositories/{repository_id}/issues/{issue_number}/issue-field-values/{issue_field_id}
```

Remove a specific custom field value from an issue.
Only users with push access to the repository can delete issue field values. If you don't have the proper permissions, you'll receive a 403 Forbidden response.
If the specified field does not have a value set on the issue, this operation will return a 404 error.
This endpoint triggers notifications. Creating content too quickly using this endpoint may result in secondary rate limiting. For more information, see "Rate limits for the API"
and "Best practices for using the REST API."


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`repository_id`** (integer) (required)
  The unique identifier of the repository.

- **`issue_number`** (integer) (required)
  The number that identifies the issue.

- **`issue_field_id`** (integer) (required)
  The unique identifier of the issue field.






### HTTP response status codes


- **204** - Issue field value deleted successfully


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation failed, or the endpoint has been spammed.


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repositories/REPOSITORY_ID/issues/ISSUE_NUMBER/issue-field-values/ISSUE_FIELD_ID
```

**Response schema (Status: 204):**