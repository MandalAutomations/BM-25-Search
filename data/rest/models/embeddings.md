# REST API endpoints for model embeddings

Use the REST API to work with embedding requests for models.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Run an embedding request attributed to an organization

```
POST /orgs/{org}/inference/embeddings
```

This endpoint allows you to run an embedding request attributed to a specific organization. You must be a member of the organization and have enabled models to use this endpoint.
The token used to authenticate must have the models: read permission if using a fine-grained PAT or GitHub App minted token.
The request body should contain the model ID and the input text(s) for the embedding request. The response will include the generated embeddings.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`api-version`** (string)
  The API version to use. Optional, but required for some features.

- **`org`** (string) (required)
  The organization login associated with the organization to which the request is to be attributed.




#### Body parameters

- **`model`** (string) (required)
  ID of the specific model to use for the request. The model ID should be in the format of {publisher}/{model_name} where "openai/text-embedding-3-small" is an example of a model ID. You can find supported models in the catalog/models endpoint.

- **`input`** (string or array) (required)
  Input text to embed, encoded as a string or array of strings. To embed multiple inputs in a single request, pass an array of strings. Each input must not exceed the max input tokens for the model, cannot be an empty string, and any array must be 2048 dimensions or less.

- **`encoding_format`** (string)
  The format to return the embeddings in. Can be either float or base64.
  Default: `float`
  Can be one of: `float`, `base64`

- **`dimensions`** (integer)
  The number of dimensions the resulting output embeddings should have. Only supported in text-embedding-3 and later models.

- **`user`** (string)
  A unique identifier representing your end-user, which can help us to monitor and detect abuse.





### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://models.github.ai/orgs/ORG/inference/embeddings \
  -d '{
  "model": "openai/text-embedding-3-small",
  "input": [
    "The food was delicious and the waiter was very friendly.",
    "I had a great time at the restaurant."
  ]
}'
```

**Response schema (Status: 200):**

* `object`: required, string, enum: `list`
* `data`: required, array of `Embedding Object`:
  * `object`: required, string, enum: `embedding`
  * `index`: required, integer
  * `embedding`: required, array of number
* `model`: required, string
* `usage`: required, object:
  * `prompt_tokens`: required, integer
  * `total_tokens`: required, integer





## Run an embedding request

```
POST /inference/embeddings
```

This endpoint allows you to run an embedding request. The token used to authenticate must have the models: read permission if using a fine-grained PAT or GitHub App minted token.
The request body should contain the model ID and the input text(s) for the embedding request. The response will include the generated embeddings.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`api-version`** (string)
  The API version to use. Optional, but required for some features.




#### Body parameters

- **`model`** (string) (required)
  ID of the specific model to use for the request. The model ID should be in the format of {publisher}/{model_name} where "openai/text-embedding-3-small" is an example of a model ID. You can find supported models in the catalog/models endpoint.

- **`input`** (string or array) (required)
  Input text to embed, encoded as a string or array of strings. To embed multiple inputs in a single request, pass an array of strings. Each input must not exceed the max input tokens for the model, cannot be an empty string, and any array must be 2048 dimensions or less.

- **`encoding_format`** (string)
  The format to return the embeddings in. Can be either float or base64.
  Default: `float`
  Can be one of: `float`, `base64`

- **`dimensions`** (integer)
  The number of dimensions the resulting output embeddings should have. Only supported in text-embedding-3 and later models.

- **`user`** (string)
  A unique identifier representing your end-user, which can help us to monitor and detect abuse.





### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://models.github.ai/inference/embeddings \
  -d '{
  "model": "openai/text-embedding-3-small",
  "input": [
    "The food was delicious and the waiter was very friendly.",
    "I had a great time at the restaurant."
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Run an embedding request attributed to an organization](#run-an-embedding-request-attributed-to-an-organization).