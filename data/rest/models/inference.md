# REST API endpoints for models inference

Use the REST API to submit a chat completion request to a specified model, with or without organizational attribution.

## About GitHub Models inference

You can use the REST API to run inference requests using the GitHub Models platform. The API requires the `models: read` scope when using a fine-grained personal access token or when authenticating using a GitHub App.

The API supports:

* Accessing top models from OpenAI, DeepSeek, Microsoft, Llama, and more.
* Running chat-based inference requests with full control over sampling and response parameters.
* Streaming or non-streaming completions.
* Organizational attribution and usage tracking.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Run an inference request attributed to an organization

```
POST /orgs/{org}/inference/chat/completions
```

This endpoint allows you to run an inference request attributed to a specific organization. You must be a member of the organization and have enabled models to use this endpoint.
The token used to authenticate must have the models: read permission if using a fine-grained PAT or GitHub App minted token.
The request body should contain the model ID and the messages for the chat completion request. The response will include either a non-streaming or streaming response based on the request parameters.


### Parameters


#### Headers


- **`content-type`** (string, required)
  Setting to `application/json` is required.


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`api-version`** (string)
  The API version to use. Optional, but required for some features.

- **`org`** (string) (required)
  The organization login associated with the organization to which the request is to be attributed.




#### Body parameters

- **`model`** (string) (required)
  ID of the specific model to use for the request. The model ID should be in the format of {publisher}/{model_name} where "openai/gpt-4.1" is an example of a model ID. You can find supported models in the catalog/models endpoint.

- **`messages`** (array of objects) (required)
  The collection of context messages associated with this chat completion request. Typical usage begins with a chat message for the System role that provides instructions for the behavior of the assistant, followed by alternating messages between the User and Assistant roles.
  - **`role`** (string) (required)
    The chat role associated with this message
    Can be one of: `assistant`, `developer`, `system`, `user`
  - **`content`** (string) (required)
    The content of the message

- **`frequency_penalty`** (number)
  A value that influences the probability of generated tokens appearing based on their cumulative frequency in generated text. Positive values will make tokens less likely to appear as their frequency increases and decrease the likelihood of the model repeating the same statements verbatim. Supported range is [-2, 2].

- **`max_tokens`** (integer)
  The maximum number of tokens to generate in the completion. The token count of your prompt plus max_tokens cannot exceed the model's context length. For example, if your prompt is 100 tokens and you set max_tokens to 50, the API will return a completion with a maximum of 50 tokens.

- **`modalities`** (array of strings)
  The modalities that the model is allowed to use for the chat completions response. The default modality is text. Indicating an unsupported modality combination results in a 422 error.
Supported values are: text, audio

- **`presence_penalty`** (number)
  A value that influences the probability of generated tokens appearing based on their existing presence in generated text. Positive values will make tokens less likely to appear when they already exist and increase the model's likelihood to output new tokens. Supported range is [-2, 2].

- **`response_format`** (object)
  The desired format for the response.
  - **`Object`** (object)
    - **`type`** (string)
      Can be one of: `text`, `json_object`
  - **`Schema for structured JSON response`** (object)
    - **`type`** (string) (required)
      The type of the response.
      Can be one of: `json_schema`
    - **`json_schema`** (object) (required)
      The JSON schema for the response.

- **`seed`** (integer)
  If specified, the system will make a best effort to sample deterministically such that repeated requests with the same seed and parameters should return the same result. Determinism is not guaranteed.

- **`stream`** (boolean)
  A value indicating whether chat completions should be streamed for this request.
  Default: `false`

- **`stream_options`** (object)
  Whether to include usage information in the response. Requires stream to be set to true.
  - **`include_usage`** (boolean)
    Whether to include usage information in the response.
    Default: `false`

- **`stop`** (array of strings)
  A collection of textual sequences that will end completion generation.

- **`temperature`** (number)
  The sampling temperature to use that controls the apparent creativity of generated completions. Higher values will make output more random while lower values will make results more focused and deterministic. It is not recommended to modify temperature and top_p for the same completion request as the interaction of these two settings is difficult to predict. Supported range is [0, 1]. Decimal values are supported.

- **`tool_choice`** (string)
  If specified, the model will configure which of the provided tools it can use for the chat completions response.
  Can be one of: `auto`, `required`, `none`

- **`tools`** (array of objects)
  A list of tools the model may request to call. Currently, only functions are supported as a tool. The model may respond with a function call request and provide the input arguments in JSON format for that function.
  - **`function`** (object)
    - **`name`** (string)
      The name of the function to be called.
    - **`description`** (string)
      A description of what the function does. The model will use this description when selecting the function and interpreting its parameters.
    - **`parameters`** (string)
      The parameters the function accepts, described as a JSON Schema object.
  - **`type`** (string)
    Can be one of: `function`

- **`top_p`** (number)
  An alternative to sampling with temperature called nucleus sampling. This value causes the model to consider the results of tokens with the provided probability mass. As an example, a value of 0.15 will cause only the tokens comprising the top 15% of probability mass to be considered. It is not recommended to modify temperature and top_p for the same request as the interaction of these two settings is difficult to predict. Supported range is [0, 1]. Decimal values are supported.





### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://models.github.ai/orgs/ORG/inference/chat/completions \
  -d '{
  "model": "openai/gpt-4.1",
  "messages": [
    {
      "role": "user",
      "content": "What is the capital of France?"
    }
  ]
}'
```

**Response schema (Status: 200):**

* one of:
  * **Non Streaming Response**
    * `choices`: array of objects:
      * `message`: object:
        * `content`: string
        * `role`: string
  * **Streaming Response**
    * `data`: object:
      * `choices`: array of objects:
        * `delta`: object:
          * `content`: string





## Run an inference request

```
POST /inference/chat/completions
```

This endpoint allows you to run an inference request. The token used to authenticate must have the models: read permission if using a fine-grained PAT or GitHub App minted token.
The request body should contain the model ID and
the messages for the chat completion request. The response will include either a non-streaming or streaming response based on the request parameters.


### Parameters


#### Headers


- **`content-type`** (string, required)
  Setting to `application/json` is required.


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`api-version`** (string)
  The API version to use. Optional, but required for some features.




#### Body parameters

- **`model`** (string) (required)
  ID of the specific model to use for the request. The model ID should be in the format of {publisher}/{model_name} where "openai/gpt-4.1" is an example of a model ID. You can find supported models in the catalog/models endpoint.

- **`messages`** (array of objects) (required)
  The collection of context messages associated with this chat completion request. Typical usage begins with a chat message for the System role that provides instructions for the behavior of the assistant, followed by alternating messages between the User and Assistant roles.
  - **`role`** (string) (required)
    The chat role associated with this message
    Can be one of: `assistant`, `developer`, `system`, `user`
  - **`content`** (string) (required)
    The content of the message

- **`frequency_penalty`** (number)
  A value that influences the probability of generated tokens appearing based on their cumulative frequency in generated text. Positive values will make tokens less likely to appear as their frequency increases and decrease the likelihood of the model repeating the same statements verbatim. Supported range is [-2, 2].

- **`max_tokens`** (integer)
  The maximum number of tokens to generate in the completion. The token count of your prompt plus max_tokens cannot exceed the model's context length. For example, if your prompt is 100 tokens and you set max_tokens to 50, the API will return a completion with a maximum of 50 tokens.

- **`modalities`** (array of strings)
  The modalities that the model is allowed to use for the chat completions response. The default modality is text. Indicating an unsupported modality combination results in a 422 error.
Supported values are: text, audio

- **`presence_penalty`** (number)
  A value that influences the probability of generated tokens appearing based on their existing presence in generated text. Positive values will make tokens less likely to appear when they already exist and increase the model's likelihood to output new tokens. Supported range is [-2, 2].

- **`response_format`** (object)
  The desired format for the response.
  - **`Object`** (object)
    - **`type`** (string)
      Can be one of: `text`, `json_object`
  - **`Schema for structured JSON response`** (object)
    - **`type`** (string) (required)
      The type of the response.
      Can be one of: `json_schema`
    - **`json_schema`** (object) (required)
      The JSON schema for the response.

- **`seed`** (integer)
  If specified, the system will make a best effort to sample deterministically such that repeated requests with the same seed and parameters should return the same result. Determinism is not guaranteed.

- **`stream`** (boolean)
  A value indicating whether chat completions should be streamed for this request.
  Default: `false`

- **`stream_options`** (object)
  Whether to include usage information in the response. Requires stream to be set to true.
  - **`include_usage`** (boolean)
    Whether to include usage information in the response.
    Default: `false`

- **`stop`** (array of strings)
  A collection of textual sequences that will end completion generation.

- **`temperature`** (number)
  The sampling temperature to use that controls the apparent creativity of generated completions. Higher values will make output more random while lower values will make results more focused and deterministic. It is not recommended to modify temperature and top_p for the same completion request as the interaction of these two settings is difficult to predict. Supported range is [0, 1]. Decimal values are supported.

- **`tool_choice`** (string)
  If specified, the model will configure which of the provided tools it can use for the chat completions response.
  Can be one of: `auto`, `required`, `none`

- **`tools`** (array of objects)
  A list of tools the model may request to call. Currently, only functions are supported as a tool. The model may respond with a function call request and provide the input arguments in JSON format for that function.
  - **`function`** (object)
    - **`name`** (string)
      The name of the function to be called.
    - **`description`** (string)
      A description of what the function does. The model will use this description when selecting the function and interpreting its parameters.
    - **`parameters`** (string)
      The parameters the function accepts, described as a JSON Schema object.
  - **`type`** (string)
    Can be one of: `function`

- **`top_p`** (number)
  An alternative to sampling with temperature called nucleus sampling. This value causes the model to consider the results of tokens with the provided probability mass. As an example, a value of 0.15 will cause only the tokens comprising the top 15% of probability mass to be considered. It is not recommended to modify temperature and top_p for the same request as the interaction of these two settings is difficult to predict. Supported range is [0, 1]. Decimal values are supported.





### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://models.github.ai/inference/chat/completions \
  -d '{
  "model": "openai/gpt-4.1",
  "messages": [
    {
      "role": "user",
      "content": "What is the capital of France?"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Run an inference request attributed to an organization](#run-an-inference-request-attributed-to-an-organization).