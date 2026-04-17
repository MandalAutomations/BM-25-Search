# REST API endpoints for models catalog

Use the REST API to get a list of models available for use, including details like ID, supported input/output modalities, and rate limits.

## About GitHub Models catalog

You can use the REST API to explore available models in the GitHub Models catalog.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List all models

```
GET /catalog/models
```

Get a list of models available for use, including details like supported input/output modalities,
publisher, and rate limits.



### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://models.github.ai/catalog/models
```

**Response schema (Status: 200):**

Array of objects:
  * `id`: string
  * `name`: string
  * `registry`: string
  * `publisher`: string
  * `summary`: string
  * `rate_limit_tier`: string
  * `html_url`: string
  * `version`: string
  * `capabilities`: array of string
  * `limits`: object:
    * `max_input_tokens`: integer
    * `max_output_tokens`: integer
  * `tags`: array of string
  * `supported_input_modalities`: array of string
  * `supported_output_modalities`: array of string