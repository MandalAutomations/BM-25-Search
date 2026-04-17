# REST API endpoints for Markdown

Use the REST API to render a markdown document as an HTML page or as raw text.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Render a Markdown document

```
POST /markdown
```

Depending on what is rendered in the Markdown, you may need to provide additional token scopes for labels, such as issues:read or pull_requests:read.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.





#### Body parameters

- **`text`** (string) (required)
  The Markdown text to render in HTML.

- **`mode`** (string)
  The rendering mode.
  Default: `markdown`
  Can be one of: `markdown`, `gfm`

- **`context`** (string)
  The repository context to use when creating references in gfm mode.  For example, setting context to octo-org/octo-repo will change the text #42 into an HTML link to issue 42 in the octo-org/octo-repo repository.





### HTTP response status codes


- **200** - OK


- **304** - Not modified




### Code examples



#### Rendering markdown

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/markdown \
  -d '{
  "text": "Hello **world**"
}'
```

**Response schema (Status: 200):**

string





## Render a Markdown document in raw mode

```
POST /markdown/raw
```

You must send Markdown as plain text (using a Content-Type header of text/plain or text/x-markdown) to this endpoint, rather than using JSON format. In raw mode, GitHub Flavored Markdown is not supported and Markdown will be rendered in plain format like a README.md file. Markdown content must be 400 KB or less.



### HTTP response status codes


- **200** - OK


- **304** - Not modified




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/markdown/raw \
  -d '{
  "text": "Hello **world**"
}'
```

**Response schema (Status: 200):**

Same response schema as [Render a Markdown document](#render-a-markdown-document).



#### Rendering markdown

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/markdown/raw \
  -d '{
  "text": "Hello **world**"
}'
```

**Response schema (Status: 200):**

Same response schema as [Render a Markdown document](#render-a-markdown-document).