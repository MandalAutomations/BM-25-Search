# REST API endpoints for community metrics

Use the REST API to retrieve information about your community profile.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get community profile metrics

```
GET /repos/{owner}/{repo}/community/profile
```

Returns all community profile metrics for a repository. The repository cannot be a fork.
The returned metrics include an overall health score, the repository description, the presence of documentation, the
detected code of conduct, the detected license, and the presence of ISSUE_TEMPLATE, PULL_REQUEST_TEMPLATE,
README, and CONTRIBUTING files.
The health_percentage score is defined as a percentage of how many of
the recommended community health files are present. For more information, see
"About community profiles for public repositories."
content_reports_enabled is only returned for organization-owned repositories.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/community/profile
```

**Response schema (Status: 200):**

* `health_percentage`: required, integer
* `description`: required, string or null
* `documentation`: required, string or null
* `files`: required, object:
  * `code_of_conduct`: required, any of:
    * **null**
    * **Code Of Conduct Simple**
      * `url`: required, string, format: uri
      * `key`: required, string
      * `name`: required, string
      * `html_url`: required, string or null, format: uri
  * `code_of_conduct_file`: required, any of:
    * **null**
    * **Community Health File**
      * `url`: required, string, format: uri
      * `html_url`: required, string, format: uri
  * `license`: required, any of:
    * **null**
    * **License Simple**
      * `key`: required, string
      * `name`: required, string
      * `url`: required, string or null, format: uri
      * `spdx_id`: required, string or null
      * `node_id`: required, string
      * `html_url`: string, format: uri
  * `contributing`: required, any of:
    * **null**
    * **Community Health File**
      * `url`: required, string, format: uri
      * `html_url`: required, string, format: uri
  * `readme`: required, any of:
    * **null**
    * **Community Health File**
      * `url`: required, string, format: uri
      * `html_url`: required, string, format: uri
  * `issue_template`: required, any of:
    * **null**
    * **Community Health File**
      * `url`: required, string, format: uri
      * `html_url`: required, string, format: uri
  * `pull_request_template`: required, any of:
    * **null**
    * **Community Health File**
      * `url`: required, string, format: uri
      * `html_url`: required, string, format: uri
* `updated_at`: required, string or null, format: date-time
* `content_reports_enabled`: boolean