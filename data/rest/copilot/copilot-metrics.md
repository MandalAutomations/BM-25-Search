# REST API endpoints for Copilot metrics

Use the REST API to view Copilot metrics.

>[!WARNING]
> These Copilot metrics endpoints were closed down on April 2, 2026. Use the **Copilot usage metrics** endpoints instead, which provide more depth and flexibility. For more details, see [the GitHub Blog](https://github.blog/changelog/2026-01-29-closing-down-notice-of-legacy-copilot-metrics-apis/).

You can use these endpoints to get a breakdown of aggregated metrics for various GitHub Copilot features. The API includes:

* Data for the last 100 days
* Numbers of active users and engaged users
* Breakdowns by language and IDE
* The option to view metrics for an enterprise, organization, or team

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get Copilot metrics for an organization

```
GET /orgs/{org}/copilot/metrics
```

Use this endpoint to see a breakdown of aggregated metrics for various GitHub Copilot features. See the response schema tab for detailed metrics definitions.
Note

This endpoint will only return results for a given day if the organization contained five or more members with active Copilot licenses on that day, as evaluated at the end of that day.

The response contains metrics for up to 100 days prior. Metrics are processed once per day for the previous day,
and the response will only include data up until yesterday. In order for an end user to be counted towards these metrics,
they must have telemetry enabled in their IDE.
To access this endpoint, the Copilot Metrics API access policy must be enabled for the organization.
Only organization owners and owners and billing managers of the parent enterprise can view Copilot metrics.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot, read:org, or read:enterprise scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`since`** (string)
  Show usage metrics since this date. This is a timestamp in ISO 8601 format (YYYY-MM-DDTHH:MM:SSZ). Maximum value is 100 days ago.

- **`until`** (string)
  Show usage metrics until this date. This is a timestamp in ISO 8601 format (YYYY-MM-DDTHH:MM:SSZ) and should not preceed the since date if it is passed.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of days of metrics to display per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `100`






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Copilot Usage Metrics API setting is disabled at the organization or enterprise level.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/metrics
```

**Response schema (Status: 200):**

Array of `Copilot Usage Metrics`:
  * `date`: required, string, format: date
  * `total_active_users`: integer
  * `total_engaged_users`: integer
  * `copilot_ide_code_completions`: object or null, additional properties allowed:
    * `total_engaged_users`: integer
    * `languages`: array of objects:
      * `name`: string
      * `total_engaged_users`: integer
    * `editors`: array of objects:
      * `name`: string
      * `total_engaged_users`: integer
      * `models`: array of objects:
        * `name`: string
        * `is_custom_model`: boolean
        * `custom_model_training_date`: string or null
        * `total_engaged_users`: integer
        * `languages`: array of object
  * `copilot_ide_chat`: object or null, additional properties allowed:
    * `total_engaged_users`: integer
    * `editors`: array of objects:
      * `name`: string
      * `total_engaged_users`: integer
      * `models`: array of objects:
        * `name`: string
        * `is_custom_model`: boolean
        * `custom_model_training_date`: string or null
        * `total_engaged_users`: integer
        * `total_chats`: integer
        * `total_chat_insertion_events`: integer
        * `total_chat_copy_events`: integer
  * `copilot_dotcom_chat`: object or null, additional properties allowed:
    * `total_engaged_users`: integer
    * `models`: array of objects:
      * `name`: string
      * `is_custom_model`: boolean
      * `custom_model_training_date`: string or null
      * `total_engaged_users`: integer
      * `total_chats`: integer
  * `copilot_dotcom_pull_requests`: object or null, additional properties allowed:
    * `total_engaged_users`: integer
    * `repositories`: array of objects:
      * `name`: string
      * `total_engaged_users`: integer
      * `models`: array of objects:
        * `name`: string
        * `is_custom_model`: boolean
        * `custom_model_training_date`: string or null
        * `total_pr_summaries_created`: integer
        * `total_engaged_users`: integer





## Get Copilot metrics for a team

```
GET /orgs/{org}/team/{team_slug}/copilot/metrics
```

Use this endpoint to see a breakdown of aggregated metrics for various GitHub Copilot features. See the response schema tab for detailed metrics definitions.
Note

This endpoint will only return results for a given day if the team had five or more members with active Copilot licenses on that day, as evaluated at the end of that day.

The response contains metrics for up to 100 days prior. Metrics are processed once per day for the previous day,
and the response will only include data up until yesterday. In order for an end user to be counted towards these metrics,
they must have telemetry enabled in their IDE.
To access this endpoint, the Copilot Metrics API access policy must be enabled for the organization containing the team within GitHub settings.
Only organization owners for the organization that contains this team and owners and billing managers of the parent enterprise can view Copilot metrics for a team.
OAuth app tokens and personal access tokens (classic) need either the manage_billing:copilot, read:org, or read:enterprise scopes to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`team_slug`** (string) (required)
  The slug of the team name.

- **`since`** (string)
  Show usage metrics since this date. This is a timestamp in ISO 8601 format (YYYY-MM-DDTHH:MM:SSZ). Maximum value is 100 days ago.

- **`until`** (string)
  Show usage metrics until this date. This is a timestamp in ISO 8601 format (YYYY-MM-DDTHH:MM:SSZ) and should not preceed the since date if it is passed.

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of days of metrics to display per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `100`






### HTTP response status codes


- **200** - OK


- **403** - Forbidden


- **404** - Resource not found


- **422** - Copilot Usage Metrics API setting is disabled at the organization or enterprise level.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/team/TEAM_SLUG/copilot/metrics
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot metrics for an organization](#get-copilot-metrics-for-an-organization).