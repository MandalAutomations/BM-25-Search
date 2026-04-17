# REST API endpoints for Copilot content exclusion management

Use the REST API to manage Copilot content exclusion rules.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get Copilot content exclusion rules for an organization

```
GET /orgs/{org}/copilot/content_exclusion
```

Note

This endpoint is in public preview and is subject to change.

Gets information about an organization's Copilot content exclusion path rules.
To configure these settings, go to the organization's settings on GitHub.
For more information, see "Excluding content from GitHub Copilot."
Organization owners can view details about Copilot content exclusion rules for the organization.
OAuth app tokens and personal access tokens (classic) need either the copilot or read:org scopes to use this endpoint.
Caution

At this time, the API does not support comments. This endpoint will not return any comments in the existing rules.
At this time, the API does not support duplicate keys. If your content exclusion configuration contains duplicate keys, the API will return only the last occurrence of that key. For example, if duplicate entries are present, only the final value will be included in the response.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - OK


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/content_exclusion
```

**Response schema (Status: 200):**

object, additional properties: array





## Set Copilot content exclusion rules for an organization

```
PUT /orgs/{org}/copilot/content_exclusion
```

Note

This endpoint is in public preview and is subject to change.

Sets Copilot content exclusion path rules for an organization.
To configure these settings, go to the organization's settings on GitHub.
For more information, see "Excluding content from GitHub Copilot."
Organization owners can set Copilot content exclusion rules for the organization.
OAuth app tokens and personal access tokens (classic) need the copilot scope to use this endpoint.
Caution

At this time, the API does not support comments. When using this endpoint, any existing comments in your rules will be deleted.
At this time, the API does not support duplicate keys. If you submit content exclusions through the API with duplicate keys, only the last occurrence will be saved. Earlier entries with the same key will be overwritten.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.






### HTTP response status codes


- **200** - Success


- **401** - Requires authentication


- **403** - Forbidden


- **404** - Resource not found


- **413** - Payload Too Large


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example of content exclusion paths

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot/content_exclusion \
  -d '{
  "octo-repo": [
    "/src/some-dir/kernel.rs"
  ]
}'
```

**Response schema (Status: 200):**

* `message`: string