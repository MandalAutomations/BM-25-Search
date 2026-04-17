# REST API endpoints for secret scanning push protection

Use the REST API to manage secret scanning push protection.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List organization pattern configurations

```
GET /orgs/{org}/secret-scanning/pattern-configurations
```

Lists the secret scanning pattern configurations for an organization.
Personal access tokens (classic) need the read:org scope to use this endpoint.


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
  https://api.github.com/orgs/ORG/secret-scanning/pattern-configurations
```

**Response schema (Status: 200):**

* `pattern_config_version`: string or null
* `provider_pattern_overrides`: array of objects:
  * `token_type`: string
  * `custom_pattern_version`: string or null
  * `slug`: string
  * `display_name`: string
  * `alert_total`: integer
  * `alert_total_percentage`: integer
  * `false_positives`: integer
  * `false_positive_rate`: integer
  * `bypass_rate`: integer
  * `default_setting`: string, enum: `disabled`, `enabled`
  * `enterprise_setting`: string or null, enum: `not-set`, `disabled`, `enabled`, `null`
  * `setting`: string, enum: `not-set`, `disabled`, `enabled`
* `custom_pattern_overrides`: array of objects:
  * `token_type`: string
  * `custom_pattern_version`: string or null
  * `slug`: string
  * `display_name`: string
  * `alert_total`: integer
  * `alert_total_percentage`: integer
  * `false_positives`: integer
  * `false_positive_rate`: integer
  * `bypass_rate`: integer
  * `default_setting`: string, enum: `disabled`, `enabled`
  * `enterprise_setting`: string or null, enum: `not-set`, `disabled`, `enabled`, `null`
  * `setting`: string, enum: `not-set`, `disabled`, `enabled`





## Update organization pattern configurations

```
PATCH /orgs/{org}/secret-scanning/pattern-configurations
```

Updates the secret scanning pattern configurations for an organization.
Personal access tokens (classic) need the write:org scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.




#### Body parameters

- **`pattern_config_version`** (string or null)
  The version of the entity. This is used to confirm you're updating the current version of the entity and mitigate unintentionally overriding someone else's update.

- **`provider_pattern_settings`** (array of objects)
  Pattern settings for provider patterns.
  - **`token_type`** (string)
    The ID of the pattern to configure.
  - **`push_protection_setting`** (string)
    Push protection setting to set for the pattern.
    Can be one of: `not-set`, `disabled`, `enabled`

- **`custom_pattern_settings`** (array of objects)
  Pattern settings for custom patterns.
  - **`token_type`** (string)
    The ID of the pattern to configure.
  - **`custom_pattern_version`** (string or null)
    The version of the entity. This is used to confirm you're updating the current version of the entity and mitigate unintentionally overriding someone else's update.
  - **`push_protection_setting`** (string)
    Push protection setting to set for the pattern.
    Can be one of: `disabled`, `enabled`





### HTTP response status codes


- **200** - OK


- **400** - Bad Request


- **403** - Forbidden


- **404** - Resource not found


- **409** - Conflict


- **422** - Validation failed, or the endpoint has been spammed.




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/secret-scanning/pattern-configurations \
  -d '{
  "pattern_config_version": "0ujsswThIGTUYm2K8FjOOfXtY1K",
  "provider_pattern_settings": [
    {
      "token_type": "GITHUB_PERSONAL_ACCESS_TOKEN",
      "push_protection_setting": "enabled"
    }
  ],
  "custom_pattern_settings": [
    {
      "token_type": "cp_2",
      "custom_pattern_version": "0ujsswThIGTUYm2K8FjOOfXtY1K",
      "push_protection_setting": "enabled"
    }
  ]
}'
```

**Response schema (Status: 200):**

* `pattern_config_version`: string