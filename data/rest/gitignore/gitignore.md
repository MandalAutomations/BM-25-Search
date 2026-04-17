# REST API endpoints for gitignore

Use the REST API to get .gitignore templates that can be used to ignore files and directories.

## About gitignore

When you create a new repository on GitHub via the API, you can specify a [.gitignore template](/en/get-started/git-basics/ignoring-files) to apply to the repository upon creation. You can use the REST API to get .gitignore templates from the GitHub [.gitignore repository](https://github.com/github/gitignore).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get all gitignore templates

```
GET /gitignore/templates
```

List all templates available to pass as an option when creating a repository.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gitignore/templates
```

**Response schema (Status: 200):**

Array of string

## Get a gitignore template

```
GET /gitignore/templates/{name}
```

Get the content of a gitignore template.
This endpoint supports the following custom media types. For more information, see "Media types."

application/vnd.github.raw+json: Returns the raw .gitignore contents.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`name`** (string) (required)

### HTTP response status codes

* **200** - OK

* **304** - Not modified

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/gitignore/templates/NAME
```

**Response schema (Status: 200):**

* `name`: required, string
* `source`: required, string