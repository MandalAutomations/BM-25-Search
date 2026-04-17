# REST API endpoints for meta data

Use the REST API to get meta information about GitHub, including the IP addresses of GitHub services.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## GitHub API Root

```
GET /
```

Get Hypermedia links to resources accessible in GitHub's REST API



### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/
```

**Response schema (Status: 200):**

* `current_user_url`: required, string, format: uri-template
* `current_user_authorizations_html_url`: required, string, format: uri-template
* `code_search_url`: required, string, format: uri-template
* `commit_search_url`: required, string, format: uri-template
* `emails_url`: required, string, format: uri-template
* `emojis_url`: required, string, format: uri-template
* `events_url`: required, string, format: uri-template
* `feeds_url`: required, string, format: uri-template
* `followers_url`: required, string, format: uri-template
* `following_url`: required, string, format: uri-template
* `gists_url`: required, string, format: uri-template
* `issue_search_url`: required, string, format: uri-template
* `issues_url`: required, string, format: uri-template
* `keys_url`: required, string, format: uri-template
* `label_search_url`: required, string, format: uri-template
* `notifications_url`: required, string, format: uri-template
* `organization_url`: required, string, format: uri-template
* `organization_repositories_url`: required, string, format: uri-template
* `organization_teams_url`: required, string, format: uri-template
* `public_gists_url`: required, string, format: uri-template
* `rate_limit_url`: required, string, format: uri-template
* `repository_url`: required, string, format: uri-template
* `repository_search_url`: required, string, format: uri-template
* `current_user_repositories_url`: required, string, format: uri-template
* `starred_url`: required, string, format: uri-template
* `starred_gists_url`: required, string, format: uri-template
* `topic_search_url`: string, format: uri-template
* `user_url`: required, string, format: uri-template
* `user_organizations_url`: required, string, format: uri-template
* `user_repositories_url`: required, string, format: uri-template
* `user_search_url`: required, string, format: uri-template





## Get GitHub meta information

```
GET /meta
```

Returns meta information about GitHub, including a list of GitHub's IP addresses. For more information, see "About GitHub's IP addresses."
The API's response also includes a list of GitHub's domain names.
The values shown in the documentation's response are example values. You must always query the API directly to get the latest values.
Note

This endpoint returns both IPv4 and IPv6 addresses. However, not all features support IPv6. You should refer to the specific documentation for each feature to determine if IPv6 is supported.



### HTTP response status codes


- **200** - OK


- **304** - Not modified




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/meta
```

**Response schema (Status: 200):**

* `verifiable_password_authentication`: required, boolean
* `ssh_key_fingerprints`: object:
  * `SHA256_RSA`: string
  * `SHA256_DSA`: string
  * `SHA256_ECDSA`: string
  * `SHA256_ED25519`: string
* `ssh_keys`: array of string
* `hooks`: array of string
* `github_enterprise_importer`: array of string
* `web`: array of string
* `api`: array of string
* `git`: array of string
* `packages`: array of string
* `pages`: array of string
* `importer`: array of string
* `actions`: array of string
* `actions_macos`: array of string
* `codespaces`: array of string
* `dependabot`: array of string
* `copilot`: array of string
* `domains`: object:
  * `website`: array of string
  * `codespaces`: array of string
  * `copilot`: array of string
  * `packages`: array of string
  * `actions`: array of string
  * `actions_inbound`: object:
    * `full_domains`: array of string
    * `wildcard_domains`: array of string
  * `artifact_attestations`: object:
    * `trust_domain`: string
    * `services`: array of string





## Get Octocat

```
GET /octocat
```

Get the octocat as ASCII art


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`s`** (string)
  The words to show in Octocat's speech bubble






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/octocat
```

**Response schema (Status: 200):**

string





## Get all API versions

```
GET /versions
```

Get all supported GitHub API versions.



### HTTP response status codes


- **200** - OK


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/versions
```

**Response schema (Status: 200):**

Array of string, format: date





## Get the Zen of GitHub

```
GET /zen
```

Get a random sentence from the Zen of GitHub



### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/zen
```

**Response schema (Status: 200):**

Same response schema as [Get Octocat](#get-octocat).