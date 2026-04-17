# REST API endpoints for licenses

Use the REST API to retrieve popular open source licenses and information about a particular project's license file.

## About licenses

GitHub uses [the open source Ruby Gem Licensee](https://github.com/benbalter/licensee) to attempt to identify the license for a project. Licensee matches the contents of a project's `LICENSE` file (if it exists) against a short list of known licenses. As a result, the API does not take into account the licenses of project dependencies or other means of documenting a project's license such as references to the license name in the documentation.

If a license is matched, the license key and name returned conforms to the [SPDX specification](https://spdx.org/).

**Note:** These endpoints will also return a repository's license information:

* [Get a repository](/en/rest/repos/repos#get-a-repository)
* [List repositories for a user](/en/rest/repos/repos#list-repositories-for-a-user)
* [List organization repositories](/en/rest/repos/repos#list-organization-repositories)
* [List forks](/en/rest/repos/forks#list-forks)
* [List repositories watched by a user](/en/rest/activity/watching#list-repositories-watched-by-a-user)
* [List team repositories](/en/rest/teams/teams#list-team-repositories)

> \[!WARNING]
> GitHub is a lot of things, but it’s not a law firm. As such, GitHub does not provide legal advice. Using the API or sending us an email about it does not constitute legal advice nor does it create an attorney-client relationship. If you have any questions about what you can and can't do with a particular license, you should consult with your own legal counsel before moving forward. In fact, you should always consult with your own lawyer before making any decisions that might have legal ramifications or that may impact your legal rights.
>
> GitHub created these endpoints to help users get information about open source licenses and the projects that use them. We hope it helps, but please keep in mind that we’re not lawyers (at least most of us aren't) and that we make mistakes like everyone else. For that reason, GitHub provides the API on an "as-is" basis and makes no warranties regarding any information or licenses provided on or through it, and disclaims liability for damages resulting from using the API.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get all commonly used licenses

```
GET /licenses
```

Lists the most commonly used licenses on GitHub. For more information, see "Licensing a repository ."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`featured`** (boolean)

* **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

* **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

### HTTP response status codes

* **200** - OK

* **304** - Not modified

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/licenses
```

**Response schema (Status: 200):**

Array of `License Simple`:

* `key`: required, string
* `name`: required, string
* `url`: required, string or null, format: uri
* `spdx_id`: required, string or null
* `node_id`: required, string
* `html_url`: string, format: uri

## Get a license

```
GET /licenses/{license}
```

Gets information about a specific license. For more information, see "Licensing a repository ."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`license`** (string) (required)

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/licenses/LICENSE
```

**Response schema (Status: 200):**

* `key`: required, string
* `name`: required, string
* `spdx_id`: required, string or null
* `url`: required, string or null, format: uri
* `node_id`: required, string
* `html_url`: required, string, format: uri
* `description`: required, string
* `implementation`: required, string
* `permissions`: required, array of string
* `conditions`: required, array of string
* `limitations`: required, array of string
* `body`: required, string
* `featured`: required, boolean

## Get the license for a repository

```
GET /repos/{owner}/{repo}/license
```

This method returns the contents of the repository's license file, if one is detected.
This endpoint supports the following custom media types. For more information, see "Media types."

application/vnd.github.raw+json: Returns the raw contents of the license.
application/vnd.github.html+json: Returns the license contents in HTML. Markup languages are rendered to HTML using GitHub's open-source Markup library.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`ref`** (string)
  The Git reference for the results you want to list. The ref for a branch can be formatted either as refs/heads/<branch name> or simply <branch name>. To reference a pull request use refs/pull/<number>/merge.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/license
```

**Response schema (Status: 200):**

* `name`: required, string
* `path`: required, string
* `sha`: required, string
* `size`: required, integer
* `url`: required, string, format: uri
* `html_url`: required, string or null, format: uri
* `git_url`: required, string or null, format: uri
* `download_url`: required, string or null, format: uri
* `type`: required, string
* `content`: required, string
* `encoding`: required, string
* `_links`: required, object:
  * `git`: required, string or null, format: uri
  * `html`: required, string or null, format: uri
  * `self`: required, string, format: uri
* `license`: required, any of:
  * **null**
  * **License Simple**
    * `key`: required, string
    * `name`: required, string
    * `url`: required, string or null, format: uri
    * `spdx_id`: required, string or null
    * `node_id`: required, string
    * `html_url`: string, format: uri